# curriculo-primaria-nem

Repositorio de referencia para aplicaciones de Educación Primaria basado en `Generador de Planeaciones Primaria.xlsx`.

## Principio
**Sin IA en el motor curricular.** El repositorio conserva datos, relaciones y reglas deterministas.

## v1.1
Reparación estructural y de calidad de datos sobre v1.0:
- 1,500 registros PDAS
- 215 contenidos
- 427 proyectos
- 7 ejes
- 4 campos formativos
- 6 grados / 3 fases
- 490 relaciones grado-campo-contenido
- 1,500 relaciones contenido-PDA
- 427 relaciones proyecto-eje
- 426 relaciones proyecto-campo
- 421 relaciones proyecto-contenido
- 1,071 relaciones proyecto-PDA derivadas

## Reparaciones realizadas
1. Se eliminó el `#N/A` del proyecto PR-0310 y se corrigió a **Mi cuerpo habla — Lenguajes — 5° — Fase 5**.
2. Se corrigió el grado de PR-0340 a **5° — Fase 5**.
3. Se corrigió el campo de PR-0074 y PR-0134 a **Ética, Naturaleza y Sociedades**, con respaldo externo y registro de la corrección.
4. Se normalizaron errores ortográficos y de puntuación en los textos de ejes sin eliminar el valor de origen.
5. Se completó el `manifest.json`, que en v1.0 omitía archivos existentes del paquete.
6. Se conservaron las incidencias no resolubles mediante inferencia como **pendientes**, en lugar de fabricar relaciones curriculares.

## Regla curricular
`Grado + Campo formativo → Contenidos`

`Grado + Campo formativo + Contenido → PDA`

## Proyecto → PDA
Solo se deriva cuando el contenido relacionado coincide exactamente en grado + campo + contenido con `PDAS`.

## Integridad
Las incidencias que requieren cotejo directo con la hoja `Libros` o con la fuente curricular maestra permanecen documentadas en `auditoria/pendientes-v1.1.json`. La reparación no inventa contenidos ni PDA.

## Trazabilidad
Cada registro conserva fuente, hoja y fila de origen. Las correcciones de v1.1 conservan además el valor previo cuando fue modificado.


## v1.2.0 — segunda reparación
Se incorporan correcciones verificadas de metadatos de proyectos, normalización de ejes, equivalencias canónicas de contenidos y derivación conservadora de PDA únicamente en coincidencias de alta confianza y mismo campo/grado. Los casos ambiguos permanecen pendientes.
