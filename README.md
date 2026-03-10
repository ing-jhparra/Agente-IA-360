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
* [Workflow](#Workflow)


## Descripción 
Este proceso automatizado con un agente de IA como Consultor 360 resuelve el sesgo subjetivo que suelen presentarse en las evaluaciones de desempeño tradicionales. Al actuar como un consultor experto, el agente integra y analiza volúmenes de datos, eliminando la carga administrativa de tabular respuestas manualmente, permitiendo una entrega de resultados inmediata y estandarizada. Así, se garantiza que cada colaborador reciba una retroalimentación justa, técnica y profundamente alineada con los objetivos estratégicos de la organización.

## Stack Tecnológico
- **Orquestador**: n8n (1.123.22).
- **LLM**: OpenAI GPT-4o.
- **Vector Store**: 
- **Embeddings**: 
- **Arquitectura RAG**: El flujo de los datos, se maneja de forma cíclica y estructurada a través de las siguientes etapas:

1. **Entrada de Datos (Carga Masiva)**: La información inicial (nombres, cargos, correos, etc.) se extrae desde un Google Sheet para alimentar la base de datos de empleados.

2. **Procesamiento y Validación**: Antes de cualquier inserción, el flujo utiliza nodos de JavaScript para formatear datos críticos como las fechas de ingreso. Posteriormente, consulta en PostgreSQL si el empleado o la relación de evaluación ya existen para evitar duplicados.

3. **Almacenamiento Estructurado**: Las calificaciones y relaciones se guardan en tablas de PostgreSQL mediante llamadas a procedimientos almacenados como insertar_detalle_evaluacion e insertar_relacion_evaluacion.

4. **Transformación para Reportes**: Para generar el informe, el sistema recupera los promedios y porcentajes calculados en la base de datos. Estos datos numéricos se envían a la API de QuickChart para transformarlos en gráficas visuales (radar y barras).

5. **Salida de Información**: Finalmente, los resultados procesados y las imágenes de las gráficas se integran en una plantilla HTML para ser enviados por correo electrónico a cada evaluado.

## Observaciones/Limitaciones

## Workflow

## 1. Carga de Empleados

<div align="center">
  <h1 align="center">
      Carga de Empleados.
      <br />
      <img src="./img/1_Empleados.png" alt="Siniestros Viales">
      <br />
  </h1>
</div>

## 2. Carga de Configuracion de Relaciones.

<div align="center">
  <h1 align="center">
      Carga de Configuracion de Relaciones.
      <br />
      <img src="./img/2_Relaciones.png" alt="Siniestros Viales">
      <br />
  </h1>
</div>

## 3. Carga de Calificaciones y Calculos.

<div align="center">
  <h1 align="center">
      Carga de Calificaciones y Calculos.
      <br />
      <img src="./img/3_Evaluaciones.png" alt="Siniestros Viales">
      <br />
  </h1>
</div>

## 4. Generar Reportes Estadisticos.

<div align="center">
  <h1 align="center">
      Generar Reportes Estadisticos.
      <br />
      <img src="./img/4_Estadisticas.png" alt="Siniestros Viales">
      <br />
  </h1>
</div>


## 5. Evaluación 360 por el Agente de IA.

<div align="center">
  <h1 align="center">
      Evaluación 360 por el Agente de IA.
      <br />
      <img src="./img/5_Retroalimentacion.png" alt="Siniestros Viales">
      <br />
  </h1>
</div>

## 6. Enviar reporte por correo al Evaluador.

<div align="center">
  <h1 align="center">
      Enviar reporte por correo al Evaluador.
      <br />
      <img src="./img/6_Correo.png" alt="Siniestros Viales">
      <br />
  </h1>
</div>
