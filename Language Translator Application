import googletrans
from googletrans import Translator
import tkinter as tk
from tkinter import ttk, messagebox
class LanguageTranslatorApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Language Translator")
        self.root.geometry("600x400")

        self.translator = Translator()

        # Title label
        self.title_label = ttk.Label(self.root, text="Language Translator", font=("Helvetica", 18))
        self.title_label.pack(pady=20)

        # Source language
        self.source_lang_label = ttk.Label(self.root, text="Source Language:")
        self.source_lang_label.pack()
        self.source_lang = ttk.Combobox(self.root, values=list(googletrans.LANGUAGES.values()))
        self.source_lang.pack(pady=5)

        # Target language
        self.target_lang_label = ttk.Label(self.root, text="Target Language:")
        self.target_lang_label.pack()
        self.target_lang = ttk.Combobox(self.root, values=list(googletrans.LANGUAGES.values()))
        self.target_lang.pack(pady=5)

        # Text to translate
        self.text_label = ttk.Label(self.root, text="Enter Text:")
        self.text_label.pack()
        self.text_entry = tk.Text(self.root, height=10, width=50)
        self.text_entry.pack(pady=10)

        # Translate Button
        self.translate_button = ttk.Button(self.root, text="Translate", command=self.translate_text)
        self.translate_button.pack(pady=10)

        # Translated Text
        self.translated_text_label = ttk.Label(self.root, text="Translated Text:")
        self.translated_text_label.pack()
        self.translated_text = tk.Text(self.root, height=10, width=50)
        self.translated_text.pack(pady=10)

    def translate_text(self):
        try:
            source_lang = self.source_lang.get()
            target_lang = self.target_lang.get()
            text = self.text_entry.get("1.0", tk.END)

            if source_lang and target_lang and text.strip():
                source_lang_code = list(googletrans.LANGUAGES.keys())[list(googletrans.LANGUAGES.values()).index(source_lang)]
                target_lang_code = list(googletrans.LANGUAGES.keys())[list(googletrans.LANGUAGES.values()).index(target_lang)]

                translated = self.translator.translate(text, src=source_lang_code, dest=target_lang_code)
                self.translated_text.delete("1.0", tk.END)
                self.translated_text.insert(tk.END, translated.text)
            else:
                messagebox.showerror("Input Error", "Please fill in all fields.")
        except Exception as e:
            messagebox.showerror("Translation Error", str(e))

if __name__ == "__main__":
    root = tk.Tk()
    app = LanguageTranslatorApp(root)
    root.mainloop()

