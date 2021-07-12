# Face-Recognition

We performed facial recognition using two different approaches: PCA and LDA.

We worked on ORL dataset that consists of forty classes each consists of ten pictures to a specific person. Each picture captures a different facial expression for that person. 
Pictures are all grayscale with dimensions (92 x 112). Each picture is converted into one vector of dimensions (1 x 10304), each column represents an attribute of that picture. 
Then all vectors are stacked under each other in a total data matrix with dimensions (400x10304). The Data set was separated into two sets testing and training. 
Each set includes two hundred pictures, five pictures for each person. Their dimensions are (200x10304).

PCA:

The PCA function takes two parameters the training set and the alpha. 
•	First, the mean is computed for each attribute in the training set
•	We subtract the mean from the training set to center the data. 
•	The centered data is the used to compute the covariance matrix.
•	The Eigen values and eigen vectors are obtained from the covariance matrix. 
•	After computing the eigen values we determine the number of dominant eigen vectors will be taken into consideration by determining the fractional variance
  that satisfy the alpha. 
•	Finally the reduced eigen vectors (projection matrix) are multiplied by the centered testing data set and training data set producing projected training data
  and projected testing data. 
•	We used KNN classifier to classify the projected testing set. KNN classifier determine the label for each element in testing set through calculating Euclidean distance
  it stores all available cases and takes into consideration the k smallest Euclidean distance to it. (in our case we used k=1 ”first nearest neighbour”)

By applying the PCA on different values of alpha w observed that accuracy increases as alpha increases(number of eigenvectors taken into consideration increases)
to a certain value of alpha then the accuracy decreases.


LDA:

LDA function explained:                       
•	We started by dividing the data into forty classes.
•	Calculated the mean for each class and the overall mean of all classes.
•	We centered each class by subtracting the mean of the class from the between-class scatter matrix.
•	Then using the centered data we compute the class scatter matrices.
•	Calculate the sum of the class scatter matrices and it’s inverse.
•	Multiply the inverse by the between-class scatter matrix 
•	Use the output to get the eigen values and eigen vectors.
•	Using the first thirty nine dominant eigen vectors we obtained the projection matrix. 
•	Then KNN was used to predict the labels of the testing data then we calculated the accuracy of the predicted labels.

We used both algorithms with different values of k for KNN classifier to tune the classifier and observe the est results.

We downloaded a natural images dataset and created a new dataset that includes faces and non-faces to train the model to classify either a face or a non-face.
We observed the perfomance of the model through measuring its accuracy every time we changed the number of non-face images included in the training set.

  
