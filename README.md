# **Supervised-Learning-Algorithms-Comparison**

The last comprehensive evaluation of supervised learning was done in the 90’s. 
Since then, multiple different experiments emerged. 
Rich Caruana and Alexandru Niculescu-Mizil conducted their own study (CNM06) in which they compared ten different supervised learning methods. 
Here, I am attempting to replicate their results. However, instead of ten different algorithms, I compared three popular algorithms, which consisted of k-nearest neighbors, logistic regression, and decision tree. I also used various performance criteria to evaluate the learning methods.

### **Here is the link to the original study:**[ An Empirical Comparison of Supervised Learning Algorithms Using Different Performance Metrics](https://drive.google.com/file/d/1BACN9m5HB4KYKPzZrNjg_KCg0FGEd5sL/view?usp=sharing) (Empirical Comparison)

## Data Sets Used 

* [Adult Data Set](https://archive.ics.uci.edu/ml/datasets/adult)
* [Letter Recognition Data Set](https://archive.ics.uci.edu/ml/datasets/letter+recognition )
* [Covertype Data Set](https://archive.ics.uci.edu/ml/datasets/covertype)

### Method
_I followed the exact steps from the original Cornell study (Empirical Comparison)._
In this study, three datasets were picked from the UCI Machine learning repository 
(ADULT, COV_TYPE and LETTER) and three algorithms were chosen (k-nearest neighbors, 
logistic regression and decision tree). First the datasets were cleaned using the methodology 
provided in the research paper by Caruana and Niculescu-Mizil (section 2.5). For the Adult data 
I labeled all the columns and gave all the data numerical values. I was trying to determine if 
income was greater or less than 50K. For Letter I added columns then changed the first row to 
1’s depending on if the letter in that row was A – M and -1 if it was M – Z. Here I was trying to 
train our algorithms to get the correct range of letters. Lastly for COV data, when cleaning I 
added column names and calculated which value was the greatest in the last column. Once I 
determined that value, I set that particular value to 1 and the rest to -1. Then I trained our 
algorithm to get that value based on the variables. For each classifier and dataset combo, I did 
three trials for a total of 27 trials. For each trial I followed CNMO6’s procedure, I randomly 
chose a sample of 5,000 for 5-fold cross-validation to select the hyperparameters via a 
gridsearch. I matched the hyperparameter values laid out in CNM06’s section2.1. “Logistic 
Regression (LOGREG): I train both unregularized and regularized models, varying the ridge 
(regularization) parameter by factors of 10 from 10^-8 to 10^4” (Caruana, R. and NiculescuMizil). “KNN: we use 26 values of K ranging from K = 1 to K = |trainset|. We use KNN with 
Euclidean distance and Euclidean distance weighted by gain ratio. We also use distance weighted 
KNN, and locally weighted averaging. The kernel widths for locally weighted averaging varyfrom 20 to 210 times the minimum distance between any two points in the train set” (Caruana, R. 
and Niculescu-Mizil). “Decision trees (DT): we vary the splitting criterion, pruning options, and 
smoothing (Laplacian or Bayesian smoothing). We use all of the tree models in Buntine’s IND 
package (Buntine & Caruana, 1991): BAYES, ID3, CART, CART0, C4, MML, and SMML. We 
also generate trees of type C44LS (C4 with no pruning and Laplacian smoothing), C44BS (C44 
with Bayesian smoothing), and MMLLS (MML with Laplacian smoothing). See (Provost & 
Domingos, 2003) for a description of C44LS” ( Caruana, R. and Niculescu-Mizil). After this I 
selected the best hyperparameter settings for the mean over all 5 folds. Then I used these 
settings to train the model one more time and ran it against the rest of the samples to see how it 
does and measured its accuracy

