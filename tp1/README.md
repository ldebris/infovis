# <img src="assets/img/pedidosya.png" alt="Logo PedidosYa" width="28"> Radiografía de mis antojos en PedidosYa

Exploración visual de 70 pedidos personales registrados en PedidosYa. El proyecto toma un historial de consumo cotidiano y lo transforma en una serie de visualizaciones sobre hábitos, gasto, repetición, horarios y formas de resolver el hambre.

Más que una lista de compras, el dataset funciona como una pequeña autobiografía de consumo: muestra la convivencia entre rutina, abastecimiento y antojo.

---

## Estructura del proyecto

- `tp1/index.html` — Página principal del proyecto
- `tp1/README.md` — Este archivo
- `tp1/data/pedidos_dataset.csv` — Dataset principal del proyecto
- `tp1/assets/img/` — Imágenes, capturas y recursos visuales
- `tp1/charts/` — Exportaciones o archivos auxiliares de gráficos

---

## De dónde vienen los datos

El dataset fue construido manualmente a partir del historial visible en la app de PedidosYa, en la sección **“Mis pedidos”**. Cada fila corresponde a un pedido realizado y reúne información observada directamente en las capturas: fecha, hora, comercio, monto, cantidad de productos y ahorro con Plus.

A partir de ese registro inicial, la base se enriqueció con variables derivadas para hacer posible el análisis visual. Entre ellas:

- `mes`
- `dia_semana`
- `franja_horaria`
- `categoria`
- `zona`
- `tipo_consumo`
- `fin_de_semana`
- `local_recurrente`

De este modo, el archivo deja de ser solo una lista de pedidos y se convierte en una base preparada para analizar patrones de consumo.

---

## Cómo se construyó y transformó el dataset

El punto de partida fue un registro manual con una fila por pedido. Luego se normalizaron y organizaron los datos para que pudieran ser leídos por distintas herramientas de visualización.

### Variables originales
- Fecha
- Hora
- Local
- Monto
- Cantidad de productos
- Ahorro con Plus

### Variables derivadas
- Mes
- Día de la semana
- Franja horaria
- Categoría del comercio
- Zona
- Tipo de consumo
- Fin de semana
- Reincidencia del local

### Criterios de clasificación
Para interpretar el historial se agruparon los pedidos en cuatro lógicas principales:

- **Abastecimiento**: compras grandes o funcionales, principalmente market o supermercado.
- **Comida resuelta**: pedidos que resuelven una comida puntual, como pizza, empanadas o comidas rápidas.
- **Antojo**: compras asociadas al gusto o al capricho, como helados o pedidos individuales.
- **Merienda / desayuno**: panadería y consumos ligados a momentos más específicos del día.

---

## Visualizaciones del proyecto

### 1 · Flourish — ¿Qué locales forman parte de mi rutina y cuáles pesan más en mi gasto?
Esta visualización compara frecuencia y gasto por local para distinguir entre hábitos recurrentes, compras de alto impacto y consumos ocasionales.

**Transformación aplicada:**
- Agrupar por `local`
- Contar cantidad de pedidos
- Sumar `monto`
- Calcular ticket promedio
- Colorear por `tipo_consumo`

El resultado muestra que no todos los locales ocupan el mismo lugar en el historial: algunos aparecen muchas veces pero con tickets bajos, mientras otros concentran más dinero aunque se pidan con menor frecuencia.

---

### 2 · DataWrapper — ¿En qué tipo de pedidos se concentra realmente mi gasto?
Esta visualización compara el gasto total acumulado por tipo de consumo mediante barras apiladas. Cada barra resume una categoría general —abastecimiento, antojo, comida resuelta y merienda/desayuno— y sus segmentos muestran los locales principales que explican ese peso económico, agrupando el resto en “Otros locales”.

**Transformación aplicada:**
- Agrupar por `tipo_consumo` y `local`
- Sumar `monto`
- Seleccionar los locales más representativos dentro de cada tipo de consumo
- Agrupar el resto en `Otros locales`
- Reestructurar la tabla para un gráfico de barras apiladas horizontal

El resultado permite ver que el gasto no se distribuye de la misma manera entre categorías: algunas se apoyan en un local claramente dominante, mientras otras reparten su peso entre varios comercios.

---

### 3 · RAWGraphs — ¿Cómo se conectan mis tipos de consumo, los locales y los momentos del día?
Para esta visualización se trabaja con relaciones entre variables. La idea es mostrar cómo ciertos tipos de consumo se asocian con comercios concretos y franjas horarias específicas.

**Transformación aplicada:**
- Tomar las columnas `tipo_consumo`, `local` y `franja_horaria`
- Mantener una fila por pedido
- Preparar la tabla para un diagrama alluvial o Sankey

El resultado revela conexiones entre hábito, comercio y horario: por ejemplo, antojo + heladería + tarde/noche o abastecimiento + market + mañana/mediodía.

---

### 4 · Tableau Public — ¿Cuándo aparecen mis pedidos y qué hábitos se repiten?
Esta visualización organiza los pedidos según el día de la semana y la franja horaria para detectar ritmos de consumo.

**Transformación aplicada:**
- Traducir y ordenar los días de la semana
- Agrupar por `dia_semana` y `franja_horaria`
- Contar cantidad de pedidos por combinación

El resultado es un mapa temporal de consumo que permite detectar momentos de rutina, compras funcionales y picos de antojo.

---

## Idea del proyecto

El proyecto parte de una hipótesis sencilla: los pedidos no son solo transacciones. También son una forma de huella cotidiana. En ellos se mezclan costumbre, practicidad, deseo y organización de la vida diaria.

Por eso, el análisis no busca solamente mostrar “qué compré”, sino leer el historial como un retrato de hábitos personales a través del tiempo, el gasto y la repetición.

---

## 🛠 Herramientas utilizadas

| Herramienta | Uso |
|---|---|
| LibreOffice / Excel | Limpieza y organización inicial del dataset |
| Flourish | Relación entre frecuencia, gasto y ticket promedio por local |
| DataWrapper | Barras apiladas del gasto total por tipo de consumo y locales principales |
| RAWGraphs | Relaciones entre tipo de consumo, local y franja horaria |
| Tableau Public | Heatmap temporal de pedidos |
| GitHub Pages | Publicación de la web del proyecto |

---

## Publicación

El trabajo se publica como una página HTML en GitHub Pages dentro del repositorio `infovis`, en la carpeta `tp1/`.

La versión final del proyecto se accede desde:

[https://ldebris.github.io/infovis/tp1/](https://ldebris.github.io/infovis/tp1/)

---

## ✍️ Autor

Luis G. Goñi
