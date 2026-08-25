# Reglas de vinculación — v1.0

## Motor
No utiliza IA. Solo consulta datos y aplica reglas deterministas.

## Currículo
`Grado + Campo formativo → Contenidos`

`Grado + Campo formativo + Contenido → PDA`

## Proyecto → PDA
Solo se deriva cuando `Grado + Campo formativo + Contenido` coincide exactamente con `PDAS`.

## Ejes
Los siete ejes son catálogo cerrado. No se infieren.

## COINCIDENCIAS
Fórmulas originales:
- D2: `=COUNTIFS(C2:C70,C2)`
- D3: `=COUNTIFS(C3:C70,C3)`

El valor de `COINCIDENCIAS` es derivado y no se trata como atributo curricular maestro.

## Vinculador de proyectos
- A7: `=_xlfn.UNIQUE(_xlfn._xlws.FILTER(Tabla32[COINCIDENCIAS],Planeaciones!$J$3=Tabla32[GRADO]))`
- B7: `=_xlfn.UNIQUE(_xlfn._xlws.FILTER(Tabla32[TÍTULOS DE PROYECTOS DE LOS LIBROS DE TEXTO],(Tabla32[COINCIDENCIAS]=$B$2)*(ISNUMBER(SEARCH(Planeaciones!$J$3,Tabla32[GRADO],1)))))`
- C7: `=VLOOKUP(_xlfn.ANCHORARRAY(B7),Libros[[ProyectosLTG]:[Propósito]],4,FALSE)`
- D7: `=IFERROR(_xlfn.UNIQUE(_xlfn.SWITCH(_xlfn.XLOOKUP(B7,Libros[ProyectosLTG],Libros[Campo Formativo]),'Proyectos CoincidenciasxEjes'!$M$3,Igualdad_de_Género,'Proyectos CoincidenciasxEjes'!$N$3,Inclusión,'Proyectos CoincidenciasxEjes'!$O$3,Interculturalidad_Crítica,'Proyectos CoincidenciasxEjes'!$P$3,Pensamiento_Crítico,'Proyectos CoincidenciasxEjes'!$Q$3,Vida_Saludable,'Proyectos CoincidenciasxEjes'!$R$3,Apropiación_de_las_Culturas_a_través_de_la_Lectura_y_la_Escritura,'Proyectos CoincidenciasxEjes'!$S$3,Artes_y_Experiencias_Estéticas,'Proyectos CoincidenciasxEjes'!$T$3,Lenguajes,'Proyectos CoincidenciasxEjes'!$U$3,Saberes_y_Pensamiento_Científico,'Proyectos CoincidenciasxEjes'!$V$3,Ética__Naturaleza_y_Sociedades,'Proyectos CoincidenciasxEjes'!$W$3,De_lo_Humano_y_lo_Comunitario),FALSE,TRUE),"")`
- E7: `=_xlfn.XLOOKUP(_xlfn.ANCHORARRAY(B7),Tabla32[TÍTULOS DE PROYECTOS DE LOS LIBROS DE TEXTO],Tabla32[EJES ARTICULADORES])`
- F7: `=_xlfn.UNIQUE(IF(ISNUMBER(SEARCH($F$6,$E7,1)),INDIRECT($F$5),""),FALSE,TRUE)`
- G7: `=_xlfn.UNIQUE(IF(ISNUMBER(SEARCH($G$6,$E7,1)),INDIRECT($G$5),""),FALSE,TRUE)`
- L7: `=_xlfn.UNIQUE(IF(ISNUMBER(SEARCH($L$6,$E7,1)),INDIRECT($L$5),""),FALSE,TRUE)`

Las fórmulas se documentan como lógica de origen, no como datos.

## Prohibiciones
No generar, completar, inferir, sustituir ni aproximar contenidos, PDA, ejes o proyectos.
