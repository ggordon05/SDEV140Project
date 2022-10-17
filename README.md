# SDEV140Project
Final Project and updates 
"""
Program: GordonGerald_FinalProject.py
Author: Gerald Gordon
Last date modified: 10/7/22

The purpose of this program is to create a GUI that shows a window with items for sale and quantities desired.
This info is taken in order to give a final price. After the final price is accepted user information is gathered and
the program is closed.

"""

from tkinter import *
from tkinter import messagebox


root = Tk()
root.title("HD Pottery")
root.iconbitmap("C:/Users/G/Documents/Intro Software Developement/Final project/favicon.ico")
# Adds Icon to left of title root window
root.geometry("800x500")

bowlPrice = 12  # Is the constant price of a bowl
platePrice = 11  # Is the constant price of a plate
mugPrice = 18  # Is the constant price of a mug
jewlPrice = 20  # Is the constant price of a Jewelry Holder
full_price = 0  # Starting point for the users price of all their items added together

def totalPrice():
    """Multiplies the amount of each item by the item price and adds all of the total prices together."""
    full_price = ((int(amountBowl.get())*bowlPrice) + (int(amountPlate.get())*platePrice) + (int(amountMug.get())*mugPrice) + (int(amountJewl.get())*jewlPrice))
    return full_price

def showTotal():
    """Makes sure that all inputs are integers and if not adds a label to the window. If all are correct a pop up with the total price comes up."""
    try:
        (int(amountBowl.get()),int(amountPlate.get()),int(amountMug.get()),int(amountJewl.get()))
    except ValueError:
        answer.config(text="Please enter a positve number from 0-100 for each option")
    messagebox.showinfo("Message", "Total Price: $" + str(totalPrice()))

def open2():
    """Opens a second window with all of it's labels and entry boxes."""
    global my_img
    top = Toplevel()
    label7 = Label(top, text="Customer Information:").pack()
    label8 = Label(top, text="Full Name:").pack()
    fullName = Entry(top).pack()
    label9 = Label(top, text="Address:").pack()
    address = Entry(top).pack()
    label10 = Label(top, text="Credit Card Number:").pack()
    creditCard = Entry(top).pack()
    btn = Button(top, text="Confirm and Close Window", command=top.destroy).pack()

# Creates background image for main window
bg = PhotoImage(file="logocup.png")
labelPic1 = Label(root, image=bg)
labelPic1.place(x=0,y=0,relwidth=1,relheight=1)
# Creating each label for main window
myLabel1 = Label(root, text="HD Pottery")
myLabel2 = Label(root, text="Available Items")
myLabel3 = Label(root, text="Enter desired amount")
myLabel4 = Label(root, text="Enter desired amount")
myLabel5 = Label(root, text="Enter desired amount")
myLabel6 = Label(root, text="Enter desired amount")
myLabelB = Label(root, text="Bowl")
myLabelP = Label(root, text="Plate")
myLabelM = Label(root, text="Mug")
myLabelJ = Label(root, text="Jewelry Holder")
answer = Label(root, text="")
# Makes sure entry is an integer
amountBowl = IntVar()
amountPlate = IntVar()
amountMug = IntVar()
amountJewl = IntVar()
# Creates entry widgets and what is autofilled in the widget for main window
amountBowl = Entry(root)
amountBowl.insert(0, "Must enter 0 if none")
amountPlate = Entry(root)
amountPlate.insert(0, "Must enter 0 if none")
amountMug = Entry(root)
amountMug.insert(0, "Must enter 0 if none")
amountJewl = Entry(root)
amountJewl.insert(0, "Must enter 0 if none")
# Creation of all buttons in main window
myButton = Button(root, text="Confirm selections", command=showTotal)
winButton = Button(root, text="Click to enter your Information", command=open2)
btn2 = btn = Button(root, text="Exit", command=root.destroy)
# Brings all widgets to the main window in the corresponding order
myLabel1.pack()
myLabel2.pack()
myLabelB.pack()
myLabel3.pack()
amountBowl.pack()
myLabelP.pack()
myLabel4.pack()
amountPlate.pack()
myLabelM.pack()
myLabel5.pack()
amountMug.pack()
myLabelJ.pack()
myLabel6.pack()
amountJewl.pack()
answer.pack()
myButton.pack()
winButton.pack()
btn2.pack()

root.mainloop()
