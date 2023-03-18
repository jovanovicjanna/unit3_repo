# Quiz 042

![](Screen%20Shot%202023-03-18%20at%2013.27.57.png)

## Python code
```.py
from kivymd.app import MDApp
from kivymd.uix.screen import MDScreen

class MysteryPageA(MDScreen):
    pass

class MysteryPageB(MDScreen):
    pass

class quiz042(MDApp):
    def build(self):
        return
test = quiz042()
test.run()
```

## Kivy code
```.py
ScreenManager:
    MysteryPageA:
        name: "MysteryPageA"

    MysteryPageB:
        name: "MysteryPageB"

<MysteryPageA>
    size: 500,500
    md_bg_color: "#A6B1E1"

    MDLabel:
        text: "This is mystery page A you pressed the button"
        font_style: "H3"
        halign: "center"

    MDRaisedButton:
        text: "Next page"
        on_press: root.parent.current = "MysteryPageB"
        size_hint: .1, .1
        md_bg_color: "#000000"

<MysteryPageB>
    size: 500,500
    md_bg_color: "#D2F898"

    MDLabel:
        text: "This is mystery page B you pressed the button"
        font_style: "H3"
        halign: "center"

    MDRaisedButton:
        text: "Previous page"
        on_press: root.parent.current = "MysteryPageA"
        size_hint: .1, .1
        md_bg_color: "#000000"
```
