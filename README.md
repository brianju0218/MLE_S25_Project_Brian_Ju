# MLE_S25_Project_Brian_Ju
Repository of Brian Ju's MLE S25 Course Project

Application of Piezoelectric Ceramic (PZT) Sensor Array for Structural Health Monitoring of a Composite UAV Wing 
Brian Ju

OBJECTIVE:
The goal of this project was to perform classification of damage severity and level using time-series data of a UAV wing. Time-series signals were collected using PZT sensors on a UAV wing while simulating damage on 3 different locations. This time series data was then used to train two models: a PCA-to-NN Model and a 1D CNN Model. These two models had their hyperparameters tuned, then tested on varying noise levels. 

DATASET: 
The dataset used was my own. It can be found in the /data folder in the repository.

MODEL/METHOD OVERVIEW:
- PCA-to-NN: The time-series data is subjected to a principal component analysis to extract its top 3 principal components as features. These features are then used as the inputs to a neural net in order to perform combined label classification. Its hyperparameters are tuned for accuracy score. Its predictions are shown in a confusion matrix. The optimized model is then subjected to testing and retraining on various noise levels. 
- 1D CNN: The time-series data is directly used to train a 1D CNN model. Its hyperparameters are tuned for accuracy score. Its predictions are shown in a confusion matrix. The optimized model is then subjected to testing and retraining on various noise levels.

INSTRUCTIONS TO RUN CODE: 
The code is written in notebooks and designed to be run in successive code blocks. Each model is given its own notebook and the code is designed to run starting from the raw data, performs the preprocessing, then the model training. The data must be accessible in order to run.
- THE FIRST TWO CODE BLOCKS ARE UNNECESSARY IF USING X_y_data_2_300.0kHz.npz. It is highly recommended to use to load in data faster. All that needs to be changed is the file path for your google drive or wherever you happen to run the colab notebook. The first two blocks are only needed if using the raw csv files (link to Google Drive for those is in /data)
- Run each code block successively to the end

- NOTE: I've done my best with seeding in order to ensure reproducibility, however, much of the work was originally run using Colab's GPUs so that my effect its reproducibility. To the best of my ability, I tried to mitigate this the best I could.

SUMMARY OF RESULTS AND KEY FINDINGS: 
- Both the PCA-to-NN and 1D CNN model provide a test accuracy of 85-90%.
- The PCA-to-NN model provides stronger robustness to noise and is quicker to train.
- The 1D CNN model is weaker to noise, however, makes more accurate predictions even when wrong, that is, when the model is wrong, its incorrect labels are closer to the actual. For example, the PCA-to-NN model would sometimes mistake A_20 as C_80, when the 1D CNN would only mistake A_20 as A_40. It is much more preferable to be slightly wrong about damage but correct about location than it is to be drastically wrong about both. 
