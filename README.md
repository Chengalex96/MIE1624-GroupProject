# MIE1624-GroupProject

**Part 1: Create a Webscraper to search through Indeed job postings using BeautifulSoup and Selenium**

The notebook is part of a project to re-design a course curriculum for MIE 1624: Introduction to Data Science and Analytics. This is done by performing a web scraping exercise to extract relevant skills required for data analyst, data scientist, data manager, data engineer, etc. from well-known job posting sites, such as Indeed, glassdoor, linkedin, upwork, etc. Additional data will also be obtained from Kaggle datasets and other online platforms such as CognitiveClas.ai, Coursera, EdX, DataCamp, etc.

This notebook will extract the skills for data related jobs from Indeed sites, focusing on North America countries: US and Canada.

The scraping is conducted using "requests", "BeautifulSoup", and if needded, "Selenium" libraries in Python, then "pandas" library will be used to assemble data into dataframe for further pre-processing and cleaning steps. Note that BeautifulSoup is:

a Python-based parsing library that allows you to extract data from web pages
It structures an HTML or XML web page. BS is made up of different parsing tools such as html.parser, lxml, and HTML5lib
user-friendly
Selenium is a library that lets you code a python script that would act just like a human user. Selenium is used when target websites has a lot of Javascript elements in its code. Selenium is an API that allow you to control a headless browser through a series of programs. When using Selenium, you can also perform other actions such as mouse clicks and filling forms.

A URL for data scientist job search in Toronto from Indeed site looks like: "https://ca.indeed.com/jobs?q=data%20scientist&l=Toronto%2C%20ON", where:

