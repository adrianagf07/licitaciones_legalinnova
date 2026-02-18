# Repositorio de Licitaciones y Resoluciones - LegalInnova

Este repositorio contiene la estructura de datos, documentación y scripts para la automatización de la captura de licitaciones públicas y resoluciones de tribunales administrativos.

## 1. Estructura del Proyecto

El repositorio está organizado de la siguiente manera:

- **/datos**: Contiene los archivos CSV/Excel con las licitaciones descargadas.
- **/resoluciones**: Repositorio de documentos PDF organizados por origen.
  - `/central`: Resoluciones del TACRC.
  - `/ccaa`: Resoluciones autonómicas organizadas por Comunidad (ej. /madrid, /cataluna).
- **/scripts**: (En desarrollo) Código Python para la actualización automática.
- **/docs**: Documentación técnica adicional.

## 2. Esquema de Datos Propuesto

### A. Base de Datos de Licitaciones
Los archivos CSV en `/datos` siguen esta estructura de columnas:

| Campo | Tipo | Descripción |
| :--- | :--- | :--- |
| `id_licitacion` | Texto | Identificador único de la plataforma |
| `organo_contratacion` | Texto | Entidad que licita (ej. Ayuntamiento de Madrid) |
| `objeto` | Texto | Descripción breve del contrato |
| `cpv` | Numérico | Código CPV (si está disponible) |
| `tipo_contrato` | Texto | Servicios, Obras, Suministros |
| `procedimiento` | Texto | Abierto, Restringido, Negociado... |
| `presupuesto_base` | Moneda | Presupuesto sin impuestos |
| `fecha_publicacion` | Fecha | DD/MM/AAAA |
| `fecha_limite` | Fecha | DD/MM/AAAA (Deadline) |
| `enlace_oficial` | URL | Link a la plataforma de contratación |

### B. Metadatos de Resoluciones
Cada PDF en la carpeta `/resoluciones` tendrá un archivo JSON asociado con:

- **Organo:** (ej. TARC Cataluña)
- **Nº Resolución:** (ej. 123/2023)
- **Sentido:** (Estimación / Desestimación / Inadmisión)
- **Acto Recurrido:** (Pliegos / Adjudicación / Exclusión)

## 3. Próximos Pasos
- [ ] Desarrollo del script de "Web Scraping" para la Plataforma del Estado.
- [ ] Automatización de la descarga de PDFs del TACRC.