# Fintech Personal - Data Transform

Microservicio para transformación de datos financieros desde MongoDB a MySQL para análisis y visualización.

## Características

- Transformación de datos de MongoDB a MySQL para optimizar consultas analíticas
- Procesamiento asíncrono mediante colas RabbitMQ
- Mapeo de esquemas de datos entre diferentes modelos de bases de datos
- Generación de vistas agregadas para reportes financieros
- Soporte para múltiples usuarios preservando la privacidad de datos

## Arquitectura

Este servicio es parte de una arquitectura de microservicios:

- **web-app**: Interfaz de usuario y API REST
- **data-import**: Procesamiento de archivos CSV/Excel
- **data-transf**: Transformación de datos para análisis (este repositorio)

## Flujo de Datos

1. Los datos crudos se importan a MongoDB por el servicio **data-import**
2. Este servicio escucha eventos de "importación completada" en RabbitMQ
3. Extrae los datos de MongoDB, los transforma y los carga en MySQL
4. Genera agregaciones y vistas optimizadas para consultas analíticas
5. Notifica a **web-app** cuando la transformación está completa

## Prerrequisitos

- Node.js >= 14.0.0
- MongoDB (origen de datos)
- MySQL (destino de datos)
- RabbitMQ (comunicación entre servicios)
- Registro NPM privado (para dependencias internas)

## Instalación

1. Clonar el repositorio
```bash
git clone https://github.com/yourusername/fintech-personal-data-transf.git
cd fintech-personal-data-transf
```

2. Instalar dependencias
```bash
npm install
```

3. Configurar variables de entorno
```bash
cp .env.example .env
# Editar el archivo .env con la configuración correcta
```

4. Iniciar el servicio
```bash
npm run dev
```

## Dependencias

Este servicio utiliza el paquete `fintech-personal-common` que proporciona:
- DTOs y esquemas compartidos
- Utilidades de validación
- Cliente RabbitMQ
- Manejo de errores estandarizado

## Licencia

AGPL-3.0
