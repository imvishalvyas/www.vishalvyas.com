### Have you ever received this error while using gmail smtp setting to send from your app? 

`ERROR` : 
```
t=2019-01-31T10:58:08+0000 lvl=eror msg="Failed to send alert notification email" logger=alerting.notifier.email error="534 5.7.9 Application-specific password required. Learn more at\n5.7.9  https://support.google.com/mail/?p=InvalidSecondFactor r12sm5483812wrq.3 - gsmtp"
```

`Reason` : you have used your email password to authorised app but app will not used your gmail password instead it will giving error to create Application Specific password.

Now If you faced this error the you have to create application specific password for your app and use that password to authenticate your app using SMTP.

`Solution` : 

### 1. Go to the google account click here : https://myaccount.google.com

### 2. On the left penal Click on the security.


vishalvyas1

### 3. Click on app password below 2-Step Verification.it will ask you password of your gmail account for verification.


vishalvyas2

### 4. Select app. i am using mail authentication so i will select mail.


vishalvyas4

### 5. Click on select device. where you want to authenticate with device. i am using monitoring tool setup and require smtp setup so i will select other option and provide that name of applicaiton.


vishalvyas5

### 6. Click on generate. 


vishalvyas6

### 7. Click on done button.


Now you can use that password to authenticate your gmail account with your app.

`Success Logs` :
```
t=2019-01-31T11:38:03+0000 lvl=info msg="Sending alert notification to" logger=alerting.notifier.email addresses="[vishal@vishalvyas.com]
```
