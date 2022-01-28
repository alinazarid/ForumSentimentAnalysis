
## 1. Overview

Automatically triaging posts in a forum aimed at users who struggle with mental health can be an efficient way to provide necessary support. We experiment with three models based on different machine learning techniques and adopt distinct feature sets. We observe that the model, which takes into account the sequential property of the dataset, outperforms other models.

The natural language of the dataset is English. This data was released on May 07, 2017 and provided to our team by [Dr. Casey Kennington](caseykennington@boisestate.edu). The data includes:
* Training data: The XML formatted posts that can be used for training the algorithm.
* Testing data: The XML formatted posts that can be used for evaluation the algorithm.
* labels.tsv: This file contains a tab separated list of post annotations. The columns are: Post (message) ID, Triage label and Fine-grained triage label.
* author_rankings.tsv: This file contains a tab-separated list of author "rankings". The columns are: Author ID and Author ranking on the forums
* author_rankings_summary.tsv: This file contains a tab-separated list of possible user rankings within the forum. It contains Author ranking on the forums, ReachOut status which indicates whether the user is ReachOut-affiliated (staff, a moderator or an invited poster) or a member of the general public.

The data for this project is considered confidential and is not available to public.

## 2. Content

Extract Project_Torsi_Nazari.tar.gz

Run jupyter-notebook from Project_Torsi_Nazari folder

The extracted folder includes:
    1. README.md
    2. XML2PKL.ipynb
    3. Doc2vec.ipynb
    4. author_activity.ipynb
    5. NB.ipynb
    6. NN.ipynb
    7. RNN.ipynb
    8. Report.pdf
    
## 3. Content Information

### README.md

This file.
 
### XML2PKL.ipynb

This notebook reads XML files and stores the required information away in a dataframe. Then save it as a pickle file.

This code needs to run once for training data and once for testing data. The instruction is as follows:
* Open *XML2PKL.ipynb* from the jupyter browser console
* Provide appropriate directories which contain the data. For example:
    * data_dir = "../testing_data/posts"
    * labels_dir = '../testing_data/labels.tsv'
    * ranks_dir = '../testing_data/author_rankings.tsv'
    * affiliation_dir = '../testing_data/author_rankings_summary.tsv'
* Provide a directory to save the pickle. For example:
    * result_dir = "../testin_data/test.pkl" 
* Run the entire notebook (It may take 30 to 40 minutes depending on the user's system)

### Doc2vec.ipynb

This notebook contains a Doc2Vec model. It reads the training pickle file and returns a Doc2Vec model.

The instruction is as follows:
* Open *Doc2vec.ipynb* from the jupyter browser console
* Provide the directory for the training data. For example:
    * train_direct = '../training_data/train.pkl'
* Provide a directory to save the model For example: 
    * result_direct = "d2v.model2"
* Run the entire notebook (It may take 30 to 40 minutes depending on the user's system)

### author_activity.ipynb

This notebook was written to observe the activity of individual authors and to generate a graph illustrating their activity.

The instruction is as follows:
* Open *author_activity.ipynb* from the jupyter browser console
* Provide the directory for the training data.
* Run the entire notebook

The graph can be observed at the bottom of the notebook.

### NB.ipynb

This notebook was written to implement a Naive Bayes classifier for the task. It includes 3 sections.
* Naive Bay's Classifier
* Classifying based on ranks
* Combining rank and NB

The instruction is as follows:
* Open *NB.ipynb* from the jupyter browser console
* Provide the directory for the training data. 
* Provide the directory for the testing data. For example:
    * test_direct = '../testing_data/test.pkl'
* Run the entire notebook

The Accuracy for each section is reported under "Accuracy".

### NN.ipynb

This notebook was written to implement a neural network for this task. There are three sections, each a model fed with a different feature set. The sections:
* NN with embedding (FS1)
* NN with embedding and sentiments (FS2)
* NN with embedding, sentiments, ranks (FS3)

The instruction is as follows:
* Open *NN.ipynb* from the jupyter browser console
* Provide the directory for the training data. 
* Provide the directory for the testing data.
* Provide the directory for the doc2vec model. For example:
    * d2v_direct = "../Doc2Vec/d2v.model2"
* Run the entire notebook

The accuracy for each section is reported under "Accuracy".

### RNN.ipynb

This script is written to implement recurrent neural network for this task. Two versions of model are developed. The instruction is as follows:
* Open *RNN.ipynb* from the jupyter browser console
* Provide the directory for the training data.
* Provide the directory for the testing data. 
* Provide the directory to save the version 1 of RNN model with a single LSTM layer:
    * model01_direct = "./models/RNN_model_v1.9.hdf5"
* Provide the directory to save the version 2 of RNN model with an additional CNN layer:
    * model02_direct = "./models/RNN_model_v2.9.hdf5"
* Run the entire notebook

The accuracy for each section is reported under "Evaluation".

### Report.pdf

A comprehensive report of the project

Credits go to:
alinazarid@gmail.com
benedettatorsi@u.boisestate.edu
