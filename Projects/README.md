# Unit 3: Campus Konbini App
![](background.jpeg)
<sub> Fig (1) shows a picture from coupons.com

# Criteria A: Planning

## Problem definition
My client, UWC ISAK Japan student, Paula Yaniz Macia is part of an entrepreneurship club. She identified a problem of our school being located too far away from the nearest konbini. With Edvards Rokens and Amine Itane by her side, she decided to make basic grocery shop items available to students on campus and made a project called “Campus Konbini”. However, she is facing a major challenge in managing and tracking all the data related to her project such as the date when they sold a product, the name of the product, the amount of product sold, and the profit they have made. The manual data management system for the 'Campus Konbini' project, writing data on paper,  is inefficient and vulnerable to physical damage, leading to data loss and errors. As a result, Paula and her team require a simple application that will store their data in a secure and accessible manner.
## Success criteria

1. The application must have a registration system where the users can register their email, username, and password which will be saved into the database.
2. The application must have a working login system, where all the credentials entered have to match with the database (registered data).
3. The application must encrypt the user's password in the local SQL database.
4. The application must have an input screen that gives the option to log data, view past data, or log out.
5. The user must be able to input all 4 attributes (date, name, quantity, and income of the product sold) into the database via the GUI.
6. The application will allow the user to view all attributes stored in the database.
7. The application must contain a  welcome screen, login screen, registration screen, home screen, screen to enter data, and screen to view the data; in total 6 unique screens.

## Design statement

I will design an application for Paula Yaniz Macia, a UWC ISAK student.  This will be a “Campus Konbini” application and will serve to store data of the sold items in digital format. To maintain security and privacy, the login system will have a hashing technique to secure everyone's password, and all of them will be saved in a local database using SQLite. The program will feature a graphical user interface (GUI) so that users may navigate it with a few mouse clicks. All of this will be written in the Python programming language with KivyMD serving as the GUI builder. The program Pycharm will be used to write and develop all of the code. It will be developed in a one-month period and judged by the success criteria previously stated.

## Rationale for proposed solution
### Why Python?
I have selected Python as my preferred programming language for a variety of reasons. To begin with, Python is the most widely used and well-known programming language worldwide [^1]. This will improve the client's overall experience by boosting the app's compatibility with a wider range of platforms and enabling me to have more access to resources and references. Python programming is what I am personally most comfortable with, therefore not only will everything be streamlined, but the client will also receive the app on time and without any extensions of the due date. Python is clearly the best programming language for this project, as seen by the advantages it provides for both the programmer and the client.

Future developers will be able to enhance and add to the program I have made because Python is claimed to be the most well-known and popular programming language in the entire world [^1]. Clients will also benefit from this since they will be able to obtain applications that are constantly updated with new features and viewpoints from other developers.

### Why KivyMd?

Using KivyMD has a significant advantage in that it enables developers to build applications that are compatible with multiple platforms, including Android, iOS, and Windows. KivyMD's small number of variables makes it highly suitable for co-development, facilitating easy interpretation and extending the application's functionality while saving time and effort [^2]. KivyMD is also the library I am the most familiar with and will help me as a developer to finish my project on time. Compared to other UI development software like Flutter, KivyMD has several advantages, such as a more supportive online community, ease of use, and, most importantly, compatibility with Python, making it the preferred choice for this project [^3].

### Why SQLite?

I opted to use SQLite as the most appropriate database management system for this solution. SQLite is a free database that runs on a single file without the need for an additional server process. It is ideal for my client's requirements as it can efficiently handle large volumes of data [^4]. Unlike IBM db2, it doesn't require lengthy procedural routines and continuously updates the stored content to minimize or eliminate data loss in the event of power failure or system crashes [^5]. This is crucial for my client, who needs fast and easy access to stored data. Additionally, its cross-platform compatibility enables future developers to extend the program to other platforms, providing additional benefits for my client. Compared to other databases, SQLite is the best option for my client due to its reliability, efficiency, cost-effectiveness, and user-friendliness [^4].

### Why is the output through GUI?

The output of the application will be a graphical user interface (GUI) instead of plain text. The reason for this is to fulfill the client's request for an application that not only captures and displays data but also does so through a GUI for ease of use. Keeping in view the client's specifications, I have concluded that a GUI-based output would be the most appropriate

## Works cited
[^1]: Eastwood, Brian. “The 10 Most Popular Programming Languages to Learn in 2021.” Northeastern University Graduate Programs, 13 Feb. 2023, www.northeastern.edu/graduate/blog/most-popular-programming-languages/. 

[^2]: Gupta, Kaustubh. “What Is KivyMD: Creating Android Machine Learning Apps Using KivyMD.” Analytics Vidhya, 6 July 2021, www.analyticsvidhya.com/blog/2021/06/creating-android-ml-app-kivymd/#:~:text=KivyMD%20is%20built%20on%20the. 

[^3]: “Kivy vs Flutter: Learn the Key Differences between Kivy and Flutter.” EDUCBA, 13 June 2022, www.educba.com/kivy-vs-flutter/. 

