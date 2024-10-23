# Análisis de Priorización de Hipótesis y Test A/B para una Tienda Online

## Descripción del Proyecto

Este proyecto forma parte de un ejercicio realizado durante un bootcamp de Data Analyst. Como analista en una tienda online, trabajé junto al departamento de marketing para priorizar una lista de hipótesis que podrían aumentar los ingresos y luego realicé un análisis de un test A/B basado en dichas hipótesis.

El proyecto tiene dos partes principales:
1. **Priorizar hipótesis**: Evaluación de hipótesis utilizando los frameworks **ICE** y **RICE**.
2. **Análisis del test A/B**: Evaluación de los resultados del test A/B con análisis estadísticos y gráficos.

## Descripción de los Datos

El proyecto utiliza tres datasets diferentes, uno para la priorización de hipótesis y dos para el análisis del test A/B.

### Datos para la Priorización de Hipótesis:

- **hypotheses_us.csv**:
  - **Hypotheses**: Breve descripción de cada hipótesis.
  - **Reach**: Alcance de la hipótesis, en una escala del 1 al 10.
  - **Impact**: Impacto esperado en los usuarios, en una escala del 1 al 10.
  - **Confidence**: Confianza en la hipótesis, en una escala del 1 al 10.
  - **Effort**: Esfuerzo requerido para implementar la hipótesis, en una escala del 1 al 10. Cuanto mayor sea el valor, más recursos requiere.

### Datos para el Análisis del Test A/B:

1. **orders_us.csv**:
   - **transactionId**: Identificador único del pedido.
   - **visitorId**: Identificador del usuario que realizó el pedido.
   - **date**: Fecha del pedido.
   - **revenue**: Ingresos generados por el pedido.
   - **group**: El grupo del test A/B al que pertenece el usuario (A o B).

2. **visits_us.csv**:
   - **date**: Fecha de la visita.
   - **group**: Grupo del test A/B al que pertenece el usuario (A o B).
   - **visits**: Número de visitas en la fecha y grupo especificado.

### Preprocesamiento:
Se aplicó preprocesamiento a los datos para corregir posibles errores, como la aparición de usuarios en ambos grupos del test A/B, lo que podría sesgar los resultados.

## Parte 1: Priorización de Hipótesis

En esta parte, trabajé con el archivo `hypotheses_us.csv`, que contiene 9 hipótesis sobre cómo aumentar los ingresos de la tienda online. Se aplicaron dos frameworks de priorización: **ICE** y **RICE**.

- **ICE (Impact, Confidence, Effort)**: Un framework simple que prioriza las hipótesis con mayor impacto y confianza, y menor esfuerzo.
- **RICE (Reach, Impact, Confidence, Effort)**: Similar a ICE, pero considera el **alcance** (Reach) para tener en cuenta el número de usuarios que podrían verse afectados por la hipótesis.

### Análisis:

1. **Priorizar hipótesis usando ICE**: 
   Las hipótesis se ordenaron en función de la fórmula:
   \[
   ICE = \frac{{Impact \times Confidence}}{{Effort}}
   \]

2. **Priorizar hipótesis usando RICE**: 
   Se añadió el factor "Reach" al análisis, utilizando la fórmula:
   \[
   RICE = \frac{{Reach \times Impact \times Confidence}}{{Effort}}
   \]

3. **Comparación de priorización**:
   Se compararon los resultados entre ambos métodos, destacando las diferencias en la clasificación de hipótesis debido a la inclusión de "Reach" en el framework RICE. Esto permitió identificar hipótesis que, aunque requieren mayor esfuerzo, tienen un mayor impacto potencial en un mayor número de usuarios.

## Parte 2: Análisis del Test A/B

En esta parte, analicé los resultados de un test A/B que evaluaba dos grupos de usuarios (A y B) para determinar el impacto de ciertos cambios en los ingresos.

### Análisis Realizado:

1. **Ingresos acumulados por grupo**:
   - Se representaron los ingresos acumulados de cada grupo para observar cómo evolucionaron a lo largo del tiempo.
   - Se realizaron conjeturas sobre posibles diferencias entre los grupos A y B.

2. **Tamaño promedio de pedido acumulado**:
   - Se graficó el tamaño promedio de los pedidos de ambos grupos y se analizaron las diferencias.

3. **Diferencia relativa en el tamaño de pedido promedio**:
   - Se representó la diferencia relativa entre los tamaños de pedido promedio de los grupos A y B a lo largo del tiempo.

4. **Tasa de conversión diaria**:
   - Se calculó la tasa de conversión diaria (número de pedidos/número de visitas) y se compararon las tasas entre los dos grupos.

5. **Gráfico de dispersión del número de pedidos por usuario**:
   - Se analizaron los percentiles 95 y 99 del número de pedidos por usuario para identificar posibles anomalías.

6. **Gráfico de dispersión de los precios de los pedidos**:
   - Se analizaron los percentiles 95 y 99 de los precios de los pedidos para definir puntos de datos anómalos.

### Análisis Estadístico:

1. **Significancia estadística**:
   - Se calculó la significancia estadística de las diferencias en la tasa de conversión y el tamaño promedio de pedido entre los grupos A y B, utilizando tanto los datos originales como los filtrados (después de eliminar anomalías).

### Conclusión:

Después de analizar los resultados del test A/B y aplicar las pruebas de significancia estadística, las posibles decisiones son:
1. **Parar la prueba** y considerar a uno de los grupos como ganador.
2. **Parar la prueba**, concluyendo que no hay diferencia significativa entre los grupos.
3. **Continuar la prueba** si los resultados no son concluyentes.

## Contenidos del Proyecto

- `notebooks/`: Contiene los Jupyter Notebooks con el análisis detallado.
- `datasets/`: Contiene los datasets utilizados en el análisis.
- `README.md`: Este archivo con la descripción completa del proyecto.

## Instalación y Uso

Para reproducir el análisis:

1. Clona este repositorio:
   ```bash
   git clone https://github.com/704k0-dev/a_b_test_shop.git
   ```

2. Instala las dependencias necesarias (usando Conda o pip):
   ```bash
   conda env create -f environment.yml
   conda activate data_analysis
   ```

3. Ejecuta el notebook:
   ```bash
   jupyter notebook
   ```

## Licencia

Este proyecto está licenciado bajo la MIT License. Consulta el archivo `LICENSE` para más detalles.