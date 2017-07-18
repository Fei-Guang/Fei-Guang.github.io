IMPORTANT NOTES:
- Congratulations! Your certificate and chain have been saved at
   /etc/letsencrypt/live/glo.com.sg/fullchain.pem. Your
   cert will expire on 2017-07-13. To obtain a new or tweaked version
   of this certificate in the future, simply run certbot again. To
   non-interactively renew *all* of your certificates, run "certbot
   renew"
- If you lose your account credentials, you can recover through
   e-mails sent to hg@glo.com.
- Your account credentials have been saved in your Certbot
   configuration directory at /etc/letsencrypt. You should make a
   secure backup of this folder now. This configuration directory will
   also contain certificates and private keys obtained by Certbot so
   making regular backups of this folder is ideal
   
   
# Nginx configuration to enable ACME Challenge support
```
   #Rule for legitimate ACME Challenge requests (like /.well-known/acme-challenge/xxxxxxxxx)
   #We use ^~ here, so that we don't check other regexes (for speed-up). We actually MUST cancel
   #other regex checks, because in our other config files have regex rule that denies access to files with dotted names. location ^~ /.well-    known/acme-challenge/ {

    #Set correct content type. According to this:
    #https://community.letsencrypt.org/t/using-the-webroot-domain-verification-method/1445/29
    #Current specification requires "text/plain" or no content header at all.
    #It seems that "text/plain" is a safe option.
    default_type "text/plain";

    #This directory must be the same as in /etc/letsencrypt/cli.ini
    #as "webroot-path" parameter. Also don't forget to set "authenticator" parameter
    #there to "webroot".
    #Do NOT use alias, use root! Target directory is located here:
    #/var/www/common/letsencrypt/.well-known/acme-challenge/
    root         /var/www/letsencrypt;
}

#Hide /acme-challenge subdirectory and return 404 on all requests.
#It is somewhat more secure than letting Nginx return 403.
#Ending slash is important!
```
  location = /.well-known/acme-challenge/ {
      return 404;
    }
