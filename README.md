# Bioinfo Text Classification — PubMed RCT

Projet de classification automatique de phrases d'abstracts biomédicaux issus du dataset PubMed 200k RCT.

## Objectif

Classifier chaque phrase d'un abstract en 5 catégories :
- BACKGROUND — contexte de l'étude
- OBJECTIVE — objectif de la recherche
- METHODS — méthodologie utilisée
- RESULTS — résultats obtenus
- CONCLUSIONS — conclusions tirées

## Dataset

PubMed 200k RCT (https://github.com/Franck-Dernoncourt/pubmed-rct)
200 000 phrases annotées issues d'essais cliniques randomisés.

## Modèles comparés

| Modèle | Accuracy | F1-Score (macro) |
|--------|----------|-----------------|
| Baseline TF-IDF + Régression Logistique (bigrammes) | 0.630 | 0.538 |
| Word Embeddings biomédicaux pré-entraînés | 0.670 | 0.580 |
| Deep Learning BiLSTM (TensorFlow/Keras) | 0.835 | 0.769 |

## Architecture du modèle LSTM

- Embedding (vocab=10 000, dim=128)
- Bidirectional LSTM (32 unités) + Dropout 0.5
- Bidirectional LSTM (16 unités) + Dropout 0.5
- Dense (64, ReLU) + Dropout 0.5
- Dense (5, Softmax)

Entraine avec EarlyStopping et ModelCheckpoint sur 200 000 exemples.

## Installation

pip install scispacy tensorflow scikit-learn pandas matplotlib seaborn pyunpack patool numpy

## Auteurs

Maram Sall GUEYE et Aya BALIS
