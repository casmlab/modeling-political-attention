# Modeling Political Attention

Code in this repo generated the models described in our __ICWSM 2020__ paper:

> Hemphill, L., & Schöpke-Gonzalez, A. M. (2020). Two Computational Models for Analyzing Political Attention in Social Media. *Proceedings of the AAAI Conference on Web and Social Media, 14*(1), 260–271. [https://www.aaai.org/ojs/index.php/ICWSM/article/view/7297](https://www.aaai.org/ojs/index.php/ICWSM/article/view/7297)

## data/

This directory provides the data that we used to train models and that we made predictions on with models. Due to Twitter terms of service limitations, we did not shared raw tweet data in this public repo. Instead, you will find our processed dataset of the 115th Congress' tweets at `data/congress_115/congress115.csv.gz`, with the file called `data/congress_115/congress115_codebook.csv` explaining column labels for this dataset.

Russell's raw data is not publicly available at this time. Processed datasets which we use to train and test our best-performing supervised models are available at `data/russell/russell_processed_0.9.csv.gz`. The file `data/russell/russell_liwc_w2v_both.csv.gz` describes the tweetset that we used for training and testing supervised classifiers with word2vec and LIWC2015 features added. See the following two papers for additional details on Russell's raw data:
    
> Russell, A. (2017). U.S. Senators on Twitter: Asymmetric Party Rhetoric in 140 Characters. *American Politics Research*, *46*(4). [https://doi.org/10.1177/1532673X17715619](https://doi.org/10.1177/1532673X17715619)

> Russell, A. (2018). The Politics of Prioritization: Senators’ Attention in 140 Characters. *The Forum*, *16*(2), 331–356. [https://doi.org/10.1515/for-2018-0020](https://doi.org/10.1515/for-2018-0020)

The directory `data/unsupervised/model_source provides` data that used to train our unsupervised model. The directory `data/unsupervised/model_output` provides data that our unsupervised models produced. The file `data/unsupervised/model_output/unsup_codebook.csv` provides annotator labels for unsupervised topics returned by our model. Note that though our model produced 50 topics, annotators grouped some of these topics together due to thematic similarity, resulting in a total of 35 unsupervised topics.


## notebooks/models/create/feature_extraction/

This directory provides jupyter notebooks that walk a user through the steps we took extract LIWC (liwc) and word2vec (w2v) features for use in classifier training and testing. We provide this code for transparency and reproducibility. The final datasets created by this code are available in the parent directory's "data" and "models" folders. Intermediate datasets produced by the code are not available. You will need to re-run the code to produce these. For those that would like to reproduce processes, we provide descriptions of each notebook's function here:

>Notebook Name: `notebooks/models/create/feature_extraction/1.0-ams-build-original-w2v-model.ipynb`

>Notebook Function: Builds a word2vec vocabulary from Russell's tweets and trains an original word2vec model

>Notebook Name: `notebooks/models/create/feature_extraction/2.0-ams-w2v-featureextraction-original.ipynb`

>Notebook Function: Extract original word2vec features from Russell's tweets using model from previous notebook

>Notebook Name: `notebooks/models/create/feature_extraction/3.0-ams-w2v-featureextraction-pretrained.ipynb`

>Notebook Function: Extract pretrained word2vec features from Russell's tweets using [Frederic Godin's model](https://www.kaggle.com/hachemsfar/cbigru/version/1). The model is originally created by Fréderic Godin, but the creator's link to the w2v model is no longer active. You will need to download `word2vec_twitter_model.bin` from the link to `external_repositories/word2vec-twitter` in order to run this notebook.


## notebooks/models/create/supervised/

This directory provides jupyter notebooks that walk a user through the steps we took to train and test supervised classifiers. For those that would like to reproduce processes, we provide descriptions of each notebook's function here:
    
> Notebook Name: `notebooks/models/create/supervised/1.0-ams-create-best-classifiers.ipynb`

>Notebook Function: Creates best performing dummy, naive bayes, and logistic regression classifiers

>Notebook Name: `notebooks/models/create/supervised/2.0-ams-create-w2vliwc-classifiers.ipynb`

>Notebook Function: Creates logistic regression and support vector machine classifiers with word2vec and LIWC2015 features


## notebooks/models/create/unsupervised/

This directory provides a jupyter notebook that walks a user through the steps we took to build our unsupervised model. For those that would like to reproduce processes, we provide a description of this notebook's function here:

> Notebook Name: `notebooks/models/create/unsupervised/1.0-ams-unigram-lda-model-MALLET.ipynb`
> 
> Notebook Function: Train unsupervised model (NOTE that some of this code must be implemented in a command line interface)

## notebooks/models/run/

This directory provides a Jupyter notebook that walks a user through the steps we took to compare the outputs of our supervised and unsupervised models. For those that would like to reproduce processes, we provide a description of this notebook's function here:
    
> Notebook Name: `notebooks/models/run/1.0-ams-label-comparisons.ipynb`
> 
> Notebook Function: Load supervised classifiers, label tweets with supervised classifier predictions, perform comparison between supervised and unsupervised model labeling patterns


## models/

This directory provides the best performing supervised and unsupervised models that we discuss in our paper under models/best. It also provides the original w2v vocabulary developed from Russell's tweetset in `models/feature_extraction`.


## reports/

This directory provides raw figure and table files used in our paper.


## external_repositories/

This folder provides external repositories used in developing models, including the code necessary to use Frederic Godin's pretrained word2vec model's vocab and MALLET's LDA model wrapper. You will need to download `word2vec_twitter_model.bin` from [https://www.kaggle.com/hachemsfar/cbigru/version/1](https://www.kaggle.com/hachemsfar/cbigru/version/1) (i.e., Godin's vocabulary) to `external_repositories/word2vec-twitter` in order to run this word2vec code.
