# HackTheKeyboard
<h3>A tiny keylogger coded with just 15 lines of Python script, which captures keystrokes and sends them to your web server of your choice.</h3>

<b>First Thing First</b>: This keylogger project is prepared for those who would like to understand the working and behaviour of keyloggers, reverse engineering the compiled version of the code to find kill-switches and build IOCs/Signatures, ethically test on systems for the purpose of Ethical Hacking/Penetration Testing such as testing the bypasses and detection by EDR, SIEM, HIPS etc.
The program should not be used for any illegal activities such as running the compiled version of this code in a user machine without his/her consent, distributing it by means of spamming/phishing campaigns etc.

<b>How stuff works?</b>

This KeyLogger uses two main packages (Keyboard and Requests)

a) Keyboard package contains pre-built classes and functions which acts as hook procedures to the system kernal using which it can intercept events, such as messages, mouse actions, and keystrokes. A package function known as read_key() runs in an infinite while loop capturing all keys into a string variable in an increamental manner upto 20 characters.

b) Once it captures all 20 keystrokes, it uses Requests package function requests.get("URL") to send the captured keystroke strings via HTTP packet using GET method directly into your chosen web server such as Apache. You can prepare your server in your Termux Environment running into Android Phone. The keystrokes are then stored in the webserver access log file as a normal HTTP GET request entries. The string variable is re-initialized and starts filling up again while in the loop.
 

<b>Setting up the Server</b>
Apache Webserver is highly recomended for its simplicity but you can use any webserver, given that it logs the incomming requests into a log file.

Here is an example of setting up environmrnt in Android Termux Environment

1) Install Apache -> `apt-get install apache2`

2) start Apache -> `apachectl start`
   Note: Ignore the warnings!!!

3) Install Open SSH -> `pkg install openssh` or `apt-get install openssh`

4) Open Reverse HTTP Tunnel to Serveo.net -> `ssh -R 80:localhost:8080 serveo.net`
   Note: 8080 is the deafault local port of apache, and port 80 will be the incomming port


<b> Editing and Compiling the Keylogger Python file</b>



 
