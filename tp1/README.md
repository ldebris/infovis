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

##  Visualizaciones del proyecto

### 1 · DataWrapper — ¿Qué locales aparecen una y otra vez en mi historial?
Esta visualización organiza los pedidos por comercio y cuenta cuántas veces aparece cada uno. El objetivo es identificar cuáles son compras excepcionales y cuáles forman parte de una rutina.

**Transformación aplicada:**
- Agrupar por `local`
- Contar cantidad de pedidos por comercio
- Ordenar de mayor a menor frecuencia

El resultado es un ranking de locales que muestra qué lugares ocupan un lugar fijo dentro de mis hábitos de consumo.

---

### 2 · Flourish  — ¿En qué se me va más plata: antojo, rutina o abastecimiento?
Esta visualización compara el gasto total por categoría o por tipo de consumo. Busca mostrar que la frecuencia no siempre coincide con el peso económico de cada tipo de pedido.

**Transformación aplicada:**
- Agrupar por `categoria` o `tipo_consumo`
- Sumar `monto`
- Comparar gasto acumulado entre grupos

El resultado permite ver, por ejemplo, si el abastecimiento aparece menos veces pero concentra más dinero que los antojos.

---

### 3 · RAWGraphs — ¿Cómo se conectan mis categorías, locales y momentos del día?
Para esta visualización se trabaja con relaciones entre variables. La idea es mostrar cómo ciertos tipos de consumo se asocian con comercios concretos y franjas horarias específicas.

**Transformación aplicada:**
- Tomar las columnas `categoria`, `local` y `franja_horaria`
- Mantener una fila por pedido
- Preparar la tabla para un diagrama alluvial o Sankey

El resultado revela conexiones entre hábito, comercio y horario: por ejemplo, heladería + tarde/noche o market + mañana/mediodía.

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
| DataWrapper | Ranking de locales más frecuentes vs Gasto|
| Flourish | Comparación de gasto por tipo de consumo |
| RAWGraphs | Relaciones entre categoría, local y horario |
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

**MCD 2026 · Visualización de Datos Personales**
