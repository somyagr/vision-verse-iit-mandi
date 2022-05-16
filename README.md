# Vision Verse IIT Mandi
## Our Goal
To create models which could classify pictures of crops as having a certain type of disease or not.
## Our Approach
We first created two models inspired by the existing ResNet and EfficientNet Architectures. As we were not allowed to use pretrained weights we trained each model from SCRATCH. Each model was trained for roughly 50 epochs on Google Colab virtual GPUs. The hyperparameters were set by running several training loops and the deciding based on the validation accuracy.
After the models were trained, our final submission was made by **taking an ensemble of the outputs of both the models**. The ensemble was a majority voting scheme. With this we got a **Public LB score of around 0.981**.
## Troubles we faced
The major trouble was that we couldn't use pretrained model. To tackle this we used longer training regimes and better learning rate schedulers and optimisers like Cosine Annealing which prevents the training to be stuck in  a local minima.
The second hurdle we faced was that we could not use any augmentations. As we were using very large and representationally rich models which are inherently prone to overfitting we were not getting very generalised models. To deal with this we saved the model which performed the best on the validation set at each epoch. During inference time we then loaded this "most generalised model" to make predictions. 
Another issue was that the dataset given had a lot of irrelevant data which hindered the training. We removed these outliers as a sort of data cleaning strategy.
## What else we could have done
To make more accurate predictions we could have used K-Fold Cross Validation and used those predictions in the majority voting scheme to get more generalised answers.  
We could have also used more models to do ensembling such as resnext and densenet which would further make the final predictions more robust.
