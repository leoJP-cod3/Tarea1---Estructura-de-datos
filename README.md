# Sistema de Planificación de Tareas Dinámico
## Descripción
Este sistema permite a los usuarios gestionar sus pendientes de manera organizada mediante el uso de categorías y una cola de atención. Los usuarios pueden registrar nuevas categorías, añadir tareas con descripciones detalladas (como listas de compras o recordatorios de estudio), y atender sus pendientes siguiendo un orden cronológico. Esta herramienta está diseñada para mejorar la productividad personal, asegurando que ninguna tarea se pierda y que las categorías se mantengan actualizadas.

## Cómo compilar y ejecutar
Este sistema ha sido desarrollado en lenguaje C y puede ejecutarse fácilmente utilizando Visual Studio Code junto con una extensión para C/C++, como C/C++ Extension Pack de Microsoft. Para comenzar a trabajar con el sistema en tu equipo local, sigue estos pasos:

### Requisitos previos:
1. Tener instalado Visual Studio Code.
2. Instalar la extensión C/C++ (Microsoft).
3. Tener instalado un compilador de C (como gcc). Si estás en Windows, se recomienda instalar MinGW o utilizar el entorno WSL. En Replit, esto ya viene configurado por defecto.

### Pasos para compilar y ejecutar:
1. **Descarga y descomprime** el archivo del proyecto en una carpeta.
2. **Abre el proyecto en Visual Studio Code**:
   * Inicia Visual Studio Code.
   * Selecciona Archivo > Abrir carpeta... y elige la carpeta del proyecto.
3. **Compila el código**:
   * Abre la terminal integrada (Terminal > Nueva terminal).
   * En la terminal, compila el programa con el siguiente comando para incluir las librerías de la carpeta `tdas`:
     ```bash
     gcc tdas/*.c tarea1.c -Wno-unused-result -o tarea1
     ```
4. **Ejecuta el programa**:
   * Una vez compilado, puedes ejecutar la aplicación con:
     ```bash
     ./tarea1
     ```

## Funcionalidades
### Funcionando correctamente:
* **Nueva Categoría:** Registro de etiquetas personalizadas para organizar las tareas.
* **Registrar Pendiente:** Adición de tareas con descripción y asignación automática de hora de registro. Incluye creación automática de categorías si la ingresada no existe.
* **Mostrar Categorías:** Visualización de todas las etiquetas creadas actualmente.
* **Atender Siguiente:** Procesamiento de la tarea más antigua en la cola (FIFO), mostrando su información completa.
* **Eliminar Categoría:** Borrado de una categoría y limpieza automática de todas las tareas asociadas a ella en la cola de pendientes.

### Problemas conocidos:
* La visualización del tablero general (opción 6) y el filtrado por categorías (opción 7) están planificados para la siguiente etapa de desarrollo y no muestran datos aún.

### A mejorar:
* Implementar un sistema de prioridades dentro de las categorías.
* Añadir persistencia de datos mediante archivos CSV para no perder las tareas al cerrar el programa.

## Ejemplo de uso

### Paso 1: Registrar una Nueva Categoría
Se comienza definiendo un área de trabajo o interés.
* **Opción seleccionada:** `1) Nueva Categoría`
* **Entrada:** `Idiomas`
* El sistema confirma que la categoría "Idiomas" ha sido agregada a la lista.

### Paso 2: Registrar un Pendiente
Se añade una tarea específica a la cola de atención.
* **Opción seleccionada:** `4) Registrar Pendiente`
* **Descripción:** `Estudiar gramática de coreano y vocabulario nuevo`
* **Categoría:** `Idiomas`
* El sistema guarda la tarea y registra internamente la hora exacta de creación.

### Paso 3: Registro Automático de Categoría
El usuario registra una tarea sin haber creado la categoría previamente.
* **Opción seleccionada:** `4) Registrar Pendiente`
* **Descripción:** `Comprar entradas para el próximo concierto de Twice`
* **Categoría:** `Música`
* El sistema detecta que "Música" no existía, la crea automáticamente y luego guarda la tarea de forma exitosa.

### Paso 4: Atender al Siguiente Pendiente
El usuario decide completar su primera tarea del día.
* **Opción seleccionada:** `5) Atender Siguiente`
* El sistema muestra los detalles de la tarea más antigua: *"Estudiar gramática de coreano y vocabulario nuevo"*, junto con su categoría y la fecha/hora en que fue registrada. La tarea es eliminada de la cola tras ser mostrada.

