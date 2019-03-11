+++
title = "Ponts en H"
dater = "12 Août 2011"
author = "Jeremie"
+++

<h2>
	Principe</h2>
<p>
	Cette carte r&eacute;alise l&#39;interface de puissance pour&nbsp; contr&ocirc;ler jusqu&#39;&agrave; 2 moteurs CC ou 1 moteur pas &agrave; pas<br />
	On peut r&eacute;gler le sens de rotation (2 ponts en H) et la vitesse du moteur en faisant varier le rapport cyclique sur les entr&eacute;es EN .<br />
	La carte fonctionne avec une tension d&#39;alimentation de +12v et jusqu&#39;a des courants de 3A<br />
	La carte se d&eacute;compose suivant :</p>
<ol type="disc">
	<li>
		1 bornier d&#39;alimentation +12V</li>
	<li>
		[ intA1/intA2] : sens moteur A</li>
	<li>
		[ EnbA] : PwmA</li>
	<li>
		[ SensA] : tension image du courant A</li>
	<li>
		[ intA1/intA2] : sens moteur A</li>
	<li>
		[ EnbA] : PwmA</li>
	<li>
		[ SensA] : tension image du courant A</li>
	<li>
		2 borniers sortie moteur A/B</li>
</ol>
<p>
	&nbsp;<br />
	<em>Rq : pour avoir un PWM d&#39;un apport de 1, mettre le cavalier sur l&#39;entr&eacute;e </em>ENB</p>
<h2>
	Mat&eacute;riel utilis&eacute;</h2>
<ol type="disc">
	<li>
		Double pont en H : L298</li>
	<li>
		8 diodes de puissances</li>
	<li>
		3 borniers doubles</li>
	<li>
		1 connecteur 8 broches</li>
</ol>
<h2>
	Sch&eacute;ma &eacute;lectrique</h2>
<p>
	<a href="/clubs/robot/img/articles/schema_ponth.png"><img src="/clubs/robot/img/articles/schema_ponth_mini.png" /></a></p>
<h2>
	Layout</h2>
<p>
	<img src="/clubs/robot/img/articles/im2.png" /></p>
<h2>
	<img src="/clubs/robot/img/articles/im1.png" /></h2>
<h2>
	Les fichiers sources (T&eacute;l&eacute;chargeable)(TODO)</h2>
<ol type="disc">
	<li>
		Fichier du projet Orcad</li>
	<li>
		Layout au format Gerber</li>
	<li>
		Liste et r&eacute;f&eacute;rence des composants</li>
</ol>
<h2>
	Datasheet du L298</h2>
<p>
	<a href="//www.datasheetcatalog.org/datasheet2/2/052daje928cw7pc0uqs1ipyryppy.pdf')"><img src="/clubs/robot/img/articles/pdf_logo.png" /></a></p>
<h2>
	Photos (TODO)</h2>
<p>
	&nbsp;</p>
<p>
	&nbsp;</p>
