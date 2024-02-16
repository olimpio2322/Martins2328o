import random
from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.button import Button
from kivy.uix.label import Label

class AcaiTreeApp(App):
    def build(self):
        self.acai_count = 0
        self.acai_varieties = ["Tradicional", "Com Granola", "Com Frutas"]
        
        layout = BoxLayout(orientation='vertical')
        
        self.label = Label(text="Bem-vindo à Açaizeira Famosa!")
        layout.add_widget(self.label)
        
        self.acai_label = Label(text="Quantidade de açaís: 0")
        layout.add_widget(self.acai_label)
        
        acai_button = Button(text="Preparar Açaí")
        acai_button.bind(on_press=self.prepare_acai)
        layout.add_widget(acai_button)
        
        return layout
    
    def prepare_acai(self, instance):
        self.acai_count += 1
        acai_type = random.choice(self.acai_varieties)
        self.label.text = f"Você pediu um açaí {acai_type}!"
        self.acai_label.text = f"Quantidade de açaís: {self.acai_count}"

if __name__ == "__main__":
    AcaiTreeApp().run()
