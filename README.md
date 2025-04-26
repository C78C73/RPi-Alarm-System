# RPi-Alarm-System
### This is a project to build a alarm system using rasperry pi's, sensors, and Python

```
# Email sending when motion is detected by a sensor
import smtplib
from email.mime.text import MIMEText

sender_email = "**INSERT EMAIL HERE**"
app_password = "**INSERT GOOGLE APP PASSWORD**"

email_recipient = "**INSERT EMAIL OF WHO YOU WANT TO SEND TO HERE**"

msg = MIMEText("** Motion at door **")
msg['From'] = sender_email
msg['To'] = email_recipient
msg['Subject'] = "🚨 Pi ALERT🚨"

try:
    server = smtplib.SMTP_SSL('smtp.gmail.com', 465)
    server.login(sender_email, app_password)
    server.sendmail(sender_email, [email_recipient], msg.as_string())
    server.quit()
    print("Message sent to email.")
except Exception as error:
    print("Failed to send message:", error)
```