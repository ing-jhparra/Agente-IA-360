<div align="center">
  <h1 align="center">
    Proceso Automatizado de Evaluación de desempeño 360 con Agente de IA
      <br />
      <img src="./img/evaluacion-360.png" alt="Siniestros Viales">
      <br />
  </h1>
</div>

# Contenido

* [Descripción](#Descripción})
* [Stack Tecnológico](#Stack-Tecnológico)


## Descripción 
Este proceso automatizado con un agente de IA como Consultor 360 resuelve el sesgo subjetivo que suelen presentarse en las evaluaciones de desempeño tradicionales. Al actuar como un consultor experto, el agente integra y analiza volúmenes de datos, eliminando la carga administrativa de tabular respuestas manualmente, permitiendo una entrega de resultados inmediata y estandarizada. Así, se garantiza que cada colaborador reciba una retroalimentación justa, técnica y profundamente alineada con los objetivos estratégicos de la organización.

## Stack Tecnológico
- **Orquestador**: n8n (1.123.22).
- **LLM**: OpenAI GPT-4o.
- **Vector Store**: 
- **Embeddings**: 
- **Arquitectura RAG**: El flujo de los datos, se maneja de forma cíclica y estructurada a través de las siguientes etapas:

* **Entrada de Datos (Carga Masiva)**: La información inicial (nombres, cargos, correos, etc.) se extrae desde un Google Sheet para alimentar la base de datos de empleados.

* **Procesamiento y Validación**: Antes de cualquier inserción, el flujo utiliza nodos de JavaScript para formatear datos críticos como las fechas de ingreso. Posteriormente, consulta en PostgreSQL si el empleado o la relación de evaluación ya existen para evitar duplicados.

* **Almacenamiento Estructurado**: Las calificaciones y relaciones se guardan en tablas de PostgreSQL mediante llamadas a procedimientos almacenados como insertar_detalle_evaluacion e insertar_relacion_evaluacion.

* **Transformación para Reportes**: Para generar el informe, el sistema recupera los promedios y porcentajes calculados en la base de datos. Estos datos numéricos se envían a la API de QuickChart para transformarlos en gráficas visuales (radar y barras).

* **Salida de Información**: Finalmente, los resultados procesados y las imágenes de las gráficas se integran en una plantilla HTML para ser enviados por correo electrónico a cada evaluado.

## Arquitectura RAG
## Observaciones/Limitaciones