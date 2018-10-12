+++
title = "Coupe de France de robotique Explications 2015"
dater = "26 Juillet 2015"
author = "Amandine"
weight = 18
+++

<p>
	La Coupe de France de Robotique (ancienne coupe E=M6) est la division Fran&ccedil;aise de la coupe Eurobot. Elle r&eacute;unit chaque ann&eacute;e <strong>180 clubs de passionn&eacute;s</strong> de moins de 30 ans, majoritairement des &eacute;coles d&#39;ing&eacute;nieurs et des universit&eacute;s.</p>
<p>
	Les r&egrave;gles changent chaque ann&eacute;e mais il y a certaines constantes, comme les dimensions du robot et du plateau. Le club construit un robot pendant l&#39;ann&eacute;e, et va participer &agrave; la coupe en juin, &agrave; la Fert&eacute;-Bernard (pr&egrave;s du Mans). C&#39;est une sacr&eacute; <strong>f&ecirc;te sur trois jours</strong>, on y retrouve plein d&#39;amis, et on apprend beaucoup des autres &eacute;quipes.</p>
<h2>
	Th&egrave;me 2015 : Robomovies !</h2>
<p>
	Cette ann&eacute;e, le but &eacute;tait de r&eacute;cup&eacute;rer des gobelets remplis de pop corn repr&eacute;sent&eacute;s par&nbsp;de petites boules en plystir&egrave;ne, mais aussi d&#39;abattre des claps, de ramasser des spots et des pop corn. Pour cela, notre robot Hitchbot &eacute;tait muni de deux pinces rattantes et d&#39;une serrante, qui &eacute;levait les spots dans un tube maintenu serr&eacute; durant ses d&eacute;placements. Il avait a l&#39;arri&egrave;re deux cales qui attrapaient et gardaient les gobelets jusqu&#39;au point de d&eacute;pot.</p>
<p>
	Mais en plus tout cela, une autre &eacute;preuve &eacute;tait de monter des marches en y d&eacute;posant de part et d&#39;autre des tapis rouge. Notre second robot, Tarantibot, s&#39;occupait de cela. Avec ses chenilles, il a grimp&eacute; facilement les marches&nbsp;lors de&nbsp;chaque combat ! Un as, notre Tarantibot.</p>
<p>
	&nbsp;</p>
<p>
	Pour voir nos photos et nos vid&eacute;os, rendez-vous sur notre FaceBook 7Robot !</p>
<h2>
	<br />
	Th&egrave;me 2014 : Pr&eacute;histobot !</h2>
<p>
	Cette ann&eacute;e, 11 membres du club sont mont&eacute;s &agrave; la Fert&eacute;-Bernard participer &agrave; la coupe de France de robotique qui s&#39;est lanc&eacute; &agrave; la chasse au mammouth.</p>
<p>
	&nbsp;</p>
<p>
	<a href="http://www.planete-sciences.org/robot/data/file/coupe/2014/Rules2014%20-%20Version%20finale%20-%20Eurobot.pdf" title="Réglement (fr)">R&eacute;glement 2014 (fr)</a></p>
<h2>
	Th&egrave;me 2013 : Joyeux Anniversaire !</h2>
<p>
	-</p>
<h2>
	Th&egrave;me 2012 : Ile au tr&eacute;sor</h2>
<p>
	<a href="http://www.planete-sciences.org/robot/index.php?section=pages&amp;pageid=108">Site de la coupe de France 2012</a></p>
<p>
	<a href="http://www.planete-sciences.org/robot/data/file/coupe/2012/E2012_Reglement_FR_final.pdf">R&eacute;glement (fr)</a></p>
<p>
	<a href="http://www.planete-sciences.org/robot/data/file/coupe/2012/E2012_Rules_EN_final.pdf">R&eacute;glement (en)</a></p>
<div>
	<h2>
		Th&egrave;me 2011 : Les &Eacute;checs</h2>
</div>
<p>
	&nbsp;</p>
<p>
	<a href="http://www.eurobot.org/commonfiles/docs/2011/E2011_Rules-EN.pdf">R&egrave;gles du jeu</a>&nbsp;(pdf)</p>
<p>
	<a href="http://www.planete-sciences.org/robot/index.php?section=pages&amp;pageid=101">Site de la coupe de France 2011</a></p>
<h2>
	Pr&eacute;hension</h2>
<p>
	La premi&egrave;re &eacute;tape a &eacute;t&eacute; de fixer les exigences techniques de la pince. Bien loin de nos cours de SI, voici les fonctions techniques que devra remplir la partie pr&eacute;hension :</p>
<ul>
	<li>
		<p>
			Etre simple &agrave; r&eacute;aliser (m&eacute;canique)</p>
	</li>
	<li>
		<p>
			Tenir une charge cylindrique de 2kg pendant 90s</p>
	</li>
	<li>
		<p>
			Pouvoir &eacute;lever celle-ci &agrave; 15cm du sol</p>
	</li>
	<li>
		<p>
			Avoir un encombrement minimal autour de la pi&egrave;ce</p>
	</li>
</ul>
<p>
	Nous avons d&eacute;cider de partir d&#39;un mat&eacute;riau de base, peu couteux et facile &agrave; fa&ccedil;oner : les barres d&#39;aliminuim &agrave; section en U.</p>
<h2>
	Intelligence</h2>
<p>
	Nous voulons mettre une cam&eacute;ra sur le robot. C&#39;est une solution puissante pour obtenir des informations sur le terrain, mais elle est complexe &agrave; mettre en oeuvre. Nous allons donc utiliser une webcam et analyser ses images avec une carte de commande pour d&eacute;terminer les actions du robot.</p>
<h3>
	Choix de la carte</h3>
<p>
	Pour g&eacute;rer la webcam simplement, nous avons achet&eacute; une carte CS-E9302. Elle dispose d&#39;un port USB ma&icirc;tre pour brancher la webcam, et fait tourner Linux avec les drivers adapt&eacute;s. Le reste des capteurs et les moteurs peuvent &ecirc;tre branch&eacute;s sur une trentaine de pins GPIO, ce qui est largement suffisant.</p>
<p>
	Reconnaissance d&#39;image</p>
<p>
	Nous allons faire la reconnaissance d&#39;image avec <a href="http://opencv.willowgarage.com/wiki/">OpenCV</a>, une puissante librairie de traitement d&#39;image con&ccedil;ue pour la robotique. Le principe est simple : on lit une image sur la webcam d&egrave;s qu&#39;une d&eacute;cision doit &ecirc;tre prise par le robot. Le principal traitement &agrave; faire pour 2011 est d&#39;identifier les pions en vue (couleur jaune), puis de calculer leur azimuth.</p>
