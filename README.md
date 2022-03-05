# Stonehill-hackathon
Project by IB1 CIS

from tkinter import *
from tkinter.font import Font
from PIL import ImageTk, Image
import os


root = Tk()
font1= Font(family="Times New Roman", size=17)
label = Label(root, background='#F5F5DC', text=" \n Thousands of products are bought, used, and discarded in such a short duration, or collect dust in the corners of the owners’ homes\n Many of these items, if given to people who need them the most, can be put to good use and fulfill the recipients’ desires. \n Reusing is better than recycling because it saves the energy that comes with having to dismantle and re-manufacture products. \n It also significantly reduces waste and pollution because it reduces the need for raw materials, saving both forests and water supplies. \n Making the best use of products no longer needed in a household, utilizing their value for helping satisfy the needs or desires of the impoverished, is our aim. \n We envision a brighter future for the needy by tapping into the society around us. \n ", font=font1).pack()

root.config(background='#F5F5DC')

    
root.geometry( "4000x4000" )
root.title('Re-Envision')

def show():
    label.config( text = clicked.get() )
  

options = [
    "Laptop",
    "Book",
    "Tablet",
    "Utensils",
    "Clothes",
    "T.V",
    "Toys",
]
  

clicked = StringVar()
clicked2 = StringVar()

clicked.set( "Look here for examples")


font2 = Font(size=19, weight="bold")
name = Label(root, font = font2, text="Enter item to be donated (in lowercase) \n", background='#F5F5DC')
name.pack()




drop = OptionMenu( root , clicked , *options )
drop.pack()


label = Label( root , text = " " )



def execute1():
    dona1 = don1_field.get()
    Label(text=f'{dona1}! Thank you for your donation!', pady=20, bg='#ffbf00').pack()
    spec = Label(root, text="\n Enter specifications \n(NGOS will be listed below, please contact them with the necessary details before donation!)", bg='#F5F5DC', font = font2)
    spec.pack()
    spec_field = Entry(root)
    spec_field.pack(pady=30)
    dona2 = spec_field.get()
    drop2 = OptionMenu( root , clicked2 , *specs, )
    drop2.pack()
    if dona1 ==("laptop") or dona1 ==("laptops"):
        clicked2.set("Laptop - RAM space, Processor, Hard Drive, etc.")
    elif dona1 ==("book") or dona1 ==("books"):
        clicked2.set("Book -  Non Fiction/Fiction, Age range, Genre")
    elif dona1 ==("tablet") or dona1==("tablets"):
        clicked2.set("Tablet - Brand, Storage in GB etc.")
    elif dona1 ==("utensil") or dona1==("utensils"):
        clicked2.set("Utensils -  Specify")
    elif dona1 ==("cloth") or dona1==("clothes"):
        clicked2.set("Clothes -  Gender, Age Range, Type")
    elif dona1 ==("tv") or dona1==("television"):
        clicked2.set("T.V - Inches, Brand")
    elif dona1 ==("toy") or dona1==("toys"):
        clicked2.set("Toys -  Age Range, Description, etc.")
    font4 = Font(size=14, slant="italic")
    Button(font = font3,
    text="Submit",
    padx=10, 
    pady=5,
    command=execute2
    ).pack()
    

def execute2():
    global img
    path = "/Users/srivishnu/Desktop/HACK2/IMG.gif"
    canvas = Canvas(root, width = 1500, height = 200)      
    canvas.pack()
    try:
        img = ImageTk.PhotoImage(Image.open(path))
        canvas.create_image(0.5, 0.5, anchor = NW, image=img)
    except IOError:
            pass

    
    
specs = [
"Laptop - RAM space, Processor, Hard Drive, etc.",
"Book -  Non Fiction/Fiction, Age range, Genre",
"Tablet - Brand, Storage in GB etc.",
"Utensils -  Specify",
"Clothes -  Gender, Age Range, Type",
"T.V - Inches, Brand",
"Toys -  Age Range, Description, etc.",]

don1_field = Entry(root)
don1_field.pack(pady=30)

font3 = Font(size=14, slant="italic")
Button(font = font3,
    text="Submit",
    padx=10, 
    pady=5,
    command=execute1
    ).pack()



root.mainloop()
