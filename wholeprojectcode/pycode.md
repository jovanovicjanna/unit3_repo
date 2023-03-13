## Pytrhon code

```.py


import sqlite3
from kivymd.app import MDApp
from kivymd.uix.dialog import MDDialog
from kivymd.uix.screen import MDScreen
from kivymd.uix.pickers import MDDatePicker
from kivymd.uix.datatables import MDDataTable
from secure_password import encrypt_password, check_password

class database_worker:
    def __init__(self, name: str):
        self.connection = sqlite3.connect(name)
        self.cursor = self.connection.cursor()

    def search(self, query):
        result = self.cursor.execute(query).fetchall()
        return result

    def run_save(self, query):
        self.cursor.execute(query)
        self.connection.commit()

    def create_tables(self):
        query1 = f"""CREATE TABLE if not exists users(
        id INTEGER PRIMARY KEY,
        username text NOT NULL unique,
        email text NOT NULL unique,
        hashed_password text NOT NULL
        )"""
        query2 = f"""CREATE TABLE if not exists items(
        id INTEGER PRIMARY KEY,
        user_id INTEGER NOT NULL,
        date INTEGER NOT NULL,
        item_name TEXT NOT NULL,
        quantity INTEGER NOT NULL,
        income INTEGER NOT NULL
        )"""
        self.run_query(query1)
        self.run_query(query2)

    def run_query(self, query: str):
        self.cursor.execute(query)
        self.connection.commit()

    def close(self):
        self.connection.close()


class HomeScreen(MDScreen):
    pass


class WelcomeScreen(MDScreen):
    pass



class LoginScreen(MDScreen):
    def try_login(self):
        uname = self.ids.uname.text
        passwd = self.ids.passwd.text

        db = database_worker("campuskonbini")
        query_2 = f"SELECT username from users"
        user_list = []
        uname_result = db.search(query_2)
        for element in uname_result:
            user_list.append(element[0])
        print(user_list)

        if len(uname)==0:
            self.ids.uname.error = True
            self.ids.uname.helper_text = "This Field requires input"

        elif uname not in user_list:
            self.ids.uname.error = True
            self.ids.uname.helper_text = "User does not exist."


        if not passwd:
            self.ids.passwd.error = True
            self.ids.passwd.helper_text = "This Field requires input"

        print("User tried to login")
        # Get the input username and password and print it
        uname = self.ids.uname.text
        passwd = self.ids.passwd.text
        db = database_worker("campuskonbini")
        query = f"SELECT * from users WHERE username='{uname}'"
        result = db.search(query)
        if len(result) == 1:
            id,email,username,hashed_password = result[0]
            if check_password(passwd, hashed_password):
                self.user_id = id
                self.ids.uname.text = ""
                self.ids.passwd.text = ""
                self.parent.current = "HomeScreen"
                print("Login successful")
                db.close()

class RegistrationScreen(MDScreen):
    def try_register(self):
        uname = self.ids.uname.text
        email = self.ids.email.text
        passwd = self.ids.passwd.text
        passwd_check = self.ids.passwd_check.text

        # Check if username exists
        db = database_worker("campuskonbini")
        query_2 = f"SELECT username from users"
        user_list = []
        uname_result = db.search(query_2)
        for element in uname_result:
            user_list.append(element[0])
        print(user_list)
        if uname not in user_list:

            if len(uname) == 0:
                self.ids.uname.error = True
                self.ids.uname.helper_text = "This field is required"
                return

            if "@" not in email:
                self.ids.email.error = True
                self.ids.email.helper_text = "Invalid email"
                return

            if len(passwd) < 6 or " " in passwd or passwd != passwd_check:
                if len(passwd) < 6:
                    self.ids.passwd.error = True
                    self.ids.passwd.helper_text = "Password must be longer than 6 characters"
                if " " in passwd:
                    self.ids.passwd.error = True
                    self.ids.passwd.helper_text = "Password cannot contain spaces"
                if passwd != passwd_check:
                    self.ids.passwd_check.error = True
                    self.ids.passwd_check.helper_text = "Passwords do not match"

            else:  # password match
                db = database_worker("campuskonbini")
                hash = encrypt_password(passwd)
                query = f"INSERT into users(username, email, hashed_password) values('{uname}', '{email}','{hash}')"
                db.run_save(query)
                db.close()
                print("Registration completed")
                self.parent.current = "WelcomeScreen"
        else:
            self.ids.uname.error = True
            self.ids.uname.helper_text = "This user already exists"




        return

class InputScreen(MDScreen):

    def add_item(self):
        date = self.ids.date.text
        item_name = self.ids.item_name.text
        quantity = self.ids.quantity.value
        income = self.ids.income.text
        user_id = self.manager.get_screen("LoginScreen").user_id

        db = database_worker("campuskonbini")
        query = f"INSERT into items (user_id,date,item_name,quantity,income) values('{user_id}','{date}', '{item_name}', '{quantity}','{income}')"
        db.run_save(query)
        db.close()
        self.parent.current = "HomeScreen"
        dialog = MDDialog(title="Item successfully added",
                          text=f"Your item ID: {item_name} has been successfully added.")
        dialog.open()

        self.ids.date.text = ""
        self.ids.item_name.text = ""
        self.ids.quantity.value = 5
        self.ids.income.text = ""

    def show_date_picker(self):
        date_dialog = MDDatePicker()
        date_dialog.bind(on_save=self.on_save)
        date_dialog.open()

    def on_save(self, instance, value, date_range):
        self.selected_date = value
        value = value.strftime("%m/%d/%Y")
        self.ids.date.text = f"{value}"


class HistoryScreen(MDScreen):
    # class attribute
    data_table = None

    # Get data from database
    def on_pre_enter(self, *args):

        self.data_table = MDDataTable(
            use_pagination=True,
            size_hint=(0.9, 0.6),
            pos_hint={"center_x": 0.5, "top": 0.75},
            column_data=[
                ("ID", 20),
                ("Date", 20),
                ("Name of the item", 35),
                ("Quantity", 20),
                ("Income", 35)
            ],
            check=True
        )
        self.data_table.bind(on_row_press=self.row_pressed)
        self.data_table.bind(on_check_press=self.check_pressed)
        self.add_widget(self.data_table)
        self.update()

    def row_pressed(self, table, row):
        print("a row was pressed", row.text)

    def check_pressed(self, table, current_row):
        print("a check mark was pressed", current_row)

    def update(self):
        db = database_worker("campuskonbini")
        user_id = self.manager.get_screen("LoginScreen").user_id
        query = f"Select id,date,item_name,quantity,income from items where user_id ='{user_id}'"
        data = db.search(query)
        db.close()
        self.data_table.update_row_data(None, data)

    def delete(self):
        # Function to delete checked rows in the table
        checked_rows = self.data_table.get_row_checks()  # Get the checked rows
        # delete
        db = database_worker("campuskonbini")
        for r in checked_rows:
            item_id = r[0]  # use item_id instead of id
            query = f"delete from items where id= {item_id}"  # use item_id instead of id
            db.run_save(query)
            # Create and open the alert dialog to confirm item has been deleted
            dialog = MDDialog(title="Thank you, item deleted!",
                              text=f"Your item has been successfully deleted.")
            dialog.open()
        db.close()
        self.update()

class project3(MDApp):
    def build(self):
        return


# create an object
db = database_worker(name="campuskonbini")
db.create_tables()
db.close()
test = project3()
test.run()
```
