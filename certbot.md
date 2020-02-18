# Secure Nginx with Let’s Encrypt on ubuntu.

Let's Encrypt is a CA authority that provides free ssl certificates. You can get a certificate for web server like apache and Nginx. In this tutorial, I will explain you how to obtain  ssl certificate using Certbot in the ubuntu server and make your website more secure. We will use Nginx web server in this tutorial.


### Prerequisites

* Setup Ubuntu 18.04 server with running Nginx webserver.

* Domain name, In this tutorial I will use `linuxguru.ml` & `www.linuxguru.ml` domain. You can buy a free domain on `https://my.freenom.com/`.



### Install certbot.

Certbot is an EFF tool that obtains a certificate from Let's Encrypt and Automatically enable HTTPS on your website. So let's install Certbot on Ubuntu 18.04. We assume that you have installed Nginx before.

Add the repository :
```
add-apt-repository ppa:certbot/certbot
```
```
 This is the PPA for packages prepared by Debian Let's Encrypt Team and backported for Ubuntu.

Note: Packages are only provided for currently supported Ubuntu releases.
 More info: https://launchpad.net/~certbot/+archive/ubuntu/certbot
Press [ENTER] to continue or Ctrl-c to cancel adding it.
```

Press ENTER and accept.

Now Install certbot nginx package.
```
apt install python-certbot-nginx
```

Certbot is installed, Now, Ley's move on Nginx configuration.

### Configure Nginx

Certbot will find `server` block from nginx config file and using that it will obtain a certificate for it, So let's create Nginx webserver. Make sure that you have map DNS entries with nginx server. I am using domain `linuxguru.ml`. I have buy a free domain from `https://my.freenom.com/`.


Create a new nginx configuration file fro your domain.
```
cp /etc/nginx/sites-available/default /etc/nginx/sites-available/linuxguru.ml
```

Open the file.
```
/etc/nginx/sites-available/linuxguru.ml
```

Find the `server_name` in the file and add your domain name there. It should look like below.
```
server_name linuxguru.ml www.linuxguru.ml;
```

Save the file and restart the nginx service.
```
systemctl reload nginx
```


### Configure firewall for nginx.
In order to access the website and fetching certificate, we have to allow http and https port.

```
ufw enable
```

```
ufw allow 'Nginx Full'
```

### Obtain an SSL certificates
We will obtain SSL certificate using certboat command.

```
certbot --nginx -d linuxguru.ml -d www.linuxguru.ml
```

Where `--nginx` is the plugin for certboat and `-d` option for domain name which you like to configure SSL.


It will ask for some information like email and agree on terms. Go ahead and provide the required details.

The output looks like below. It will also ask for https redirection, You have to select option `2` for auto redirect to https.

```
Saving debug log to /var/log/letsencrypt/letsencrypt.log
Plugins selected: Authenticator nginx, Installer nginx
Obtaining a new certificate
Performing the following challenges:
http-01 challenge for www.linuxguru.ml
Waiting for verification...
Cleaning up challenges
Deploying Certificate to VirtualHost /etc/nginx/sites-enabled/default
Deploying Certificate to VirtualHost /etc/nginx/sites-enabled/default

Please choose whether or not to redirect HTTP traffic to HTTPS, removing HTTP access.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1: No redirect - Make no further changes to the webserver configuration.
2: Redirect - Make all requests redirect to secure HTTPS access. Choose this for
new sites, or if you're confident your site works on HTTPS. You can undo this
change by editing your web server's configuration.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Select the appropriate number [1-2] then [enter] (press 'c' to cancel): 2
Redirecting all traffic on port 80 to ssl in /etc/nginx/sites-enabled/default
Redirecting all traffic on port 80 to ssl in /etc/nginx/sites-enabled/default

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Congratulations! You have successfully enabled https://linuxguru.ml and
https://www.linuxguru.ml

You should test your configuration at:
https://www.ssllabs.com/ssltest/analyze.html?d=linuxguru.ml
https://www.ssllabs.com/ssltest/analyze.html?d=www.linuxguru.ml
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/linuxguru.ml/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/linuxguru.ml/privkey.pem
   Your cert will expire on 2020-05-18. To obtain a new or tweaked
   version of this certificate in the future, simply run certbot again
   with the "certonly" option. To non-interactively renew *all* of
   your certificates, run "certbot renew"
 - If you like Certbot, please consider supporting our work by:

   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le

```


Now, We have successfully configure SSL for our domain on nginx. Let's verify.





### Auto renew SSL certificate.
By default let's encrypt certificate validity is 90 days. So we have to configure auto-renew. We will test the renewal process using the command below. You have to  configure Cron Job for it.


```
certbot renew --dry-run
```

```
0 * * * * certbot renew
```

I hope that you like the tutorial, Please share and subscribe for more interesting topics.
