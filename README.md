# Financial-Fraud-Detection-Using-Text-Mining
Groupmate: Vickie Chang, Chris Yeung

Applied BERT based model to extract relations from 29 annual reports of listed companies and news; Used spaCy library and BERT model for name-entity recognition and relations extraction, and generated a network graph that summarises the key relation

## Methodology
![Methodology](https://user-images.githubusercontent.com/61792992/150742131-61a8e895-6b38-43e3-8c62-7b68558f840e.PNG)

29 sets of annual report and news from Reuter are inputted to the trained SpaCy pipeline to identify entities. The entity comes along with a label to classify the entity's nature. The paragraph is then split into sentences. Sentences containing less than two entities are removed as they contain no valid relations. For sentences containing three or more entities, combinations of two are generated from the multiple entities in a sentence by using itertools from the combinations package and hence each sentence contains exactly two entities. Then the relations between the entities in each sentence are manually labelled. The data are then splited into train and test set for training the BERT model from plkmo/BERT-Relation-Extraction (link:https://github.com/plkmo/BERT-Relation-Extraction). We have then apply our model on data related to Tencent as a case study target.

- [Data_preprocessing.ipynb](https://github.com/Christy-Lo/Financial-Fraud-Detection-Using-Text-Mining/blob/main/data_preprocessing.ipynb) contains code of data collection and data preprocessing.
- [Tencent_RE BERT model.ipynb](https://github.com/Christy-Lo/Financial-Fraud-Detection-Using-Text-Mining/blob/main/Tencent_RE%20BERT%20model.ipynb) contains code to implement the github repo of [plkmo/BERT-Relation-Extraction](https://github.com/plkmo/BERT-Relation-Extraction)
- The confusion matrix and network graph are generated in [Confusion_Matrix.ipynb](https://github.com/Christy-Lo/Financial-Fraud-Detection-Using-Text-Mining/blob/main/Confusion_Matrix.ipynb) and [RelationGenerator.ipynb](https://github.com/Christy-Lo/Financial-Fraud-Detection-Using-Text-Mining/blob/main/RelationGenerator.ipynb)

## Training Data
We have labelled a total of 2973 sentences with the following labels
Labels | Number | Percentage
--- | --- | ---
Colleague | 475 | 15.98%
Relative | 61 | 2.05%
Employee-Company | 407 | 13.69%
Educated-Institute | 83 | 2.79%
Founder-Company | 51 | 1.72%
Shareholder-Company | 143 | 4.81%
Within-Same-Company-Group | 78 | 2.62%
Cooperate-Partner | 76 | 2.56%
Subsidary-ParentCompany | 98 | 3.30%
Same-Entity | 97 | 3.26%
Other | 1404 | 47.23%

## Example of data
Input:
```
Subsidary-ParentCompany(e1,e2)
Sentence:  As [E1]Advance Data Services Limited[/E1] is wholly-owned by [E2]Ma[/E2] Huateng, Mr Ma has an interest in these shares as disclosed under the section of “Directors’ Interests in Securities”.
```

Output:
```
Predicted:  Subsidary-ParentCompany(e1,e2)
```

## Model Preformance and Visualization
We have choosen to train the model with 11 epoch based on the training accuracy, losses and f1 score
Parameter at Epoch 11|Value
--- | --- 
Train accuracy | 0.8767857
Losses | 0.3696946
Test F1 score | 0.2857143

Losses|F1 score
---|---
<img src="https://user-images.githubusercontent.com/61792992/150761563-155ddc26-ec7b-4b29-ad9a-ef38c8de9810.png" width="700" height="500">| <img src="https://user-images.githubusercontent.com/61792992/150761569-8936b9c2-0fe3-4763-ac68-7279f3960642.png" width="700" height="500">
Training Accuracy|
<img src="https://user-images.githubusercontent.com/61792992/150761572-c6070b03-7247-4db6-b44a-64bd32218841.png" width="700" height="500">|

#### Confusion Matrix
<img src="https://user-images.githubusercontent.com/61792992/150760319-f3e61d43-152b-4951-abcd-9be6b4b7c260.PNG" width="850" height="800">

#### Network Graph
![TencentGraph](https://user-images.githubusercontent.com/61792992/150748585-06d4109c-56a1-42ea-a75d-03a25bda3604.png)


## Acknowledgement
We would like to thanks Dr. K. P. Chow's research team for sharing their research data. We do not own any of the data. We have also refer to different tutorial throughout the project and we do not own the code. The links are stated when their code are adopted.
