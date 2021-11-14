# A Network Based Music Recommendation System

### Introduction
In this era of the Internet, popular music has also been greatly developed, with more and more ordinary musicians publishing their works on the Internet platform, and new popular musics born almost every day; besides, the taste of the audience is no longer limited to their favorite singers. Based on this background, we want to set up a music recommendation system based on the song network to help the audience to find more music that suits their taste.

During the process to build the recommendation system, we are curious about 1) what characteristics of the song network are based on the user’s playing history and 2) whether the network can meet the basis to build a recommendation system – they are exactly our research questions.

### Data Resource
We use the dataset called Million Song Dataset(http://millionsongdataset.com), one of the publicly available large-scale
collections, which has been used and analyzed by all kinds of music processing technologies. 

- Song Dataset (subset-compiled.csv​): as the original data from Million Song Dataset directly is very large, approximately 500 GB, we use the subset exposed on GitHub for this project. The subset consists of 10,000 songs, about 1% selected at random from the original data.

- Taste Profile Dataset ([songs_dic.txt](https://github.com/sarahzhao21/A-Recommendation-System-Based-on-Network/blob/333a59a1a8bb0e69c5a6cbb630e1537a2813d81d/songs_dict.txt)): Million Song Dataset also provides the taste
profile data, which contains 1,019,318 unique users, 384,546 unique songs, and 48,373,586 records of triplets (user id, song id and play count). This is an important basis for building the network.

### Exploration Data Analysis
The song with the largest number of users has 30,117 users; the user who played the largest number of songs played 48 songs, and the distributions are shown below. Both two distributions seem to follow the power-law distribution. This result means that the largest connected component of the network would contain the most part of it. Thus, if we want to randomly select a small fraction to do our analysis, the network might be sparse. In addition, it tells us that people prefer to select the most popular songs which only take a very small proportion of all the songs. 

![Distribution of number of users of each song distribution](https://github.com/sarahzhao21/A-Recommendation-System-Based-on-Network/blob/326dc7fd02a8f60e387a50a0c1e82f00986a21b8/images/number%20of%20users%20of%20each%20song%20distribution.png)
![Distribution of number of songs played by each user](https://github.com/sarahzhao21/A-Recommendation-System-Based-on-Network/blob/326dc7fd02a8f60e387a50a0c1e82f00986a21b8/images/Distribution%20of%20number%20of%20songs%20played%20by%20each%20user.png)

### Network Graph Building
The relationship between users and songs can be considered as a bipartite network with users group and songs group, so we built a one-mode projection graph of the songs for our sample set. The weight of each edge that connects a pair of songs was created by the number of users who played the pair of songs. So, the entire network graph includes 3535 nodes and 201,205 edges.
![Graph of the network](https://user-images.githubusercontent.com/54957469/119571132-fb9f9280-bd7e-11eb-92e4-6a5be58ea903.png)

### Algorithms
Two features have been used as reference to evaluate the accuracy of the algorithms, song play count and song hotness.
Our approach is: sort the songs with the top 50 highest values of total play count, song hotness, and also sort the songs with the top 50 highest values of pagerank, authorities, hubs and degree centrality, then compare the similarity of the songs between PageRank|Authorities|Hubs|Degree Centrality group with the play_count|song_hotness group by jaccard_similarity_score.
The result shows that: referring to play_count is better than referring to song_hotness, PageRank has a higher similarity score, and the similarity score of Authorities, Hubs and Degree Centrality are much lower.
So, we use PageRank to do the recommendation.
![Recommendation cartoon](https://github.com/sarahzhao21/A-Recommendation-System-Based-on-Network/blob/326dc7fd02a8f60e387a50a0c1e82f00986a21b8/images/Recommendation%20graph.png)

### Summary
In this repository, the [A Network Based Recommendation System.ipynb](https://github.com/sarahzhao21/A-Recommendation-System-Based-on-Network/blob/326dc7fd02a8f60e387a50a0c1e82f00986a21b8/A%20Network%20Based%20Recommendation%20System.ipynb) and [A Music Recommendation System Based on Network.pdf](https://github.com/sarahzhao21/A-Recommendation-System-Based-on-Network/blob/326dc7fd02a8f60e387a50a0c1e82f00986a21b8/A%20Music%20Recommendation%20System%20Based%20on%20Network.pdf) provide the details about this study, and the [songs_dic.txt](https://github.com/sarahzhao21/A-Recommendation-System-Based-on-Network/blob/326dc7fd02a8f60e387a50a0c1e82f00986a21b8/songs_dict.txt) is a python dictionary with all the users as the keys and the songs played by each user as values, which can be used to build network.


