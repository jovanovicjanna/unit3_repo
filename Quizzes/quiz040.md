# Quiz 040

## python file
```.py
from kivymd.app import MDApp

class quiz040(MDApp):
    def build(self):
        return
    def dark_mode(self):
        print (self.root.ids.main_box.md_bg_color)
        if self.root.ids.main_box.md_bg_color == [1.0, 1.0, 1.0, 1.0]:
            self.root.ids.main_box.md_bg_color = "black"
            self.root.ids.name.color = 1, 1, 1, 1

        else:
            self.root.ids.main_box.md_bg_color = "white"
            self.root.ids.name.color = 0, 0, 0, 1

app = quiz040()
app.run()
```

## kivy file

```.kv
Screen:
    size:500, 500

#white
    MDBoxLayout:
        id: main_box
        orientation: "vertical"
        size_hint: 1, 1
        md_bg_color: "white"

        MDLabel:
            id: name
            text: "Jana"
            font_style: "H1"
            pos_hint: {"center_x": .5}
            halign: "center"
            color: "black"

        MDRaisedButton:
            id:darkmode
            text: "Dark mode"
            size_hint: .1, .05
            on_press: app.dark_mode()
```

## Evidence
