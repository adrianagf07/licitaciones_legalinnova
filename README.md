# Repositorio de Licitaciones y Resoluciones – LegalInnova

Este repositorio contiene la estructura de datos, documentación y scripts para la captura, almacenamiento y futura automatización de:

- Licitaciones públicas (plataformas estatal y autonómicas)
- Resoluciones de tribunales administrativos de recursos contractuales

El objetivo es construir una base de datos estructurada, ampliable y automatizable para su posterior análisis y explotación.

---

## 1. Estructura del Proyecto
/datos → Archivos CSV con las licitaciones
/resoluciones → PDFs organizados por órgano
/central → TACRC
/ccaa → Tribunales autonómicos
/CAT
/GAL
/EUS
/MAD
/scripts → Scripts Python de actualización (en desarrollo)
/docs → Documentación técnica (esquema de datos, decisiones de diseño)


---

## 2. Esquema de Datos

### A. Base de Datos de Licitaciones

Los archivos en `/datos` siguen la siguiente estructura:

| Campo | Tipo | Descripción |
|-------|------|------------|
| id_licitacion | Texto | Identificador único de la plataforma |
| organo_contratacion | Texto | Entidad que licita |
| objeto | Texto | Descripción del contrato |
| cpv | Texto | Código CPV (si está disponible) |
| tipo_contrato | Texto | Servicios / Obras / Suministros / Concesión |
| procedimiento | Texto | Abierto / Abierto simplificado / Restringido / Negociado |
| presupuesto_base | Numérico | Presupuesto sin impuestos |
| fecha_publicacion | Fecha | Formato YYYY-MM-DD |
| fecha_limite | Fecha | Formato YYYY-MM-DD |
| enlace_oficial | URL | Enlace directo a la licitación |

---

### Tipologías normalizadas

Se han definido valores homogéneos para garantizar coherencia en el dataset.

#### Tipo de contrato
- Servicios  
- Obras  
- Suministros  
- Concesión de servicios  
- Concesión de obras  

#### Procedimiento
- Abierto  
- Abierto simplificado  
- Restringido  
- Negociado sin publicidad  
- Acuerdo Marco  

---

### B. Metadatos de Resoluciones

Cada PDF almacenado en `/resoluciones` tendrá un archivo JSON asociado con los siguientes campos:

- organo  
- numero_resolucion  
- fecha  
- sentido (estimación / desestimación / inadmisión)  
- acto_recurrido  
- tipo_contrato  
- enlace_origen  

---

## 3. Objetivo Técnico

El sistema debe permitir:

- Comparación entre plataformas
- Filtrado por tipo, fecha o procedimiento
- Actualización automática (diaria o semanal)
- Detección de duplicados
- Registro de nuevos elementos añadidos (log de cambios)

---

## 4. Próximos pasos

- Desarrollo del script de actualización para la Plataforma del Estado.
- Automatización de descarga y registro de resoluciones del TACRC.
- Migración futura a base de datos SQLite.



