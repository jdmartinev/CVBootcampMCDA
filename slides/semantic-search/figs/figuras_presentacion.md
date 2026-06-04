# Figuras para la presentación — Búsqueda Semántica Multimodal con CLIP

Cada figura reemplaza un placeholder `[FIGURA: ...]` en la presentación.  
Formato de entrega: PNG con fondo blanco, resolución mínima 1200×900 px.  
El estilo debe ser **minimalista y académico**: líneas limpias, sin adornos, sin texto decorativo.  
Paleta: negro `#1A1A1A`, gris medio `#666666`, gris claro `#DDDDDD`. Solo usar color cuando sea estrictamente necesario para distinguir elementos (clusters, modalidades).

---

## FIGURA 1 — Slide 3: Píxeles vs Representación

**Placeholder izquierdo:**  
Fragmento ampliado de una imagen de un perro mostrando la cuadrícula de píxeles. Cada celda tiene su valor RGB visible (ej. `[255, 180, 90]`). La imagen original pequeña en la esquina superior izquierda con una flecha hacia el zoom. Estilo: cuadrícula nítida, valores en fuente monospace pequeña.

**Placeholder derecho:**  
Dos partes:
1. Arriba: un vector horizontal de 512 elementos representado como una barra de celdas de ancho variable (primeras 8-10 visibles con valores como `[0.32, -0.18, 0.71, ...]`, luego `...` y las últimas 3). Etiqueta `ℝ⁵¹²` a la derecha.
2. Abajo: dos vectores en un espacio 2D simplificado. Un vector azul etiquetado "imagen perro" y un vector rojo etiquetado "texto: a dog". Ambos apuntando en la misma dirección con ángulo θ pequeño entre ellos. Eje X e Y sin etiqueta (es solo ilustrativo).

---

## FIGURA 2 — Slide 4: Embeddings — clusters

Espacio 3D simplificado (representado en perspectiva isométrica o vista oblicua).  
Tres clusters de puntos bien separados:
- 5-6 puntos **rojos** con etiqueta pequeña "perros" (uno tiene miniatura de perro)
- 5-6 puntos **azules** con etiqueta "gatos" (uno tiene miniatura de gato)
- 5-6 puntos **verdes** con etiqueta "autos" (uno tiene miniatura de auto)

Flechas dobles cortas entre puntos del mismo cluster con etiqueta "cercanos".  
Flecha larga entre clusters con etiqueta "lejanos".  
Ejes X, Y, Z dibujados como líneas simples desde el origen. Sin cuadrícula.

---

## FIGURA 3 — Slide 5: Similitud coseno — tres diagramas de vectores

Tres diagramas pequeños independientes (uno por columna de la slide).  
Cada uno: plano 2D con dos vectores saliendo del origen.

1. **Similar (≈1):** Dos vectores **a** y **b** casi paralelos, ángulo θ muy pequeño (~15°). Arco de ángulo anotado `θ ≈ 15°`, etiqueta `sim ≈ 1`.
2. **Sin relación (≈0):** Vectores perpendiculares, ángulo `θ = 90°`, etiqueta `sim = 0`.
3. **Opuesto (≈-1):** Vectores apuntando en sentidos contrarios, ángulo `θ ≈ 175°`, etiqueta `sim ≈ −1`.

Vectores en negro/gris. Arcos de ángulo en gris claro. Todo minimalista.

---

## FIGURA 4 — Slide 6: Normalización L2 — esfera unitaria

Esfera en 3D (wireframe o semi-transparente). Color gris claro.  
Cuatro o cinco vectores de distintas longitudes originales (líneas discontinuas desde el origen) que se **proyectan** sobre la superficie de la esfera (líneas sólidas desde el origen hasta la esfera).  
Todos los puntos proyectados están sobre la superficie.  
Dos de ellos marcados **a** y **b** con un arco entre ellos y la etiqueta `cos(θ) = a·b` anotada.  
El radio de la esfera etiquetado `‖v‖ = 1`.

---

## FIGURA 5 — Slide 7: Espacio compartido CLIP

Diagrama horizontal en tres columnas:

**Izquierda — par correcto:**
- Miniatura de imagen de un perro (cuadrado ~100px)
- Flecha → caja "ViT encoder" → vector pequeño `I₁`

**Centro:**
- Espacio común representado como un plano o esfera simplificada
- Dos puntos muy cercanos: `I₁` (imagen) y `T₁` (texto "a dog playing") — unidos por línea corta con etiqueta `sim ≈ 0.28`
- Otros dos puntos alejados: `I₂` (imagen auto) y `T₁` — unidos por línea larga con etiqueta `sim ≈ 0.08`

**Derecha:**
- Texto "a dog playing" → caja "Text encoder" → vector `T₁`
- Texto "a red car" → caja "Text encoder" → vector `T₂` (más pequeño, secundario)

Flechas negras entre elementos. Cajas con borde gris, sin relleno especial.

---

