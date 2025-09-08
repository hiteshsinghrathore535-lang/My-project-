# My-project-
It is basically my first project 
from tkinter import *

expr = ""  # Global expression string

def press(key):
    global expr
    expr += str(key)
    display.set(expr)

def equal():
    global expr
    try:
        result = str(eval(expr))
        display.set(result)
        expr = ""
    except:
        display.set("error")
        expr = ""

def clear():
    global expr
    expr = ""
    display.set("")

root = Tk()
root.configure(bg="light green")
root.title("Simple Calculator")
root.geometry("270x150")

display = StringVar()
entry = Entry(root, textvariable=display)
entry.grid(columnspan=4, ipadx=70)

# Number buttons
buttons = [
    ('1', 2, 0), ('2', 2, 1), ('3', 2, 2),
    ('4', 3, 0), ('5', 3, 1), ('6', 3, 2),
    ('7', 4, 0), ('8', 4, 1), ('9', 4, 2),
    ('0', 5, 0)
]
for (text, row, col) in buttons:
    Button(root, text=text, fg='black', bg='red',
           command=lambda t=text: press(t), height=1, width=7).grid(row=row, column=col)

# Operator buttons
operators = [('+', 2, 3), ('-', 3, 3), ('*', 4, 3), ('/', 5, 3)]
for (text, row, col) in operators:
    Button(root, text=text, fg='black', bg='red',
           command=lambda t=text: press(t), height=1, width=7).grid(row=row, column=col)

# Other buttons
Button(root, text='=', fg='black', bg='red',
       command=equal, height=1, width=7).grid(row=5, column=2)
Button(root, text='Clear', fg='black', bg='red',
       command=clear, height=1, width=7).grid(row=5, column=1)
Button(root, text='.', fg='black', bg='red',
       command=lambda: press('.'), height=1, width=7).grid(row=6, column=0)

root.mainloop()
