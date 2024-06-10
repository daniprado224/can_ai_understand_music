# Can AI Understand Music? Recommender System 

For my personal project, I built my own music recommendation system using my own Spotify data. The purpose of this was for me to try to get some hands-on experience on the technologies that I had researched in the Fall semester. Additionally, I wanted to take advantage of the opportunity of having a project that I could call my own.
The first step for this project was to request data from my music streaming service - Spotify. This data can be requested on Spotify’s web page by going to Home > Safety & Privacy. In this page, the user can then log into their account. Once this is done, one must scroll down until they reach the “Download your data” section. Then, the user must confirm their request on another page and specify the email address they would like to receive this information in. An email from Spotify will be sent to this account confirming their request has been received, and that they should receive their data in no more than 30 days. 

In my experience, this data took about 10 days to be received from Spotify. Once the data has been received, Spotify sends additional documentation explaining what this data means, since when it has been collected, and how to use it or understand it. The data itself is in separate JSON files and the ones focused on for this project were the files containing Streaming History, Streaming History, and Playlist1. After analyzing these datasets, the three files containing Streaming History were the ones that were used to build a model. This data came in the format of:

{
    "endTime" : "DATETIME",
    "artistName" : " ",
    "trackName" : " ",
    "msPlayed" : 
  },
  
Using Pycaret and JupyterNotebook, all this data was then read and minimally processed to get an idea on how to be able to use this data to make predictions on music recommendations. The statistics retrieved from these datasets were: most streamed artist, most streamed song, least streamed song, and the amount of time spent listening to the most streamed artist. 
The results were shown in the following format: 

  |    Most listened to song in file x: |
  |    Artist:                          |
  |    Track:                           |
  |    Miliseconds played:              |

This dataset was intended to be used to study the user’s information and then make a prediction on a song they would like to listen to. To do this, a target variable “liked_or_not” was added to combined_user_data with a value of either 0 or 1. A score of 1 meaning the user liked the song if it was streamed for over 1000 ms and 0 if otherwise. Then, the combined user data was preprocessed to match the column names of the dataset downloaded.

After data cleaning, I used a KNN model to predict what songs from the downloaded dataset had similarities to the 50 most streamed songs. The characteristics used to make this prediction were: 'danceability', 'energy', 'key', 'loudness', 'mode', 'speechiness','acousticness', 'instrumentalness', 'liveness', 'valence', 'tempo', 'duration_ms', 'time_signature'

After these features were used in the model to create a prediction, the system recommends 10 songs I should listen to. 

This project is ran on JupyterLab. 
