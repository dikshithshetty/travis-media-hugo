---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2018-06-26T10:36:15Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/bitcoin-price-alert-app-python-featured.jpg"
slug:  "create-bitcoin-price-alert-app-in-python-tutorial"
tags:  ["Coding Tutorials"]
title:  "Let's Create a Bitcoin Price Alert App in Python: Tutorial"

---


<p class="textcenter"><img dara-rjs="2" src="/images/2019/12/bitcoin-price-alert-app-python-featured.jpg" /></p>
<p>Need an alert when Bitcoin prices drop so you can buy? Here&#8217;s a simple Python app I created that sends you a Bitcoin price alert email when it drops below a specified amount.</p>
<p>Two days ago, for about 12 hours, Bitcoin <a href="https://cointelegraph.com/news/crypto-markets-recover-after-weekend-losses-saw-bitcoin-at-lowest-2018-level" target="_blank" rel="noopener">dropped below $6000</a>, the lowest price it&#8217;s seen in 2018. While bloggers and news outlets took the opportunity to criticize cryptocurrency again, many of us who believe in the future of digital assets found it a wonderful time to buy.</p>
<p>Well, except for me as I didn&#8217;t happen to check it in that time period. By the time I did it was back up over $6,100.</p>
<p>So, to avoid this again I created a simple Bitcoin price alert app that will shoot me an email when it drops again below $6,000.</p>
<p>And given that I love coding and <a href="/learn-to-code-and-get-a-job-in-six-months-step-by-step">helping others learn to code</a>, I created this brief tutorial on how I created it. In this tutorial you will learn:</p>
<ul>
<li>How to send an email with Python</li>
<li>How to pull data from an API</li>
<li>How to mask your password in the Terminal with Python</li>
<li>How to use timeouts with the Time module</li>
</ul>
<p class="textcenter"><img src="/images/2019/12/bitcoin-price-alert-app-python.jpg" alt="bitcoin price alert app python" /></p>
<h3>A word about the Bitcoin price alert app</h3>
<p>I&#8217;ve become completely enamored with Python and am learning as much as I can about it these days.</p>
<p>So logically this app would present a wonderful opportunity for more practice with the language and its modules. That&#8217;s the main drive behind creating this little Bitcoin price alert app.</p>
<p><em><strong>So remember, this is just a fun experiment. It runs in the terminal. It&#8217;s very, very basic and intended for hobbyists and of course, fellow CodeNewbies out there learning to code.</strong></em></p>
<p>That&#8217;s all it is. But&#8230;..enjoy!</p>
<h4>An outline of the Bitcoin price alert app</h4>
<ol>
<li>You are asked for a few inputs: Enter your name, Enter your email address (gmail&nbsp;only), Enter your password, Enter an email address to send alerts to, and the amount of Bitcoin by which you want to be alerted.</li>
<li>Next, it checks the Coinbase API for the current price (which is updated every minute).</li>
<li>If it is NOT below the amount you indicated, it will check again in 5 minutes.</li>
<li>If it IS below the amount you indicated, it will send you an email alert, and it will check again in 3 minutes.</li>
</ol>
<h3></h3>
<h3>The Code Explained</h3>
<p><strong>PREREQUISITE</strong>: You have to <a href="https://myaccount.google.com/u/1/lesssecureapps" target="_blank" rel="noopener">allow for Less Secure Apps</a> in your Google settings. Just set this feature on &#8216;On&#8217; and everything will work fine. If you have double verification, you cannot do this.</p>
<p>So here we go:</p>
<p>&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;</p>
<p><strong>First, we have to insert a number of Python modules:</strong></p>
<p>requests &#8211; to pull the API data<br />
time &#8211; to set the 5-minute timeouts<br />
email.mime &amp; smtplib &#8211; to send the emails<br />
getpass&nbsp;&#8211; to mask your password when you enter it.</p>
{{< highlight python "style=pygments" >}}import requests
import time
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
import smtplib
import getpass</pre>
<p>&nbsp;</p>
<p><strong>Next, we create a function to send the email called send_email():</strong></p>
<p>Each section is explained with comments</p>
{{< highlight python "style=pygments" >}}def send_email():
  # create message object instance
  msg = MIMEMultipart()
  
  # the parameters of the message
  password = your_password
  msg['From'] = your_email
  msg['To'] = send_email_to
  msg['Subject'] = "Bitcoin price, ACT FAST"

  # your message
  message = "Dear " + your_name + "\nBitcoin prices are now " + str(bitcoin_rate) + ". Better buy quick.\nRegards,\n" + your_name
  
  # adds in the message from the above variable
  msg.attach(MIMEText(message, 'plain'))
  
  # create the gmail server
  server = smtplib.SMTP('smtp.gmail.com: 587')
  
  server.starttls()
  
  # Login Creds for sending the email
  server.login(msg['From'], password)
  
  # sends the message
  server.sendmail(msg['From'], msg['To'], message)
  
  server.quit()
  
  # prints to your console
  print("successfully sent email to %s:" % (msg['To']))
  print("Price of bitcoin was at " + str(bitcoin_rate)){{< / highlight >}}
