# VLM Bootcamp: Semantic Image Search with CLIP

## Goal

Build a semantic image search engine using CLIP.

Students will learn how Vision-Language Models represent images and text in a shared embedding space, and how this enables zero-shot retrieval.

---

## Learning Outcomes

By the end of the bootcamp, students will be able to:

- Explain the basic idea behind CLIP and multimodal embeddings.
- Encode images and text into a shared vector space.
- Compute similarity between text queries and images.
- Build a simple image retrieval system.
- Improve retrieval results using prompt engineering.
- Evaluate retrieval performance using retrieval metrics.

---

## Bootcamp Schedule

| Time | Activity |
|---|---|
| 08:00 - 08:30 | Introduction to VLMs and CLIP |
| 08:30 - 09:30 | Build the baseline retrieval system |
| 09:30 - 10:00 | Retrieval metrics and evaluation |
| 10:00 - 11:30 | Mini-competition |
| 11:30 - 12:00 | Presentations and discussion |

---

## Repository Structure

```text
vlm-clip-bootcamp/
│
├── README.md
├── requirements.txt
│
├── notebooks/
│   ├── 01_clip_baseline.ipynb
│   ├── 02_image_retrieval.ipynb
│   └── 03_competition_submission.ipynb
│
├── data/
│   ├── images/
│   ├── queries.csv
│   ├── ground_truth.csv
│   └── sample_submission.csv
│
├── src/
│   ├── clip_utils.py
│   ├── retrieval.py
│   ├── evaluation.py
│   └── visualization.py
│
├── submissions/
│   └── sample_submission.csv
│
└── assets/
    └── figures/
```

---

## Dataset

The dataset contains:

- A collection of images.
- A set of text queries.
- A ground-truth file indicating relevant images for each query.
- A sample submission file.

Recommended datasets:

- Oxford Pets
- Food101
- Caltech101
- Fashion products
- Colombian biodiversity
- Tourism images

Recommended dataset size:

- Between 200 and 1000 images.

---

## Input Files

### queries.csv

```csv
query_id,query_text
q001,a photo of a small white dog
q002,a plate of pasta with tomato sauce
q003,a red flower with long petals
```

### ground_truth.csv

```csv
query_id,image_id
q001,img_023.jpg
q001,img_145.jpg
q002,img_087.jpg
```

### sample_submission.csv

```csv
query_id,image_id_1,image_id_2,image_id_3,image_id_4,image_id_5
q001,img_001.jpg,img_002.jpg,img_003.jpg,img_004.jpg,img_005.jpg
q002,img_006.jpg,img_007.jpg,img_008.jpg,img_009.jpg,img_010.jpg
```

---

## Competition Task

Given a text query, retrieve the top-k most relevant images.

Example:

```text
Query:
"a dog running on grass"

Output:
Top 5 most relevant images
```

Students should submit a ranked list of image predictions for each query.

---

## Baseline Method

The baseline system uses CLIP as follows:

1. Load a pretrained CLIP model.
2. Encode all images.
3. Encode text queries.
4. Compute cosine similarity.
5. Return the top-k images.

---

## Mini-Competition Rules

Students compete by improving the baseline retrieval system.

Students are NOT allowed to train large models.

### Allowed Improvements

- Better prompts.
- Multi-prompt averaging.
- Query expansion.
- Embedding normalization.
- Image preprocessing.
- Model comparison.
- Reranking strategies.

### Not Allowed

- Manual labeling of test queries.
- Hardcoding query-image pairs.
- Using ground-truth labels from the test set.

---

## Evaluation

Main metric:

- Recall@5

Optional metrics:

- Recall@1
- Recall@10
- Mean Reciprocal Rank (MRR)
- Mean Average Precision (mAP)

### Recall@5

A prediction is considered correct if at least one relevant image appears in the top 5 retrieved images.

---

## Deliverables

Each team must submit:

1. A notebook with the solution.
2. A CSV file with predictions.
3. A short explanation of the strategy used.

---

## Suggested Explanation Format

```md
# Team Name

## Strategy

Briefly describe your retrieval approach.

## Improvements over baseline

Explain what you changed.

## Results

Report your Recall@5 score.

## Reflections

Mention one success and one limitation.
```

---

## Suggested Notebooks

### 01_clip_baseline.ipynb

Topics:

- Load CLIP.
- Encode images.
- Encode text.
- Compute similarity.

### 02_image_retrieval.ipynb

Topics:

- Build retrieval functions.
- Visualize top-k results.
- Test prompts.

### 03_competition_submission.ipynb

Topics:

- Generate predictions.
- Save submission CSV.
- Evaluate locally.

---

## Technical Stack

Required libraries:

```txt
torch
torchvision
transformers
pillow
numpy
pandas
matplotlib
scikit-learn
tqdm
```

Optional libraries:

```txt
faiss-cpu
gradio
umap-learn
```

---

## Suggested Starter Functions

```python
load_clip_model()
encode_images()
encode_texts()
compute_similarity()
retrieve_top_k()
evaluate_recall_at_k()
plot_retrieval_results()
```

---

## Discussion Questions

- Why can CLIP retrieve images without task-specific training?
- What types of prompts worked best?
- What types of prompts failed?
- How does prompt wording affect embeddings?
- What are the limitations of semantic retrieval?
- How could this system evolve into a multimodal RAG system?

---

## Possible Extensions

For advanced students:

- Add a Gradio interface.
- Compare CLIP vs SigLIP.
- Add FAISS indexing.
- Build a visual recommendation system.
- Add metadata filtering.
- Use a VLM to explain retrieved images.

---

## Suggested Repository Name

```text
vlm-clip-semantic-search-bootcamp
```
