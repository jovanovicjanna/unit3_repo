# Quiz041

![](Screen%20Shot%202023-03-18%20at%2013.23.42.png)

## Python code
```.py
from kivymd.app import MDApp

class quiz041(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.values = [0, 0, 0, 0, 0, 0, 0, 0, 0]
        self.player = "X"

    def pressed(self, button_id):
        print(button_id)
        current_player = self.player
        temp = "self.root.ids.button" + button_id
        current_button = eval(temp)
        if self.values[int(button_id) - 1] == 0:
            current_button.text = current_player
            if current_player == "X":
                self.player = "O"
                current_button.md_bg_color = "#ff0040"
                self.values[int(button_id) - 1] = 1
            else:
                self.player = "X"
                current_button.md_bg_color = "#fae7b5"
                self.values[int(button_id) - 1] = 2

    def build(self):
        return

app = quiz041()
app.run()
```

## Kivy code
```.kv
Screen:
    size:500, 500

    MDBoxLayout:
        id: main_box
        orientation: "vertical"
        size_hint:.8,.2
        pos_hint: {'center_x':.5,'center_y':.8}

        MDLabel:
            id: name
            text: "Tic Tac Toe by Jana"
            font_style: "H5"
            halign: "center"
            color: "black"
        MDLabel:
            id: turn
            text: "It is X's turn"
            font_style: "H6"
            halign: "center"
            color: "black"

    MDBoxLayout:
        id: row1
        size_hint:.6,.2
        pos_hint: {'center_x':.5,'center_y':.6}
        MDRaisedButton:
            id: button1
            font_style: "H3"
            text: ""
            size_hint: .3, 1
            md_bg_color: "#aaf0d1"
            on_release: app.pressed("1")
        MDRaisedButton:
            id: button2
            text: ""
            font_style: "H3"
            size_hint: .3, 1
            md_bg_color: "#aaf0d1"
            on_release: app.pressed("2")
        MDRaisedButton:
            id: button3
            text: ""
            font_style: "H3"
            size_hint: .3, 1
            md_bg_color: "#aaf0d1"
            on_release: app.pressed("3")

    MDBoxLayout:
        id: row2
        size_hint:.6,.2
        pos_hint: {'center_x':.5,'center_y':.4}
        MDRaisedButton:
            id: button4
            text: ""
            font_style: "H3"
            size_hint: .3, 1
            md_bg_color: "#aaf0d1"
            on_release: app.pressed("4")
        MDRaisedButton:
            id: button5
            text: ""
            font_style: "H3"
            size_hint: .3, 1
            md_bg_color: "#aaf0d1"
            on_release: app.pressed("5")
        MDRaisedButton:
            id: button6
            text: ""
            font_style: "H3"
            size_hint: .3, 1
            md_bg_color: "#aaf0d1"
            on_release: app.pressed("6")

    MDBoxLayout:
        id: row
        size_hint:.6,.2
        pos_hint: {'center_x':.5,'center_y':.2}
        MDRaisedButton:
            id: button7
            text: ""
            font_style: "H3"
            size_hint: .3, 1
            md_bg_color: "#aaf0d1"
            on_release: app.pressed("7")
        MDRaisedButton:
            id: button8
            text: ""
            font_style: "H3"
            size_hint: .3, 1
            md_bg_color: "#aaf0d1"
            on_release: app.pressed("8")
        MDRaisedButton:
            id: button9
            text: ""
            font_style: "H3"
            size_hint: .3, 1
            md_bg_color: "#aaf0d1"
            on_release: app.pressed("9")
```
## Evidence
![](Screen%20Shot%202023-03-18%20at%2013.34.10.png)

https://user-images.githubusercontent.com/111895127/226085578-3bdf201d-abf3-4491-b07a-d0a3eb58fc1a.mov



