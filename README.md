# Bitnami Nginx Configuration Files
This repo saves you 5 minutes per project, no need to type repetative config, just clone & edit few things and you are ready to run.

# Installation

Clone this repo into /home/bitnami/apps/YOUR_APP_NAME and edit pre-configurated files to match your settings:

```bash
# Example of /home/bitnami/apps/YOUR_APP/conf/ngin-app.conf
index index.php index.html index.htm;
allow all;
deny all;

error_log  "/home/bitnami/apps/YOUR_APP/logs/error.log";
access_log "/home/bitnami/apps/YOUR_APP/logs/access.log";

client_max_body_size 20m;

location ~ \.php$ {
    fastcgi_split_path_info ^(.+\.php)(/.+)$;
    fastcgi_read_timeout 300;
    fastcgi_pass unix:/opt/bitnami/php/var/run/www.sock;
    fastcgi_index index.php;
    fastcgi_param  SCRIPT_FILENAME $request_filename;
    include fastcgi_params;
}
```

After creating this config file remove remote from your local git

```bash
git remote -v
git remote remove origin
```

Optionally you can create your own private repo to track changes there

```bash
git remote add origin YOUR_REPO.GIT
```

Then commit and push changes as ussual (but to private repo offcourse)