# Sistema de Planificación de Tareas Dinámico
## Descripción
Este sistema permite a los usuarios gestionar sus pendientes de manera organizada mediante el uso de categorías y una cola de atención. Los usuarios pueden registrar nuevas categorías, añadir tareas con descripciones detalladas (como listas de compras o recordatorios de estudio), y atender sus pendientes siguiendo un orden cronológico. Esta herramienta está diseñada para mejorar la productividad personal, asegurando que ninguna tarea se pierda y que las categorías se mantengan actualizadas.

## Cómo compilar y ejecutar
Este sistema ha sido desarrollado en lenguaje C y puede ejecutarse fácilmente utilizando Visual Studio Code junto con una extensión para C/C++, como C/C++ Extension Pack de Microsoft. Para comenzar a trabajar con el sistema en tu equipo local, sigue estos pasos:

### Requisitos previos:
1. Tener instalado Visual Studio Code.
2. Instalar la extensión C/C++ (Microsoft).
3. Tener instalado un compilador de C (como gcc). Si estás en Windows, se recomienda instalar MinGW o utilizar el entorno WSL.

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
   * Si se usa windows, para ejecutar:
     ```bash
     .\tarea1.exe
     ```
### Solución de problemas: Error de directorios
Si al intentar compilar el código la terminal arroja un error indicando que no encuentra los archivos de los TDAs (como `list.h`, `queue.h`, etc.), se debe a que los archivos están separados o sueltos en el directorio principal y el código espera que estén agrupados.

Para solucionar esto de manera rápida:
1. Crea una nueva carpeta llamada `tdas` en el mismo lugar donde está el archivo principal (`tarea1.c`).
2. Mueve todos los archivos correspondientes a las herramientas (`list.c`, `list.h`, `queue.h`, `extra.c`, `extra.h`, etc.) dentro de esa nueva carpeta `tdas`. El único archivo de código que debe quedar afuera es `tarea1.c`.
3. Una vez hecho esto, vuelve a intentar compilar utilizando el comando original:
   ```bash
   gcc tdas/*.c tarea1.c -Wno-unused-result -o tarea1
   ```
4. **Ejecuta el programa**:
   * Una vez compilado, puedes ejecutar la aplicación con:
     ```bash
     ./tarea1
     ```
   * Si se usa windows, para ejecutar:
     ```bash
     .\tarea1.exe
     ```

## Funcionalidades
### Funcionando correctamente:
* **Nueva Categoría:** Registro de etiquetas personalizadas para organizar las tareas.
* **Registrar Pendiente:** Adición de tareas con descripción y asignación automática de hora de registro. Incluye creación automática de categorías si la ingresada no existe.
* **Mostrar Categorías:** Visualización de todas las etiquetas creadas actualmente.
* **Atender Siguiente:** Procesamiento de la tarea más antigua en la cola (FIFO), mostrando su información completa.
* **Eliminar Categoría:** Borrado de una categoría y limpieza automática de todas las tareas asociadas a ella en la cola de pendientes.
* **Mostrar Tablero General:** Visualización de todas las tareas en cola, ordenadas desde la más antigua a la más reciente, sin modificar la fila de atención.
* **Filtrar por Categoría:** Búsqueda específica que muestra solo los pendientes de una categoría elegida, manteniendo intacto el orden y los datos del sistema.

### Posibles Mejoras Futuras:
* **Sistema de Prioridades:** Añadir un nivel de urgencia (Alta, Media, Baja) que permita a ciertas tareas críticas saltarse la fila normal de atención.
* **Añadir persistencia de datos mediante archivos CSV para no perder las tareas al cerrar el programa.**
* **Fechas Límite :** Registrar no solo la hora de creación, sino también solicitar una fecha de entrega para ordenar visualmente las tareas por urgencia.
* **Validación Robusta de Entradas:** Mejorar el manejo de errores del teclado para evitar que el usuario ingrese categorías en blanco o caracteres no permitidos.

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

### Paso 5: Visualización del Tablero General
El usuario quiere revisar cuántas tareas le quedan pendientes en total después de haber trabajado.
* **Opción seleccionada:** `6) Mostrar Tablero General`
* El sistema despliega una tabla ordenada mostrando la tarea restante: "Comprar entradas para el próximo concierto de Twice", indicando su categoría ("Música"). La tarea no se borra, solo se muestra para tener un panorama visual.

### Paso 6: Filtrar Pendientes por Categoría
El usuario desea buscar si tiene más pendientes relacionados con un área en específico sin alterar el orden de llegada.
* **Opción seleccionada:** `7) Filtrar por Categoría`
* **Entrada:** `Música`
* El sistema busca en la cola y muestra en pantalla exclusivamente los detalles de las entradas para el concierto. Si existieran más tareas de "Música", se listarían todas. La cola principal de atención se mantiene intacta.

### Paso 7: Eliminar una Categoría y Limpieza
El usuario decide que ya gestionó todo lo relacionado con esa área y quiere borrarla del sistema.
* **Opción seleccionada:** `2) Eliminar Categoría`
* **Entrada:** `Música`
* El sistema elimina de forma definitiva "Música" de las opciones disponibles. Además, revisa automáticamente la cola de atención y borra la tarea de comprar las entradas, dejando la memoria limpia. Si el usuario vuelve a presionar la opción 6, el sistema le avisará que el tablero está vacío.
