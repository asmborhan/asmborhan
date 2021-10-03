import pyttsx3
import speech_recognition as sr
import datetime
import wikipedia
import webbrowser
import os
from playsound import playsound
import subprocess
import pywhatkit
from bs4 import BeautifulSoup
import requests
from wikipedia.wikipedia import search
import random
# import wolframalpha



# app = wolframalpha.Client = wolframalpha.Client("EL2RQ8-2PHA3GUH96")

engine = pyttsx3.init('sapi5')
voices = engine.getProperty('voices')
# print(voices)
engine.setProperty('voice', voices[1].id)
engine.setProperty('rate',180)


def speak(audio):
    pass
    engine.say(audio)
    engine.runAndWait()

def wishMe():
  hour = int(datetime.datetime.now().hour)
  if hour>=0 and hour<12:
        a = "Good morning", "Good morning sir", "Hello Good Morning", "O, Good morning ", "O, good morning", "Wow! Welcome back"
        speak(random.choice(a))
    
  elif hour>=12 and hour<18:
        speak("good afternoon")

        speak("how may i help you")


  else:
        speak("good evening")

        speak("how may i help you")


def takeCommand():

    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening...")
        r.pause_threshold = 2
        r.energy_threshold =4000
        audio=r.listen(source)
    try:
        print("Recognizing...")

        query = r.recognize_google(audio, language='en')
        print(f"user said: {query}\n")

    except Exception as e:
        # print(e)
        print("cudent get it")
        return "none"
    return query


if __name__=="__main__":
    wishMe()
    while True:
     query = takeCommand().lower()




     if 'wikipedia' in query:
         speak('serching wiki...please wait')
         query = query.replace("wikipedia", "")
         results = wikipedia.summary(query, sentences=2)
         speak("Accoding to wikipedia")
         print(results)
         speak(results)


     if 'stop' in query or 'over' in query or 'quit' in query or 'see you' in query or 'go' in query:
            f = "bye", "ok bye", "see you again ", "bye bye", "As your wish", "see ya", "As your wish"
            speak(random.choice(f))

     elif 'open youtube' in query:
         subprocess.call("youtube.com")

     elif 'open insta' in query:
           webbrowser.open("instagram.com")

     elif 'open google' in query:
          webbrowser.open("google.com")

     elif 'play music' in query:
         playsound('death bed.mp3')


     elif 'the time' in query:
         time = datetime.datetime.now().strftime('%I:%M %P')
         speak('currant time is' + time)


     elif 'open discord' in query:
         subprocess.call("C:\\Users\\RAYHAN_MAHI\\AppData\\Local\Discord\\Update.exe --processStart Discord.exe")
     
     elif 'open chrome' in query:
         subprocess.call("C:\Program Files\Google\Chrome\Application\chrome.exe")

     elif 'open onix' in query:
         subprocess.call("C:\\Users\\RAYHAN_MAHI\\Desktop\\Onix_Launcher.exe")

     elif 'on youtube' in query:
         pywhatkit.playonyt(query)

     elif 'name' in query:
         speak('my owner did not give me a name')

     elif 'joke' in query:
         speak('two plus two is twintytwo')

    #  elif "temperature" in query:
    #      webbrowser.open("https://weather.com/weather/today")


     elif "open microsoft teams" in query:
         subprocess.call("C:\\Users\\RAYHAN_MAHI\\AppData\\Local\\Microsoft\\Teams\\Update.exe --processStart Teams.exe")

     elif "open opera" in query:
         subprocess.call("C:\\Users\\RAYHAN_MAHI\\AppData\\Local\\Programs\\Opera GX\\launcher.exe")


     elif "close opera" in query:
         os.system("taskkill/im opera.exe")

     elif 'how are you' in query:
        speak('i am fine what about you')

     elif 'fine' in query:
         speak('gread to listen')
     
    
     

     elif 'open roblox' in query:
          webbrowser.open("roblox.com/home")


     elif 'on google' in query:
         speak("this is what i found on the web")
         pywhatkit.search(query)
         result = googleScrap.summary(query,3)
         speak (result)



     elif 'open chess' in query:
          webbrowser.open("chess.com")



     elif 'temperature'in query:
         search = "temperature in my location"
         url = f"https://www.google.com/search?client=opera-gx&q={search}"
         r = requests.get(url)
         data = BeautifulSoup(r.text,"html.parser")
         temp = data.find("div", class_="BNeawe").text
         speak(f"current {search} is {temp}")
         print(requests)


     elif 'shutdown' in query or 'shut down' in query:
         speak("Do you really want to shutdown the system sir?")
         ch = takeCommand()
         if "yes" in ch:
                
          os.system("shutdown /s /t 1")
         else:
          speak("as you wish")

     elif 'bye' in query:
         speak("call me when you want call me when you need")


     
         




