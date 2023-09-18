# Project 1: Burnout - Calorie App

## OBSERVED PAIN POINTS
**Missing documentation on configuring the chatbot**
- **Description of the Issue:**
  - We found an undocumented chatbot component in the application. After examining the code, we discovered it was a Dialogflow chatbot created with a hardcoded agent ID in an HTML template. Unfortunately, we cannot recreate, modify, or extend the chatbot because none of the queries it was trained on are present in the codebase. All the efforts invested by the previous team seem to be lost, as the only remaining component of the chatbot is the trained agent hosted on the Google Cloud, to which we have no access.
- **How it could have been avoided:**
  - Documentation could have significantly reduced the effort and time required to identify and analyze this issue. If the steps and queries used to train the Dialogflow model had been committed to the codebase, it would have enabled us to easily retrain, update, and extend the agent as needed to keep it up to date.

**Email functionality not working**
- **Description of the Issue:**
  - This issue was specific to one of the features: the 'send email' option allowed users to send their calorie history. However, this project used hardcoded values for the sender's email details, and due to some policy changes in Google, it no longer accepted authentication from third-party libraries. This caused the page to break every time we tried using this feature.
- **How it could have been avoided:**
  - Instead of relying on third-party libraries for authentication (an SMTP library was used here), we can make use of official Gmail APIs for sending emails. These would be less prone to such issues in the future.

**Incorrect data displayed on User Profile**
- **Description of the Issue:**
  - During 'User Profile' testing, we encountered an issue where the height, weight, and target weight values entered by users were not displaying correctly on the user profile page. Our investigation revealed that although the data was successfully stored in the database, the code responsible for fetching and displaying user profile information was not dynamically retrieving it from the database; instead, it relied on hardcoded values. Furthermore, there is no option to update user profile values in the database after submission.
- **How it could have been avoided:**
  - Regular code reviews and quality checks should have been in place as they would have highlighted the use of hardcoded values and prompted corrective action. Thorough testing along with unit tests should have been covered to ensure functionalities are working as expected.

**Calories dropdown not populated**
- **Description of the Issue:**
  - In the 'Enter Calories' scenario, we observed that the dropdown did not contain the correct data. To make the data available, we had to manually execute the 'insert\_food\_data.py' script, which populated the database. However, this information was not included in the Readme file.
- **How it could have been avoided:**
  - Documentation should have covered setting up the DB before running the project. There can also be certain pre-checks while trying to run the application to notify us if any prerequisite setup process is not complete.

**Test cases not functional**
- **Description of the Issue:**
  - All the test cases were commented out, and no test cases were being run. This is a major issue as bugs are not identified, and there are no checks on the correctness of the functionality.
- **How it could have been avoided:**
  - By updating and extending the test suite everytime changes were made to the application. Having automated testing to be run via hooks or github actions will ensure that tests are run frequently.
  - Having good documentation and guidelines for writing and running test cases also encourages regular testing.

**Lack of code organization**
- **Description of the Issue:**
  - The project had scattered Python files with no clear structure being followed. This affected code readability and required more time to be spent on figuring out their locations. This issue can also be noticed in the 'Templates' folder, which contains a large number of HTML files.
- **How it could have been avoided:**
  - When working with frameworks like Flask, it's beneficial to adhere to a predefined file structure, which aids in organizing our files effectively. Additionally, dividing the HTML components based on individual pages can significantly enhance code readability and maintainability.

## **PRACTICES WE WILL FOLLOW**

- **Completing Each Functionality in Full**

    - It was observed that the application has an abundance of features, many of which are merely placeholders with no actual impact. During our time, we would like to prioritize completing the selected features before considering additional ones.
- **Improving Documentation**
    - Documentation should provide a better understanding of third-party libraries and services that are integrated into the application. It should also cover how to configure and maintain them.
    - Thoroughly document all the versions of the third-party software required by the application, including the installation steps.
- **Implementing Standardized Approaches for Enhanced Functionality**
    -   The project should make use of common APIs and approaches which are less likely to change with time to ensure our code has minimum maintenance, allowing our development team to focus on innovation and improvements rather than constant updates.
- **Test Driven Development**

    -  We will try to ensure tests cases are well planned out and written before moving into implementing the actual functionality.
    - Set up guidelines for writing and running test cases and setup hooks or actions to run them before or after each commit to ensure tests are run regularly.