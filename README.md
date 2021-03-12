# A-Recommendation-System-Based-on-Network

In this era of the Internet, popular music has also been greatly developed, with more and more ordinary musicians publishing their works on the Internet platform, and new popular musics born almost every day; besides, the taste of the audience is no longer limited to their favorite singers. Based on this background, we want to set up a music recommendation system based on the song network to help the audience to find more music that suits their taste.

During the process to build the recommendation system, we are curious about 1) what characteristics of the song network are based on the user’s playing history and 2) whether the network can meet the basis to build a recommendation system – they are exactly our research questions.

We use the dataset called Million Song Dataset(http://millionsongdataset.com), one of the publicly available large-scale
collections, which has been used and analyzed by all kinds of music processing technologies. 

● Song Dataset (subset-compiled.csv​): as the original data from Million Song Dataset
directly is very large, approximately 500 GB, we use the subset exposed on GitHub for this project. The subset consists of 10,000 songs, about 1% selected at random from the original data.

● Taste Profile Dataset (train_triplets.txt​): Million Song Dataset also provides the taste
profile data, which contains 1,019,318 unique users, 384,546 unique songs, and 48,373,586 records of triplets (user id, song id and play count). This is an important basis for building the network.
