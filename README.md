# termimport tkinter as tk
from tkinter import ttk
import math
import numpy as np

class EngineerCalculator:
    def __init__(self, root):
        self.root = root
        self.root.title("Engineer Calculator")
        self.root.geometry("400x600")
        self.root.configure(bg='#f0f0f0')
        
        # Entry field for display
        self.display = tk.Entry(root, width=30, font=('Arial', 20), justify='right', bg='#ffffff')
        self.display.grid(row=0, column=0, columnspan=4, padx=5, pady=5, sticky='nsew')
        
        # Scientific functions frame
        self.sci_frame = ttk.LabelFrame(root, text="Scientific Functions")
        self.sci_frame.grid(row=1, column=0, columnspan=4, padx=5, pady=5, sticky='nsew')
        
        # Scientific buttons
        self.create_scientific_buttons()
        
        # Basic operations frame
        self.basic_frame = ttk.LabelFrame(root, text="Basic Operations")
        self.basic_frame.grid(row=2, column=0, columnspan=4, padx=5, pady=5, sticky='nsew')
        
        # Basic operation buttons
        self.create_basic_buttons()
        
        # Configure grid weights
        for i in range(4):
            root.grid_columnconfigure(i, weight=1)
        for i in range(3):
            root.grid_rowconfigure(i, weight=1)
            
    def create_scientific_buttons(self):
        scientific_buttons = [
            ('sin', 'cos', 'tan', 'π'),
            ('log', 'ln', '√', 'x²'),
            ('(', ')', 'e', 'C'),
            ('7', '8', '9', '/'),
            ('4', '5', '6', '*'),
            ('1', '2', '3', '-'),
            ('0', '.', '=', '+')
        ]
        
        for i, row in enumerate(scientific_buttons):
            for j, text in enumerate(row):
                btn = tk.Button(self.sci_frame, text=text, width=5, height=2,
                              command=lambda t=text: self.button_click(t))
                btn.grid(row=i, column=j, padx=2, pady=2, sticky='nsew')
                
    def create_basic_buttons(self):
        basic_buttons = [
            ('7', '8', '9', '/'),
            ('4', '5', '6', '*'),
            ('1', '2', '3', '-'),
            ('0', '.', '=', '+')
        ]
        
        for i, row in enumerate(basic_buttons):
            for j, text in enumerate(row):
                btn = tk.Button(self.basic_frame, text=text, width=5, height=2,
                              command=lambda t=text: self.button_click(t))
                btn.grid(row=i, column=j, padx=2, pady=2, sticky='nsew')
                
    def button_click(self, value):
        current = self.display.get()
        
        if value == 'C':
            self.display.delete(0, tk.END)
        elif value == '=':
            try:
                result = eval(current)
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, str(result))
            except:
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, "Error")
        elif value == 'sin':
            try:
                result = math.sin(math.radians(float(current)))
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, str(result))
            except:
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, "Error")
        elif value == 'cos':
            try:
                result = math.cos(math.radians(float(current)))
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, str(result))
            except:
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, "Error")
        elif value == 'tan':
            try:
                result = math.tan(math.radians(float(current)))
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, str(result))
            except:
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, "Error")
        elif value == 'π':
            self.display.insert(tk.END, str(math.pi))
        elif value == 'log':
            try:
                result = math.log10(float(current))
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, str(result))
            except:
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, "Error")
        elif value == 'ln':
            try:
                result = math.log(float(current))
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, str(result))
            except:
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, "Error")
        elif value == '√':
            try:
                result = math.sqrt(float(current))
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, str(result))
            except:
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, "Error")
        elif value == 'x²':
            try:
                result = float(current) ** 2
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, str(result))
            except:
                self.display.delete(0, tk.END)
                self.display.insert(tk.END, "Error")
        elif value == 'e':
            self.display.insert(tk.END, str(math.e))
        else:
            self.display.insert(tk.END, value)

if __name__ == "__main__":
    root = tk.Tk()
    app = EngineerCalculator(root)
    root.mainloop()

