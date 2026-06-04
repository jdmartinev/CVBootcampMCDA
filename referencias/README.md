# Referencias

Hojas de referencia rápida para consultar **mientras trabajas en los TODOs**. No son lecturas previas — ábrelas cuando te atasques en algo concreto.

---

## Cuándo usar cada una

| Si tienes dudas sobre... | Consulta |
|--------------------------|----------|
| Cómo cargar CLIP con HuggingFace | `ref_01` § 1 |
| Cómo mover el modelo a GPU/CPU | `ref_01` § 2 |
| Por qué usar `model.eval()` | `ref_01` § 3 |
| Por qué usar `torch.no_grad()` | `ref_01` § 4 |
| Cómo mover los inputs al device | `ref_01` § 5 |
| Cómo extraer embeddings con CLIP | `ref_01` § 6 |
| Un error de device o de gradiente | `ref_01` § Errores comunes |
| Qué shape tiene mi tensor | `ref_02` § 1 |
| Cómo hacer producto matricial | `ref_02` § 2 |
| Cómo normalizar L2 | `ref_02` § 3 |
| Cómo obtener los top-k | `ref_02` § 4 |
| Cómo ordenar scores con argsort | `ref_02` § 5 |
| Cómo indexar con otro tensor | `ref_02` § 6 |
| Cómo concatenar batches | `ref_02` § 7 |
| Cómo hacer la fusión lineal | `ref_02` § 8 |
| Cómo verificar que mi código es correcto | `ref_02` § 9 |

---

## `ref_01_pytorch_hf_models` — Modelos de HuggingFace con PyTorch

!(reref_01_pytorch_hf_models.ipynb)[ref_01_pytorch_hf_models.ipynb]

Cubre el ciclo completo de uso de un modelo preentrenado: carga, configuración para inferencia, procesamiento de inputs y extracción de embeddings. Incluye la tabla de errores más comunes y sus soluciones.

**Relevante para:** TODO 1, TODO 2, TODO 5, TODO 6, TODO 7, TODO B.

---

## `ref_02_tensor_operations.md` — Operaciones con tensores

Cubre las operaciones de tensor que aparecen en los TODOs: shapes, multiplicación matricial, normalización L2, topk, argsort, indexación y concatenación. Incluye el flujo completo del pipeline con los shapes en cada paso.

<!-- FIGURA REF-01: Flujo del pipeline con shapes -->
<!-- Ver descripción abajo -->
![Flujo del pipeline con shapes](../assets/ref_pipeline_shapes.png)

**Relevante para:** TODO 3, TODO 4, TODO 5, TODO 6, TODO 7, TODO A, TODO B, TODO C.

---
