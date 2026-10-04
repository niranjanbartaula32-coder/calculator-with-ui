import tkinter,math
from math import sqrt
from tkinter import Button,StringVar,Entry
root =tkinter.Tk()
root.title("CALCULATOR")
root.geometry("400x400")
root.resizable(False,False)
root.configure(bg="gray")

#the function run everytime when user perform action

def press(value):

        #for performing the action of user when clicked AC
        if value == "AC":
             entryspace.delete(0, tkinter.END )
#perform the real calculation logic
        elif value == "=":
               #it means trying out this if it fail there is expectation
               try: 
                  
                  expression = entryspace.get()
                  expression = expression.replace("x","*")
                  expression = expression.replace("^","**")

          #run actual calculation
#the thing that we expect if any error occur
                  result = eval(expression)

                  entryspace.delete(0,tkinter.END)
                  entryspace.insert(tkinter.END,str(result))

               except Exception:
                 entryspace.insert(tkinter.END,"Error")
                 entryspace.delete(0,tkinter.END)
    
             
                    
                  


        else: 
             entryspace.insert(tkinter.END,value)
              

right_side=  ["AC","=",".","%","^"]
left_side=  ["1","2","3","4","5","6","7","8","9","0","+","-","*","/"]
all_buttons= right_side+left_side

#entry space
entryspace= tkinter.Entry(root,width=10,font=("Arial",30))
entryspace.grid(row=0,column=0,columnspan=4,padx=10,pady=10,sticky="nsew")



row_num = 1
column_num = 0
for label in all_buttons:
    column_num = column_num+1
    if column_num > 3:
        column_num= 0
        row_num=row_num+1
    button = tkinter.Button(root, text=label, width=10, command=lambda value=label: press(value))
    button.configure(bg="#FF00FF",fg="#000080")

    button.grid(row = row_num,column = column_num,padx = 1,pady =2) 



root.mainloop()
