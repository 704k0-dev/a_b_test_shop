# An�lisis de Priorizaci�n de Hip�tesis y Test A/B para una Tienda Online

## Descripci�n del Proyecto

Este proyecto forma parte de un ejercicio realizado durante un bootcamp de Data Analyst. Como analista en una tienda online, trabaj� junto al departamento de marketing para priorizar una lista de hip�tesis que podr�an aumentar los ingresos y luego realic� un an�lisis de un test A/B basado en dichas hip�tesis.

El proyecto tiene dos partes principales:
1. **Priorizar hip�tesis**: Evaluaci�n de hip�tesis utilizando los frameworks **ICE** y **RICE**.
2. **An�lisis del test A/B**: Evaluaci�n de los resultados del test A/B con an�lisis estad�sticos y gr�ficos.

## Descripci�n de los Datos

El proyecto utiliza tres datasets diferentes, uno para la priorizaci�n de hip�tesis y dos para el an�lisis del test A/B.

### Datos para la Priorizaci�n de Hip�tesis:

- **hypotheses_us.csv**:
  - **Hypotheses**: Breve descripci�n de cada hip�tesis.
  - **Reach**: Alcance de la hip�tesis, en una escala del 1 al 10.
  - **Impact**: Impacto esperado en los usuarios, en una escala del 1 al 10.
  - **Confidence**: Confianza en la hip�tesis, en una escala del 1 al 10.
  - **Effort**: Esfuerzo requerido para implementar la hip�tesis, en una escala del 1 al 10. Cuanto mayor sea el valor, m�s recursos requiere.

### Datos para el An�lisis del Test A/B:

1. **orders_us.csv**:
   - **transactionId**: Identificador �nico del pedido.
   - **visitorId**: Identificador del usuario que realiz� el pedido.
   - **date**: Fecha del pedido.
   - **revenue**: Ingresos generados por el pedido.
   - **group**: El grupo del test A/B al que pertenece el usuario (A o B).

2. **visits_us.csv**:
   - **date**: Fecha de la visita.
   - **group**: Grupo del test A/B al que pertenece el usuario (A o B).
   - **visits**: N�mero de visitas en la fecha y grupo especificado.

### Preprocesamiento:
Se aplic� preprocesamiento a los datos para corregir posibles errores, como la aparici�n de usuarios en ambos grupos del test A/B, lo que podr�a sesgar los resultados.

## Parte 1: Priorizaci�n de Hip�tesis

En esta parte, trabaj� con el archivo `hypotheses_us.csv`, que contiene 9 hip�tesis sobre c�mo aumentar los ingresos de la tienda online. Se aplicaron dos frameworks de priorizaci�n: **ICE** y **RICE**.

- **ICE (Impact, Confidence, Effort)**: Un framework simple que prioriza las hip�tesis con mayor impacto y confianza, y menor esfuerzo.
- **RICE (Reach, Impact, Confidence, Effort)**: Similar a ICE, pero considera el **alcance** (Reach) para tener en cuenta el n�mero de usuarios que podr�an verse afectados por la hip�tesis.

### An�lisis:

1. **Priorizar hip�tesis usando ICE**: 
   Las hip�tesis se ordenaron en funci�n de la f�rmula:
   \[
   ICE = \frac{{Impact \times Confidence}}{{Effort}}
   \]

2. **Priorizar hip�tesis usando RICE**: 
   Se a�adi� el factor "Reach" al an�lisis, utilizando la f�rmula:
   \[
   RICE = \frac{{Reach \times Impact \times Confidence}}{{Effort}}
   \]

3. **Comparaci�n de priorizaci�n**:
   Se compararon los resultados entre ambos m�todos, destacando las diferencias en la clasificaci�n de hip�tesis debido a la inclusi�n de "Reach" en el framework RICE. Esto permiti� identificar hip�tesis que, aunque requieren mayor esfuerzo, tienen un mayor impacto potencial en un mayor n�mero de usuarios.

## Parte 2: An�lisis del Test A/B

En esta parte, analic� los resultados de un test A/B que evaluaba dos grupos de usuarios (A y B) para determinar el impacto de ciertos cambios en los ingresos.

### An�lisis Realizado:

1. **Ingresos acumulados por grupo**:
   - Se representaron los ingresos acumulados de cada grupo para observar c�mo evolucionaron a lo largo del tiempo.
   - Se realizaron conjeturas sobre posibles diferencias entre los grupos A y B.

2. **Tama�o promedio de pedido acumulado**:
   - Se grafic� el tama�o promedio de los pedidos de ambos grupos y se analizaron las diferencias.

3. **Diferencia relativa en el tama�o de pedido promedio**:
   - Se represent� la diferencia relativa entre los tama�os de pedido promedio de los grupos A y B a lo largo del tiempo.

4. **Tasa de conversi�n diaria**:
   - Se calcul� la tasa de conversi�n diaria (n�mero de pedidos/n�mero de visitas) y se compararon las tasas entre los dos grupos.

5. **Gr�fico de dispersi�n del n�mero de pedidos por usuario**:
   - Se analizaron los percentiles 95 y 99 del n�mero de pedidos por usuario para identificar posibles anomal�as.

6. **Gr�fico de dispersi�n de los precios de los pedidos**:
   - Se analizaron los percentiles 95 y 99 de los precios de los pedidos para definir puntos de datos an�malos.

### An�lisis Estad�stico:

1. **Significancia estad�stica**:
   - Se calcul� la significancia estad�stica de las diferencias en la tasa de conversi�n y el tama�o promedio de pedido entre los grupos A y B, utilizando tanto los datos originales como los filtrados (despu�s de eliminar anomal�as).

### Conclusi�n:

Despu�s de analizar los resultados del test A/B y aplicar las pruebas de significancia estad�stica, las posibles decisiones son:
1. **Parar la prueba** y considerar a uno de los grupos como ganador.
2. **Parar la prueba**, concluyendo que no hay diferencia significativa entre los grupos.
3. **Continuar la prueba** si los resultados no son concluyentes.

## Contenidos del Proyecto

- `notebooks/`: Contiene los Jupyter Notebooks con el an�lisis detallado.
- `datasets/`: Contiene los datasets utilizados en el an�lisis.
- `README.md`: Este archivo con la descripci�n completa del proyecto.

## Instalaci�n y Uso

Para reproducir el an�lisis:

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

Este proyecto est� licenciado bajo la MIT License. Consulta el archivo `LICENSE` para m�s detalles.