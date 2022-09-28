#PROGRAM FOR AIRLINE FOOD MANAGEMENT SYSTEM

import pickle

#Creating the data       
def create_air():
    file=open("test11.dat","wb")
    airline=[]
    mainlist=[]
    ans="y"
    while ans=="y":
        pno=int(input("Enter the passenger' number"))
        name=input("Enter the passenger' name")
        food=input("Enter your choice of food available in the menu")
        airline=[pno, name,food]
        mainlist.append(airline)
        ans=input("Do you wish to proceed? \n Enter y/n:")
    pickle.dump(mainlist,file)
    file.close()
    return
#create_air()

#Searching for data
def search_air():
    file=open("test11.dat","rb")
    found=False
    mainlist=[]
    while True:
        try:
             mainlist=pickle.load(file)
        except EOFError:
            break
    schk=int(input("Enter the passenger number to be searched"))
    for i in (mainlist):
                if i[0]==schk:
                    print("The passenger data exists:", i)
                    found=True
    if found==False:
        print("Passenger record not found.")
    file.close()
    return
#search_air()

#Updating data
def update_air():
    file=open("test11.dat","rb")
    found=False
    mainlist=[]
    while True:
        try:
            mainlist=pickle.load(file)
        except EOFError:
            break
    file.close()
    uchk=int(input("Enter the passenger number whose menu has to be updated:"))
    upfood=input("Enter the food item you wish to change:")
    for i in (mainlist):
        if i[0]==uchk:
            print("Old record is:",i)
            i[2]=upfood
            print("Updated record is:", i)
            found=True
    if found==True:
        file=open("test11.dat","wb")
        pickle.dump(mainlist,file)
        print("Record successfully updated!")
        file.close()
    else:
        print("Update failed, record not found! Try again....")
    return
#update_air()

#Deleting data
def delete_air():
    mainlist=[]
    found=False
    file=open("test11.dat","rb")
    while True:
        try:
            mainlist=pickle.load(file)
        except EOFError:
            break
    file.close()
    dchk=int(input("Enter the passenger number which has to be deleted"))
    for i in mainlist:
        if i[0]==dchk:
            mainlist.remove(i)
            found=True
            print(mainlist)
            print("Record successfully deleted!")
    if found==True:
        file=open("test11.dat","wb")
        pickle.dump(mainlist,file)
        file.close()
    else:
        print("Could not delete! Please try again.")
    return
#delete_air()

#MENU DRIVEN PART

choice=None
print("WELCOME TO SHELDON AIRLINES")
print("1. Enter passenger details")
print("2. Search for a passenger' details")
print("3. Update the food selection of a passenger")
print("4. Delete a passenger' ticket")
print("5. Exit menu")

while choice!=0:
    choice=int(input("Enter your choice"))
    if choice==1:
        create_air()
    elif choice==2:
        search_air()
    elif choice==3:
        update_air()
    elif choice==4:
        delete_air()
    elif choice==5:
        print("Thankyou! Please visit again!")
        break
    else:
        print("Invalid entry! Try again.")
    


            
    



















    

         


    
