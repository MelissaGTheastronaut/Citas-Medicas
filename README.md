Sistema de Citas Médicas

Este proyecto es una implementación de un sistema básico de gestión de citas médicas utilizando Java. Incluye funciones para registrar pacientes, agendar citas, ordenar listas de pacientes y buscar citas específicas en un árbol binario.

Características Principales

Gestión de Pacientes: Añadir y mostrar pacientes.

Gestión de Citas: Agendar citas y evitar conflictos de horarios.

Ordenamiento de Pacientes: Utiliza Bubble Sort y Selection Sort para ordenar listas de pacientes.

Búsqueda en Árbol Binario: Selección de la k-ésima cita en un árbol binario de búsqueda.

Estructura del Código

Clases

Paciente: Representa a un paciente con atributos id y nombre.

Métodos: toString para mostrar información del paciente.

CitaNode: Nodo del árbol binario que almacena la fecha/hora de la cita y el nombre del paciente.

ArbolCitas: Árbol binario de búsqueda que administra las citas.

Métodos:

insertarCita: Inserta una nueva cita en el árbol.

seleccionarK: Busca la k-ésima cita en el árbol.

Citas: Clase principal que administra el flujo del sistema.

Métodos:

bubbleSortPacientes: Ordena pacientes por ID usando Bubble Sort.

selectionSortPacientes: Ordena pacientes por ID usando Selection Sort.

Cómo Usar

Ejecutar el programa: Corre la clase Citas para iniciar el sistema.

Opciones del menú:

1: Añadir un nuevo paciente proporcionando ID y nombre.

2: Agendar una cita ingresando la fecha/hora y el nombre del paciente.

3: Mostrar la lista de pacientes ordenada con Bubble Sort.

4: Mostrar la lista de pacientes ordenada con Selection Sort.

5: Seleccionar la k-ésima cita en el árbol binario.

6: Salir del programa.

Requisitos

Java 8 o superior.

Conocimiento básico de Java y estructuras de datos.

Rendimiento

Ordenamiento:

Bubble Sort y Selection Sort tienen una complejidad de O(n^2).

Árbol Binario:

Inserciones y búsquedas tienen un rendimiento promedio de O(log n).