"q=" begins the string for the “what” field on the page, separating search terms with “+” (i.e. searching for “data+scientist” jobs)
“&l=” begins the string for city of interest, separating search terms with “+” if city is more than one word (i.e. “New+York”
Each page of the job results have 15 job posts.

Webscraping: Initialing fak agents to prevent being detected by the website's bot tracker, create a for loop to loop throung multiple pages of data, with rangom gaps of time in between, using the requests.get() function, parse all of the data using BeautifulSoup, the job description is parsed using html tags (div tag). CHange the User Agent every 10 pages to avoid suspiciion. The data is then placed into a pandas dataframe.

THe topics, tools and softskills are sorted and converted to a csv file to indicate the most important traints for that job position.

**Part 1-1: Indeed Text Analytics**

From Indeed_JobDescription_TextAnalytics.ipynb, we can examine the top key skills (soft and hard skills) across multiple job categories. Using nltk to preprocess the words, convert all of the words to lower case and convert the strings into a list, stop words are removed, and then the words are converted from a list back into a string. 

Used WordCloud to help visuaize the most common words.

![image](https://github.com/user-attachments/assets/48714e28-9003-463f-9897-2f979d53706b)

These are also plotted for each job category to see if there are major differences between them.

**Part 1-2: Kaggle Webscraping**

Using the Kaggle Dataet provided for Assignment 1 and 2, we can examine many key features of Data and ML jobs. Firstly, the jobs weere cleaned of to only filter through people in Canada and United Sates, salary distributions were bar plooted for each job description with the salry being bucketed from 0-14, heatmaps were created to show the relationship between jobs, skills, and tools. 

Programming Languages:

![image](https://github.com/user-attachments/assets/b11b89ab-9e87-4b61-87c7-6fce371809e4)

IDEs:

![image](https://github.com/user-attachments/assets/aa27b574-0bb7-40d3-ada7-b07c486a95b2)

Notebooks:

![image](https://github.com/user-attachments/assets/ce4641c8-9757-4a31-bc69-63aa081e228c)

Visualizion Libraries:

![image](https://github.com/user-attachments/assets/19ae05d5-3628-48d8-a185-15e6fdd33750)

Machine Learning Frameworks:

![image](https://github.com/user-attachments/assets/c6b94c30-1e0f-48dc-8425-4d3454bdabc5)

Heatmaps for multiple features were listed. 

Used the Mann-Whitney U-test to determine which features were correlated with a higher salary, determine it to be to 4 features ["Q17", "Q19", "Q23", "Q33"]

Performed bootstrapping to convery the data into a normal distribution. Determine which model the data fits.

**Part 2: Redesign the MAster's Program**

**Part 2-1: Examining Coursera and EdX**

Courses info was manually scraped, data was cleaned: html tags removed, character codes, nans were filled as blanks, lowercases, removed puncuations, remove stop words, count to see the most common words, 2 most common words used together using nltk ngrams, visualize using WordCloud

![image](https://github.com/user-attachments/assets/36016c60-abb5-4adc-8da3-664e4e876b48)


**Part 2-2: Clustering COurses**

Two datasets: Universities and Online courses that were both manually scraped,covert both datasets into the same format, data was preprocessed for Lowercasing, removing punctzation and word counting. Tokenization and Stop Word removal Words are first separated in tokens and then the stop words from a list of most common english words are removed. Later it was considered to remove words that are common in every document such as data. However, it was determined that the words would distort the analysis. For example the word data was very frequent but when it would be removed the cluster regarding databases etc. would be lost combined with the insights taken from this. Vectorization using TF-IDF Vectorizer Representing words in the form of their term frequency and inverse document frequency. (Overall appearance and number of documents they appeared in).

CLustering: First the dimensions of the embeddings are reduced. Therfor the UMAP algorithm is used.

Visuzlization: T-SNE is required to enable the low dimensional visualization

![image](https://github.com/user-attachments/assets/125f6658-f25b-4748-ae9c-337554584baa)

The clustering based on the syllabi showes two big clusters. Basically the algorithm separates the online and the university courses to some extent but fails to establish subclusters.

For this reason the clustering is repeated based on the course descriptions rather than the syllabi.

![image](https://github.com/user-attachments/assets/c0dc6e18-3a29-4608-997d-eaf7a26a99a1)

This shows much better results and 8 distinguishable clusters as well as a cluster containing outliers are created. The clusters are all analyzed in the following Please note that rerunning the code changes the numbers of the clusters with the content reamaining the same. Therefore the comments will be not representing the actual cluster after rerunning.

CLusters were made for each of them (8), to showcase the frequent words and skills used. 

**Part 3: Recommender System**

Generated random data to represent a random student choosing a random course, then will recommended an appropriate course.

This function will generate a dataset with features associated to courses. 

The dataset will have the following columns:
  - course_id (String): Unique identifier for the course
  - course_topic (Integer): An integer value representing the topic for the course, value is between 1 and 5, 
                            indicating that there are 5 unique topics. Each course can only have 1 topic.
  - professor_id (String): Unique identifier for the professor
  - student_id (String): Unique identifier for the student
  - course_rating (Integer): A value between 0 and 5

params:
  n_courses (Integer): The number of courses in the dataset
  n_topics (Integer): The number of course topics to be chosen from
  n_professors (Integer): Number of professors to be generated
  n_students (Integer): Number of students for the dataset
  size (Integer): The number of rows in the dataset

**Recommender System - Collaborative Filtering:**

**Model BAsed:**

Generate predictions using matrix projections, return predictions of top three courses

**Memory based using User-User**
Find similarity between users by assessing the rating pattern of two users. Using KNN with Means and calculate the rmse.

User Based: Here, we look for the users who have rated various items in the same way and then find the rating of the missing item with the help of these users.

**Item to Item Collaborative FIltering**

Used if more users than items. Looks for the similar items, which user X has already rated and recommends the most similar items. Here similarity means how people treat two items in terms of ratings. If two items get same kind of ratings with the same users then they are similar.

Item Based: Here, we explore the relationship between the pair of items (the user who bought Y, also bought Z). We find the missing rating with the help of the ratings given to the other items by the user.




