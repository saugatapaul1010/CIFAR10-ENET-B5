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
