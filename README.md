# ejercicio-2.7
tarea 

Introducción
El presente informe describe la arquitectura conceptual y funcional de un sistema de evaluación de opción múltiple con calificación automatizada. El objetivo es estructurar un sistema escalable y eficiente que permita la interacción fluida entre el estudiante y el contenido evaluativo, asegurando la integridad de los resultados mediante procesos lógicos bien definidos.
Identificación de Clases y Objetos
A continuación, se presentan las clases principales bajo el paradigma de Orientación a Objetos:
Estudiante: Representa al usuario que rinde la prueba. Almacena credenciales y su historial de intentos.
Evaluación: Clase contenedora que agrupa un conjunto de preguntas, define el tiempo límite y el puntaje de aprobación.
Pregunta: Objeto que contiene el enunciado y una colección de opciones.
Opción: Representa cada una de las alternativas de una pregunta, con un atributo booleano que indica si es la correcta.
Intento: Clase transaccional que vincula a un Estudiante con una Evaluación, registrando las respuestas seleccionadas y la fecha.
Calificador (Puntaje): Objeto encargado de comparar las opciones marcadas contra las correctas para emitir un resultado final.
Glosario de Términos
1. Intento: Instancia única en la que un estudiante accede y completa una evaluación.
2. Opción Correcta: La alternativa predefinida dentro de una pregunta que suma puntos al ser seleccionada.
3. Puntaje : Sumatoria de puntos obtenidos antes de aplicar ponderaciones o escalas de calificación.
4. Evaluación Activa: Estado de un examen que permite el acceso y envío de respuestas por parte de los estudiantes.
5. Retroalimentación: Información entregada al estudiante tras finalizar el intento, detallando aciertos y errores.
Casos de Uso y Diagrama
Las interacciones principales se centran en la ejecución del examen y la gestión de resultados.
1: Responder Preguntas: El estudiante selecciona opciones y navega por la evaluación.
2: Calcular Puntaje: El sistema procesa las respuestas al finalizar el tiempo o al enviar el examen.
3: Mostrar Resultado: El sistema presenta la calificación y retroalimentación al usuario.
4: Gestionar Evaluación: El administrador/docente crea o modifica el banco de preguntas.
FICHA
AtributoDetalle: Responder PreguntasActorEstudiantePrecondicionesEl estudiante debe estar autenticado y tener una evaluación activa disponible.PostcondicionesLas respuestas quedan guardadas temporalmente en la sesión del intento.Flujo Principal1. El estudiante selecciona una evaluación. 2. El sistema muestra la primera pregunta. 3. El estudiante marca una opción. 4. El estudiante avanza a la siguiente pregunta. 5. Se repite hasta completar el set.Flujo AlternativoSi el estudiante pierde conexión, el sistema guarda el progreso localmente hasta que se restablezca el servicio.
AtributoDetalle: Calcular PuntajeActorSistema (Automático)PrecondicionesEl estudiante ha enviado el intento o el tiempo ha expirado.PostcondicionesSe genera un registro de puntaje final vinculado al estudiante.Flujo Principal1. El sistema recupera las respuestas del intento. 2. Compara cada ID de opción marcada con el ID de la opción correcta. 3. Suma el valor asignado a cada acierto. 4. Registra el total en la base de datos.Flujo AlternativoSi una pregunta no fue respondida, el sistema le asigna automáticamente un valor de 0 puntos para ese ítem.
