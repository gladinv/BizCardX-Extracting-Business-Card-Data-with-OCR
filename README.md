OCR,streamlit GUI, SQL,Data Extraction

Here's a stepwise walkthrough of the code:

1. The code starts by importing the required libraries:
   - `easyocr` for text extraction from images
   - `cv2` for image processing
   - `pandas` for data manipulation and analysis
   - `re` for regular expression matching
   - `sqlite3` for working with SQLite databases
   - `base64` for encoding and decoding images
   - `streamlit` for creating web applications
   - `streamlit_option_menu` for creating a menu bar in Streamlit

2. A file name is assigned to store the image. In this case, it is set as "Gladin".

3. The code establishes a connection with an SQLite database named "data.db" and creates a table named "Business_data" if it doesn't already exist.

4. The code defines a function named `upload_database` to retrieve data from a business card image and upload it to the database. This function takes an image file as input.

5. Inside the `upload_database` function, the image is read using OpenCV's `cv2.imread` function.

6. The image is processed by converting it to grayscale and applying a threshold to zero using OpenCV's `cv2.cvtColor` and `cv2.threshold` functions.

7. The `easyocr` library is used to extract text from the processed image. The `easyocr.Reader` is initialized with the language set to English, and the `readtext` function is called to get both paragraph and non-paragraph text.

8. The extracted text is concatenated into a single string.

9. The code extracts different pieces of information from the text using regular expressions:
   - Name: The first element of the `result` list.
   - Designation: The second element of the `result` list.
   - Email: Matches any email addresses in the text using a regular expression.
   - Contact Numbers: Matches phone numbers using a regular expression.
   - Address: Matches a pattern of digits followed by a sequence of characters and digits.
   - Website: Matches any website links using a regular expression.
   - Company Name: The last element in the `res` list after removing other extracted information.

10. The image is read again as binary data and encoded using `base64.b64encode` to store it as a blob in the database.

11. The retrieved data is inserted into the database using an SQL query.

12. Another function named `extracted_data` is defined to extract data from the image and return the image with detected text highlighted.

13. Inside the `extracted_data` function, the image is read and processed similar to the previous function.

14. The `easyocr` library is used again to read the text from the processed image, but this time, the `decoder` parameter is set to 'wordbeamsearch' for better accuracy.

15. The extracted text is drawn on the image using OpenCV's `cv2.rectangle` and `cv2.putText` functions.

16. The `st.set_page_config` function is called to set the title and icon for the Streamlit app.

17. The title is added to the app using `st.title`.

18. A menu bar is created using the `option_menu` function from the `streamlit_option_menu` library. The menu has four options: Home, Process, Search, and Contact.

19. The code checks the selected option using an `if` statement and executes the corresponding section of code.

20. In the Home section, some introductory text and animated GIFs are displayed using `st.subheader` and `st.markdown`.

21. In the Process section, the user can choose an image file to extract data