[^4]: Petros Koulianos. “5 Reasons to Use Sqlite the Tiny Giant for Your next Project.” Medium, The Startup, 9 Aug. 2020, medium.com/swlh/5-reasons-to-use-sqlite-the-tiny-giant-for-your-next-project-a6bc384b2df4. 

[^5]: “SQLite Advantages and Disadvantages - Javatpoint.” Www.javatpoint.com, www.javatpoint.com/sqlite-advantages-and-disadvantages. 

# Criteria B: Design

## System diagram
![](systemdiagram.png)

Fig. 2 This is the system diagram for the proposed solution.

It provides a graphic picture of the system, its parts, and how they work together. The application will function on Python and KivyMD, as was already mentioned. The user will provide the application with a variety of inputs, all of which will be stored in a database using SQLite. The Pycharm program will be used to carry out all of this, and the output will be shown on a screen.

## Wireframe diagram

![](Wireframe_diagram.png)

Fig. 3 This is the wireframe diagram for the application
  
This Wireframe Diagram displays the application's GUI's produced design. All six of the application's screens are displayed, along with the functionality of each button that was intended for use. The user can see which screen will open when they press the button thanks to the arrows that extend from the button to the screen.

## ER Diagram
  
![](ER_Diagram.png)

Fig. 4 This is the ER diagram 

This is the ER diagram for the database illustrating the relationship between the items table and users table from the "campuskonbini" database. In the items table, there are 6 different columns including id, user_id, date, item_name, quantity, and income which each column will have the specific data type after the column name. The second table has 4 columns which are username, id, email and password. This diagram also shows that 1 user can have multiple items.

## UML Diagram

![](UML_diagram.png)

Fig. 5 This is UML diagram

This UML diagram for the OOP classes illustrates the classes and methods utilized during the development of the application. It showcases two primary parent classes, namely MDApp and MDScreen. All the classes inherit the methods and attributes of these parent classes, which is demonstrated by the arrows displayed on the diagram.

## Flow diagrams

![](Try_register_flowchart.png)

Fig. 6 This is flow chart for try_register function

Figure shows the flow diagram of the method used for registration of a new user. It validates data entered for username, email, password and repeated password text fields, and if all credential requirements are met, data are stored successfully in the "campuskonbini" database.

![](Delete_flowchart.png)

Fig. 7 This is flow chart for delete function

Based on the checked rows in a user interface data table, this function deletes items table entries from the "campuskonbini" database. The function retrieves the chosen rows from the data table, extracts the "id" value from each row, and builds a query to remove the matching record from the database. The data table was updated after the selected rows were removed from the database, and a pop-up notice followed to confirm the deletion of the specified row(s).
  
![](update_flowchart.png)
  
Fig. 8 This is flow chart for update function
  
This function serves to update the table displayed in the History Screen. The purpose of this function is to keep the data table in sync with the database so that any changes made to the database are immediately reflected in the data table.

## Test plan

| Description              | Category     | Input                                                                                                                                                 | Expected output                                                                                                                                                                                                                                                                                                                                                                                                                  |
|--------------------------|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Test registration system | Unit testing | 1. Run project3.py 2. Click the register button on the Welcome Screen 3. Input data on all the fields 4. Click register                               | After clicking the register button, if the user already exists in the database, a pop-up message will appear and let the user know. If any of the fields where the user input data do not meet specific requirements error message will appear. If all the instructions were followed correctly user will be taken back to the Welcome screen, and be able to log in as all the data are now stored in "campuskonbini" database. |
| Test login system        | Unit testing | 1. Run project3.py 2. Click the login button on the Welcome Screen 4. Input data on all the fields 5. Click login                                     | After clicking the log-in button, if the user doesn't exist, a pop-up message will appear letting the user know. If user exists and the password is correct user will be taken to the Home screen                                                                                                                                                                                                                                |
| Test Home screen         | Unit testing | 1. Run project3.py 2. Login 3. Click all the 3 buttons displayed on the Home screen (add a new item, history, log out)                                | After clicking the "Add new item" button user should be taken to the Input screen; History screen if the user clicked the "History" button and Welcome screen if a user clicked "Log out".                                                                                                                                                                                                                                       |
| Test Input screen        | Unit testing | 1. Run project3.py  2. Login 3. Input data on all the 4 fields (date, name of the item, quantity, and the profit made)                                | After clicking "Select Date of Entry" the date picker will be displayed. After clicking input all of the data input should be stored in the database in the "items" table. A pop-up message appears letting the user know that the item was stored successfully                                                                                                                                                                  |
| Test History screen      | Unit testing | 1. Run project3.py 2. Login 3. Press "History" button on the Home Screen                                                                              | After clicking the "History" button, all the data inputted by the user is displayed in the table, the user will not be able to see the data input by another user.                                                                                                                                                                                                                                                               |
| Test delete Item System  | Unit testing | 1. Run project3.py 2. Login  3. Click "History" button  4. Click on checkboxes of the item(s) that the user wants to delete  5. Click "delete" button | A checkmark will show up inside the box when the user selects the checkbox next to the item. The selected item(s) should then be deleted from the table when they click the delete item button.                                                                                                                                                                                                                                  |
| Code review              | Code review  | Check the Project3.py file for any inadequate variable names or repetitive and inefficient programming methods                                        | The user can better grasp how the code works according to the variable names and comment. The code should be simple to understand and easy to follow.                                                                                                                                                                                                                                                                            |

