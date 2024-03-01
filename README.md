
Firstly lets recall that the squared error can be decomposed into bias, variance and noise:

> E[(hD(x) − y)2] = E[(hD(x) − h¯(x))2] + E[(h¯(x) − y¯(x))2] + E[(y¯(x) − y(x)2] 

 
We then create a data set for which we can approximately compute this decomposition. The function to our data generates a binary data set with class 1 and 2. 

Both are sampled from Gaussian distributions:

>  p(x|y = 1) ∼ N (0, I) and p(x|y = 2) ∼ N (µ2, I),	(4) where µ2 = [2; 2]^⊤
(the global variable OFFSET = 2 regulates these values: µ2 = [OFFSET ; OFFSET]⊤).

we will need to implement four functions: computeybar, computehbar, computevariance and biasvari- ancedemo.

(a)	Noise (computeybar):  First we focus on the noise.  For this, you need to compute y¯(x) in computeybar. With  the  equations,  p(x|y  =  1)  ∼ N (0, I) and p(x|y  =  2)  ∼ N (µ2, I),  you  can  compute  the  probability p(⃗x|y).  Then use Bayes rule to compute p(y|x).

Also we may want to use the norm probability density function, which you can directly use some package to call this function if you find some. With the help of computeybar you can now compute the “noise” variable within biasvariancedemo.

Figure 4: Data Distribution
![image](https://github.com/koushik16/Bias-Variance-Decomposition/assets/63333977/c0d4d690-4b6c-4094-838e-08bb9c92052e)


(b)	Bias  (computehbar):  For  the  bias,  you  will  need  h¯.   Although  we  cannot  compute  the  expected  value h¯ = E[h],  we  can  approximate  it  by  training  many  hD  and  averaging  their  predictions.   Edit  the  function computehbar: average over n models different hD, each trained on a different data set of n inputs drawn from the same distribution. Feel free to call toydata to obtain more data sets.

Hint: You can use ridge regression for hD. With the help of computehbar you can now compute the “bias” variable within biasvariancedemo.

(c)	Variance (computevariance):  Finally, to compute the variance, we need to compute the term E[(hD −h¯)2]. Once again, we can approximate this term by averaging over n models models. Edit the file computevariance. With the help of computevariance you can now compute the “variance” variable within biasvariancedemo.

(d)	Demo (biasvariancedemo): In this function, you need to implement a plotting function that how the error decomposes (roughly) into bias, variance and noise when regularization constant λ increases. You can see the trend if you did everything correctly.

Hint: You can set a training dataset with a size of 500, for a really big dataset you can set the size as 100000. You can try average over 25 models. But all these parameters you can change freely.

The bigger number for the number of models and/or the training dataset, the better your approximation will be for E[h] and E[(hD − h¯)2]).
