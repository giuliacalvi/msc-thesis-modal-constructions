# MSc Thesis Code – Modal Constructions: Collostructional and Neural Analysis

This repository contains selected code from my MSc thesis in Linguistic Computing (Università Cattolica del Sacro Cuore).

## Overview

The project investigates Italian modal constructions using collostructional analysis, clustering techniques, masked language modeling tasks, and sentence similarity in embedding space. The repository includes notebooks implementing the following methods:

- collocation-based clustering  
- embedding-based clustering  
- modal prediction task  
- infinitive prediction task  
- sentence similarity search  

## Notebooks

- `1_clustering.ipynb` – collocation and embedding-based clustering  
- `2_infinitive_prediction.ipynb` – predicting infinitives  
- `3_modal_prediction.ipynb` – predicting modal verbs  
- `4_sentence_similarity.ipynb` – semantic similarity search  

## Data

The datasets used in this project are not included due to licensing restrictions (itTenTen20, Sketch Engine).

The experiments rely on corpus data extracted from the itTenTen20 corpus (Sketch Engine), a large web-based corpus of Italian. The corpus is lemmatized and part-of-speech tagged, and was queried using Corpus Query Language (CQL).

Modal–infinitive constructions were extracted using queries targeting sequences in which a modal verb (*dovere*, *potere*, *volere*) is immediately followed by an infinitive (tagged as `VMN0000`). Concordance lines were exported from Sketch Engine, including reference, left context, the key-word-in-context (modal + infinitive), and right context.

Due to export limitations, a maximum of 10,000 concordance lines per query was retrieved. Sentence-level data was reconstructed by merging context fields (left, KWIC, right) and removing annotation markup.

For different tasks, datasets were constructed as follows:

- **Collostructional clustering**: based on the most strongly attracted infinitives for each modal, identified via collostructional analysis; for each collexeme, concordance lines were retrieved from the corpus using targeted CQL queries of the form *modal + infinitive*, and used to build context-based representations  
- **Prediction tasks**: balanced datasets of modal–infinitive constructions were created by sampling concordance lines for each modal  
- **Sentence similarity**: a large background corpus was constructed through repeated random exports (shuffle option), combined with targeted exports for the modal verbs to ensure sufficient coverage of modal–infinitive constructions  

Collostructional analysis was conducted separately using R, and its results (e.g., lists of strongly attracted collexemes) are used as input for clustering and modeling tasks.

### Reproducibility

To reproduce the experiments, data should be extracted using Sketch Engine and CQL queries as described above.

Expected input formats:

- KWIC exports (columns: Reference, Left, KWIC, Right)  
- Sentence-level exports (columns: Reference, Sentence)  


## Setup

Install dependencies:

pip install -r requirements.txt

For the clustering notebook, install the Italian spaCy model:

python -m spacy download it_core_news_sm

## Notes

- Code is provided for demonstration and research purposes  

## Author

Giulia Calvi
