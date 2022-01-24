# Financial-Fraud-Detection-Using-Text-Mining
Groupmate: Vickie Chang, Chris Yeung [github profile]

Applied BERT based model to extract relations from 29 annual reports of listed companies and news; Used spaCy library and BERT model for name-entity recognition and relations extraction, and generated a network graph that summarises the key relation

## Methodology
![Methodology](https://user-images.githubusercontent.com/61792992/150742131-61a8e895-6b38-43e3-8c62-7b68558f840e.PNG)

29 sets of annual report and news from Reuter are inputted to the trained SpaCy pipeline to identify entities. The entity comes along with a label to classify the entity's nature. The paragraph is then split into sentences. Sentences containing less than two entities are removed as they contain no valid relations. For sentences containing three or more entities, combinations of two are generated from the multiple entities in a sentence by using itertools from the combinations package and hence each sentence contains exactly two entities. Then the relations between the entities in each sentence are manually labelled. The data are then splited into train and test set for training the BERT model from plkmo/BERT-Relation-Extraction (link:https://github.com/plkmo/BERT-Relation-Extraction).

- "Data_preprocessing.ipynb" contains code of data collection and data preprocessing.
- "Tencent_RE BERT model.ipynb" contains code to implement the github repo of plkmo/BERT-Relation-Extraction (link:https://github.com/plkmo/BERT-Relation-Extraction)
- The confusion matrix and network graph are generated in "Confusion_Matrix.ipynb" and "RelationGenerator.ipynb"

## Acknowledgement
We have refer to different tutorial throughout the project and we do not own the code. The links are stated when their code are adopted. We would also thanks Dr. K. P. Chow's research team for sharing data. We do not own any of the data.
