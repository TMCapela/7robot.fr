+++
title = "Les servomoteurs AX-12 avec un Arduino"
dater = "17 Septembre 2011"
author = "Martin"
+++

<p>
	<img src="/img/articles/ax12a_medium.jpg" style="float:right;margin:15px" /></p>
<p>
	Dans le top des servomoteurs, l&#39;AX-12 tient une bonne place. Il est fabriqu&eacute; en Cor&eacute;e par Robotis, vendu $45, et vous fera gagner un temps &eacute;norme. On le contr&ocirc;le avec un bus s&eacute;rie, de type <strong>RS-485 &agrave; trois fils</strong>, et un syst&egrave;me d&#39;adresses. Voici comment utiliser vos AX-12 (et peut-&ecirc;tre d&#39;autres produits Dynamixel) <strong>simplement avec un Arduino</strong>.</p>
<div>
	<p>
		Datasheet :</p>
	<p>
		<a href="/img/AX-12A.pdf">AX-12A.pdf</a></p>
	<p>
		Biblioth&egrave;que&nbsp;&agrave; mettre dans un dossier&nbsp;<em>libraries</em>&nbsp;dans votre <em>Sketchbook</em>&nbsp;:</p>
	<p>
		<a href="https://github.com/7Robot/Eurobot-2012/tree/master/Arduino">https://github.com/7Robot/Eurobot-2012/blob/master/Arduino/libraries/ax12v2.0.rar</a>&nbsp;(<a href="http://www.pablogindel.com/2010/01/biblioteca-de-arduino-para-ax-12/">source</a>)</p>
	<h2>
		Branchement</h2>
	<p>
		<img src="/img/articles/ax12pinout_medium.png" style="float:left;margin:15px" /></p>
	<p>
		La commande s&#39;effectue via un bus en <em>daisy chain</em>&nbsp;c&#39;est-&agrave;-dire que chaque servo a deux connecteurs identiques, pour raccorder facilement plusieurs servos en parall&egrave;le.</p>
	<p>
		Sur le sch&eacute;ma ci-contre Data transmet les donn&eacute;es en s&eacute;rie (TX / RX alternativement, cf <a href="http://fr.wikipedia.org/wiki/RS-485">RS-485</a>).</p>
	<p>
		<strong>Attention : VDD doit &ecirc;tre entre 7V et 10V pour que le servo s&#39;allume</strong>.</p>
	<p>
		Nous allons utiliser les pins 0 (RX) et &nbsp;1 (TX) de votre Arduino, car le pseudo RS-485 des servos n&#39;est pas tr&egrave;s diff&eacute;rent du RS-232 classique. Il suffit de brancher TX ou RX sur le fil Data suivant la direction du flux. La datasheet des AX-12 parle du composant&nbsp;74HC126 mais il suffit en r&eacute;alit&eacute; de faire passer alternativement les pins de l&#39;arduino en haute imp&eacute;dance (<em>tri-state</em>). C&#39;est ce que la libraire que nous utiliserons fait.</p>
	<p>
		R&eacute;sum&eacute; du branchement :</p>
	<p>
		- <strong>GND</strong> sur le GND de votre Arduino</p>
	<p>
		- <strong>VDD</strong> sur du 7V-10V, par exemple sur la pin&nbsp;<b>Vin</b>&nbsp;de votre Arduino, qui est reli&eacute;e au connecteur d&#39;alimentation de la carte ; et sur ce connecteur vous branchez un transformateur 9V par exemple.</p>
	<p>
		- <strong>Data</strong> sur les pins TX et RX (1 et 0) de votre Arduino, par exemple en soudant le fil &agrave; deux pins d&#39;une tulipe m&acirc;le.</p>
	<a href="/img/articles/ax12-test.jpg"><img src="/img/articles/ax12-test_medium.jpg" style="float:right;margin:15px" /></a>
	<h2>
		Programmes de test</h2>
	<p>
		Voici deux programmes simples pour tester votre arduino, et comprendre l&#39;utilisation d&#39;ax12.h :</p>
	<ol type="disc">
		<li>
			<a href="https://github.com/7Robot/Eurobot-2012/blob/master/Arduino/ax12_aller_retour/ax12_aller_retour.pde">ax12_aller_retour.pde</a> : Le servo fait des aller-retour entre +90&deg; et -90&deg;.</li>
		<li>
			<a href="https://github.com/7Robot/Eurobot-2012/blob/master/Arduino/ax12_blink_id/ax12_blink_id.pde">ax12_blink_id.pde</a> : Fait clignoter les LEDs int&eacute;gr&eacute;es aux AX-12 pou afficher leur adresse. Trois flashs pour le servo num&eacute;ro 3 par exemples. Utile quand plusieurs servos sont sur un m&ecirc;me bus.</li>
	</ol>
	<h2>
		Utilisation de <a href="https://github.com/7Robot/Eurobot-2012/blob/master/Arduino/libraries/ax12/ax12.h">ax12.h</a></h2>
	<p>
		Apr&egrave;s avoir install&eacute; la biblioth&egrave;que (soit quatre fichiers dans &quot;Sketchbook/libraries/ax12/&quot;) voici les grandes &eacute;tapes pour l&#39;utiliser :</p>
	<ol type="disc">
		<li>
			Cr&eacute;er une instance de la classe : <strong>AX12 moteur(<em>id</em>);</strong></li>
		<li>
			Dans setup() :&nbsp;<strong>AX12::init(1000000);</strong> pour r&eacute;gler la vitesse du port s&eacute;rie.</li>
		<li>
			L&#39;AX-12 est vu comme une grande m&eacute;moire, refl&eacute;tant la position, le couple, la temp&eacute;rature du servo, etc. Pour donner une consigne de position&nbsp;par exemple, on &eacute;crit &agrave; l&#39;adresse <em>GOAL_POSITION</em>, avec l&#39;instruction :<br />
			<strong>moteur.writeInfo(GOAL_POSITION, <em>entier</em>);</strong> o&ugrave; <em>entier</em> est une valeur entre 0 et 1023. On peut utiliser la fonction <em>map</em>&nbsp;pour utiliser des angles en faisant attention aux limites physiques de l&#39;AX-12 (60&deg; d&#39;angle mort), par exemple :<br />
			<strong>entier = map(angle, -150, 150, 0, 1023);</strong></li>
		<li>
			Il existe aussi&nbsp;<strong>moteur.readInfo(<em>adresse</em>)&nbsp;;</strong></li>
		<li>
			La liste des adresses est au d&eacute;but de <em>ax12.h</em>, et leur explication dans la datasheet.</li>
	</ol>
	<p>
		Pour le reste je vous laisse lire les sources de la librairie, dont on pourra d&eacute;plorer que les commentaires soient en espagnol...</p>
</div>
<p>
	&nbsp;</p>
