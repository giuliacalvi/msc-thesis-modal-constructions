# MSc Thesis Code – Modal Constructions: Collostructional and Neural Analysis

This repository contains selected code from my MSc thesis in Linguistic Computing (Università Cattolica del Sacro Cuore).

## Overview

This project investigates how Italian modal constructions are represented in neural language models, combining corpus-based and cognitive linguistic analysis with computational modeling.
It integrates collostructional analysis, clustering techniques, masked language modeling tasks, and sentence similarity in embedding space to compare distributional patterns derived from corpus data, reflecting usage-based and cognitively grounded regularities, with representations learned by neural models.
The goal is to evaluate how well neural models capture constructional meaning and to explore the gap between usage-based, cognitively motivated linguistic patterns and model representations. The repository includes notebooks implementing the following methods:

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

The full corpus data used in this project is not included due to licensing restrictions (itTenTen20, Sketch Engine).

The experiments rely on data extracted from the itTenTen20 corpus (Sketch Engine), a large web-based corpus of Italian. The corpus is lemmatized and part-of-speech tagged, and was queried using Corpus Query Language (CQL).

Modal–infinitive constructions were extracted using queries targeting sequences in which a modal verb (*dovere*, *potere*, *volere*) is immediately followed by an infinitive (tagged as `VMN0000`). Concordance lines were exported from Sketch Engine, including reference, left context, the key-word-in-context (modal + infinitive), and right context. Due to export limitations, a maximum of 10,000 concordance lines per query was retrieved. 

### Included derived datasets

This repository includes **processed outputs from collostructional analyses**, which serve as input to the modeling tasks:

- `colldov_out.csv` – Simple Collexeme Analysis results for *dovere*
- `collpot_out.csv` – Simple Collexeme Analysis results for *potere*
- `collvol_out.csv` – Simple Collexeme Analysis results for *volere*
- `covar_out.csv` – Covarying Collexeme Analysis results across modal constructions

These datasets were generated in R and contain association scores used to derive:
- ranked lists of infinitives significantly attracted to each modal construction  
- association patterns between modal verbs and infinitives (used for modal prediction)  

### Task-specific dataset construction

- **Collostructional clustering**: based on the most strongly attracted infinitives for each modal, identified via collostructional analysis; for each collexeme, concordance lines were retrieved using targeted CQL queries of the form *modal + infinitive*, and used to build context-based representations  
- **Prediction tasks**: balanced datasets of modal–infinitive constructions were created by sampling concordance lines for each modal  
- **Sentence similarity**: a large background corpus was constructed through repeated random exports (shuffle option), combined with targeted exports for the modal verbs to ensure sufficient coverage of modal–infinitive constructions  

Collostructional analysis was conducted separately in R, and its outputs are used as input for the clustering and modeling tasks implemented in this repository.

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