## FIGURA 6 — Slide 8: Histograma distribuciones similitud

Histograma con dos distribuciones superpuestas:
- **Azul semitransparente:** "Pares aleatorios" — campana centrada en ~0.15, más ancha
- **Rojo semitransparente:** "Pares correctos" — campana centrada en ~0.28, más estrecha, superpuesta parcialmente con la azul
- Dos líneas verticales discontinuas en las medias: azul en 0.15, roja en 0.28
- Etiquetas: `media = 0.15` y `media = 0.28`
- Eje X: "Similitud coseno" de 0.0 a 0.5
- Eje Y: "Densidad"
- Leyenda en la esquina superior derecha
- Sin cuadrícula o cuadrícula muy sutil gris claro

---

## FIGURA 7 — Slide 9: Pipeline de búsqueda

Diagrama de flujo horizontal con 4 etapas. Flechas gruesas negras entre etapas.

**Etapa 1 — Corpus:**  
Icono de galería (cuadrado con borde, 3 thumbnails superpuestos). Etiqueta: "2 000 imágenes".

**Etapa 2 — Índice vectorial:**  
Representación de matriz rectangular estrecha `N×512` (columnas comprimidas, filas visibles). Etiqueta: "Índice vectorial". Nota pequeña debajo: "~5 min, una sola vez".

**Etapa 3 — Búsqueda:**  
Caja dividida verticalmente:
- Izquierda: texto `query → (1×512)` con flecha hacia abajo
- Derecha: `· (N×512)ᵀ → scores (N,)`
Nota debajo: `< 1 ms`.

**Etapa 4 — Resultados:**  
Tres miniaturas de imágenes ordenadas `#1`, `#2`, `#3` con barras de score decrecientes junto a cada una.

Todo en blanco y negro. Cajas con borde gris `#DDDDDD`. Texto en Calibri o Arial.

---

## FIGURA 8 — Slide 13: UMAP — modality gap

Gráfico de dispersión 2D limpio (estilo publicación):
- ~40 círculos **azules** (⬤) agrupados en la mitad izquierda — etiqueta "Imágenes"
- ~40 triángulos **rojos** (▲) agrupados en la mitad derecha — etiqueta "Textos"
- ~10 líneas grises finas conectando pares imagen-texto (cruzando el espacio vacío central)
- Sin ejes numéricos (solo etiquetas "UMAP dim 1" y "UMAP dim 2")
- Leyenda arriba a la derecha
- Título interno opcional: "300 pares imagen-texto"

---

## FIGURA 9 — Slide 15: Diagrama RAG

Diagrama de flujo horizontal con 6 pasos. Estilo: cajas redondeadas con borde, flechas entre ellas.

1. **"Pregunta del usuario"** — caja con icono de persona/chat
2. **"Query embedding"** — caja con fórmula pequeña `(1×512)`
3. **"Búsqueda vectorial"** — caja con borde **más grueso** o fondo gris claro y etiqueta inferior en rojo/cursiva: *"esto es lo que acabas de implementar"*
4. **"Top-k documentos"** — caja con 3 líneas de texto representadas como rectángulos
5. **"[pregunta + contexto] → LLM"** — caja con icono de modelo/cerebro
6. **"Respuesta fundamentada"** — caja con icono de texto/documento

Flechas negras entre cada caja. Sin colores excepto el borde destacado del paso 3.

---

## FIGURA 10 — Slide 17: Timeline frontier AI

Timeline horizontal lineal.  
Línea de tiempo gruesa con años marcados: `2021`, `2022`, `2023`, `2024`, `2025`.

Cajas encima/debajo de la línea (alternadas) con:
- **2021:** "CLIP" — "Espacio compartido imagen-texto"
- **2022:** "DALL-E 2 / Stable Diffusion" — "texto → CLIP embedding → imagen"
- **2023:** "GPT-4V" — "encoder de visión alineado con LLM"
- **2024:** "Gemini / GPT-4o" — "multimodal nativo desde el inicio"
- **2025:** "Modelos de video" — "video, audio, código en un solo espacio"

Línea inferior a lo largo de toda la timeline con etiqueta:  
`"hereda el concepto de alineamiento de espacios de representación"`

Estilo: cajas con borde gris, texto en negro, línea de tiempo negra. Sin colores de marca.

---

## FIGURA 11 — Slide 18: Alineamiento de espacios multimodal

Diagrama radial con un nodo central y 5 modalidades alrededor.

**Centro:** círculo gris medio con texto "Espacio compartido (512-D)".

**Nodos externos** (círculos más pequeños con borde, sin relleno) conectados al centro con flechas bidireccionales:
- "Texto" — arriba
- "Imagen" — arriba derecha
- "Audio" — derecha
- "Video" — abajo derecha
- "Código" — abajo

Flechas bidireccionales (←→) desde cada nodo hacia el centro.  
Estilo: minimalista, todo en negro/gris. Sin colores por modalidad.
