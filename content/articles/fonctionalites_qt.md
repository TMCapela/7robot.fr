+++
title = "Autres fonctionalités de Qt (avancé)"
dater = "02 Septembre 2011"
author = "Jeremie"
+++

<h2>
	Intro</h2>
<p>
	De nombreuse librairies externes permettent d&#39;etendre les fonctionalit&eacute;s de Qt . Nous porterons notres attention sur ces 2 librairies :</p>
<ol type="disc">
	<li>
		Qextserialport : permet de g&eacute;rer une liaison rs232 sous Qt</li>
	<li>
		Qwt : permet de r&eacute;alis&eacute; des trac&eacute;s de courbes</li>
</ol>
<h3>
	Rq :</h3>
<p>
	Ces 2 librairies sont compatibles linux et windows , nous allons expliquer leur utilisation sous un systeme linux .</p>
<h2>
	Qextserialport pour la gestion rs232</h2>
<p>
	Qextserialport permet de configurer la liaison :</p>
<ol type="disc">
	<li>
		choix du port : ttyUSB0</li>
	<li>
		choix du mode lecture/ecriture</li>
	<li>
		choix de la vitesse/bit de stop ....</li>
</ol>
<p>
	une fois la liaison configur&eacute;e on utilise les fonctions du type :</p>
<ol type="disc">
	<li>
		port-&gt;write(data)</li>
	<li>
		port-&gt;read(buffer)</li>
</ol>
<h3>
	Rq:</h3>
<p>
	Afin de recuperer les donn&eacute;es de mani&egrave;re &quot;continue&quot; , nous on peut utiliser des Timers ou des Threads . Un Thread peut lire en permanace le port serie de mani&egrave;re parral&egrave;le &agrave; notre programme .&nbsp; &nbsp;<br />
	&nbsp;</p>
<h2>
	Qwt pour tracer des courbes</h2>
<p>
	Qwt donne les outils necessaires &agrave; Qt pour tracer des coubes de mani&egrave;re statique.</p>
<p>
	<img src="/clubs/robot/img/articles/qwt_sinus.png" /></p>
<p>
	&nbsp;</p>
<p>
	Mais aussi en temps r&eacute;el :</p>
<p>
	&nbsp;</p>
<p>
	<img src="/clubs/robot/img/articles/qwt_oscillo.png" /></p>
<p>
	<a href="/clubs/robot/img/articles/Oscillo_video.mpeg">voir la video de demo</a></p>
<h2>
	Les sources :</h2>
<ol type="disc">
	<li>
		<a href="http://graal.ens-lyon.fr/~fvivien/Enseignement/PPP-2001-2002/LibDyn.pdf">Un compl&eacute;ment de cour pour comprendre l&#39;utilisation d&#39;une librairie</a></li>
	<li>
		<a href="http://jmfriedt.free.fr/lm_qt.pdf">Un rapport de l&#39;utilisation Qt/Qwt/Qextserialport &agrave; travers divers r&eacute;alisations</a></li>
</ol>
