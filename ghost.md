# default-setting

    /var/www/ghost/versions/1.18.2/core/server/data/schema/default-settings.json


# blog mail configuration using Amazon SES

Ghost is a blogging platform written in nodejs.
Edit the config.js file at the ghost root directory

```
mail: {
   from: 'from@email.com',
   transport: 'SMTP',
   options: {
     host: "your-amazon-host",
     port: 465,
     service: "SES",
     auth: {
       user: "your-amazon-user",
       pass: "your-amazon-password"
     }
   }
}
```

Amazon SES credential can be generated from amazon control panel.
From address must be registered and verified as sender.
