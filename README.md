# Voice_Assistant
A text to speech assitant made in python using pyttsx3 and datetime modules.
# Import required module files
import pyttsx3
import datetime

#Importing the voice function from 'pyttsx3' into a variable named 'engine'
engine=pyttsx3.init('sapi5')
voices=engine.getProperty('voices')
print(voices[1].id)
engine.setProperty('voice',voices[1].id)

#Define a function named 'speak' for converting the text into speech
def speak(audio):
    engine.say(audio)
    engine.runAndWait()

#Set a password for your assitant
speak("please enter the password")
password=input()

# Using If else statement Verify if the password is true or false

if password=="thursday":
    # If the password is true then ask the user his/her name
    speak("please tell me your name")
    name = input()
    if __name__ == "__main__":
        speak(" Welcome")
        speak(name)
        engine.runAndWait()
    speak("This is Thursday ")
    speak("What can I help you with")
#Using a while loop create a loop so that your assistant does not stop after completing the task
    while True:
# Ask the user what task he would like assistant to do for him/her
        speak("select task from below")
        print("1.tell me the time")
        print("2.tell me the date")
        print("3.open calculator")
        task=input()
        work=int(task)
        hour=int(datetime.datetime.now().hour)
        day =datetime.datetime.now().date()
        time_now = float(datetime.datetime.now().hour)
# Using If statement perform the desired task the user would like assistant to perform

#If the user selects the task to know the time , use datetime module to get the time and greet the user accordingly
        if work==1:
            speak("the time is")
            speak(time_now)
            if hour >= 5 and hour < 12:
                speak("Good Morning!")
            if hour >= 12 and hour < 18:
                speak("Good Afternoon")
            if hour >= 18 and hour < 20:
                speak("Good Evening!")
            if hour >= 20 and hour < 25:
                speak("Good Night!")

#If the user selects the task to know the date , by using datetime module tell the user todays'date
        if work==2:
            speak(day)

#If the user selects the task to use calculator, perform simple calculation using a basic calculator program to perform basic operations
        if work==3:

#Define 'add','subtract','multiply','division' to recall these function according to users choice of operation
            def add(x, y):
                return x + y
            def subtract(x, y):
                return x - y
            def multiply(x, y):
                return x * y
            def divide(x, y):
                return x / y

#Tell the user what are the operations he can perform on the calculator
            speak("Select operation")
            print("1.Add")
            print("2.Subtract")
            print("3.Multiply")
            print("4.Divide")

# Create a while loop so that the program does not get terminate after performing a single operation
            while True:
                choice = input("Enter choice(1/2/3/4): ")

# Perform the desired operation the user wants to perform using If,elif statement
                if choice in ('1', '2', '3', '4'):
                    speak("Enter Two Number")
                    num1 = float(input("Enter first number: "))
                    num2 = float(input("Enter second number: "))
                    if choice == '1':
                        speak("The addition of two number is")
                        adittion=add(num1,num2)
                        speak(adittion)
                    elif choice == '2':
                        speak("The subtraction of two number is")
                        subtractio= subtract(num1, num2)
                        speak(subtractio)
                    elif choice == '3':
                        speak("The multiplication of two number is")
                        multiplication = multiply(num1, num2)
                        speak(multiplication)
                    elif choice == '4':
                        speak("The division of two number is")
                        division = divide(num1, num2)
                        speak(division)

# Ask the user if wants to do any other calculation
                    speak("want to do another calculation")
                    next_calculation = input("Let's do next calculation? (yes/no): ")

# If the answer is no break the while loop
                    if next_calculation == "no":
                        break

                else:
                    speak("Invalid Input")

# Ask the user if he would like the assistant to do something else or not

        speak("want me to help with some thing else ")
        next_task= input("Let's do next task? (yes/no): ")

# If the answer for the next task question is 'no' terminate the assistant
        if next_task=="no":
            speak("Thanks for letting me help you!")
            speak("Have a nice day!")
            break


# If the password is wrong tell the user he has given 'wrong password'
else:
    speak("wrong password")
