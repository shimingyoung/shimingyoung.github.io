---
layout: post
title: Is Anomaly Detection Better? 
---

---
Recently we had an article published titled as _Anomaly Detection Outperforms Logistic Regression in Predicting Outcomes in Trauma Patients_ in [Prehospital Emergency Care](http://www.tandfonline.com/doi/full/10.1080/10903127.2016.1241327).
---

---
The anomaly detection (AD) method was compared with logistic regression (LR), a very commonly used prediction or statistical analysis tool in medicine research. Given the characteristics of the dataset in this paper, AD shows some promising performances. Based on my past experience of using LR as a prediction tool, I think AD could be considered when the data **(1)** have highly imbalanced outcomes, e.g. very small proportion of one label over another label. **(2)** not so many feature variables **(3)** the two ends of feature variable values are associated to the same label. However, often if the dataset is large enough with many feature variable, or the outcome labels are balanced, AD does not show much advantage over LR.
---

---
AD is a name often seen in signal processing. In machine learning, this method is known as the one-class classification. In this paper, the kernel Reed-Xiaoli detector  _y=(x-\mu)^TK^{-1}(x-\mu)_, where the matrix K is the covariance matrix of the training set. If we compare this to the quadratic discriminant analysis [(QDA) method](http://scikit-learn.org/stable/modules/lda_qda.html), it is the part inside the exponential equation in ![equation](http://www.sciweavers.org/tex2img.php?eq=p%28X%7Cy%3D1%29%20%3D%20%5Cfrac%7B1%7D%7B%282%5Cpi%29%5En%7CK%7C%5E%7B1%2F2%7D%7Dexp%28-%5Cfrac%7B1%7D%7B2%7D%28X-%5Cmu_1%29%5ETK%5E%7B-1%7D%28X-%5Cmu_1%29%29&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)
---

---
Now, we can see the AD is basically a quadratic classifier, which in theory should have better(no worse) performance than a linear classifier. I initially was reluctant to agree to use the word "outperforms" in the title, since it is not a fair comparison. However, after considering that the AD does do better than LR in this data set that has all three items listed above, I guess it is OK to use that title. In many our hospital dataset, those three characteristics are quite often seen. We do need an alternative way to create prediction models other than LR. As we wrote in the discussion, the AD, or say the QDA, has many merits (see pages 4 and 5 in the paper). 
---

---
Note that, if we assume that the data set is mostly dominated by the major class and use the entire data set to estimate the mean and covariance matrix, we could be free of outcome labels, which means that this method could still work in an unsupervised way. This may be useful in some clinical problems when labelling a large amount of outcomes is expensive or infeasible. 


Also note that, LR may outperforms AD in some situations. If the variables are many enough or have been mapped to a (higher) space that the outcomes are already linearly separable, LR could perform as good as a higher order classifier. If the class labels are well balanced, then the AD has no advantage to be used as an unsupervised method.  

In short, choose appropriate methods based on the characteristics of the dataset. There is no one super method that is definitely better than another. 