# Barcelona Data Explorer

Mapa interactivo multicapa de Barcelona construido con datos abiertos del [Ajuntament de Barcelona](https://opendata-ajuntament.barcelona.cat/) y otras fuentes públicas.

![Leaflet](https://img.shields.io/badge/Leaflet-1.9.4-green) ![Open Data](https://img.shields.io/badge/Open%20Data-BCN-blue) ![License](https://img.shields.io/badge/license-MIT-lightgrey)

## Capas disponibles

| Capa | Descripción | Fuente |
|------|------------|--------|
| **Distritos y Barrios** | Límites administrativos de los 10 distritos y 73 barrios | [bcn-geodata](https://github.com/martgnz/bcn-geodata) |
| **Ruido ambiental** | Zonas acústicas, puntos de medición y heatmap. Filtrable por fuente (tráfico, ocio nocturno, ferrocarril) | [Mapa Estratègic de Soroll](https://opendata-ajuntament.barcelona.cat/) |
| **Bicing (tiempo real)** | Estaciones con disponibilidad, bicis eléctricas, clustering y heatmap. Intermodalidad con Metro | [CityBikes API](https://api.citybik.es/) |
| **Accidentalidad vial** | ~55 accidentes geolocalizados (Guardia Urbana 2023). Filtros: vehículo, gravedad, hora, mes, día de la semana | [Accidents GU BCN](https://opendata-ajuntament.barcelona.cat/data/es/dataset/accidents-gu-bcn) |
| **Carriles bici** | Infraestructura ciclista GeoJSON | [Carril Bici BCN](https://opendata-ajuntament.barcelona.cat/data/es/dataset/carril-bici) |
| **Atlas demográfico** | Coroplético por distrito con 8 variables: población, densidad, edad, envejecimiento, extranjeros, juventud, tamaño hogar, ratio M/H | [Padrón Municipal](https://opendata-ajuntament.barcelona.cat/data/es/dataset/est-padro) |
| **Arbolado urbano** | ~213 árboles con clustering. Filtrable por especie (plátano, almez, naranjo, tipuana, jacaranda, pino) + heatmap de densidad verde | [Arbrat Viari](https://opendata-ajuntament.barcelona.cat/data/es/dataset/arbrat-viari) |
| **Equipamientos culturales** | Museos, bibliotecas, mercados, centros deportivos, teatros y patrimonio | [Open Data BCN](https://opendata-ajuntament.barcelona.cat/) |
| **Presión turística** | Alojamientos turísticos (hoteles, hostales, apartamentos) | [Allotjaments Turístics](https://opendata-ajuntament.barcelona.cat/data/es/dataset/allotjaments-turistics) |
| **Centros sanitarios** | Hospitales, CAPs y CUAPs | [Sanitat BCN](https://opendata-ajuntament.barcelona.cat/data/es/dataset/sanitat-salut) |
| **Centros educativos** | ~121 centros: CEIP, IES, concertados y privados. Filtros por titularidad y nivel educativo | [Centres Educatius](https://opendata-ajuntament.barcelona.cat/data/es/dataset/centres-educatius) |

## Análisis cruzados

El panel lateral genera automáticamente **11 patrones cruzados** entre capas:

- **Isla de calor vs arbolado**: distritos con déficit verde y alto ruido
- **Segregación educativa**: distribución de colegios privados vs públicos por distrito y renta
- **Accesibilidad sanitaria vs envejecimiento**: ratio de centros de salud en distritos envejecidos
- **Presión turística vs habitabilidad**: alojamientos turísticos, ruido y calidad de vida en Ciutat Vella
- **Seguridad ciclista vs infraestructura**: accidentes de bici en zonas sin carril protegido
- **Desiertos de servicios**: distritos con menor dotación combinada (cultura, verde, salud, educación)
- **Diversidad cultural vs desigualdad**: modelos de ciudad contrapuestos
- **Justicia ambiental**: correlación entre población infantil, arbolado y ruido

## Tecnología

- **Single-file HTML** (~2100 líneas) — sin build, sin dependencias server-side
- [Leaflet.js](https://leafletjs.com/) con basemap CARTO Dark
- [Leaflet.markercluster](https://github.com/Leaflet/Leaflet.markercluster) para agrupación
- [leaflet-heat](https://github.com/Leaflet/Leaflet.heat) para mapas de calor
- APIs en tiempo real con fallback multi-fuente y timeout pattern

## Uso local

```bash
git clone https://github.com/caicrucial/barcelona-data-explorer.git
cd barcelona-data-explorer
python3 -m http.server 8000
# Abrir http://localhost:8000 en el navegador
```

## Licencia

MIT. Los datos son propiedad del Ajuntament de Barcelona bajo licencia [CC-BY](https://creativecommons.org/licenses/by/4.0/).

---

Para cualquier duda o sugerencia: **caicrucial@gmail.com**
