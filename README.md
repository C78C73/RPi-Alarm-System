# RPi-Alarm-System
## This is a project to build an alarm system using Raspberry Pi's, sensors, and Python.

```
# Email sending when motion is detected by a sensor
import smtplib
from email.mime.text import MIMEText
from time import sleep
from datetime import datetime
from gpiozero import MotionSensor

def SendEmailAlert():
    sender_email = ""
    app_password = ""

    email_recipient = ""

    msg = MIMEText("** Motion at door **")
    msg['From'] = sender_email
    msg['To'] = email_recipient
    msg['Subject'] = "🚨 Pi ALERT🚨"

    try:
        server = smtplib.SMTP_SSL('smtp.gmail.com', 465)
        server.login(sender_email, app_password)
        server.sendmail(sender_email, [email_recipient], msg.as_string())
        server.quit()
        print("\nMessage sent to email.\n")
    except Exception as error:
        print("\nFailed to send message:", error, "\n")

def MotionDetected():
    pir = MotionSensor(4) # fix this number when you build it
    
    while True:
        if (pir.motion_detected):
            print("Motion detected @ " + str(datetime.now()))
            sleep(1)
            #return True
        else:
            sleep(1)

def Main():
    if (MotionDetected):
        SendEmailAlert()

Main()
```
