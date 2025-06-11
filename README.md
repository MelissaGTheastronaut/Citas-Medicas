Sistema de Gestión de Citas Médicas

Este proyecto implementa un sistema de gestión de citas médicas utilizando estructuras de datos avanzadas como árboles AVL y algoritmos de ordenamiento. Permite registrar
pacientes, agendar citas, y realizar consultas de manera eficiente. Es ideal para clínicas pequeñas o proyectos académicos relacionados con estructuras de datos.

Estructura del Proyecto

El sistema está dividido en varias clases principales:

- Paciente: Representa la información básica de un paciente, como su ID y nombre.
- CitaNode: Define los nodos utilizados en el árbol AVL para gestionar las citas.
- ArbolCitas: Implementa un árbol AVL para manejar las citas médicas, asegurando equilibrio y eficiencia.
- Citas: Contiene el punto de entrada principal (`main`) y la lógica del sistema, incluyendo las opciones del menú para interactuar con el usuario.

Características Principales

1. Gestión de Pacientes:
   - Registro de pacientes con su ID y nombre.
   - Almacenamiento en una lista y en un mapa hash para búsquedas rápidas.

2. Gestión de Citas:
   - Programación de citas con fecha y hora específicas.
   - Evita conflictos de horario usando un árbol AVL.

3. Ordenamiento de Pacientes:
   - Ordenamiento por ID utilizando algoritmos de ordenamiento como QuickSort y SelectionSort.

4. Selección de citas:
   - Acceso a la k-ésima cita en orden mediante un árbol AVL.

5. Búsqueda de Pacientes:
   - Localización rápida de pacientes por su ID utilizando un mapa hash.

Requisitos del Sistema

Para ejecutar este proyecto, necesitas lo siguiente:

1. Java Development Kit (JDK): Versión 11 o superior.
2. Entorno de desarrollo: Eclipse, IntelliJ IDEA o cualquier IDE compatible con Java.
3. Terminal o Consola: Para ejecutar el programa desde la línea de comandos.

