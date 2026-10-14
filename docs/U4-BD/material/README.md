# Material adicional — Unidad 4: Diseño de bases de datos y recolección de información

Seminario de Proyecto I (MCDI). Material **opcional** de consulta que acompaña la presentación de la Unidad 4. No forma parte de la sesión: es para que revises, con datos reales, lo que la presentación explica.

| Notebook | Qué muestra | Datos | Tiempo de ejecución |
|---|---|---|---|
| [`01_privacidad_y_datos_sinteticos`](01_privacidad_y_datos_sinteticos.ipynb) ([HTML](01_privacidad_y_datos_sinteticos.html)) | Parte A: seudonimización y enmascaramiento (k-anonimato, generalización, supresión). Parte B: datos sintéticos con SDV, con medidas de **utilidad** y de **privacidad**. | UCI *Adult* (CC BY 4.0) | ~30 s |
| [`02_ejemplo_calidad_aire`](02_ejemplo_calidad_aire.ipynb) ([HTML](02_ejemplo_calidad_aire.html)) | **Ejemplo de punta a punta 1.** Tabla plana con series de tiempo: valores centinela, faltantes, imputación, agregación hora → día, diccionario, README. | UCI *Air Quality* | ~10 s |
| [`03_ejemplo_indicadores_banco_mundial`](03_ejemplo_indicadores_banco_mundial.ipynb) ([HTML](03_ejemplo_indicadores_banco_mundial.html)) | **Ejemplo de punta a punta 2.** Varias fuentes → modelo relacional en SQLite → una tabla de análisis; agregados mezclados con países, atípicos, agregación espacial ponderada. | API del Banco Mundial (WDI, CC BY 4.0) | ~15 s |

Los dos ejemplos de punta a punta terminan con lo que se considera **buena práctica** (diccionario de datos, README, estructura de carpetas, transformaciones documentadas). Son *ejemplos de razonamiento y documentación*, no plantillas para copiar.

## Cómo ejecutarlos

**En Google Colab** (sin instalar nada): abre cada notebook con el botón *Abrir en Colab* de su primera celda. El notebook 01 instala SDV por sí mismo.

**En tu computadora:**

```bash
python -m venv .venv
source .venv/bin/activate          # en Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook
```

Cada notebook crea su carpeta de trabajo (`proyecto_privacidad/`, `proyecto_calidad_aire/`, `proyecto_indicadores_wdi/`) con la estructura recomendada en la presentación, y **descarga los datos originales** la primera vez que se ejecuta (requiere internet).

## Sobre los datos y las licencias

- Los datos **no se incluyen** en este repositorio: cada notebook los descarga de su fuente y los guarda en `datos/originales/`, que nunca se modifica.
- *Adult* y *Air Quality* tienen licencia CC BY 4.0 en el UCI Machine Learning Repository. La página de *Air Quality* añade que los datos son **solo para uso en investigación, no comercial**. Respeta esa indicación si los reutilizas.
- Los indicadores del Banco Mundial (WDI) se publican con licencia CC BY 4.0. El Banco Mundial **revisa** sus cifras: los resultados que imprime el notebook 03 pueden variar ligeramente respecto a los del texto, que corresponden a la descarga del 13 de octubre de 2026.
- SDV usa la licencia *Business Source License 1.1*: permite el uso no productivo (docencia, investigación) y prohíbe ofrecer con él un servicio comercial de datos sintéticos.
- El notebook 01 usa **nombres ficticios** generados al azar; ninguna persona real aparece en el ejercicio.

## Versiones probadas

Los notebooks se ejecutaron de principio a fin con las versiones de [`requirements-probado.txt`](requirements-probado.txt) (Python 3.12). Con otras versiones, especialmente de SDV (su API cambia entre versiones), puede haber diferencias.
