<h1>Weather Recognition</h1>

<h2>Description</h2>
Books are identified by their respective ISBN. Invalid ISBNs have already been removed from the dataset. Moreover, some content-based information is given (Book-Title, Book-Author, Year-Of-Publication, Publisher), obtained from Amazon Web Services. Note that in case of several authors, only the first is provided. URLs linking to cover images are also given, appearing in three different flavours (Image-URL-S, Image-URL-M, Image-URL-L), i.e., small, medium, large. These URLs point to the Amazon web site. Contains the book rating information. Ratings (Book-Rating) are either explicit, expressed on a scale from 1-10 (higher values denoting higher appreciation), or implicit, expressed by 0. Contains the users. Note that user IDs (User-ID) have been anonymized and map to integers. Demographic data is provided (Location, Age) if available. Otherwise, these fields contain NULL-values. 

<br />


<h2>Sheets and features</h2>

3 sheets in the dataset: Books, Ratings and Users

- Books:  ISBN,  Title, Author, Year of publication, Publisher, Images
- Ratings: User’s ID, ISBN, Book rating
- Users: ID, Location, Age

<h2>Modifications and output</h2>

- Year of publication

To delete the outliers in the “Years of publication” column, we decided to filter the column to select only the years between 1900 and 2024. The outliers as the year 0 or the year 2024 were in this way deleted.

- Ratings - Book rating

In the details of the dataset, we saw that book ratings could be between 1 and 10, a 0 rating means the reader didn’t give his appreciation. Thus, we filtered the ratings to have a minimum of 1

<h2>Hybrid model</h2>

- Filter recommended books with IMDB

We only want to recommend books that readers like. Therfore, we use IMDB to score books appreciation and we filter books with the highest score. Here are some takes : 
Dealing with representation bias: books must have at least 5 reviews to appear on the list
We only keep books that have an IMDB score higher than 5, so that our model only recommends books that have good ratings.

- Recommendation with Cosine Similarity
  
Key features : 
Book-Title,
Book-Author
Publisher
Period_Of_Publication
We combine these key features in one single feature. We clean it, build a count matrix, and use cosine similarity on it.
