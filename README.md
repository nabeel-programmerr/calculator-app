# calculator-app

import tkinter as tk
from tkinter import messagebox

# Function to handle button clicks
def on_click(event):
    text = event.widget.cget("text")
    if text == "=":
        try:
            result = eval(str(screen.get()))
            screen.set(result)
        except Exception as e:
            messagebox.showerror("Error", "Invalid Input")
            screen.set("")
    elif text == "C":
        screen.set("")
    else:
        screen.set(screen.get() + text)

# Create the main application window
app = tk.Tk()
app.title("Calculator")
app.geometry("300x400")
app.resizable(0, 0)

# Create a StringVar to hold the input
screen = tk.StringVar()

# Entry widget for the display
entry = tk.Entry(app, textvar=screen, font=("Arial", 20), bd=10, relief=tk.SUNKEN)
entry.pack(fill=tk.BOTH, ipadx=8, pady=10)

# Create the button layout
buttons = [
    ['7', '8', '9', '/'],
    ['4', '5', '6', '*'],
    ['1', '2', '3', '-'],
    ['C', '0', '=', '+']
]

# Add buttons to the application
for row in buttons:
    frame = tk.Frame(app)
    frame.pack(expand=True, fill=tk.BOTH)
    for btn_text in row:
        button = tk.Button(frame, text=btn_text, font=("Arial", 15), bd=5)
        button.pack(side=tk.LEFT, expand=True, fill=tk.BOTH)
        button.bind("<Button-1>", on_click)

# Run the application
app.mainloop()
