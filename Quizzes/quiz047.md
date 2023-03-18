# Quiz 047

![Screen Shot 2023-03-18 at 17 18 56](https://user-images.githubusercontent.com/111895127/226094122-e0bdd3a0-3b88-4f0e-b364-ae591b06a74e.png)

## Python code
```.py
import sqlite3
from kivymd.app import MDApp
from unit3lib import encrypt_password

class database_worker:
    def __init__(self, name):
        self.connection = sqlite3.connect(name)
        self.cursor = self.connection.cursor()

    def search(self, query):
        result = self.cursor.execute(query).fetchall()
        return result

    def run_save(self, query):
        self.cursor.execute(query)
        self.connection.commit()

    def close(self):
        self.connection.close()

class quiz047(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.components = {"basic":0}

    def build(self):
        return

    def update(self):
        # This function updates all the labels in the form using the base salary and the percentage
        # Pseudocode
        # 1- get the base salary from the GUI
        base = self.root.ids.base.text
        hash = ""
        # 2- if base salary define total=int(base) and an empty string to store build a hash (for_hash="") if no base then end the function
        test_field_ids = ['health', 'pension', 'income_tax', 'inhabitant']
        if base != "":
            total = int(base)
            hash += f"base{total}"

            for i in test_field_ids:
                value = self.root.ids[i].text
                if value != "":
                    new_value = f"{int(value) * int(base) / 100} JPY"
                    total -= int(value) * int(base) / 100
                    hash += f"{i}{value}"
                else:
                    new_value = "JPY"
                label_id = f"{i}_label"
                self.root.ids[label_id].text = new_value

            hash += f"total{int(total)}"
            self.root.ids.salary_label.text = f"{total} JPY"
            hashed = encrypt_password(hash)
            self.hash = hashed
            self.root.ids.hash.text = hashed[-50:]

    def save(self):
        def save(self):
            base_widget = self.root.ids.base
            base = base_widget.text.strip()
            values = {
                "base": self.root.ids.base_label.text.strip()[:-4],
                "inhabitant": self.root.ids.inhabitant_label.text.strip()[:-4],
                "income_tax": self.root.ids.income_tax_label.text.strip()[:-4],
                "pension": self.root.ids.pension_label.text.strip()[:-4],
                "health": self.root.ids.health_label.text.strip()[:-4],
                "salary": self.root.ids.salary_label.text.strip()[:-4],
                "hash": self.hash,
            }

            query = "INSERT INTO payments (base, inhabitant, income_tax, pension, health, total, hash) VALUES (?, ?, ?, ?, ?, ?, ?)"
            db = database_worker("payments.db")
            try:
                db.cursor.execute(query, [values[key] for key in values.keys()])
                db.connection.commit()
                self.root.ids.hash_label.text = "Payment saved"
            except Exception as e:
                print(f"Error saving payment: {e}")
            finally:
                db.close()
        self.root.ids.hash.text = f"Payment saved"

    def clear(self):
        for label in ["base", "inhabitant","income_tax","pension","health"]:
            self.root.ids[label].text = ""
            self.root.ids[label+"_label"].text = " JPY"

        self.root.ids["salary_label"].text = " JPY"
        self.root.ids.hash.text = "----"


test = quiz047()
create = """CREATE TABLE if not exists payments(
     id         INTEGER primary key,
     base       INTEGER,
     inhabitant INTEGER,
     income_tax INTEGER,
     pension    INTEGER,
     health     INTEGER,
     total      INTEGER,
     hash       TEXT);"""
db = database_worker("payments.db")
db.run_save(create)
db.close()
test.run()
```

## Kivy code

```.kv
MDScreen:
    id:bck
    size: 200, 500

    MDBoxLayout:
        id: bck
        size_hint: .8,.9
        md_bg_color: "#F2F2F2"
        orientation: "vertical"
        pos_hint: {"center_x":.5, "center_y":.5}
        spacing: dp(10)

        MDLabel:
            text:"Compensation Calculator"
            halign: "center"
            font_style:"H4"
            color: "#222222"

        MDBoxLayout:
            size_hint_x: .8
            height: dp(46)
            valign: "center"
            md_bg_color: "#FFFFFF"
            pos_hint: {"center_x":.5, "center_y":.5}
            spacing: dp(10)

            MDIcon:
                icon: "plus-circle"
                pos_hint: {"center_x": .5, "center_y": .5}
            MDLabel:
                text:"Base Salary"
                size_hint_x: .4
            MDTextField:
                id:base
                mode: "rectangle"
                input_filter:"int"
                text_color_normal: "#222222"
                line_color_normal: "#222222"
                hint_text: "Base Salary"
                pos_hint: {"center_x": .5, "center_y": .5}
                on_text:
                    root.ids.base_label.text = f"{self.text} JPY"
                    app.update()
            MDLabel:
                id: base_label
                text:" JPY"

        MDBoxLayout:
            size_hint_x: .8
            height: dp(46)
            valign: "center"
            md_bg_color: "#FFFFFF"
            pos_hint: {"center_x":.5, "center_y":.5}
            spacing: dp(10)


            MDIcon:
                icon: "minus-circle"
                pos_hint: {"center_x": .5, "center_y": .5}
                color: "#9d0208"
            MDLabel:
                text:"Health"
                size_hint_x: .4
                color: "#6a040f"
            MDTextField:
                id:health
                mode: "rectangle"
                input_filter:"int"
                hint_text: "% Health"
                pos_hint: {"center_x": .5, "center_y": .5}
                text_color_normal: "#9d0208"
                line_color_normal: "#9d0208"
                on_text:
                    self.text = str(max(0, min(100, int(self.text or 0))))
                    app.update()
            MDLabel:
                id: health_label
                text:" JPY"
                color: "#9d0208"

        MDBoxLayout:
            size_hint_x: .8
            height: dp(46)
            valign: "center"
            md_bg_color: "#FFFFFF"
            pos_hint: {"center_x":.5, "center_y":.5}
            spacing: dp(10)


            MDIcon:
                icon: "minus-circle"
                pos_hint: {"center_x": .5, "center_y": .5}
                color: "#9d0208"
            MDLabel:
                text: "Pension"
                size_hint_x: .4
                color: "#9d0208"
            MDTextField:
                id:pension
                mode: "rectangle"
                input_filter:"int"
                hint_text: "% Pension"
                text_color_normal: "#9d0208"
                line_color_normal: "#9d0208"
                pos_hint: {"center_x": .5, "center_y": .5}
                on_text:
                    self.text = str(max(0, min(100, int(self.text or 0))))
                    app.update()
            MDLabel:
                id: pension_label
                text:" JPY"
                color: "#9d0208"


        MDBoxLayout:
            size_hint_x: .8
            height: dp(46)
            valign: "center"
            md_bg_color: "#FFFFFF"
            pos_hint: {"center_x":.5, "center_y":.5}
            spacing: dp(10)

            MDIcon:
                icon: "minus-circle"
                pos_hint: {"center_x": .5, "center_y": .5}
                color: "#9d0208"
            MDLabel:
                text:"Income Tax"
                size_hint_x: .4
                color: "#9d0208"
            MDTextField:
                id:income_tax
                mode: "rectangle"
                input_filter:"int"
                hint_text: "% Income"
                text_color_normal: "#9d0208"
                line_color_normal: "#9d0208"
                pos_hint: {"center_x": .5, "center_y": .5}
                on_text:
                    self.text = str(max(0, min(100, int(self.text or 0))))
                    app.update()
            MDLabel:
                id: income_tax_label
                text:" JPY"
                color: "#9d0208"

        MDBoxLayout:
            size_hint_x: .8
            height: dp(46)
            valign: "center"
            md_bg_color: "#FFFFFF"
            pos_hint: {"center_x":.5, "center_y":.5}
            spacing: dp(10)


            MDIcon:
                icon: "minus-circle"
                pos_hint: {"center_x": .5, "center_y": .5}
                color: "#9d0208"
            MDLabel:
                text:"Inhabitant Tax"
                size_hint_x: .4
                color: "#9d0208"
            MDTextField:
                id:inhabitant
                mode: "rectangle"
                input_filter:"int"
                hint_text: "%  Income"
                text_color_normal: "#9d0208"
                line_color_normal: "#9d0208"
                pos_hint: {"center_x": .5, "center_y": .5}
                on_text:
                    self.text = str(max(0, min(100, int(self.text or 0))))
                    app.update()
            MDLabel:
                id: inhabitant_label
                text:" JPY"
                color: "#9d0208"


        MDBoxLayout:
            size_hint_x: .8
            height: dp(46)
            valign: "center"
            md_bg_color: "#22223b"
            pos_hint: {"center_x":.5, "center_y":.5}
            spacing: dp(10)

            MDLabel:
                size_hint_x: .5
            MDIcon:
                icon: "calculator"
                pos_hint: {"center_x": .5, "center_y": .5}
                color: "#F2F2F2"
            MDLabel:
                text:"Net Salary"
                size_hint_x: .4
                color: "#F2F2F2"
            MDLabel:
                id: salary_label
                text:" JPY"
                color: "#F2F2F2"
            MDFloatingActionButton:
                icon:"content-save-plus"
                md_bg_color:"#ffc300"
                icon_color:"#222222"
                pos_hint: {"center_x": .5, "center_y": .5}
                on_press:
                    app.save()

            MDFloatingActionButton:
                icon:"autorenew"
                md_bg_color:"#2a9d8f"
                icon_color:"#222222"
                pos_hint: {"center_x": .5, "center_y": .5}
                on_press:
                    app.clear()

        MDBoxLayout:
            size_hint: .8, .2
            valign: "center"
            md_bg_color: "#FFFFFF"
            pos_hint: {"center_x":.5, "center_y":.5}

            MDLabel:
                id: hash
                halign: "center"
                text: "----"
                font_style: "Caption"
```

## Evidence

https://user-images.githubusercontent.com/111895127/226094332-9ef8bda1-6b11-4773-93a5-c5814f369603.mov