## Record of tasks
  
| Task No | Planned action                                           | Planned outcome                                                                                                              | Time estimate | Target completion | Criteria |
|---------|----------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|---------------|-------------------|----------|
| 1       | First meeting with client                                | To understand client problem and requirements                                                                                | 10 minutes    | 09.2.2023         | A        |
| 2       | Write down success criteria                              | To list down the first success criteria                                                                                      | 30 minutes    | 12.2.2023.        | A        |
| 3       | Write problem definition                                 | A clear problem definition of what the client is facing.                                                                     | 20 minutes    | 12.2.2023.        | A        |
| 4       | Write down a design statement for the client             | A clear design statement that suits the need of the client                                                                   | 20 minutes    | 12.2.2023         | A        |
| 5       | Research and write a rationale for the proposed solutio  | A clear justification that suits the client and developer.                                                                   | 45 minutes    | 13.2.2023.        | A        |
| 6       | Meet with the client to discuss the success criteria.    | Receive the final approval to start creating the application                                                                 | 15 minutes    | 14.2.2023.        | A        |
| 7       | Create system diagram                                    | Develop a clear idea of the hardware and software requirements for the proposed solution                                     | 30 minutes    | 15.2.2023.        | B        |
| 8       | Create ER diagram                                        | ER diagram is created for both tables                                                                                        | 20 minutes    | 18.2.2023         | B        |
| 9       | Create Wireframe diagram                                 | A clear and creative wireframe diagram of the GUI                                                                            | 50 minutes    | 18.2.2023.        | B        |
| 10      | Create UML diagram                                       | Have a finsihed UML diagram, an accurate representation of all classes and object in the python code                         | 60 minutes    | 19.2.2023         | B        |
| 11      | Produce Flow diagrams including descriptions             | Flowcharts and a brief explanation for each section of the solution to obtain a clearer understanding of the code's proccess | 2 hours       | 19.2.2023         | B        |
| 12      | Code Welcome screen                                      | Create visually appealing design on the Welcome screen and buttons positioned correctly                                      | 50 minutes    | 21.2.2023.        | C        |
| 13      | Code and create a working registration screen of the app | A working registration screen with python or kivyMD with a GUI                                                               | 3 hours       | 25.2.2023         | C        |
| 14      | Code and create a working log in screen of the app       | A working log in screen with python or kivyMD with a GUI                                                                     | 2 hours       | 26.2.2023.        | C        |
| 15      | Create database                                          | Insert and store inputs of users and items into the database                                                                 | 30 minutes    | 26.2.2023.        | C        |
| 16      | Create Home screen according to the wireframe diagram    | Screen that contains buttons Input, History, Logout                                                                          | 30 minutes    | 28.2.2023.        | C        |
| 17      | Create Input screen                                      | A page that allows the user to enter items into the 'items' table within the database                                        | 4 hours       | 1.3.2023.         | C        |
| 18      | Add MDSlider                                             | Use MDSlider so user can put the number of product sold                                                                      | 1 hour        | 2.3.2023.         | C        |
| 19      | ADD MDDatePicker                                         | Use MDDatePicker so user can select the date of entry                                                                        | 30 minutes    | 2.3.2023.         | C        |
| 20      | Show add item screen to client                           | Making sure that Input screen meet client's requirements                                                                     | 15 minutes    | 4.3.2023.         | A        |
| 21      | Create table in the History screen                       | Creating table which will display data stored in the table                                                                   | 50 minutes    | 5.3.2023.         | C        |
| 22      | Creating delete item function                            | Adding checkboxes to the table and allowing user to select row which will be deleted                                         | 2 hours       | 5.3.2023.         | C        |
| 23      | Working on buttons functionality                         | Making sure that screens are well connected through buttons                                                                  | 30 minutes    | 6.3.2023.         | C        |
| 24      | Finalise program                                         | Fixing errors found, fixing unwanted repetition of the code                                                                  | 3 hours       | 6.3.2023.         | C        |
| 25      | Present application to the client                        | Having a feedback about application from the client                                                                          | 20 minutes    | 6.3.2023.         | C        |
| 26      | Finalize test plans                                      | Write test plan with inputs and expected outputs                                                                             | 45 minutes    | 7.3.2023.         | B        |
| 27      | Finalize program based on the feedback                   | Add improvements to the code based on the clients feedback                                                                   | 4 hours       | 7.3.2023.         | C        |
| 28      | Write criteria C                                         | Add parts of the code and descriptions                                                                                       | 2 hours       | 8.3.2023.         |          |

  
# Criteria C: Development
