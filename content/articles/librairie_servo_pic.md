+++
title = "Librairie C18 pour servomoteurs standards et PIC18F"
dater = "07 Octobre 2011"
author = "Martin"
+++

<p>
	La librairie C18 que nous vous proposons est courte (une centaine de lignes), mais simplifie l&#39;utilisation de <strong>servomoteurs sur les PIC18F</strong>. Nous l&#39;avons principalement test&eacute;e sur le 2550.</p>
<h2>
	Rappels sur les servomoteurs</h2>
<p>
	Ce sont des boitiers con&ccedil;us pour le mod&eacute;lisme qui contiennent un <strong>moteur continu</strong>, un <strong>r&eacute;ducteur</strong>, et de l&#39;&eacute;lectronique de commande. Il sont souvent limit&eacute;s &agrave; 180&deg; de d&eacute;battement (certains plus, certains moins). On les <strong>commande en position</strong>, contrairement aux moteurs continus qui se commandent en vitesse.</p>
<p>
	D&#39;ailleurs &agrave; ce sujet attention, vous tomberez peut-&ecirc;tre sur des servos modifi&eacute;s, dont une partie de l&#39;&eacute;lectronique a &eacute;t&eacute; enlev&eacute;e. R&eacute;sultat : vous ne commanderez que la vitesse. Dans ce cas une commande inf&eacute;rieure &agrave; 90&deg; fait marche arri&egrave;re, 90&deg; l&#39;immobilisent, et au del&agrave; marche avant progressivement. D&egrave;s qu&#39;un servo fait plus d&#39;un tour sur lui-m&ecirc;me c&#39;est qu&#39;il est modifi&eacute;.</p>
<p>
	Les servos ont trois fils : la masse GND (Noir ou Marron), l&#39;alimentation en 5V par exemple (Rouge), et la commande (Blanc ou Orange), que nous allons maintenant &eacute;tudier.</p>
<h2>
	Principe de la librairie</h2>
<p>
	Les servomoteurs se commandent par <strong>largeur de pulsation</strong>. Une pulsation toutes les 20ms, dont la largeur est reli&eacute;e lin&eacute;airement &agrave; la consigne donn&eacute;e. Pour un servo 180&deg; typique, la largeur correspondant &agrave; 0&deg; est 544&micro;s, et 2400&micro;s pour 180&deg;. Vous pouvez envoyer ces signaux avec un PWM (c&#39;est ce que fait la librairie Servo d&#39;Arduino), mais sur les PICs que nous utilisons au club on manque de r&eacute;solution avec l&#39;oscillateur interne (10&deg; max).</p>
<p>
	Cette librairie utilise donc les interruptions sur le <strong>Timer0</strong> pour commander jusqu&#39;&agrave; 8 servos connect&eacute;s sur le <strong>port B</strong>. Nous allons Envoyer les pulsations pour chaque servo &agrave; la suite, puis attendre 20ms avant de recommencer. Sur le sch&eacute;ma suivant vous voyez bien que le d&eacute;lai entre deux pulsations sur RB0 va varier en fonction de ce qu&#39;on envoie &agrave; RB1, mais c&#39;est n&eacute;gligeable.</p>
<p>
	<a href="/clubs/robot/img/articles/chronographe-servo.svg"><img src="/clubs/robot/img/articles/chronographe-servo.png" /></a></p>
<h2>
	Utilisation</h2>
<p>
	Le code &agrave; inclure est dans le fichier suivant :</p>
<p>
	<a href="https://github.com/7Robot/Eurobot-2012/blob/master/timerservo.X/servo.c">https://github.com/7Robot/Eurobot-2012/blob/master/timerservo.X/servo.c</a></p>
<p>
	Et un exemple d&#39;utilisation :</p>
<p>
	<a href="https://github.com/7Robot/Eurobot-2012/blob/master/timerservo.X/main.c">https://github.com/7Robot/Eurobot-2012/blob/master/timerservo.X/main.c</a></p>
<p>
	Vous avez trois fonctions &agrave; utiliser :</p>
<p>
	-&nbsp;<strong>OpenServo(<em>nombre</em>);</strong>&nbsp;pour choisir combien de servos vous utiliserez et initialiser les interruptions. Par exemple pour <em>nombre</em>=3 les pins &agrave; connecter sont RB0 pour le servo 1, RB1 pour le servo 2 et RB2 pour le servo 3. Le nombre maximum de servos pouvant &ecirc;tre utilis&eacute; en m&ecirc;me temps est de 8.</p>
<p>
	-&nbsp;<strong>InterruptServo();</strong> &agrave; appeller quelque part dans la routine de traitement des interruptions. Par d&eacute;faut il s&#39;agit de celle de priorit&eacute; haute.</p>
<p>
	-&nbsp;<strong>WriteServo(<em>servo</em>, <em>angle</em>);</strong> pour donner la consigne <em>angle</em> &agrave; la pin num&eacute;ro <em>servo</em>.</p>
<p>
	Et voil&agrave;.</p>
