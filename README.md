# Multiple Saliency Techniques as an Explanation Interface in General Image Recognition Systems
 Dynamic image classification algorithm consisting of an explainable artificial intelligence interface combining traditional statistical model summary information and white-box Saliency techniques.
 
 **Introduction of Project**

Thesis mentor provided a dataset containing satellite images of natural disasters. I was tasked with developing an Explainable Artificial Intelligence Interface that provides post hoc explanations as to how neural nets classify images in such a set. 

Transfer Learning Neural Nets (TLNNs) are predictively powerful black box AI systems that provide no explanations as to how or why they arrived at their conclusions. As the prevalence of AI use has expanded, the black-box nature of TLNNs has been problematic in their acceptance to society. White-box salency techniques were developed to combat neural networks lack of transparency with two major classes being developed: one class for feature recognition and one class for sensitivity readings.      

Literature reviews revealed extensive research in the use of single white-box saliency techniques used to transform black box neural nets into Explainable AI (XAI) systems. The single white-box saliency techniques used to provide XAI interfaces were always of one category, feature recognition or sensitivity readings. No research was found that used multiple saliency techniques in one XAI interface. The goal was to develop an explanation interface for TLNN image classification that uses both feature recognition and sensitivity heatmaps to provide robust explanations as to how and why neural nets classify images in a dataset. 

Keras is a transfer learning API that runs on top of the machine learning platform TensorFlow. It was selected to be used as the transfer learning image recognition API for this project.   

**The SetUp**

The explainable artificial intelligence interface consists of four object oriented classes: a data processor class, a transfer learning neural net training and testing class, an application of saliency technique class and a random forest decision tree class.

The Data Processor: takes in an image dataset consisting of filenames for pixelated images stored in the users directory as well as classification labels for each file name. The algorithm is dynamically programmed to handle datasets of differing numbers of classes. User provides the dataset, the path to the folder where the images are stored, the training and test sizes wanted and the seed used to split the dataset. Train and test pixel arrays are extrapolated and processed for TLNN application. A data processing folder is saved to the explanation interface consisting of a classes count plot, a numerical label dictionary of the classes along with a data frame that has the file name, classification labels, label array and label number as columns. 

The TLNN Training Class: User selects one of 10 different Keras APIs to classify their images. Keras APIs are trained using a two-part fine-tuning methodology. User selects which Keras API to run, the learning rate and epochs to both stages of the fine-tuning process. A Keras Model Training folder is saved to the explanation interface containing training accuracy and loss history for both the stages of the training process, a final classification report and confusion matrix summarising the models performance and a results data frame containing the same information as the data processing data frame but with an array predictions column and a numerical predictions column. 

Once the training and testing is complete users are given the option to repeat a model’s training and testing or select a different Keras API to train and test on the same processed dataset. A model object is saved for all trained and tested models that is used to generate saliency heatmaps by the Saliency Technique Class. 

The Saliency Techniques Class: takes user selects trained and tested Keras TLNN model object and one of 6 saliency techniques to apply to the model object. Saliency heatmaps are produced that offer information to the internal reasoning of the Keras TLNN. Saliency heatmaps for all trained and tested images are saved to the explanation interface. 
GradCam produced heatmaps highlight areas of the image that the TLNN defined as important to its classification. 
Gradient, Integrated Gradient, Guided Blur IG heatmaps provide a visual representation of what the neural network “saw” when looking at an image. 


Random Forest Decision Tree: Takes final results data frames from user selected trained and tested Keras TLNNs. Resulting data frames are processed and the Random Forest Decision Tree generates a final robust classification for image classification based on the outputs of the individual models used. This step is meant to be done after users inspect the heatmaps given by the Saliency technique class and verify the logic of the Keras APIs used. A final classification report, confusion matrix, result data frame and visualisations of the resulting Random Forest Decision Tree are saved to the explanation interface. 


