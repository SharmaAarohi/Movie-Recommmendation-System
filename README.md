# Movie-Recommmendation-System

### Import Dependencies

1. **Installing Required Libraries**: 
    - `numpy`, `pandas`, `matplotlib`, `plotly`, `wordcloud`, `scikit-learn` are installed to handle data manipulation, visualization, and machine learning tasks.

2. **Importing Libraries**:
    - Standard libraries (`string`, `numpy`, `pandas`, `matplotlib.pyplot`, `plotly.graph_objects`, `plotly.express`, `wordcloud`, `pickle`, `sklearn`, `warnings`) are imported for data processing, visualization, machine learning, and handling warnings.

### Data Loading

3. **Loading Data**:
    - Netflix dataset is read from a CSV file into a pandas DataFrame named `netflix_data`.

### Data Pre-Processing and EDA (Exploratory Data Analysis)

4. **Initial Data Exploration**:
    - `info()` method is called to get a concise summary of the DataFrame.
    - Missing values are checked using `isnull().sum()`.
    - Missing values are filled with empty strings using `fillna('')`.
    - `describe(include='all').T` gives a statistical summary of the DataFrame.

5. **Visualizations**:
    - **Movies Released Each Year**: A bar plot is created showing the number of movies released each year.
    - **Distribution of Content Types**: A pie chart shows the distribution of content types (Movies vs. TV Shows).
    - **Top Countries**: A treemap visualization shows the top countries with the highest number of movies.
    - **Number of Movies by Country**: A choropleth map visualizes the number of movies released by country.
    - **Movie Ratings Distribution**: A bar plot displays the distribution of movie ratings.
    - **Movie Durations Distribution**: A bar plot shows the distribution of movie durations.
    - **Word Clouds**: Word clouds are generated for titles, descriptions, and genres to visualize the most common words.

### Feature Engineering

6. **Selecting and Preparing Features**:
    - A new DataFrame `new_data` is created with selected columns: 'title', 'type', 'director', 'cast', 'rating', 'listed_in', 'description'.
    - The index is set to 'title'.

7. **Text Cleaning**:
    - A `TextCleaner` class is defined with methods to clean and preprocess text data.
        - `separate_text()`: Separates and lowers text.
        - `remove_space()`: Removes spaces and converts text to lowercase.
        - `remove_punc()`: Removes punctuation and lowers text.
        - `clean_text()`: Combines the above methods to clean text.
    - Columns are cleaned using these methods and updated in `new_data`.

8. **Creating Bag of Words (BoW)**:
    - A new column 'BoW' is created by combining all cleaned text features into a single string for each record.
    - All other columns are dropped, leaving only the 'BoW' column.

9. **TF-IDF Vectorization**:
    - `TfidfVectorizer` is used to convert the 'BoW' text data into a TF-IDF matrix.
    - Cosine similarity is calculated between TF-IDF vectors to measure similarity between titles.
    - The TF-IDF matrix and cosine similarity matrix are saved to files using `numpy` and `pickle`.

### Saving Final Data

10. **Saving Processed Data**:
    - A final DataFrame `final_data` with 'title' and 'type' columns is created and saved to a CSV file.

### Movie Recommendation System (FLIX-HUB)

11. **Defining FlixHub Class**:
    - A `FlixHub` class is defined to handle the recommendation logic.
        - `__init__()`: Initializes the class with the dataset and cosine similarity matrix.
        - `recommendation()`: Recommends similar movies and TV shows based on the cosine similarity.
        - `find_id()`: Finds the index of a given title in the DataFrame.

12. **Testing Recommendations**:
    - An instance of `FlixHub` is created with the final data and cosine similarity matrix.
    - Recommendations are generated for two example titles ('Blood & Water' and 'Chappie').
    - The recommended movies and TV shows are printed.


## RESULTS:
Movies and TV Shows recommended for 'Blood & Water':


![image](https://github.com/SharmaAarohi/Movie-Recommmendation-System/assets/122620269/85123bc1-fdf8-4359-896e-e50ac3167f79)

Movies and TV Shows recommended for 'Chappie':


![image](https://github.com/SharmaAarohi/Movie-Recommmendation-System/assets/122620269/f8f39891-5295-4937-8f79-18cd5a961197)
