# Spotify Listening Data Analysis
## Introduction
Analysis to see if Spotify's most streamed songs can be classified based on various factors.

The dataset I am working with contains detailed information on Spotify’s most streamed songs, featuring 943 tracks. For each song, the data includes its popularity metrics, such as the number of streams and the number of Spotify playlists it appears in. The dataset includes 27 variables, some of which are numerical attributes that describe the song’s musical features, such as BPM (beats per minute), danceability (%), valence (%), energy (%), acousticness (%), and liveness (%).

My objective is to derive a class label representing relative popularity (categorized as low, medium, or high) based on the number of streams, and the number of Spotify playlists the song is featured in. I will analyze how well the numeric predictors can classify songs into these popularity categories.

The dataset was sourced from Kaggle and can be accessed via the following link: https://www.kaggle.com/datasets/abdulszz/spotify-most-streamed-songs?resource=download

## Exploratory Data Analysis (EDA)
The exploratory data analysis revealed moderate correlations between some features, such as a positive correlation between danceability and valence, and a negative correlation between energy and acousticness. The distribution of the number of streams was skewed, requiring a log transformation for better analysis.

The dataset consists of 943 observations and 27 variables, out of which key numeric variables such as danceability, energy, valence, acousticness, and liveness will be used as predictors in the classification models. The outcome of interest is the popularity class, which has three categories: high, medium, and low popularity. These categories were derived by calculating the 33rd and 66th percentiles for the number of streams and Spotify playlists. Songs were classified as follows:
Low popularity: Songs in the lower third of streams and playlists. Medium popularity: Songs between the 33rd and 66th percentiles. High popularity: Songs in the upper third of streams and playlists. The distribution of popularity categories shows that 266 songs are classified as high popularity, 218 as low popularity, and 468 as medium popularity, indicating a slight imbalance favoring the medium category.

## Results
Insert images

## Conclusions
Among the models compared, LDA and SVM performed similarly, with accuracy just under 50%, but both struggled to classify high and low popularity songs. QDA performed slightly worse, while KNN had the highest misclassification rate, even after cross-validation.

None of the models were effective at distinguishing the three popularity levels, especially high and low popularity. LDA, QDA, and SVM mostly classified songs as medium popularity, likely due to dataset imbalance. KNN did better at identifying high and low popularity but struggled with medium popularity.

The overall poor classification results may stem from the numeric predictors (e.g., danceability, energy, and valence) lacking strong correlations with a song's popularity.
If I were to select the best model for real-world applications, considering the higher cost of misclassifying high or low popularity songs (such as over-promoting a low-popularity track or missing a potential hit) than misclassifying medium popularity songs, I would lean towards cross validated KNN. Despite its lower overall accuracy, KNN may be the most suitable model for addressing these critical categories in practice.

## Technologies Used
* R and R Studios
* dplyr
* tidyr
* MASS
* caret
