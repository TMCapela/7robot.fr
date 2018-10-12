+++
title = "A la découverte du Bus CAN"
dater = "30 Octobre 2011"
author = "Jeremie"
+++

<h2>
	I - Introduction</h2>
<p>
	<span>Le bus <strong>CAN</strong> <em>(Control Area Network)</em> est un bus de communication s&eacute;rie, principalement con&ccedil;u pour mettre en reseau diverses cartes &eacute;l&eacute;ctroniques.</span><br />
	<span>Il est utilis&eacute; dans l&rsquo;automobile pour faire dialoguer les divers systemes de contr&ocirc;le ou de commande : ABS, systeme de freinage, de supenssion etc.</span>..</p>
<h2>
	<img src="/img/articles/canAuto.png" /></h2>
<h3>
	1.1-Comment imaginer une conversation CAN ?</h3>
<p>
	<span>Pour imager le protocole CAN on peut faire l&#39;analogie avec une discution que vous avez entre amis. Et oui, vous utilisez le m&ecirc;me formalisme que le CAN chaque jour (enfin c&#39;est lui qui utilise le m&ecirc;me que vous...).</span><br />
	<span>En effet avant de parler avec vos amis vous annoncez le theme de votre message c&rsquo;est <strong>l&rsquo;identifiant</strong>, ensuite certains de vos amis ne sont pas interess&eacute;s par votre message et ne vous ecouterons pas : ils continurons leurs activit&eacute;s. Ceux qui veulent vous &eacute;couter vous &eacute;coutent et vous commencez &agrave; parler (en respectant des regles).&nbsp;</span>Imaginez que lors de votre discussion en cours, un autre amis a un message tr&egrave;s urgent &agrave; vous transmettre &nbsp;(IL Y A LE FEU, SORTEZ !) vous allez arr&ecirc;ter votre discusion, l&rsquo;ecouter et courir en lieux s&ucirc;rs. Une fois hors de danger &nbsp;vous aller reprendre votre conversation l&agrave; ou vous l&rsquo;aviez laiss&eacute;e .</p>
<p>
	<br />
	<span>R&eacute;sumons, dans un protocole <strong>CAN</strong>, tout les p&eacute;riph&eacute;riques sont au m&ecirc;me niveau (pas de relation m&acirc;itre-esclave) &nbsp;seul les messages sont class&eacute; par ordre de priorit&eacute;s. Chaque message est prec&eacute;d&eacute; d&rsquo;un identifiant, vous n&#39;&eacute;coutez donc que les messages qui vous int&eacute;ressent (comme dans la vraie vie !).</span></p>
<p>
	&nbsp;</p>
<h3>
	<span>1.3 Le CAN et un peu de th&eacute;orie</span></h3>
<p>
	<span>Le bus <strong>CAN</strong> est constituer de 2 fils termin&eacute;s par des r&eacute;sistance de terminaisons. Un grand nombre de periph&eacute;riques peuvent venir se raccorder au bus.</span></p>
<p>
	<span><img src="/img/articles/canStruct.png" /></span></p>
<h4>
	<span>La structure d&rsquo;un trame CAN :</span></h4>
<ol type="disc">
	<li>
		<span>ID</span> (11 bits)</li>
	<li>
		<span>Message</span> (8 octets)</li>
	<li>
		<span>Plein d&rsquo;autre chose pour contoler les erreurs</span></li>
</ol>
<p>
	<img src="/img/articles/canTram.png" /></p>
<h4>
	Les signaux :</h4>
<p>
	<span>Les signaux ne sont pas TTL , mais on s&rsquo;interresse &agrave; la diff&eacute;rence de tension entre CANH et CANL se qui rend le bus tr&egrave;s stables au divers perturbations (car si on modifie de la m&ecirc;me mani&egrave;re la tension des 2 canaux la diff&eacute;rence reste inchang&eacute;e)</span></p>
<p>
	<img src="/img/articles/canSignal.png" /></p>
<h4>
	Le materiel :</h4>
<p>
	<span>Pour r&eacute;aliser un periph&eacute;rique <strong>CAN</strong> nous avons donc besoin :</span></p>
<ol type="disc">
	<li>
		<span>d&#39;un transcrivers pour adapter les signaux sur le bus</span></li>
	<li>
		<span>d&#39;un controleur <strong>CAN</strong> pour g&eacute;rer les regles d&rsquo;emmision et de la r&eacute;ception </span></li>
	<li>
		<span>d&rsquo;un microcontroleur </span></li>
</ol>
<h2>
	<img src="/img/articles/canArchi.png" /></h2>
<h2>
	&nbsp;</h2>
