Lms program:
In this project, Adline neural network has been used. In the iris data, the Setosa group data are linearly separable from the Virginica and Versicolor groups.
In the main program, we first read the input and output values of the iris data set and store them in two variables, p and t. We form the matrices w, b and define the maximum epoch and the evaluation and training performance vector.The MSE value is calculated for each epoch.
Then we do the training and update the weight and bias in each step and finally we get the MSE value.
batch program:
The only difference between this part and the previous part is in the training part, in which case the variables are updated at the end of each epoch.
In versicolor data, since this data is not linearly separable, the MSE increases.
In general, in batch, we have less MSE and it is more convenient and faster.