<p>&nbsp;</p>
<p><strong>Next, we create our user inputs to get the intended data and save to appropriate variables.</strong><br />
FYI: Your password is masked with the getpass module.</p>
{{< highlight python "style=pygments" >}}# user inputs
your_name = input('Enter your name: ')
your_email = input('Enter your email address (gmail only): ')
your_password = getpass.getpass()
send_email_to = input('Enter email address to send to: ')
alert_amount = input('Alert if Bitcoin drops below: '){{< / highlight >}}
<p>&nbsp;</p>
<p><strong>Then we create an infinite while loop that will:</strong><br />
1. Check the current Bitcoin price.<br />
2. If it is above your specified amount it will check again in 5 minutes.<br />
3. If it is below your specified amount, it will run our function to send the email and check again in 3 minutes.</p>
{{< highlight python "style=pygments" >}}while True:
  url = "https://api.coindesk.com/v1/bpi/currentprice.json"
  response = requests.get(
    url, 
    headers={"Accept": "application/json"},
  )
  data = response.json()
  bpi = data['bpi']
  USD = bpi['USD']
  bitcoin_rate = int(USD['rate_float'])
  if bitcoin_rate < int(alert_amount):
    send_email()
    print('Will check again in 3 minutes. Ctrl + C to quit.')
    
    time.sleep(180)
  else:
    time.sleep(300)
    print('Price is ' + str(bitcoin_rate) + '. Will check again in 5 minutes. Ctrl + C to quit.')

{{< / highlight >}}
<h3>The Final Code</h3>
<p>So with all that being said, here is the final code:</p>
{{< highlight python "style=pygments" >}}import requests
import time
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
import smtplib
import getpass

def send_email():
  # create message object instance
  msg = MIMEMultipart()
  
  # the parameters of the message
  password = your_password
  msg['From'] = your_email
  msg['To'] = send_email_to
  msg['Subject'] = "Bitcoin price, ACT FAST"

  # your message
  message = "Dear " + your_name + "\nBitcoin prices are now " + str(bitcoin_rate) + ". Better buy quick.\nRegards,\n" + your_name
  
  # adds in the message from the above variable
  msg.attach(MIMEText(message, 'plain'))
  
  # create the gmail server
  server = smtplib.SMTP('smtp.gmail.com: 587')
  
  server.starttls()
  
  # Login Creds for sending the email
  server.login(msg['From'], password)
  
  # sends the message
  server.sendmail(msg['From'], msg['To'], message)
  
  server.quit()
  
  # prints to your console
  print("successfully sent email to %s:" % (msg['To']))
  print("Price of bitcoin was at " + str(bitcoin_rate))

# user inputs
your_name = input('Enter your name: ')
your_email = input('Enter your email address (gmail only): ')
your_password = getpass.getpass()
send_email_to = input('Enter email address to send to: ')
alert_amount = input('Alert if Bitcoin drops below: ')

while True:
  url = "https://api.coindesk.com/v1/bpi/currentprice.json"
  response = requests.get(
    url, 
    headers={"Accept": "application/json"},
  )
  data = response.json()
  bpi = data['bpi']
  USD = bpi['USD']
  bitcoin_rate = int(USD['rate_float'])
  if bitcoin_rate < int(alert_amount):
    send_email()
    print('Will check again in 3 minutes. Ctrl + C to quit.')
    
    time.sleep(180)
  else:
    time.sleep(300)
    print('Price is ' + str(bitcoin_rate) + '. Will check again in 5 minutes. Ctrl + C to quit.')

{{< / highlight >}}
<p><strong>Further Improvements You Could Make To the Bitcoin Price Alert App</strong></p>
<ul>
<li>Dress up the email with some HTML and CSS. Make it look great!</li>
<li>Change the time intervals</li>
<li>Get the Subject to work as it currently doesn&#8217;t.</li>
<li>Get other Altcoin requests and set alerts.</li>
<li>Have it <a href="https://gist.github.com/Cam1337/380121" target="_blank" rel="noopener">play an iTunes song</a> for an alert, or have it send you a text.</li>
</ul>
<p>Have at it!</p>
<p>And let me know if you have any questions or comments!</p>



