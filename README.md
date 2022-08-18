Key Observations Version 1:

Experiment 1 --

1. The train loss and validation loss reduces gradually (i.e. gradient updates are very smooth) and is seen to converge between epoch 27 and 32. Beyond epoch 32, the curves starts diverging which implies the model is getting overfitted to the train data.
2. Initially lower dropout rate was used which was later increased to have more aggressive dropout, to deal with overfitting.
3. Using a much much lower learning rate and training the model for more number of epochs will help further to reduce the most optimal solution. 
4. A partial overfit can be seen even when selecting the models between epoch 27 and 32.
5. More hyper parameter tuning needs to be done to improve the model's performance.

Experiment 2 --

1. Beyond epoch 30, the losses starts diverging and overfitting increases.
2. Optimal model is generated around epoch 30. 
3. Image augmentation improved the performance of the model very minutely.
4. Image Augmentation is slightly overfitting the model.

Experiment 3 --

1. Using the same architecture as model 1, but with RELU.
1. Here also a gradual decrease in train and  validation loss is seen, but the losses starts diverging beyond epoch 40.
2. Partial overfit is observed.
3. Gradient updates are not as smooth as Model with (Because of RELU as compared t SWISH)

Experiment 4, 5, 6 --

1. For 4 and 5, the validation loss remains constant around 2.32
2. Experiment with different optimizers, model architecture, learning rate, activation (leaky relu)
3. The losses doesn't converge at all.
4. For 6, the gradient updates are very nosiy, and the model have not converged at all across multiple tried for the last experiment 6.



Clearly all the top 3 performing models shows signs of partial overfitting. Few things that can be tried to reduce the overfitting much more is to reduce the learning rate combined with reduced batch size and train the model for significantly much larger epochs and check if it improves model performance as well as reduce model overfitting even more. Used cosine-annealing scheduler, reduce learning rate scheduler to deal with overfitting. We can also use Hough Transormation on the input images and check if it improves the model performance and reduces overfitting more. The scope for further experimentation is huge but it needs a very good compute engine and sufficient time to try out more techniques.




Key Observations Version 2:

Experiment 1 --
For experiment 1, I have selected the model at the 29th epoch, after which the model accuracy on validation data remains constant. There is a significant improve in model performance from version 1. A 3.86% difference is observed between the train and validation set, and 4% between the train and test set. This indicates that the overfitting has been reduced considerably

Experiment 2 --
For experiment 2, adding L2 regularizer to the last fully connected layers and tweaking the augmentation strategy by introducing zoom, increased all the train, validation and test accuracies. I have selected the model generated at epoch 83, post which there's no significant difference observed in model accuracy. There's a 6.13% difference in error observed between train and validation accuracies. This implies that overfitting has increased in experiment 2, from experiment 1.

Experiment 3 --
For experiment 3, I have added regularization to all the fully connected layers and trained the model. The gap between train and validation error has now increased to almost 7%, which suggests significant overfitting than experiment 1.

Experiment 4 --
For experiment 4, I have added both L1 and L2 regularizer for both the convolution layers as well as the convolution layers of efficient net. Tweaked the augmentation paparemeters more. I have also tried to freeze the convolution base and unfreeze only the top 20 layers. However, the accuracy was constant at 10% afte rmany epochs. Tried changing many hyperparameters, but there's no real effect. That's the reason I have not included the experiment in this notebook.


Key Takeaway:
If we look at all the experiments, experiment 1 has generated the least overfitted model after training for only 29 epochs (early stopped). The difference between train and validation dataset is 3.86%, which indicates slight overftting. On close observation we also notice that the train and validation loss are very very similar to each other (about 0.44 value for both losses), which indicates the model will generalize well on unseen data points. For a custom architecture, we could also have used SpatialDropout to tackle overfitting more. For the pre-trained architecture, I need more time and many more iterations to successfully integrate SpatialDropout.
