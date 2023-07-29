# Diabetes Prediction Using Machine Learning(Python)
In this project, I've taken a dataset from Kaggle based upon diabetes prediction. After checking outliers and null values in the dataset proper reduction is done. Using Random Forest Model I've checked important feature and then make a final dataset. Then I've trained 4 models(KNN, Decision Tree, Naive Bayes, Logistic Regression). Compared the accuracy and implemented the User Interface using the most accurate model.

![](https://github.com/Subhajit-Ghatak/diabetes_prediction_ML_webApp/blob/master/images/banner.png?raw=true)

---
####
## Resources

> Dataset taken from Kaggle
`<link>` <https://www.kaggle.com/datasets/akshaydattatraykhare/diabetes-dataset>

####
## 1. Diabetes_Prediction_Project.ipynb
### Modules Used 

``` $ pip install numpy ```

``` $ pip install pandas ```

``` $ pip install matplotlib ```

``` $ pip install seaborn ```

``` $ pip install scikit-learn ```

``` $ pip install scipy ```

### Data Description  
####
| glucose | bp | insulin | bmi | pedigree |	age | outcome |
 -----:| -----:| -----:| -----:| -----:| -----:| -----:|
| 148 |	72.0 |	0 |	33.6 |	0.627 |	50 |	Yes |
|85	|66.0|	0|	26.6|	0.351|	31|	No|
|183|	64.0|	0|	23.3|	0.672|	32|	Yes|
|89|	66.0|	94|	28.1|	0.167|	21|	No|
|137|	40.0|	168|	43.1|	2.288|	33|	Yes|

### Pre-processing
``` dataset.outcome.replace(['No','Yes'],[0,1], inplace=True) ```
|Before|After|
-----:| -----:| 
|Yes|1|
|No|0|
|Yes|1|
|No|0|
|Yes|1|

### Outliers Removal: Using Z-Score method
``` sns.histplot(ax=axes[0],data=having_outliers) sns.histplot(ax=axes[1],data=no_outliers) ```

![](https://github.com/Subhajit-Ghatak/diabetes_prediction_ML_webApp/blob/master/images/outliers.png?raw=true)
####
### Feature Importance: Using Random Forest
####
|Feature|Importance|
-----:| -----:|
|glucose| 0.28611949728592045|
|bmi | 0.18573718776000556|
|age| 0.17642392953409966|
|pedigree| 0.1555065645601749|
|~~bp~~| ~~0.10406010982541437~~|
|~~insulin~~| ~~0.09215271103438498~~|
####
### Accuracy Comparison After Model Training 
####
|Model|Accuracy|
-----:| -----:|
|KNN|  0.7549019607843137|
|GNB|  0.7941176470588235|
|LR|  0.7794117647058824|
|DTree|  0.7549019607843137|

![](https://github.com/Subhajit-Ghatak/diabetes_prediction_ML_webApp/blob/master/images/accuracy.png?raw=true)
### Saving Model: Gaussian Naive Bayes
``` 
import pickle
filename = 'diabetes_model.sav'
pickle.dump(naive_bayes_model, open(filename, 'wb')) 
```
#
## 2. User Interface: `prediction.py`
With the help of `diabetes_model.sav` file and streamlit library of Python I've designed the user interface.
`$ pip install streamlit`
### How To Run?
Open cmd in the same path where all the files are located specially `prediction.py` and `diabetes_model.sav`. 
Then paste this command into the cmd and hit enter.
`streamlit run "prediction.py"`

![](https://github.com/Subhajit-Ghatak/diabetes_prediction_ML_webApp/blob/master/images/output.png?raw=true)
