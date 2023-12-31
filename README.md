# Password-Generator
from tkinter import * 
import string
import random


def generator():
    small_alphabets = string.ascii_lowercase
    capital_alphabets = string.ascii_uppercase
    numbers = string.digits
    specia_characters = string.punctuation

    
    all_ = small_alphabets+capital_alphabets+numbers+specia_characters
    password_length=int(length_Box.get())
    
    if choice.get()==1:
        password = ''.join(random.sample(small_alphabets,password_length))
    
    elif choice.get()==2:
        password = ''.join(random.sample(small_alphabets + capital_alphabets, password_length))
        
    elif choice.get()==3:
        password = ''.join(random.sample(all_,password_length))
        
        
    passwordField.delete(0,END)
    passwordField.insert(0,password)
    


def reset():
    length_Box.delete(0,END)
    passwordField.delete(0,END)
    
root = Tk()
root.config(bg='white')
choice = IntVar()
Font = ('Calisto MT',15,'bold')


passwordLabel = Label(root,text='Auto Password Generator', font=('times new roman',30,'bold'),bg='black',fg='white')
passwordLabel.grid(pady=10)

weakradioButton = Radiobutton(root,text='Weak',value=1,variable= choice,font=Font)
weakradioButton.grid(pady=10)

mediumradioButton = Radiobutton(root,text='Medium',value=2,variable= choice,font=Font)
mediumradioButton.grid(pady=8)

StrongradioButton = Radiobutton(root,text='Strong',value=3,variable= choice,font=Font)
StrongradioButton.grid(pady=8)

lengthLabel = Label(root,text='Select Password Length', font=Font,bg='white',fg='black')
lengthLabel.grid(pady=7)

length_Box = Spinbox(root,from_=6,to=17,width=6,font=Font)
length_Box.grid(pady=8)

generateButton = Button(root,text=' Generate Password ',command=generator)
generateButton.grid()

passwordField = Entry(root,width=25,bd=3,font=Font)
passwordField.grid(pady=8)

resetButton = Button(root,text='Reset',command=reset)
resetButton.grid(pady=8)

root.mainloop()
