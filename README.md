# Optimización de supermercados — Grupo 2

Repositorio del **proyecto final** del curso de Optimización Industrial: selección de ubicaciones de supermercados en Lima mediante **algoritmos genéticos** (mono-objetivo y **NSGA-II**), con restricciones de distancia y codificación binaria.

## Contenido de esta carpeta

| Archivo | Descripción |
|--------|-------------|
| [`Grupo_2_Ubicacion_de_supermercados.ipynb`](Grupo_2_Ubicacion_de_supermercados.ipynb) | Notebook principal pensado para **Google Colab**: datos, parámetros, reparación de factibilidad, AG mono, NSGA-II, pipeline experimental, figuras y **conclusiones** al final. |
| `README.md` | Este archivo. |
| `Candidatos_supermercardos.xlsx` | Dataset utilizado.

## Integrantes

- HUANACO MEDINA, JHON  
- RAMÍREZ UCAÑAY, BARBARITA PAULA JANETH  
- UGAZ PERALES, CARLOS ANDRÉ  
- VILLA LONGA, JOSE AARON  

## Problema (resumen)

- Elegir **10** supermercados entre **60** candidatos.  
- **Maximizar** población atendida (radio 500 m) y **suma de distancias** entre pares seleccionados (dispersión).  
- **Restricción:** distancia geodésica (Haversine) **≥ 1 km** entre cualquier par de ubicaciones elegidas.  
- Representación: **cromosoma binario** de 60 genes con exactamente 10 unos; **reparación** tras operadores genéticos.

## Entorno y dependencias

- **Python 3** (en Colab viene preinstalado).  
- Paquetes: `numpy`, `pandas`, `matplotlib`, `openpyxl` (el notebook instala `openpyxl` con `pip` si hace falta).

## Uso en Google Colab

1. Subir el notebook a Colab o abrirlo desde Drive/GitHub.  
2. Subir **`Candidatos_supermercados.xlsx`** al entorno (por ejemplo en `/content/`).  
3. Ajustar si hace falta `BASE_DIR` y `DATA_PATH` en la celda de rutas (por defecto `/content/Trabajo final` y `/content/Candidatos_supermercados.xlsx`).  
4. Ejecutar las celdas **en orden**: dependencias → rutas → parámetros y geometría → bloques evolutivos → pipeline → lectura de resultados y figuras.

Al ejecutar el pipeline se crean (bajo `BASE_DIR`) carpetas como:

- `resultados/mono/` — mejores individuos mono por réplica.  
- `resultados/nsga2/` — frentes de Pareto por réplica.  
- `resultados/figuras/` — PNG (convergencia, Pareto, métricas por réplica, comparación, mapa, etc.).  
- `data/` — datos limpios y matriz de distancias exportada.  
- `resultados/metricas_globales.json` — métricas agregadas.

## Metodología (referencia rápida)

- Distancias: **Haversine** (km).  
- **AG mono-objetivo:** fitness ponderado (`alpha`, `beta`), torneo, cruce uniforme, mutación swap, elitismo.  
- **NSGA-II:** ordenamiento no dominado, crowding, mismos operadores con reparación.  
- **Experimentación:** varias **réplicas** con semillas distintas; **generaciones** evolutivas por réplica (no confundir con “épocas” de redes neuronales).

## Licencia y uso académico

Material elaborado para el **Diplomado de Desarrollo de Aplicaciones con IA — Optimización Industrial**. Uso académico según las normas del curso.
