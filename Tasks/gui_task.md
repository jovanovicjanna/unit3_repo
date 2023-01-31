# TASK 1

## gui_task.py

```.py
from kivymd.app import MDApp


class gui_task(MDApp):
    def __init__(self,**kwargs):
        super().__init__(**kwargs)
        self.amount = 0

    def build(self):
        return

    def set_counter(self):
        user_start = int(self.root.ids.amount_rsd.text)
        self.amount= user_start


    def change(self,name:str):


        if 'dollar' in name:
            self.amount = self.amount * 0.0092
            self.root.ids.counter_label.text = f"{round(self.amount,2)} USD"
        else:
            self.amount *= 1.2
            self.root.ids.counter_label.text = f"{round(self.amount,2)} JPY"

convert_class = gui_task()
convert_class.run()
```

## gui_task.kv

```.kv
# Layout_demo_kv
Screen:
    size: 500,500


    MDBoxLayout:
        id: main_box
        orientation: "vertical"
        size_hint:1,.5
        pos_hint: {"center_x": .5, "center_y": .5}

        MDLabel:
            text: "Currency Converter <3"
            halign: "center"
            font_size: "30pt"
            pos_hint: {'center_x': .5}

        MDTextField:
            id: amount_rsd
            hint_text: "Enter an amount in RSD"
            validator: "phone"
            line_color_focus: "blue"
            text_color_normal: "blue"
            size_hint: .10,0.5
            pos_hint: {"center_x":.12,}
            on_text:
                app.set_counter()

        MDBoxLayout:
            id: box2
            orientation: "horizontal"


            MDLabel:
                id:counter_label
                font_style: "H3"
                halign: "center"
                text: "Click to convert ->"
                font_size: "15pt"


            MDBoxLayout:
                id: box3
                orientation: "vertical"

                MDRaisedButton:
                    id: dollar_button
                    text: "USD"
                    on_press: app.change("dollar")
                    size_hint:1,1.5
                    md_bg_color: "#80A4ED"

                MDRaisedButton:
                    id: yen_button
                    text: "JPY"
                    on_press: app.change("yen")
                    size_hint:1,1.5
                    md_bg_color: "#BFCDE0"
```

## Evidence

![](Screen%20Shot%202023-01-31%20at%2017.34.24.png)

