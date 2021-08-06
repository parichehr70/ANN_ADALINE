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

valIndex = 1:2:150;
trainIndex = 2:2:150;

vperformance_mat = power(t(:,valIndex) - TransferFcn_purelin(w, p(:,valIndex), b),2);
vperformance(1) = sum(vperformance_mat(:))/length(vperformance_mat(:));
performance_mat = power(t(:,trainIndex) - TransferFcn_purelin(w, p(:,trainIndex), b),2);
performance(1) = sum(performance_mat(:))/length(performance_mat(:));

for epoch = 2:(maximum_epoch+1)
   
    for index = trainIndex
        w = w + 2*learningrate*(t(:,index) - TransferFcn_purelin(w, p(:,index), b))*transpose(p(:,index));
        b = b + 2*learningrate*(t(:,index) - TransferFcn_purelin(w, p(:,index), b));
    end
    
vperformance_mat = power(t(:,valIndex) - TransferFcn_purelin(w, p(:,valIndex), b),2);
vperformance(epoch) = sum(vperformance_mat(:))/length(vperformance_mat(:));
performance_mat = power(t(:,trainIndex) - TransferFcn_purelin(w, p(:,trainIndex), b),2);
performance(epoch) = sum(performance_mat(:))/length(performance_mat(:));
    
end

plot(epochs, vperformance)
hold on
plot(epochs, performance)
grid on
xlabel('epoch');
ylabel('MAE');
