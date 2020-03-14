## Machine Learning
### Summary
This repository contains a code with three models that were developed to determine a False Positive, a candidate or an actual hidden planet outside our solar system. <br>
### Technical Details
In order to run the code, it is required Visual Studio or Jupyter Notebook.<br>
### Screenshots
MinMax.JPG<br>
![MinMax](MinMax.JPG)<br><br>
SVC.JPG<br>
![SVC](SVC.JPG)<br><br>
GridSearch.JPG<br>
![GridSearch](GridSearch.JPG)<br><br>
### Explanations<br>
The outcome is shown in screenshots for reference purpose of the public.<br>

### Summary about findings<br>
Two models were developed to determine a False Positive, a candidate or an actual hidden planet outside our solar system. The first model was SVC linear scaled with the initial and last quartile (MinMax). In addition, a variant of the same model was built with a standard-lineal scaler providing the best result of the analysis at 89%. Finally, the GridSearchCV with parameters C:10 and gamma:0.001 slightly underfitted in comparison with the best score. <br>
Introduction <br>
The koi_disposition was the dependent variable and was calculated based on independent variables with numerical data. However, some columns included unique numerical data which was impossible to analyze. Therefore, the unnecessary variables were not considered such as “rowed”, “kepid”, “kepoi_name”, “kepler_name”, “koi_pdisposition”, “koi_score” and “koi_tce_delivname”. <br>
A comparison of each performance <br>
First, the model score for linear SVC was 85.36% in comparison with 84.62% provided by the testing data scaled through MinMax. Having almost the same score in testing and training, the model was considered to be in the ‘sweet spot’.  <br>

MinMaxScaler()<br>
                precision    recall  f1-score   support

     CANDIDATE       0.15      0.01      0.02       529
     CONFIRMED       0.08      0.03      0.04       568
     FALSE POSITIVE  0.46      0.83      0.60      1089

     micro avg       0.42      0.42      0.42      2186
     macro avg       0.23      0.29      0.22      2186
     weighted avg    0.29      0.42      0.31      2186

Training Data Score: 0.8536139066788655<br>
Testing Data Score: 0.8462946020128088<br>

The same model scaled with StandardScaler showed a Training Data Score at 89.17% while its testing data derived an 88.92%. But for the small difference between both scores, the model would be under or over fitted. <br>

StandardScaler()
                precision    recall  f1-score   support

     CANDIDATE       0.29      0.02      0.04       529
     CONFIRMED       0.00      0.00      0.00       568
     FALSE POSITIVE  0.49      0.98      0.66      1089

     micro avg       0.49      0.49      0.49      2186
     macro avg       0.26      0.33      0.23      2186
     weighted avg    0.32      0.49      0.34      2186

Training Data Score: 0.8917352851479109<br>
Testing Data Score: 0.889295516925892<br>

Second, the ‘C’:10 and ‘gamma’:0.0001 GridSearchCV reached a model score just over 87% compared to its testing score at 86.96%. Hardly ever does not GrisSearchCV reach an optimal point but also it never misleads the sweet point far away from its best calculated parameters. <br>

GridSearchCV()
                precision    recall  f1-score   support

     CANDIDATE       0.27      0.05      0.08       529
     CONFIRMED       0.18      0.16      0.17       568
     FALSE POSITIVE  0.50      0.74      0.60      1089

     micro avg       0.42      0.42      0.42      2186
     macro avg       0.32      0.31      0.28      2186
     weighted avg    0.36      0.42      0.36      2186

Testing Data Score : 0.8696248856358646 <br>
Training Data Score: Best Parameters {'C': 10, 'gamma': 0.0001}<br>
Training Data Score: Best Score  0.8720646538578835<br>

Given narrow distances between training and testing scores, the best of the previous models will be the one with the highest accuracy such as the SVC standard scaler. It is worth to mention that GrisSearchCV estimated a better score than the SVC with MinMax scaler. 
Any assumptions you can make based on the model.<br>
The classification report shows the harmonic mean of precision and recall, also known as f1-score, from 60% to 66 % in False Positive Categories. (F1 Score = 2*(Recall * Precision) / (Recall + Precision)). For instance, “Precision is the ratio of correctly predicted positive observations to the total predicted positive observations. On the other hand, recall is the ratio of correctly predicted positive observations to the all observations in actual class. The support is the number of samples of the true response that lie in that class.” (https://blog.exsilio.com/all/accuracy-precision-recall-f1-score-interpretation-of-performance-measures/)<br>
Is your model good enough to predict new exoplanets? Why or why not?<br>
Generally speaking, it is possible to point out a False Positive with a greater degree of certainty than identify or confirm a planet. Once the False Positives are discarded, a second analysis must be run to distinguish between genuine planets and False Positives leaked into other categories. <br>
It can be possible to determine a false positive with a probability of success up to 89% if the following variables are taken into account:<br>

rowid<br>
kepid<br>
kepoi_name<br>
kepler_name<br>
koi_disposition<br>
koi_pdisposition<br>
koi_score<br>
koi_fpflag_nt<br>
koi_fpflag_ss<br>
koi_fpflag_co<br>
koi_fpflag_ec<br>
koi_period<br>
koi_period_err1<br>
koi_period_err2<br>
koi_time0bk<br>
koi_time0bk_err1<br>
koi_time0bk_err2<br>
koi_impact<br>
koi_impact_err1<br>
koi_impact_err2<br>
koi_duration<br>
koi_duration_err1<br>
koi_duration_err2<br>
koi_depth<br>
koi_depth_err1<br>
koi_depth_err2<br>
koi_prad<br>
koi_prad_err1<br>
koi_prad_err2<br>
koi_teq<br>
koi_teq_err1<br>
koi_teq_err2<br>
koi_insol<br>
koi_insol_err1<br>
koi_insol_err2<br>
koi_model_snr<br>
koi_tce_plnt_num<br>
koi_tce_delivname<br>
koi_steff<br>
koi_steff_err1<br>
koi_steff_err2<br>
koi_slogg<br>
koi_slogg_err1<br>
koi_slogg_err2<br>
koi_srad<br>
koi_srad_err1<br>
koi_srad_err2<br>
ra<br>
dec<br>
koi_kepmag<br>


What would make your model be better at predicting new exoplanets?<br>
The model would be more significant to confirm a planet if more relevant and independent variables are integrated to the model or the noise produced by the False positives is removed permanently of the analysis. <br>
