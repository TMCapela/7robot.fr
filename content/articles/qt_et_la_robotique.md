+++
title = "Qt et la Robotique (Intro)"
dater = "1 Septembre 2011"
author = "Jeremie"
+++

<h2>
	Intro</h2>
<p>
	Il peut etre utile de concevoir des interfaces utilisateur, pour pouvoir debuger facilement, prendre controle du robot et afficher des informations (position, niveau de baterrie, messages d&#39;erreurs ...).</p>
<p>
	Nous allons voir quels sont les possibilit&eacute;s que nous offre <strong>Qt</strong> et le <strong>C++</strong> pour cr&eacute;er des interfaces de debug .</p>
<p align="center">
	<img src="/clubs/robot/img/articles/Qt_small.png" /></p>
<h2>
	Principe de Qt</h2>
<p>
	Qt est une bilioth&egrave;que qui permet de creer des fenetres et de g&eacute;rer les actions (ex: appui sur un bouton) .Elle&nbsp; utilise les notions de classe et d&#39;objet du <strong>C++</strong> ce qui rend le code simple et tr&egrave;s lisible .</p>
<p>
	Ses principales caract&eacute;ristiques sont :</p>
<ol type="disc">
	<li>
		gratuit</li>
	<li>
		portable sur linux / windows / MacOs</li>
	<li>
		une tres bonne documention</li>
	<li>
		comporte une bilioth&egrave;que graphique 2D</li>
	<li>
		...</li>
</ul>
<h2>
	Interface de commande</h2>
<p>
	Voici les principaux widgets qui peuvent servir pour commnader un robot&nbsp; :</p>
<p>
	&nbsp;</p>
<p>
	.<img src="/clubs/robot/img/articles/int_action.png" /></p>
<p>
	On y trouve :</p>
<ul>
	<li>
		<strong>les checkBox </strong>:&nbsp; pour activer des options du robot</li>
	<li>
		<strong>les curseurs</strong> : pour choisir un nombre (vitesse ..)</li>
	<li>
		<strong>les boutons </strong>: pour realiser un jostik de commande</li>
	<li>
		<strong>une zonne d&#39;envoi</strong> : pour envoyer des commandes pr&eacute;cises au robot</li>
</ul>
<h2>
	Interface d&#39;Affichage</h2>
<p>
	Voici les principaux widgets qui peuvent servir pour afficher des informations sur le robot&nbsp; :</p>
<p>
	<img src="/clubs/robot/img/articles/int_aff.png" /></p>
<p>
	On y trouve :</p>
<ol type="disc">
	<li>
		<strong>les afficheurs</strong> :<em> </em>pour afficher des donn&eacute;es d&#39;odom&eacute;trie</li>
	<li>
		<strong>une zonne </strong>de texte : pour afficher un message</li>
	<li>
		<strong>une bare de progression </strong>: pour suivre le niveau de la baterrie</li>
	<li>
		<strong>une autre zonne de texte</strong> : qui permet d&#39;afficher et de suivre l&#39;avancement du programme</li>
</ol>
<h2>
	Gestion du 2D avec QT</h2>
<p>
	Et oui Qt dispose aussi d&#39; une biblioth&egrave;que graphique qui permet de dessiner et faire mouvoir vos dessins !!</p>
<p>
	<img src="/clubs/robot/img/articles/simu1.png" /></p>
<h3>
	<em><a href="/clubs/robot/img/articles/simu_video.mpeg">Voir la video de demo</a></em></h3>
<h3>
	Rq:</h3>
<p>
	Avec pas mal d&#39;heures de programation en plus on pourrait peut etre imaginer un simulateur ! Sinon on&nbsp; peut l&#39;utiliser plus simplement&nbsp; comme une recopie de ce qui se passe sur le plateau de jeux .</p>
<h2>
	Bilan</h2>
<p>
	<strong>Qt</strong> semble tr&egrave;s prometeur pour la realisation d&#39;interface de debug , il y aurra sans doute une suite d&#39;autres articles dans le courrant de l&#39;ann&eacute;e qui expliqueront notre interface de debug et le mini-simulateurs pour <strong>Eurobot 2012</strong> .</p>
<p>
	Nous esp&eacute;rons que cet article vous a donn&eacute; envie de vous lancer dans la cr&eacute;ation d&#39;interface graphique avec<strong> Qt </strong>.</p>
<p>
	Voici 2 tr&egrave;s bon tutoriels du <strong>Site Du Zero</strong>&nbsp; concacr&eacute;s &agrave; <strong>Qt </strong>et au <strong>C++</strong> :</p>
<ol type="disc">
	<li>
		<a href="http://www.siteduzero.com/tutoriel-3-11406-programmez-avec-le-langage-c.html">tuto donnant les bases du C++/QT</a></li>
	<li>
		<a href="http://www.siteduzero.com/tutoriel-3-128052-commencons.html">tuto sur la partie gestion graphique 2D avec Qt</a></li>
</ol>
<h3>
	Rq:</h3>
<p>
	La partie dialogue entre le Pc et le Robot n&#39;a pas &eacute;tait &eacute;voqu&eacute;e, il sera le sujet d&#39; autres articles . On expliquera la gestion de la<em> rs232 en C&nbsp; sur linux</em> , le p<em>rotocole de communication</em> utilis&eacute; et enfin cot&eacute; &eacute;l&eacute;ctronique nous mettrons en oeuvre une solution<em> rs232 filaire et sans fils</em> .</p>
