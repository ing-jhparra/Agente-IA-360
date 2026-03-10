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
- **Backend & Carga de Datos**: Laravel (utilizando plantillas Blade para la estandarización).
- **Fuente de Entrada**: Google Sheets (como interfaz de gestión administrativa).
- **Base de Datos Relacional**: PostgreSQL (donde se consolidan y estructuran los datos de evaluación tras el flujo de sincronización).
- **LLM**: OpenAI GPT-4o.
- **Metodología RAG**: Recuperación de contexto basada en datos estructurados (SQL) en lugar de búsqueda vectorial tradicional.

## Arquitectura RAG: 

El flujo de los datos, se maneja de forma cíclica y estructurada a través de las siguientes etapas:

1. **Entrada de Datos (Carga Masiva)**: La información inicial (nombres, cargos, correos, etc.) se extrae desde un Google Sheet para alimentar la base de datos de empleados.

2. **Procesamiento y Validación**: Antes de cualquier inserción, el flujo utiliza nodos de JavaScript para formatear datos críticos como las fechas de ingreso. Posteriormente, consulta en PostgreSQL si el empleado o la relación de evaluación ya existen para evitar duplicados.

3. **Almacenamiento Estructurado**: Las calificaciones y relaciones se guardan en tablas de PostgreSQL mediante llamadas a procedimientos almacenados como insertar_detalle_evaluacion e insertar_relacion_evaluacion.

4. **Transformación para Reportes**: Para generar el informe, el sistema recupera los promedios y porcentajes calculados en la base de datos. Estos datos numéricos se envían a la API de QuickChart para transformarlos en gráficas visuales (radar y barras).

5. **Salida de Información**: Finalmente, los resultados procesados y las imágenes de las gráficas se integran en una plantilla HTML para ser enviados por correo electrónico a cada evaluado.

## Observaciones/Limitaciones

Este sistema implementa una arquitectura RAG basada en datos estructurados que sustituye las bases de datos vectoriales por una fuente de conocimiento en Google Sheets. La gestión se realiza desde Laravel, utilizando plantillas Blade para estandarizar la carga de información. Posteriormente, un flujo automatizado sincroniza estos datos hacia tablas en PostgreSQL, permitiendo que el agente de IA consulte registros organizados y precisos. Esto garantiza una recuperación de datos exacta, auditable y fácilmente gestionable por el equipo administrativo.

## Workflow

## 1. Carga de Empleados

<div align="center">
  <h1 align="center">
      <br />
      <img src="./img/1_Empleados.png" alt="Siniestros Viales">
      <br />
  </h1>
</div>

## 2. Carga de Configuracion de Relaciones.

<div align="center">
  <h1 align="center">
      <br />
      <img src="./img/2_Relaciones.png" alt="Siniestros Viales">
      <br />
  </h1>
</div>

## 3. Carga de Calificaciones y Calculos.

<div align="center">
  <h1 align="center">
      <br />
      <img src="./img/3_Evaluaciones.png" alt="Siniestros Viales">
      <br />
  </h1>
</div>

## 4. Generar Reportes Estadisticos.

<div align="center">
  <h1 align="center">
      <br />
      <img src="./img/4_Estadisticas.png" alt="Siniestros Viales">
      <br />
  </h1>
</div>


## 5. Evaluación 360 por el Agente de IA.

<div align="center">
  <h1 align="center">
      <br />
      <img src="./img/5_Feedback.png" alt="Siniestros Viales">
      <br />
  </h1>
</div>

## 6. Enviar reporte por correo al Evaluador.

<div align="center">
  <h1 align="center">
      <br />
      <img src="./img/6_Correo.png" alt="Siniestros Viales">
      <br />
  </h1>
</div>

[Descargar JSON de Evaluación 360](https://raw.githubusercontent.com/ing-jhparra/Agente-IA-360/refs/heads/main/scripts/Evaluacion%20360.json)
