This MRTG-rrd version is an update of the old MRTG-rrd script (official website is [https://www.fi.muni.cz/~kas/mrtg-rrd/](https://www.fi.muni.cz/~kas/mrtg-rrd/))

The intent of this version is to solve the problems linked to the Perl update. Modification are based on the [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=799097](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=799097) discussion.

It also tries to update the script to an updated version.

# Origin
I use this script to present some indicators for a Raspberry Pi. As the standalone MRTG will use intensively the cpu each time the script is called by the cron task, I elect to use the rrdtool and the mrtg-rrd script.

Like several MRTG scripts, it is an old code and of course not functional directly with the current Perl version.
After some searches, I identified the Debian discussion and correct the problems. Now, mrtg-rrd script is available and functional.

I also did some modifications to present the results in a single column instead of two. This will increase the display of the results in a wordpress document.

# Aim of the repository
The aim is simple:
 1. Share this functional version
 2. Propose the updates

# What remains to do?
 I would like to increase the display of the results (number of columns, use of different colors,...). 

# Installation
There is no change between this version and the previous one. I use this script in the /usr/mib/cgi-bin directory but you should be able to install it where you want. If you are looking about mrtg-rrd, I guess you ae an experimented (or at least have some knowledges) with Apache and its configuration so, you should know what to do to activate the cgi mod and cgi configuration in apache.

For the non expert, here a summary:

* Install in the /usr/lib/cgi-bin/ directory
* Active the cgi support in Apache
 sudo a2enmod cgi
* Configure the virtualhost by adding this lines (if you don't have it before)

`ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/`

`<Directory /usr/lib/cgi-bin>`

       AllowOverride None

       Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch

       Order allow,deny

       Allow from all

       Require all granted`

`</Directory>`

For the MRTG installation and configuration, you could refer to the MRTG website [https://www.fi.muni.cz/~kas/mrtg-rrd/](https://www.fi.muni.cz/~kas/mrtg-rrd/)

If everythink is well done, you dhould have access to the page through the adress http://yourserver/cgi-bin/mrtg-rrd.cgi


 





