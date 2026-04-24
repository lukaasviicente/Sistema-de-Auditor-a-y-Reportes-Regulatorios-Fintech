## Arquitectura Seleccionada
El sistema está construido sobre una arquitectura **Lakehouse**, utilizando Apache Kafka para la ingesta de eventos de pago en tiempo real, Apache Spark para el procesamiento estructurado, y Delta Lake como capa de almacenamiento que asegura la consistencia e inmutabilidad requerida. Apache Airflow orquesta la generación mensual de reportes.

## Requisitos y Configuración del Entorno Técnico
Para ejecutar y contribuir a este proyecto, el desarrollador necesita las siguientes herramientas instaladas en su entorno local:
* **Control de Versiones:** Git v2.30+
* **Contenedores:** Docker y Docker Compose v2.0+
* **Lenguajes:** Python 3.10+, Java 11 (requerido por Spark/Kafka)
* **Frameworks y Librerías:** PySpark 3.4+, Delta-Spark 2.4.0, Apache Airflow 2.7+

## Instrucciones de Instalación
1. **Clonar el repositorio:**
   `git clone https://github.com/fintech-org/auditoria-lakehouse.git`
   `cd auditoria-lakehouse`
2. **Configurar variables de entorno:**
   Copiar el archivo de ejemplo y configurar credenciales:
   `cp .env.example .env`
3. **Levantar la infraestructura (Kafka, Spark, Airflow) vía Docker:**
   `docker-compose up -d`
4. **Instalar dependencias de Python para desarrollo local:**
   `pip install -r requirements.txt`
5. **Ejecutar pruebas unitarias (verificando ACID):**
   `pytest tests/`

## Estructura del Repositorio
* `/config/` - Archivos de configuración de Kafka, Spark y Airflow.
* `/dags/` - Pipelines y flujos de orquestación (Airflow) para reportes mensuales.
* `/data/` - Volumen montado localmente simulando el almacenamiento de Delta Lake.
* `/docs/` - Documentación extendida, DFDs y arquitectura.
* `/src/` - Código fuente principal (PySpark jobs de ingesta y validación).
* `/tests/` - Pruebas unitarias de inmutabilidad y auditoría.
* `docker-compose.yml` - Definición de la infraestructura local.
* `requirements.txt` - Dependencias del proyecto Python.
