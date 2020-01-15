# face_parameters_predictor

1. Split the dataset into training and validation: \
The dataset was divided into training and test samples (divided files). \
I put it in train and test directory (its important for correct testing models after training on dataset).
I was load train dataset as pandas "DataFrame" and divide it onto train and validation dataset (This division only for example, validation does not needed later). 
I'm not analyze data (with .describe()) and not use data cleaning techniques. I suggested dataset was cleaned.
2. Create an algorithm that can predict blend shape values for an unseen encoding: \
Algorithm was been defined as multiple linear regression. I choose keras implementation of regression with multiple outputs.
3. Implement the algorithm using Python and your favourite ML library.
I create simple model for test multiple regression.
Basically its Dence layers where last layer has linear activation function.
I choose adamax optimizer instead adam because adamax more robust to noise in the gradients.
PS. Later I choose SGD with momentum to solve exploding gradients problem.
I fit the model and save it for subsequent implementation. \
<b>Results of last iteration:</b> \
<i>Epoch 200/200
3696/3696 - 7s - loss: 3.6995e-05 - mean_absolute_error: 0.0046
</i>
I'm visualize loss (mse) and metric (mae) with pyplot. Mae usually used in regression.
4. Describe how would you approach this problem if instead of encoding vectors, the input data would be face photographs (in case face recognition encodings were not available).
From the point of view of medicine, facial parameters (nose size, chin width and others) has correlation with face size. 
I would identify the key points of the face and train the neural network to detect such points on the photo 
(this is the same for dlib landmarks detection but more accurate). 
The ratio of the location of these points relative to each other, as well as the size of the face, 
would allow us to determine a set of face parameters (blends) for different faces.
For example, if we take the maximum and minimum width of the chin from dataset and designate the maximum as 1 and the minimum as 0, then the width for any person will have a corresponding value between 1 and 0.

# Next steps
What would I do next?
1. Analyze the data and remove the noise if needed
2. Optimize model and hyperparameters(with keras tuner)
3. Check trained model on test data (complex tests for each of result parameters)
4. Implement trained model for testcases and visualization