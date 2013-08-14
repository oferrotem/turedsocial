Forked from https://github.com/kissrobber/turedsocial
______________________________________________________

Installing: https://github.com/oferrotem/turedsocial
=====================================================

1. You need to install “punjab” and it has the following dependencies:  
    1. Python >= 2.6.  
        1. Type “python --version” in the command line to see if you’ve got it.  
    2. Twisted >= 11.1 http://twistedmatrix.com/  
        1. Type “twistd --version” in the command line to see if you’ve got it.  
    3. pyopenssl - if you want tls to work.  
        1. Get the pip installer: “sudo apt-get install python-pip”  
        2. Install: “pip install pyopenssl”  
        3. If you already got it, upgrade: “pip install pyopenssl --upgrade”  
    4. A jabber server like jabberd2  
        1. Type “sudo apt-get install jabberd2” in the command line.  
2. Now install “punjab”:  
    1. choose a dir and do “git clone https://github.com/twonds/punjab.git”.  
    2. Write in Terminal (in the same dir): “sudo python setup.py install”.  
3. If running Nginx as a server software, open a new vhost file. Mine is in /etc/nginx/sites-available/dev.amigobar.com (don’t forget to make a symbolic link in ../sites-enabled [ln -s]).  
    1. In the new vhost file, enter the following configuration:  
```
    server {
        listen       80;
        server_name  dev.amigobar.com;
        # root /home/ofer/projects/amigobar/turedsocial/facebook-chat-example;

        # This regexp did not work for me.
        # location ~ ^/http-bind/ {
        location /http-bind {
            proxy_pass http://localhost:5280;
        }

        location / {
            # This is where you place your strophejs sample.
            # root /Users/makoto/work/sample/strophejs-1.0;
            root /home/ofer/projects/amigobar/turedsocial/facebook-chat-example;
        }
    }
```
    2. Run “sudo service nginx reload” or “sudo service nginx start” to include the latest change in vhosts.  
4. Getting the code: run “git clone https://github.com/oferrotem/turedsocial.git”.  
    1. In dir “turedsocial/facebook-chat-example/” edit the javascript in the facebook_strophe.html file to have your “app id”, “secret key” and “BOSH_SERVICE” (lines 121, 151, 152, 10).  
    2. In your browser, go to “http://dev.amigobar.com/facebook_strophe.html”, enter your JID (Mine is ofer.goldbar@chat.facebook.com) and facebook password, then click on “connect”.  
    3. To send a message, enter in the “to” field your friend’s UID, the format is a minus, “-”, sign followed by the friend’s Facebook ID number, followed by  “@chat.facebook.com”. For example: “-65482519@chat.facebook.com”.  

=====================================================================
Credits:  
1. https://github.com/javierfigueroa/turedsocial  
2. Nginx: https://gist.github.com/makoto/272956  
3. New facebook-strophe.html: https://gist.github.com/RudyLu/5641350  
4. Special thanks to [Gilad Dayagi](https://github.com/giladaya)  
