# Web-Scrapping-Hindi-Movies using selenium

### Problem Statement

In the realm of digital data, there is often a need to collect structured information from websites automatically. This is especially relevant for gathering up-to-date information about new movie releases, including details such as movie names, release years, directors, ratings, genres, cast, and associated image links. Manually collecting this data from websites can be laborious and inefficient, prompting the necessity for an automated solution.

### Solution

Web scraping offers an efficient way to automate the extraction of data from websites. In this context, Python provides robust libraries and tools to facilitate web scraping. The provided code leverages several Python libraries, including `requests`, `pandas`, `BeautifulSoup`, and `selenium`, to scrape movie data from the Gadgets360 website. The solution involves the following steps:

1. **Importing Necessary Libraries**:
   The code begins by importing essential libraries. `requests` handles HTTP requests, `pandas` is used for data manipulation and storage, `BeautifulSoup` from `bs4` parses HTML content, and `selenium` automates browser interactions. This combination of tools allows for efficient data extraction and processing.

2. **Initializing Data Storage Lists**:
   Several lists are initialized to store extracted movie details: `Movie_Name`, `Year_list`, `Director_List`, `Rating`, `Genre`, `Top_5_cast`, and `Image_links`. These lists will hold the data for each movie attribute as the script processes the website content.

3. **Setting Up Selenium WebDriver**:
   Selenium is used to automate web browser interactions. The code sets up the Chrome browser in headless mode (without a GUI) using specific options (`chrome_options`). This setup ensures the scraping process runs smoothly in the background. The `Service` object specifies the path to the ChromeDriver executable, which is necessary for controlling the browser. The `webdriver.Chrome()` function initializes the browser with the configured options and service.

4. **Defining the Data Parsing Function**:
   The `parse_movies()` function is defined to extract movie details from the HTML content. Using `BeautifulSoup`, the function identifies relevant HTML elements containing movie data and extracts:
   - **Movie Name**: Retrieved from the `h3` tag.
   - **Release Year**: Extracted from a specific `div` element.
   - **Director**: Retrieved from a `li` element with a class indicating it contains director information.
   - **Rating**: Extracted from a `span` element containing review information.
   - **Genre**: Retrieved from another `li` element and cleaned to remove extraneous characters.
   - **Top 5 Cast**: Extracted and formatted from a `li` element containing cast details.
   - **Image Links**: Extracted from `img` tags, ensuring only relevant links are appended to the list.

5. **Loading the Base URL and Interacting with the Web Page**:
   The script navigates to the base URL of the target website using `driver.get()`. It waits for the initial content to load using `WebDriverWait`. The script then simulates scrolling and clicking the "view more" button multiple times to load additional content dynamically. This process is crucial for scraping paginated data or data loaded dynamically via JavaScript.

6. **Parsing the Loaded Content**:
   After loading the content, `BeautifulSoup` parses the final HTML page source. The `parse_movies()` function is called to extract and store movie details in the initialized lists.

7. **Closing the WebDriver**:
   Once data extraction is complete, the Selenium WebDriver is closed using `driver.quit()`. This step is important to free up system resources and prevent potential memory leaks.

8. **Ensuring Data Consistency**:
   Before creating the DataFrame, the code ensures all lists have the same length by calculating the minimum length among them. This step avoids mismatched data entries when constructing the DataFrame.

9. **Creating a DataFrame and Saving to Excel**:
   The extracted data is organized into a pandas DataFrame. The DataFrame structure allows for easy data manipulation and analysis. Finally, the DataFrame is saved to an Excel file (`movie_data_final.xlsx`) using `df.to_excel()`, providing a structured and accessible format for the scraped data.

### Conclusion

This Python script effectively automates the process of scraping movie data from a website, demonstrating the power and versatility of web scraping techniques. By combining libraries like `requests`, `pandas`, `BeautifulSoup`, and `selenium`, the solution efficiently collects, processes, and stores structured data. This approach can be adapted for various web scraping tasks, making it a valuable tool for data collection and analysis in diverse applications.
