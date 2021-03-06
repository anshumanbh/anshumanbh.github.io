---
layout: post
title: Installing MySQL via Homebrew on Mac OS X Lion 10.7.2
date: 2011-11-12 03:41:07.000000000 -08:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Miscellaneous
tags:
- Homebrew
- Mac OS X Lion
- MySQL
meta:
  _edit_last: '28002546'
  _wpas_done_yup: '1'
  _wpas_done_fb: '1'
  _wpas_done_linkedin: '1'
  tagazine-media: a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";s:1:"0";s:6:"author";s:8:"28002546";s:7:"blog_id";s:8:"28453754";s:9:"mod_stamp";s:19:"2011-11-12
    10:43:08";}
  _wpas_skip_twitter: '1'
author:
  login: abhartiya
  email: anshuman.bhartiya@gmail.com
  display_name: abhartiya
  first_name: ''
  last_name: ''
---
I had a brainfreeze while trying to figure this stupid installation of MySQL on my Mac OS X Lion 10.7.2 so I decided I am going to write a post about it so that others who were doing the same mistake I was don't have to spend so much time wondering what is going on.

So, I installed Homebrew (I decided to install Homebrew over MacPorts) and then was trying to get my Ruby on Rails environment setup. I came across a lot of hurdles while installing RVM and Ruby itself. But, googling helped me so i didn't have a difficult time here. Now, I have the following configured:

```
Ruby 1.9.3p0
RVM 1.9.2
git version 1.7.7.3
Rails 3.1.1
```

When it came to installing MySQL, google was the least helpful. I am going to get straight to the installation problems that you might face.

So, once you have homebrew installed, you can just type `brew install mysql` and it will do all the needful and install it on your workstation. But, the fun starts after this when you need to configure it. The catch here is to read the instructions carefully once mysql is installed and not try to read between the lines literally.

The first 2 steps should be done as it is:
```
unset TMPDIR
mysql_install_db --verbose --user=`whoami` --basedir="$(brew --prefix mysql)" --datadir=/usr/local/var/mysql --tmpdir=/tmp
```

Now, if you start the sqlserver manually after this step by typing `mysql.server start` as per the instructions, it will start without any problems initially. You can even connect as a root by typing `mysql -uroot`. Everything is fine till this point.

After this, I tried to continue with the steps without understanding what I was doing. I used the *launchctl* utility to automatically load the mysqld daemon on startup. So, I typed in exactly the same commands as shown by homebrew:
```
mkdir -p ~/Library/LaunchAgents
cp /usr/local/Cellar/mysql/5.5.15/com.mysql.mysqld.plist ~/Library/LaunchAgents/
launchctl load -w ~/Library/LaunchAgents/com.mysql.mysqld.plist
```

This is where the problems started! I dont remember the errors I got and the changes I tried to do after reading in various forums and stackoverflow. All I remember is that nothing worked. The errors were related to some /tmp/mysql.sock file.

Basically, I started the sqlserver manually and then without stopping it, I used the launchctl utility to automatically start it on startup simultaneously. There was already the mysqld daemon running and listening on the port 3306 and I tried to start it again. Not to mention, it failed and I wasn't thinking straight. I should have looked at the log file which gets generated at `/usr/local/var/mysql/.err` but I didn't. It was clearly mentioned there that the port is already in use.

Anyways, so the summary is that you can either start and stop mysqld daemon manually by typing `mysql.server start` and `mysql.server stop` or you can use the launchctl utility to automate it at startup. From the instructions, it seems like we have to do both but it's just common sense that I guess I didn't have at that moment.

So, I finally did `ps -ef | grep mysqld` and saw 2 processes running. I killed them and finally used the launchctl utility to load the `com.mysql.mysqld.plist` (I didn't want to start and stop mysqld manually) . It started the mysqld daemon without any errors and i was good to go. I then proceeded with creating the root password and mysql was finally installed! Phew..

I saw so many people have commented different things like touching `/tmp/mysql.sock and` copying `my-small.cnf` to `/usr/local/var/mysql` to blah. Nothing makes sense. Period. I am pretty sure a lot of people are pretty much doing the same thing I was. We just need to be more attentive of what we are doing.

I feel so stupid I wasted almost 3 hours on this.