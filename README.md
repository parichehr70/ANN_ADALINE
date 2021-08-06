close all
clear all
[p t] = iris_dataset;

w = zeros(size(t,1), size(p,1));
b = zeros(size(t,1), 1);

maximum_epoch = 200;
epochs = 0:maximum_epoch;
learningrate = .001;
valRatio = 0.5;
trainRatio = 0.5;
vperformance = zeros(1, maximum_epoch+1);
performance = zeros(1, maximum_epoch+1);
