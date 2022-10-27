---
title: Wordpress cli install and first use steps
date: 2022-09-09 01:21:45
tags: wordpress console cli automation headless-install
---

#### install wordpres cli 
```
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
chmod +x wp-cli.phar
ln -s wp-cli.phar /usr/local/bin/wpcli

# test
wpcli help cache --allow-root 

```
###### info: --allow-root not recommended to use in prod environtment

#### initialize wordpress
```
wpcli core download --version=5.5 --locale=de_DE --skip-content
wpcli config create --dbname=DATABASE-NAME --dbuser=DBUSERNAME --dbpass=PASSWORD --allow-root
wpcli core install --url="your_domain"  --title="Blog Title" --admin_user="admin username" --admin_password="enter_your_password" --admin_email="enter_your_email"
```
#### wp clear all default pages posts widgets plugins

```
wpcli post delete $(wpcli post list --post_type='post' --format=ids --allow-root) --force --allow-root
wpcli post delete $(wpcli post list --post_type='post' --format=ids --allow-root) --allow-root
wpcli post delete $(wpcli post list --post_type='page' --format=ids --allow-root) --allow-root
wpcli plugin delete --all  --allow-root
wpcli theme delete $(wpcli theme list --status=inactive --field=name --allow-root) --allow-root
wpcli widget delete $(wpcli widget list sidebar-1 --fields=id --allow-root) --allow-root
wpcli widget delete $(wpcli widget list sidebar-2 --fields=id --allow-root) --allow-root

```
#### disable gutenberg
```
wp plugin install disable-gutenberg --activateV
```

#### install theme from local
```
wpcli theme install onepress.2.3.0.zip  --allow-root --activate
```
