package estructura;

import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;
import java.util.ArrayList;
import java.util.Scanner;

class Paciente {
    int id;
    String nombre;

    public Paciente(int id, String nombre) {
        this.id = id;
        this.nombre = nombre;
    }

    @Override
    public String toString() {
        return "ID: " + id + ", Nombre: " + nombre;
    }
}

class CitaNode {
    LocalDateTime fechaHora;
    CitaNode izquierda, derecha;
    String paciente;

    public CitaNode(LocalDateTime fechaHora, String paciente) {
        this.fechaHora = fechaHora;
        this.paciente = paciente;
    }
}

class ArbolCitas {
    private CitaNode raiz;
    private final DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyyMMddHHmm");

    public void insertarCita(String fechaHoraStr, String paciente) {
        LocalDateTime fechaHora = LocalDateTime.parse(fechaHoraStr, formatter);
        raiz = insertar(raiz, fechaHora, paciente);
    }

    private CitaNode insertar(CitaNode nodo, LocalDateTime fechaHora, String paciente) {
        if (nodo == null) {
            return new CitaNode(fechaHora, paciente);
        }
        if (fechaHora.isBefore(nodo.fechaHora)) {
            nodo.izquierda = insertar(nodo.izquierda, fechaHora, paciente);
        } else if (fechaHora.isAfter(nodo.fechaHora)) {
            nodo.derecha = insertar(nodo.derecha, fechaHora, paciente);
        } else {
            System.out.println("¡Conflicto de horario! Ya existe una cita a esta hora.");
        }
        return nodo;
    }

    public CitaNode seleccionarK(int k) {
        return seleccionarK(raiz, k);
    }

    private CitaNode seleccionarK(CitaNode nodo, int k) {
        if (nodo == null) {
            return null;
        }

        int tamañoIzquierda = tamañoSubarbol(nodo.izquierda);

        if (tamañoIzquierda + 1 == k) {
            return nodo;
        } else if (k <= tamañoIzquierda) {
            return seleccionarK(nodo.izquierda, k);
        } else {
            return seleccionarK(nodo.derecha, k - tamañoIzquierda - 1);
        }
    }

    private int tamañoSubarbol(CitaNode nodo) {
        if (nodo == null) {
            return 0;
        }
        return 1 + tamañoSubarbol(nodo.izquierda) + tamañoSubarbol(nodo.derecha);
    }
}

public class Citas {
    static ArrayList<Paciente> pacientes = new ArrayList<>();
    static ArbolCitas arbolCitas = new ArbolCitas();

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int opcion;

        do {
            System.out.println("--- Sistema de Citas ---");
            System.out.println("1. Añadir un Paciente");
            System.out.println("2. Agendar Cita");
            System.out.println("3. Mostrar Pacientes (Bubble Sort)");
            System.out.println("4. Ordenar Pacientes (Selection Sort)");
            System.out.println("5. Seleccionar k-ésima Cita en Árbol Binario");
            System.out.println("6. Salir");
            System.out.print("Seleccione una opción: ");
            opcion = sc.nextInt();
            sc.nextLine(); // Consumir salto de línea

            switch (opcion) {
                case 1:
                    System.out.print("Ingrese ID del paciente: ");
                    int id = sc.nextInt();
                    sc.nextLine();
                    System.out.print("Ingrese nombre del paciente: ");
                    String nombre = sc.nextLine();
                    pacientes.add(new Paciente(id, nombre));
                    System.out.println("Paciente añadido con éxito.");
                    break;

                case 2:
                    System.out.print("Ingrese fecha y hora (yyyyMMddHHmm): ");
                    String fechaHora = sc.nextLine();
                    System.out.print("Ingrese nombre del paciente: ");
                    String pacienteCita = sc.nextLine();
                    arbolCitas.insertarCita(fechaHora, pacienteCita);
                    System.out.println("Cita añadida con éxito.");
                    break;

                case 3:
                    bubbleSortPacientes();
                    System.out.println("--- Pacientes Ordenados (Bubble Sort) ---");
                    for (Paciente p : pacientes) {
                        System.out.println(p);
                    }
                    break;

                case 4:
                    selectionSortPacientes();
                    System.out.println("--- Pacientes Ordenados (Selection Sort) ---");
                    for (Paciente p : pacientes) {
                        System.out.println(p);
                    }
                    break;

                case 5:
                    System.out.print("Ingrese el valor de k: ");
                    int k = sc.nextInt();
                    CitaNode kthCita = arbolCitas.seleccionarK(k);
                    if (kthCita != null) {
                        System.out.println("Cita " + k + "-ésima: " +
                            kthCita.fechaHora.format(DateTimeFormatter.ofPattern("dd/MM/yyyy HH:mm")) +
                            " - Paciente: " + kthCita.paciente);
                    } else {
                        System.out.println("No se encontró la cita.");
                    }
                    break;

                case 6:
                    System.out.println("Saliendo del sistema...");
                    break;

                default:
                    System.out.println("Opción inválida. Intente de nuevo.");
            }
        } while (opcion != 6);
    }

    static void bubbleSortPacientes() {
        boolean swapped;
        do {
            swapped = false;
            for (int i = 0; i < pacientes.size() - 1; i++) {
                if (pacientes.get(i).id > pacientes.get(i + 1).id) {
                    Paciente temp = pacientes.get(i);
                    pacientes.set(i, pacientes.get(i + 1));
                    pacientes.set(i + 1, temp);
                    swapped = true;
                }
            }
        } while (swapped);
    }

    static void selectionSortPacientes() {
        for (int i = 0; i < pacientes.size() - 1; i++) {
            int minIndex = i;
            for (int j = i + 1; j < pacientes.size(); j++) {
                if (pacientes.get(j).id < pacientes.get(minIndex).id) {
                    minIndex = j;
                }
            }
            Paciente temp = pacientes.get(i);
            pacientes.set(i, pacientes.get(minIndex));
            pacientes.set(minIndex, temp);
        }
    }
}
