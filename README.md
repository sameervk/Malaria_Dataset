# malaria-ds_classification
Transfer Learning in tensorflow (version 2.0.0 in v1; 2.1.0 in v2)

Summary
=======

* Using MobileNetV2 as the base model.

* The images are of different sizes, so have to resize all images to one standard size.

* MobileNetV2 accepts only standard input dimensions

* Scaling the images using the StandardScaler function from scikit-learn

* Uses lot of RAM (~ 20 GB)

* Adding a global averaging layer, dropout layer and one dense layer on top

* Train:Validation:Test dataset ratio = 0.8:0.1:0.1

* Training only the top layers from number 100 in the base model along with the added layers

* Best test accuracy 93.4% (in file v1) but with overfitting (training accuracy ~ 99.1%).

* Learning how to add regularizations to the pretrained model (files v1 (at the end) and v2)
	
	..* Simply added regularizers does nothing.
	
	..* Need to add regularizers using the method detailed in
		https://sthalles.github.io/keras-regularizer/

* With L2 regularization (file v2;  l2 = 0.001) - added to the trainable layers in the base model - test accuracy: 93.2% and training accuracy: 95.6%, reducing overfitting


Issues
======
* The metrics (accuracy, loss) are different for the training dataset under fit and evaluation modes.

* In some cases, it falls from 99% in training to 50% (including validation) in evaluation mode.

* The issue is a bit complex as detailed in the blog

	http://blog.datumbox.com/the-batch-normalization-layer-of-keras-is-broken/

* This issues is apparently specific to using pretrained models for transfer learning.
