+++
title = "Utilisation du port série"
dater = "01 Septembre 2011"
author = "Maxime"
+++

<h2>
	Pr&eacute;sentation</h2>
<p>
	Le port s&eacute;rie commun&eacute;ment appell&eacute; liaison RS232 est une valeur sure en robotique amateur malgr&egrave;s<img src="/img/articles/portserie.jpg" style="float:right;margin:15px" /> son &acirc;ge. Il offre des supports de communication robustes et simples &agrave; mettre en oeuvre.</p>
<p>
	Etant donn&eacute; que ce bus est &quot;s&eacute;rie&quot;, les informations sont envoy&eacute;es bit &agrave; bit, &quot;&agrave; la chaine&quot; (on parle de trames), contrairement au port parall&egrave;le. Il en r&eacute;sulte un d&eacute;bit moins important mais n&eacute;anmoins suffisant pour nos applications.</p>
<p>
	Deux modes de fonctionnement sont possibles pour le port s&eacute;rie. Le mode est choisi en fonction des besoins. A chaque mode correspondent des pisns ur le connecteur DB9 ci contre.</p>
<ol type="disc">
	<li>
		Le mode synchrone</li>
</ol>
<p>
	Electriquement, le sch&eacute;ma se r&eacute;sume &agrave; trois fils : un pour l&#39;horloge,&nbsp; un pour les donn&eacute;es et une masse commune (comme pour le bus I&sup2;C). Ce mode a l&#39;avantage de mettre plusieurs p&eacute;riph&eacute;riques en s&eacute;rie via une relation m&acirc;itre esclave. Cependant bien que semblable &agrave; l&#39;I&sup2;C, il n&#39;offre pas les m&ecirc;mes fonctionnalit&eacute;s : tout est &agrave; reprendre (arbitrage du bus, adressage...). De plus il fonctionne en half duplex : deux p&eacute;riph&eacute;riques ne peuvent pas parler en m&ecirc;me temps.</p>
<p>
	TODO : sch&eacute;ma</p>
<p>
	En robotique, nous pr&eacute;f&eacute;rons utiliser le bus I&sup2;C plut&ocirc;t que du s&eacute;rie asynchrone lorqu&#39;il s&#39;agit de faire communiquer plusieurs p&eacute;riph&eacute;riques en s&eacute;rie, les fonctions mat&eacute;rielles comme l&#39;adressage et l&#39;arbitrage du bus sont tr&egrave;s appr&eacute;ci&eacute;es.</p>
<ol type="disc">
	<li>
		Le mode asynchrone</li>
</ol>
<p>
	Il <strong>s&#39;agit de la plus large application</strong> du port s&eacute;rie en robotique. L&agrave; encore, le sch&eacute;ma &eacute;lectrique se r&eacute;sume &agrave; trois fils : un pour &eacute;mettre les donn&eacute;es (TX), un pour les recevoir (RX), et une masse.</p>
<p>
	Nous n&#39;entrons pas ici dans les d&eacute;tails du fonctionnement de la liaison s&eacute;rie comme la gestion de l&#39;horloge et le format des trames. Vous pouvez consulter :</p>
<p>
	TODO : liens</p>
<p>
	L&#39;informaticien peut faire abstraction de ces informations en consid&eacute;rant qu&#39;il ne s&#39;agit que de transit de chaines de caract&egrave;res d&#39;un buffer A bers un buffer B.</p>
<p>
	Je tiens cependant &agrave; mettre en &eacute;vidence l&#39;importance du <strong>croisement </strong>de la ligne. En effet, en mode asynchrone, non seulement il n&#39;y a<strong> que deux p&eacute;riph&eacute;riques</strong> qui peuvent communiquer ensembles et pour ce faire il faut que l&#39;&eacute;mission de l&#39;un de fasse sur le r&eacute;cepteur de l&#39;autre et vice ver&ccedil;a : on parle de ligne crois&eacute;e. Ceci permet une liaison <strong>full duplex</strong> : les deux p&eacute;riph&eacute;riques peuvent parler en m&ecirc;me temps.</p>
<p>
	TODO : sch&eacute;ma</p>
<h2>
	Utilisation logicielle du port s&eacute;rie</h2>
<p>
	TODO : pr&eacute;sentation de la librairie C utilis&eacute;e...</p>
<p>
	&nbsp;</p>
