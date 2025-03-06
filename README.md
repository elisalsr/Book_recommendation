<h1>Book recommendation</h1>

<h2>Description</h2>
Books in this dataset are identified by their respective ISBNs, with invalid entries already removed. Each book includes key metadata sourced from Amazon Web Services, such as the title, author, year of publication, and publisher. If a book has multiple authors, only the first one is listed.  

Additionally, the dataset provides URLs linking to book cover images in three different sizes: small (Image-URL-S), medium (Image-URL-M), and large (Image-URL-L). These images are hosted on Amazon’s website.  

Book rating information is also included. Ratings (Book-Rating) can be either explicit—on a scale from 1 to 10, where higher values indicate greater appreciation—or implicit, represented by a score of 0.  

User data is available, with anonymized user IDs (User-ID) mapped to integers. When provided, demographic information such as location and age is included; otherwise, these fields contain NULL values.  


<br />


<h2>Sheets and features</h2>

3 sheets in the dataset: Books, Ratings and Users

- Books:  ISBN,  Title, Author, Year of publication, Publisher, Images
- Ratings: User’s ID, ISBN, Book rating
- Users: ID, Location, Age

<br />

<h2>Modifications and Output</h2>

### Year of Publication  
To remove outliers in the "Year of Publication" column, we applied a filter to retain only years between 1900 and 2024. This process eliminated extreme values such as year 0 or incorrect entries like 2024.

### Ratings – Book Rating  
Book ratings in the dataset range from 1 to 10, with a rating of 0 indicating that the reader did not provide feedback. To ensure meaningful recommendations, we filtered out ratings of 0, keeping only explicit ratings (1–10).  

<br />

<h2>Hybrid Model</h2>

### Filtering Recommended Books with IMDb  
To recommend books that readers genuinely appreciate, we incorporate IMDb scores as an additional filtering criterion. The process involves:  

- **Addressing representation bias**: Books must have at least **five reviews** to be considered.  
- **Ensuring quality recommendations**: Only books with an **IMDb score higher than 5** are retained, ensuring that our model suggests well-rated books.  

### Recommendation Using Cosine Similarity  
To compute similarity between books, we leverage the **cosine similarity** technique based on key book attributes:  

- **Book Title**  
- **Book Author**  
- **Publisher**  
- **Period of Publication**  

These attributes are combined into a single feature, cleaned, and converted into a count matrix. We then apply cosine similarity to identify books that share similar characteristics.  
