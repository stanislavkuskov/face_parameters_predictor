# face_parameters_predictor

1. Split the dataset into training and validation: \
The dataset was divided into training and test samples (divided files). \
I put it in train and test directory (its important for correct testing models after training on dataset).
I was load train dataset as pandas "DataFrame" and divide it onto train and validation dataset (This division only for example, validation does not needed later). 
I'm not analyze data (with .describe()) and not use data cleaning techniques. I suggested dataset was cleaned.
2. Create an algorithm that can predict blend shape values for an unseen encoding.
Algorithm was been defined as multiple linear regression. I choose keras implementation of regression with multiple outputs.
3. Implement the algorithm using Python and your favourite ML library.
I create simple model for test multiple regression.
Basically its Dence layers where last layer has linear activation function.
I choose adamax optimizer instead adam because adamax more robust to noise in the gradients.
I fit the model and save it for subsequent implementation.
I'm visualize loss (mse) and metric (mae) onto plot. Mae usually used in regression.
4. Describe how would you approach this problem if instead of encoding vectors, the input data would be face photographs (in case face recognition encodings were not available).
From the point of view of medicine, facial parameters (nose size, chin width and others) has correlation with face size. 
I would identify the key points of the face and train the neural network to detect such points on the photo 
(this is the same for dlib landmarks detection but more accurate). 
The ratio of the location of these points relative to each other, as well as the size of the face, 
would allow us to determine a set of face parameters (blends) for different faces.
For example, if we take the maximum and minimum width of the chin from a large sample and designate the maximum as 1 and the minimum as 0, then the width for any person will have a corresponding value between 1 and 0.