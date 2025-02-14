﻿# Data-Extraction-and-NLP

Approach towards to the problem :

1. Import Necessary Libraries
   
The script begins by importing libraries required for:
● Data manipulation: pandas
● Web scraping: requests, BeautifulSoup from bs4
● Text processing: NLTK , re

2. Load Input Data
● The dataset is read from an Excel file (Input.xlsx) using pandas.
● This dataset contains two columns:
   1. URL_ID: A unique identifier for each URL.
   2. URL: The web address to be analyzed.

3. Load Auxiliary Data
  ● Stopwords: All stopwords are loaded from .txt files located in a specified folder (StopWords) 
    and combined into a single set. These are used to clean text.
  ● Master Dictionary: Positive and negative word lists are loaded from positive-words.txt and 
    negative-words.txt in the MasterDictionary folder for sentiment analysis.

4. Define Utility Functions
Several utility functions are implemented to process and analyze the text:

4.1. Text Cleaning (clean_text)
● Removes punctuation and converts text to lowercase.
● Tokenizes the text into words.
● Filters out stopwords.

4.2. Sentiment Analysis (calculate_sentiment_scores)
● Calculates the following scores:
 ○ Positive Score: Number of words found in the positive words list.
 ○ Negative Score: Number of words found in the negative words list.
 ○ Polarity Score:(Positive Score – Negative Score)/ ((Positive Score + Negative Score) + 
  0.000001)
 ○ Subjectivity Score:(Positive Score + Negative Score)/ ((Total Words after cleaning) + 0.000001)
 
4.3. Readability Analysis (analyze_readability)
● Splits the text into sentences and words.
● Calculates:
 ○ Average Sentence Length = the number of words / the number of sentences
 ○ Percentage of Complex words = the number of complex words / the number of words
 ○ Fog Index = 0.4 * (Average Sentence Length + Percentage of Complex words)

4.4. Syllable Count (syllable_count)
● Counts the syllables in a word based on vowel occurrences.

4.5. Personal Pronouns (personal_pronouns_count)
● Counts occurrences of pronouns like I, we, my, ours, us.

5. Extract Text from URL
● The extract_text_from_url function fetches web page content using requests.
● Text content is extracted from the <h1> (title) and <p> (paragraph) tags using BeautifulSoup.

6. Process Each URL
The main function process_url performs the following:
1. Extracts the text content from the given URL.
2. Cleans the text and tokenizes it.
3. Calculates:
 ○ Sentiment scores.
 ○ Readability metrics (Fog Index, average sentence length, etc.).
 ○ Structural details (word count, syllables per word, personal pronouns, etc.).
4. Returns a dictionary containing all calculated metrics.

7. Analyze All URLs
The function analyze_urls:
1. Iterates through each row in the input dataset.
2. Calls process_url for each URL.
3. Aggregates the results into a list of dictionaries.

8. Save Results
● The aggregated results are saved to an Excel file (Output Data
Structure.xlsx) using pandas.
● The output contains columns for all calculated metrics:
 ○ URL_ID, URL
 ○ Sentiment scores (Positive Score, Negative Score, Polarity Score, etc.)
 ○ Readability metrics (Fog Index, Average Sentence Length, etc.)
 ○ Structural metrics (Word Count, Syllable Count Per Word, etc.)

Execution Instructions
1. Open the Python script in Visual Studio Code (VS Code).
2. Ensure all required dependencies (mentioned above) are installed.
3. Place the script and necessary files (Input.xlsx, StopWords
folder, and MasterDictionary folder) in the same directory.
4. Run the script in VS Code .
5. The output will be saved as Output Data Structure.xlsx in the same directory.
Note: Use VS Code for seamless execution.

Dependencies that I have used in this project:
To run this script, the following dependencies must be installed:
● Python packages: requests, beautifulsoup4, pandas, NLTK
● Input files: Input.xlsx, stopwords .txt files, and the
