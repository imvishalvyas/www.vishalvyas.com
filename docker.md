`Error` : 

### Another instance of Certbot is already running

```
certbot --server https://acme-v02.api.letsencrypt.org/directory --manual --preferred-challenges dns  --installer nginx -d *.vishalvyas.com
```

`Another instance of Certbot is already running`




`Reason` :

 when you run certbot form your machine and unexpectedly stop the command, Then cert bot is not running but it left some .certbot.lock files behind.You need to kill the certbot instance form your machine.



`Solution` : 

* Run the below command to find killed certbot.
```
find / -type f -name ".certbot.lock"
```

You can see result of the command, If there are, you can remove them.


* Run below command to remove them.
```
find / -type f -name ".certbot.lock" -exec rm {} \;
```

And try again.