<h2>
	II- Le Bus CAN et les PIC&nbsp;</h2>
<h3>
	2.1- La partie mat&eacute;riel</h3>
<p>
	<span>On a vue que l&rsquo;on a besoin :</span></p>
<ul>
	<li>
		<p>
			<span>d&#39;un controleurs <strong>CAN</strong> pour la gestion du protocole</span></p>
	</li>
	<li>
		<p>
			<span>d&#39;un transcriver pour adapter les niveaux de tension</span></p>
	</li>
</ul>
<p>
	<span>Les <strong>pic 18FXX80</strong> intergre materiellemnt le contoleur <strong>CAN</strong> , cependant il n&#39;integre pas de transcriver, il faut donc avoir un transcriver externe <em>(MCP2551 de Microhip) </em>.</span><br />
	<span>Il est conseill&eacute; d&rsquo;avoir un <strong>quartz</strong> cristal externe, pour avoir une horloge stable</span><br />
	&nbsp;</p>
<h3>
	2.2 La partie logiciel</h3>
<p>
	Dans la datasheet du pic nous avons tous les registre du<strong> CAN </strong>dans la partie ECAN.<br />
	Cependant Microhip nous facilite les choses grace &agrave; sa librairie<strong> CAN</strong> ecrit pour les pic <strong>18FXX </strong>qui est compatible avec le compilteur <strong>C18.</strong></p>
<p>
	Nous avons donc &agrave; notre dispositon des fonctions en C, qui permettent<span> de g&eacute;r&eacute;es de mani&egrave;re tr&egrave;s intuitive le Bus <strong>CAN</strong></span><br />
	<span>Ces fonctions se regroupent suivant :</span></p>
<ol type="disc">
	<li>
		<p>
			<span>fonction li&eacute;es &agrave; la configurations du bus </span></p>
	</li>
	<li>
		<p>
			<span>fonctions li&eacute;es &agrave; l&rsquo;emmission de donn&eacute;e</span></p>
	</li>
	<li>
		<p>
			<span>fonctions li&eacute;es &agrave; la reception de donn&eacute;</span>e</p>
	</li>
	<li>
		<p>
			<span>fonctions li&eacute;es &agrave;&agrave; la gestion des erreurs</span></p>
	</li>
</ol>
<h3>
	<span>2.3- Notions de mask et de filtre </span></h3>
<p>
	<br />
	<span>Pour que un message arrive dans votre buffer de r&eacute;ception (possibilit&eacute; de declencher un interruption), il faut qu&rsquo;il soit accept&eacute; . Grace au mask vous pouver choisir quel bits de l&rsquo;identifiant doivent &ecirc;tre compar&eacute; avec le filtre pour que le message soit valid&eacute; et arrive dans votre buffer . </span><br />
	<span>Voici un exemple :</span></p>
<p>
	ID du message : 101001111<strong>101</strong></p>
<p>
	dans la config du PIC :<br />
	mask : 00000000<strong>111</strong><br />
	ex n&deg;1 de filtre: 110110000<strong>101</strong><br />
	ex n&deg;2 de filtre: 110110000<strong>111</strong></p>
<p>
	Dans l&#39;exemple n&deg;1 le on voit que les 3 premiers bits sont identiques, le message est accept&eacute;</p>
<p>
	Dans l&#39;exemple n&deg;2 le on voit que les 3 premiers bits sont diff&eacute;rents, le message est refuss&eacute;</p>
<p>
	<span>Avec les pic18F vous dispos&eacute; de 2 buffer de recptions, ayant un maks et des filtre qu&rsquo;ils leurs sont propre et que vous r&eacute;gler lors de la &nbsp;configuration du bus <strong>CAN</strong> du Pic .</span></p>
<h3>
	2.4- Schema</h3>
<p>
	<img src="/img/articles/canPic.png" /></p>
<p>
	&nbsp;</p>
<h2>
	III - Exemple de code</h2>
<p>
	&nbsp;</p>
<h2>
	IV - Liens et documentation</h2>
<p>
	Dans le fichier <strong><em>ressource.zip</em></strong> <a href="/img/articles/canRessource.zip">(cliquer pour le t&eacute;l&eacute;charger)</a>, nous avons regrouper toutes les documments qui nous ont aid&eacute; &agrave; mettre au point le Bus CAN sur PIC. Voici le d&eacute;taille :</p>
<ol type="disc">
	<li>
		Datasheet du PIC18F2680</li>
	<li>
		Datasheet du transcriver MCP2551</li>
	<li>
		Librairie CAN de microchip</li>
	<li>
		Exemple de r&eacute;alisation CAN (projet Robusta)</li>
</ol>
