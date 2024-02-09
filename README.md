# BinaryConverter
A binary and denary conversion program using python. I defined many functions to streamline the process at the end of thep program.

# Here is the code snippet below:

```python
#      _       _        _       ____  _                           ____                          _            
#     | | __ _| | _____( )___  | __ )(_)_ __   __ _ _ __ _   _   / ___|___  _ ____   _____ _ __| |_ ___ _ __ 
#  _  | |/ _` | |/ / _ \// __| |  _ \| | '_ \ / _` | '__| | | | | |   / _ \| '_ \ \ / / _ \ '__| __/ _ \ '__|
# | |_| | (_| |   <  __/ \__ \ | |_) | | | | | (_| | |  | |_| | | |__| (_) | | | \ V /  __/ |  | ||  __/ |   
#  \___/ \__,_|_|\_\___| |___/ |____/|_|_| |_|\__,_|_|   \__, |  \____\___/|_| |_|\_/ \___|_|   \__\___|_|   
#                                                        |___/                                               
# A simple project that allows me to convert denary numbers to binary. I will do my best to explain the functions I am defining and calling throughout the code.

#Lets import any functions we need to run this code:
import time

#We will start by creating a function that will ask for the user's binary input and validate that they have entered a sufficient input.

#region############################################################## START OF BINARY INPUT HERE ############################################################################

#I am also going to define a function that verifies that the input is binary itself.
def is_binary(number):
    return all(bit == '0' or bit == '1' for bit in number) 
    #In this Boolean while loop, we are checking that the input is eight characters long and only contains 1s and 0s

#This is the main binary input function here:
def main_binary_input():
    while True: #Using the boolean values allow us to verify the integrity of the input.
        number_input = str(input("Please input an eight digit binary value. It can only consist of ones and zeroes.\n"))
        if all(char.isalpha() or char.isspace() for char in number_input):
            print("Letters are not valid!")
            time.sleep(1) #We are checking for any alpha numerical characters and spaces here.
            continue

        if len(number_input) != 8:
            print("Invalid length!")
            time.sleep(1) #We are verifying that the length of the binary number are exactly eight.
            continue

        if is_binary(number_input) == False:
            print("Only 1s and 0s are allowed!")
            time.sleep(1) #We are verifying that there are only 1s and 0s in this input.
            continue

        else: 
            time.sleep(1)
            print("Thank you.")
            return number_input #If it passes all the previous checks, then we use an else statement to pass it along and return it to the main_binary_input variable.

#endregion################################################################ END OF BINARY INPUT HERE #########################################################################
        

#region############################################################## START OF DENARY INPUT HERE ############################################################################

#Next thing we need is the Denary input and verification. I will verify that the number given to us is a number between 1 and 255.
        
def main_denary_input():
    while True: #Again using Boolean values to verify the integrity of the input.
        number_input = ""
        number_input = str(input("Please input a number between 1 and 255.\n"))
        if not number_input.isdigit():
            print("Letters and/or spaces are not valid!")
            time.sleep(1) #We are checking for letters and spaces here.
            continue

        if int(number_input) < 1 or int(number_input) > 255:
            print("This number is too high or too low!")
            time.sleep(1) #We are verifying that the number is within the acceptable range of 1-255.
            continue

        else:
            print("Thank you.")
            return int(number_input) #returns the data as an integer for the next process.
        
#endregion########################################################### END OF DENARY INPUT HERE ##############################################################################

#region#################################################### START OF BINARY TO DENARY CONVERSION HERE #######################################################################
        
#We are going to create the binary to denary conversion here.
        
def binary_to_denary(binary):
   denary = int(binary, 2)
   return denary

#binary = main_binary_input()
#denary = binary_to_denary(binary)
#print (denary)

#endregion################################################### END OF BINARY TO DENARY CONVERSION HERE #######################################################################

#region#################################################### START OF DENARY TO BINARY CONVERSION HERE #######################################################################
        
#We are going to create the binary to denary conversion here.
        
def denary_to_binary(denary):
   binary = bin(denary)[2:]
   return binary

#denary = main_denary_input()
#binary = denary_to_binary(denary)
#print (binary)

#endregion################################################### END OF DENARY TO BINARY CONVERSION HERE #######################################################################

#region###################################################### START OF USER SELECTION OF CHOICES HERE #######################################################################

#Now that we have defined all our necessary functions, 
#lets go ahead and welcome the user:

print("Jake's Binary Converter")
time.sleep(1)
print("Version 1.0")
time.sleep(1)

# This is a match function I am borrowing from one of my other projects in the past. It will ask the user what they want to do before anything else happens.

def choiceMatch():
    while True:
        choice = str(input("Would you like to convert your [B]inary number, [D]enary number, or [Q]uit the program? \n"))
        match choice:
            case "Q":
                print("You chose to Quit the program.")
                time.sleep(1)
                print("Goodbye!")
                break
            case "B":
                time.sleep(1)
                print("You chose to convert your Binary number to Denary.")
                binary = main_binary_input()
                denary = binary_to_denary(binary)
                time.sleep(1)
                print (f"Your denary number is: {denary}")
            case "D":
                time.sleep(1)
                print("You chose to convert your Denary number to Binary.")
                denary = main_denary_input()
                binary = denary_to_binary(denary)
                time.sleep(1)
                print (f"Your decrypted message is: {binary}")
            case _:
                print("Invalid Selection! Please select [B,D,E].")

choiceMatch()
#endregion

#endregion################################################### END OF USER SELECTION OF CHOICES HERE #########################################################################
```
