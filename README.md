# A Network Based Music Recommendation System

In this era of the Internet, popular music has also been greatly developed, with more and more ordinary musicians publishing their works on the Internet platform, and new popular musics born almost every day; besides, the taste of the audience is no longer limited to their favorite singers. Based on this background, we want to set up a music recommendation system based on the song network to help the audience to find more music that suits their taste.

During the process to build the recommendation system, we are curious about 1) what characteristics of the song network are based on the user’s playing history and 2) whether the network can meet the basis to build a recommendation system – they are exactly our research questions.

We use the dataset called Million Song Dataset(http://millionsongdataset.com), one of the publicly available large-scale
collections, which has been used and analyzed by all kinds of music processing technologies. 

● Song Dataset (subset-compiled.csv​): as the original data from Million Song Dataset
directly is very large, approximately 500 GB, we use the subset exposed on GitHub for this project. The subset consists of 10,000 songs, about 1% selected at random from the original data.

● Taste Profile Dataset (train_triplets.txt​): Million Song Dataset also provides the taste
profile data, which contains 1,019,318 unique users, 384,546 unique songs, and 48,373,586 records of triplets (user id, song id and play count). This is an important basis for building the network.

The relationship between users and songs can be considered as a bipartite network with users group and songs group, so we built a one-mode projection graph of the songs for our sample set. The weight of each edge that connects a pair of songs was created by the number of users who played the pair of songs.
![Picture1](https://user-images.githubusercontent.com/54957469/119571132-fb9f9280-bd7e-11eb-92e4-6a5be58ea903.png)

Two features have been used as reference to evaluate the accuracy of the algorithms, song play count and song hotness.
Approach: sort the songs with the top 50 highest values of total play count, song hotness, and also sort the songs with the top 50 highest values of pagerank, authorities, hubs and degree centrality, then compare the similarity of the songs between PageRank|Authorities|Hubs|Degree Centrality group with the play_count|song_hotness group by jaccard_similarity_score.
Result: referring to play_count is better than referring to song_hotness, PageRank has a higher similarity score, and the similarity score of Authorities, Hubs and Degree Centrality are much lower.
So, we use PageRank to do the recommendation.

In this repository, the "Recommendation_system_final_report.pdf" provides the details about this study, the "Recommendation_system_Fival_Version.ipynb" includes the python code that used for this study and the "songs_dic.txt" is a python dictionary with all the users as the keys and the songs played by each user as values, which can be used to build network.


