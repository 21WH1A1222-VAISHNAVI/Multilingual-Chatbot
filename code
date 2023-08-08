import tkinter as tk
from googletrans import Translator
import wikipedia

translator = Translator()

# Set up the GUI
root = tk.Tk()
root.title("Multilingual Chatbot")

# Create widgets
language_label = tk.Label(root, text="Select language to translate to:")
language_var = tk.StringVar()
language_var.set("en")  # default language is English
language_menu = tk.OptionMenu(root, language_var, "en", "fr", "es", "de", "ja", "ko", "zh-cn","te","hi")
output_label = tk.Label(root, text="Responses")
output_box = tk.Text(root, height=30, width=90,bg='light blue')
input_box = tk.Entry(root, width=50)
input_label = tk.Label(root, text="")


def get_input_and_translate():
    input_text = input_box.get()
    dest_language = language_var.get()
    
    # Use Wikipedia to get the answer to the question
    try:
        if input_text in ['hi', 'hello']:
            answer = "Hi there! How can I assist you today?"
        elif input_text in ['how are you', 'how are you doing']: 
            answer = "I'm doing well, thank you. How about you?"
        elif input_text in ['what is your name', 'who are you']:
            answer = "My name is ChatBot. How can I help you today?"
        elif input_text in ['thank you', 'thanks']:
            answer = "You're welcome. Is there anything else I can help you with?"
        else :
            answer = wikipedia.summary(input_text)
    except:
        answer = "Sorry, I couldn't find an answer to that question."
    
    # Translate the answer to the desired language
    if dest_language != "en":
        answer = translator.translate(answer, dest=dest_language).text
    
    # Display the answer in the output box
    output_box.configure(state='normal')
    output_box.insert(tk.END, "You: " + input_text + "\n")
    output_box.insert(tk.END, "Bot: " + answer + "\n")
    output_box.configure(state='disabled')
    
    # Clear the input box
    input_box.delete(0, tk.END)
    
# Add widgets to the GUI
output_label.pack()
output_box.pack()
language_label.pack()
language_menu.pack()
input_label.pack(side=tk.BOTTOM)
input_box.pack(side=tk.BOTTOM)

# Add a button to get the input and translate
translate_button = tk.Button(root, text="Send", command=get_input_and_translate)
translate_button.pack(side=tk.BOTTOM)

# Run the GUI
root.mainloop()
