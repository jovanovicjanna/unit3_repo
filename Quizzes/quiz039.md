# Quiz 039

## python file
```.py
from kivymd.app import MDApp


class quiz039(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.counter = 0

    def build(self):
        return

    def click(self):
        self.counter += 1
        self.root.ids.counter_label.text = str(self.counter)


quiz039().run()
```

## kivy file

```.kv
MDScreen:
    size: 500,500

    MDBoxLayout:
        orientation: 'horizontal'
        pos_hint: {"center_x": .5, "center_y": .5}
        size_hint: .7,.3
        md_bg_color: 'red'

        MDLabel:
            id: counter_label
            text:"0"
            halign: "center"
            size_hint: .5,1
            font_size: '34pt'
            md_bg_color: '#219ebc'

        MDRaisedButton:
            id: counter_btn
            text: "Add +1"
            size_hint: .5,1
            font_size: '34pt'
            md_bg_color: '#023047'
            on_release:
                app.click()
```

## Evidence
![](Screen%20Shot%202023-02-06%20at%2017.38.48.png)


