# Alexa-AI-Desktop-Asistance
You can  Aotumate your desktop by using your Voice





    import pyttsx3
    import datetime
    import pyaudio
    import wikipedia
    import speech_recognition as sr
    import webbrowser
    import os
    import random
    import pywhatkit
    engine=pyttsx3.init('sapi5')

    voices=engine.getProperty('voices')
    #print(voices[1].id)
    engine.setProperty('voice',voices[1].id)
    

    def speak(audio):
        engine.say(audio)
        engine.runAndWait()
    
    def WishMe():
        hour=int(datetime.datetime.now().hour)
        if hour>=0 and hour<12:
            speak("Welcome in Desktop asistance created by Alos")
            speak("Good Morning Sir!")
        elif hour>=12 and hour<18:
            speak("Welcome in Desktop asistance created by Alos")
            speak("Good Afternoon Sir!")
        else:
            speak("Welcome in Desktop asistance created by Alos")
            speak("Good Evening sir !")
        speak("I am Alexa Sir . Please tell me Sir, How may i help You")
    def takeCommand():
        r=sr.Recognizer()
        with sr.Microphone() as source:
        
            print("Listenning........")
            r.pause_threshold=1
            audio=r.listen(source)
      try:
          print("Recognizer..........")
          query=r.recognize_google(audio,language='en-in')
          print(f"User said: {query}\n")
      except Exception as e:
          #print(e)
          print("Say that again please........")
          speak("what are you tell me i can't understand")
          return "None"
      return query
    if __name__ == "__main__":
        WishMe()
        while True:
            query=takeCommand().lower()
            if 'wikipedia' in query:
                speak("Searching Wikipedia.....")
                query=query.replace("Wikipedia","")
                results=wikipedia.summary(query,sentences=2)
                speak("According to Wikipedia")
                print(results)
                speak(results)  
            elif "open youtube" in query:
            
                webbrowser.open("youtube.com/watch?v=VuG7ge_8I2Y&list=RDMMVuG7ge_8I2Y&start_radio=1") 
    
            elif "open instagram" in query:
                webbrowser.open("instagram.com/?utm_source=pwa_homescreen")
            
            elif "open code" in query:
                openpath=("C:\\Users\\Hp\\AppData\\Roaming\\Microsoft\\Windows\\Start Menu\\Programs\\Visual Studio Code\\Visual Studio Code.lnk")
                os.startfile(openpath)
            elif "open facebook" in query:
                webbrowser.open("facebook.com")
            elif "play game" in query:
                webbrowser.open("chess.com")
            elif "play tandav" in query:
                webbrowser.open("https://wynk.in//music//song//shiv-tandav-stotram//ti_timesmusic7932")
            elif "play sad song" in query:
                webbrowser.open("https://wynk.in//music//song//tum-hi-aana-sad-version-from-marjaavaan//hu_50458101?q=sad+songs")
            elif "play music" in query:
                music_dir=("C:\\old songs")
                songs=os.listdir(music_dir)
                rnd=random.randint(1,100)
            
                os.startfile(os.path.join(music_dir, songs[rnd]))
            elif"open image" in query:
                image_dir=("C:\\oppo a16\\images")
                image=os.listdir(image_dir)
                rnd1=random.randint(1,950)
                os.startfile(os.path.join(image_dir, image[rnd1]))
        
            elif"send message" in query:
                hour=int(datetime.datetime.now().hour)
                min=int(datetime.datetime.now().minute)
                
                pywhatkit.sendwhatmsg("+919999999992", "ALOS", hour, min+1)
            elif"open excel" in query:
                excelpath=("C:\\Users\\Hp\\Msfile")
                Apps=os.listdir(excelpath)
                os.startfile(os.path.join(excelpath, Apps[0])) 
            elif"open word" in query:
                wordpath=("C:\\Users\\Hp\\Msfile")
                Apps=os.listdir(excelpath)
                os.startfile(os.path.join(excelpath, Apps[7])) 
            elif"open powerpoint" in query:
                powerpointpath=("C:\\Users\\Hp\\Msfile")
                Apps=os.listdir(excelpath)
                os.startfile(os.path.join(excelpath, Apps[5]))   
            elif"open notebook" in query:
                notebookpath=("C:\\ProgramData\\Microsoft\\Windows\\Start Menu\\Programs\\Anaconda3 (64-bit)\\Jupyter Notebook (Anaconda3).lnk")
                #Apps=os.listdir(excelpath)
                os.startfile(excelpath) 
            elif"open command" in query:
                commandpath=("C:\\Users\\Hp\\AppData\\Roaming\\Microsoft\\Windows\\Start Menu\\Programs\\Windows PowerShell\\Windows PowerShell.lnk")
                os.startfile(commandpath)      
        
            
        
    
