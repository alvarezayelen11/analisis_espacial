# Análisis espacial de infraestructura pública e indicadores sociodemográficos

Este repositorio reúne análisis territoriales desarrollados con **QGIS** a partir de datos públicos del **Censo Nacional de Población, Hogares y Viviendas 2022** -procesados mediante **REDATAM**- y otras fuentes oficiales.

Los casos de estudio exploran la distribución espacial de infraestructura sanitaria y educativa en distintos partidos de la provincia de Buenos Aires, en relación con indicadores sociodemográficos construidos a nivel de radio censal.

## Mapas interactivos

- [Explorar el mapa de salud en La Plata](https://alvarezayelen11.github.io/analisis_espacial/la_plata_establecimientos_salud/mapa_interactivo/)
- [Explorar el mapa de educación en Ituzaingó](https://alvarezayelen11.github.io/analisis_espacial/ituzaingo_establecimientos_educativos/mapa_interactivo/)

Los visores permiten activar y desactivar capas, consultar los atributos de cada radio censal y comparar diferentes representaciones territoriales.

---

## Casos de estudio

### 1. Cobertura médica y establecimientos públicos de salud en La Plata

El análisis compara:

- el porcentaje de población con cobertura médica en cada radio censal;
- la localización de establecimientos públicos de salud;
- áreas de influencia de 500, 1.000 y 1.500 metros alrededor de esos establecimientos.

Se considera población con cobertura médica a quienes declararon contar con:

- obra social o prepaga, incluido PAMI;
- programas o planes estatales de salud.

Se incluyeron establecimientos públicos con atención directa a la población y localización territorial estable:

- C.A.P.S. -Centros de Atención Primaria de la Salud-;
- emergencias;
- hospitales;
- establecimientos de salud mental y adicciones;
- U.P.A. -Unidades de Pronta Atención-.

Se excluyeron organismos administrativos, unidades móviles, C.A.P.S. pertenecientes a instituciones cerradas y establecimientos de atención específica no equiparables con la red general, como geriátricos, laboratorios e institutos.

### 2. Nivel educativo y establecimientos educativos en Ituzaingó

El análisis compara:

- el porcentaje de población con secundario completo o un nivel educativo superior en cada radio censal;
- la cantidad y localización de establecimientos educativos;
- un área de influencia de 500 metros alrededor de cada establecimiento.

Se incluyeron establecimientos educativos de gestión pública y privada ubicados dentro del partido de Ituzaingó.

---

## Fuentes de datos

### Radios censales

**Datos Abiertos de la Provincia de Buenos Aires – Censo 2022**

[Acceder al recurso de radios censales](https://catalogo.datos.gba.gob.ar/dataset/radios-censales/archivo/0e7c784b-5229-4f79-b20b-5d357b57ccaa)

Los radios fueron filtrados mediante los códigos de partido:

- La Plata: `441`
- Ituzaingó: `410`

### Indicadores censales

**INDEC – REDATAM, Censo 2022**

[Acceder a REDATAM](https://redatam.indec.gob.ar/)

Los datos fueron procesados a nivel de radio censal mediante:

`Censo 2022 → Resultados básicos → Viviendas particulares → Listas de áreas → De hogares y personas`

- Para La Plata se utilizaron las variables: `Sexo registrado al nacer` y `Cobertura de Salud`
- Para Ituzaingó se utilizó la variable: `Máximo nivel de instrucción alcanzado`.

### Establecimientos públicos de salud

**Datos Abiertos de la Provincia de Buenos Aires**

[Acceder al dataset de establecimientos de salud](https://catalogo.datos.gba.gob.ar/dataset/establecimientos-salud)

### Establecimientos educativos

**Mapa Educativo Nacional – Geoservicios WFS**

[Acceder a los geoservicios](https://mapa.educacion.gob.ar/geoservicios)

---

## Procesamiento

El flujo de trabajo incluyó:

1. descarga y filtrado de radios censales;
2. obtención de indicadores mediante REDATAM;
3. unión de atributos por código de radio censal;
4. cálculo de indicadores porcentuales;
5. incorporación y filtrado de establecimientos sanitarios y educativos;
6. uniones espaciales para contabilizar establecimientos por radio;
7. reproyección a un sistema de coordenadas proyectado;
8. generación y recorte de buffers;
9. construcción de mapas temáticos;
10. publicación de visores interactivos mediante `qgis2web`.

---

## Resultados preliminares

### La Plata

Se observa una mayor concentración de establecimientos públicos de salud en el **casco urbano de la ciudad de La Plata**. En esa zona también predominan radios con porcentajes relativamente altos de población con cobertura médica.

Sin embargo, el patrón no es uniforme. Los radios `64419010` y `64416708`, por ejemplo, presentan niveles elevados de cobertura aun cuando se encuentran alejados del casco urbano.

### Ituzaingó

En sectores del oeste del partido se observa una concentración de establecimientos educativos junto con radios que presentan porcentajes relativamente altos de población con secundario completo o superior.

También aparecen configuraciones que no siguen ese patrón:

- radios sin establecimientos educativos y con porcentajes altos de secundario completo: `64100201`, `64101408`, `64100203` y `64101501`;
- radios con varios establecimientos, pero con menos del 40 % de población con secundario completo: `64101502`, `64100505`, `64101601`, `64101605`, `64101606`, `64101607`, `64100603`, entre otros. 

Estos casos muestran que la distribución espacial de los establecimientos y la de los indicadores sociodemográficos no presentan una correspondencia homogénea entre radios censales.

---

## Alcances y limitaciones

Los buffers representan una aproximación de la **proximidad geográfica en línea recta**. No consideran:

- la red vial;
- barreras físicas;
- disponibilidad de transporte;
- tiempos reales de viaje.

Los patrones identificados son descriptivos y exploratorios. La coexistencia espacial entre infraestructura y determinados indicadores sociodemográficos **no constituye evidencia de una relación causal**.

Los niveles de cobertura médica y de logro educativo dependen de múltiples factores no incluidos en este análisis, como la estructura etaria, los ingresos, el empleo formal, las trayectorias residenciales, la oferta de transporte y otras características socioeconómicas.

---

## Reflexión metodológica

Las herramientas de análisis espacial permiten identificar concentraciones, vacíos territoriales y casos que se apartan de los patrones generales. Su utilidad, sin embargo, depende de complementar la visualización cartográfica con análisis estadístico, conocimiento del territorio y una interpretación crítica de los resultados.

Este repositorio busca avanzar en esa dirección: utilizar los mapas como instrumentos para formular mejores preguntas, no como evidencia automática de relaciones de causa y efecto.
