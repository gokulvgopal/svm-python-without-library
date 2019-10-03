### svm-python-without-library
Support Vector Machine in python with and without using a standard library

There are two jupyter notebook files:
### 1. SVM using library on digit classification
### 2. SVM without library basic

# SVM using library on digit classification
This notebook is about creating an SVM using sklearn on data set in sklearn.datasets. The purpose of this project is to train an SVM to classify digits ranging from 0-9.
```
Number of Records in data set: 1797
```

# SVM without library
This notebook is to undersand the logic of SVM by implementing the lofic without using any library. For easy implementation, the data set is divided into two class 1 and -1 and sample data set will contain 40 records. Testing data set will contain another 10 records. Idea is to find the lowest weights(w) and lowest bias(b) that satisfy:
```
y ̅_i (x ̅_i⋅w ̅+b)-1=0
Where y ̅_i - class of a data point
x ̅_i - input data point (features)
w ̅ - weights
b - bias
```

The optimization problem is resolved by going through each possible combination of vector w and b. To make calculation easier, I have defined three step sizes 0.1, 0.01, 0.001 to cover all possible smallest values at the same time not going to more decimal places which can cause computation cost. Using this step values, all possible values of w0, w1 and b are iterated from – (maximum value of input data) * 10  to (maximum value of input data)*10 and –(maximum value of input data)*5 to (maximum value of input data * 5) respectively. After each iteration using step value, range of w will be updated with the least value of w from the previous iteration. This is to make computation faster and to ignore those cases which are known to be thrown out. This iteration processes the loop compiles all iterations of w and b using step values. An high level implementation logic is as follows:
1.	Find maximum value in the input data set
2.	Initialize weights vector w with max value. i.e w0 and w1 is equal to max value
3.	Define max value for b
4.	Define step sizes
5.	Iterate though step sizes.
6.	For each step size, Iterate over b from -(max value * 5) to (max value *5) with intervals at step size*5
7.	Along with this iteration, iterate over w from –(max value * 10) to (max value * 10) with intervals at step size.
8.	Thought the magnitude of w will be same, there can be many cases of w that can happen. So we find out (w0,w1), (w0,-w1), (-w0,-w1), and (-w0,w1)
9.	For all these combinations find if it satisfies hyperplane equation.
10.	If yes, then store the combination until one iteration over step is over.
11.	When that iteration is over, then find least value of optimal.
12.	This value is store as the value of w.
13.	Continue till all iterations are over.
14.	Find least magnitude index of w, and store w0, w1 and b of that combination.
15.	Use these parameters to predict the new data set.
