+++
title = "Communication sans fil avec Xbee"
dater = "16 Septembre 2011"
author = "Jeremie"
+++

<h2>
	Intro</h2>
<p>
	Les modules<strong> XBee</strong> permettent d&#39;&eacute;tablir une liaison RS232 sans fils .</p>
<p>
	<strong>Avantages :</strong> prix ; simplicit&eacute; de mise en oeuvre ; fiabilit&eacute; ; port&eacute;e</p>
<p>
	<strong>Inconv&eacute;nients</strong> : pas un emp&acirc;tement de type labdec ; alim 3.3V</p>
<p>
	Nous allons d&eacute;crire les &eacute;tapes qui nous ont permis de comprendre et de faire fonctionner cette liaison sans fil .</p>
<p>
	<img src="/clubs/robot/img/articles/usb_xbee_medium.jpg" style="float:right" /><img src="/clubs/robot/img/articles/xbee_im_medium.jpg" style="float:left" /></p>
<h2>
	Le mat&eacute;riel utilis&eacute;</h2>
<div>
	- &Agrave; gauche un des&nbsp;deux XBee pro ;
	<p>
		- &Agrave; droite l&#39;XBee explorer (de <a href="http://www.sparkfun.com/products/8687">SparkFun</a>), qui est un adaptateur USB/XBee ;</p>
	<p>
		- Et finalement un Arduino Uno.</p>
	<p>
		&nbsp;</p>
	<p>
		Comment s&#39;y prendre ?</p>
	<p>
		De nombreux tutoriels sur internet, ne mentionnent pas la configuration des<strong> xbee</strong> , ils les utilisent directement et &ccedil;a marche pour 90% des cas (car la configuration par d&eacute;faut est bien pens&eacute;e). Pour les 10% restant, il faut v&eacute;rifier, mettre &agrave; jour le<strong> firmware </strong>et configurer le <strong>mode de fonctionement</strong> !&nbsp;</p>
	<h2>
		Etape 1 : Communication Xbee &lt;-&gt; Pc</h2>
	<p>
		Les d&eacute;veloppeurs d&#39;<strong>XBee</strong> proposent un <strong>logiciel (XTCU)</strong> de test et configuration car chaque<strong> </strong>XBee poss&egrave;de un <strong>firmware (</strong>qui peut &ecirc;tre mis &agrave; jour) et qu&#39;il est aussi possible, voire indispensable, de r&eacute;gler les diff&eacute;rents param&egrave;tres :</p>
	<ol type="disc">
		<li>
			Identifiant du reseau (PANID)</li>
		<li>
			Channel de comunication</li>
		<li>
			Le mode de fonctionnement</li>
		<li>
			Et plein d&#39;autre param&egrave;tres (pour une utilisation plus pouss&eacute;e)</li>
	</ol>
	<p>
		Ce test permet dans un premier temps de v&eacute;rifier le fonctionement,&nbsp;<strong>la version</strong> du firmware, et de r&eacute;gler le <strong>mode de fonctionnement</strong> de chaque<strong> </strong>xbee . L&#39;adapteur<strong> usb/xbee</strong> est tr&egrave;s utile pour cette &eacute;tape .</p>
	<h2>
		Etape 2 : Choix du mode de fonctionnement</h2>
	<p>
		Avec des<strong> </strong>XBee on peut faire des choses plus ou moins compliqu&eacute;es , si vous utiliser&nbsp;<strong>2 XBee</strong> pour r&eacute;aliser une simple liaison <strong>RS232 </strong>sans fils, le mode <strong>&quot;peer to peer&quot;</strong> est conseill&eacute;. Les r&eacute;glages sont alors les suivants :</p>
	<ol type="disc">
		<li>
			PanID et Channel sont identiques pour les 2 Xbee</li>
		<li>
			CE=0 (vous choisissez le mode &quot;peer to peer&quot; et non &quot;coordinator/endDevice&quot;</li>
		<li>
			A1=1</li>
		<li>
			A2=0</li>
	</ol>
	<p>
		Nous avons trouv&eacute; ces r&eacute;glages sur&nbsp;<a href="/clubs/robot/sites/default/files/files/XBee-Manual.pdf">la datatsheet</a> et <a href="/clubs/robot/sites/default/files/files/xbee_config.pdf">un tr&egrave;s bon document &eacute;crit par D.MENESPLIER</a></p>
	<h2>
		Etape 3 : Savoir s&#39;ils se sont reconnus</h2>
	<p>
		On met en place les 2 xbee (1 sera reli&eacute; au pc et l&#39; autre sera aliment&eacute; et connect&eacute; &agrave; un arduino).</p>
	<p>
		Gr&acirc;ce au logiciel fourni, on va demander au xbee raccord&eacute; au pc si il reconnait l&#39;autre XBee. Pour cela on utilise le<strong> terminal du logiciel</strong> et on suit ces etapes :</p>
	<ul>
		<li>
			Mise en mode configuration (<strong> +++ et AT,&nbsp;</strong>cf la doc )</li>
		<li>
			La commande <strong>ATND</strong> permet de r&eacute;cup&eacute;rer les informations sur le module trouv&eacute; et les affiche</li>
		<li>
			La commande<strong> ATCN </strong>quitte le mode configuration</li>
	</ul>
	<h3>
		<em><img src="/clubs/robot/img/articles/capt_ecranXTCU.PNG" /></em></h3>
	<h2>
		Bilan</h2>
	<p>
		On sait &agrave; la fin de l&#39;&eacute;tape 3, que nos xbee fonctionent s&eacute;parement, qu&#39;ils ont la bonne configuration et qu&#39;ils se reconaissent. La liaison est donc bien &eacute;tablie ! Cette liaison se teste comme une simple<strong> liaison s&eacute;rie RS232 </strong>filaire.</p>
	<h2>
		Ressources :</h2>
	<ol type="disc">
		<li>
			<a href="/clubs/robot/sites/default/files/files/XBee-Manual.pdf">La datasheet Xbee</a></li>
		<li>
			<a href="/clubs/robot/sites/default/files/files/xbee_config.pdf">Un document qui explique&nbsp; la configuration des xbee </a></li>
		<li>
			<a href="/clubs/robot/sites/default/files/files/XCTU_xbee.pdf">L&#39;explication du logiciel</a></li>
	</ol>
</div>
<p>
	&nbsp;</p>
