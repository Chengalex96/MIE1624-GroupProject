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












