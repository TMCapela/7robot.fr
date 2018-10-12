+++
title = "Convertisseurs CAN↔UART"
dater = "01 Décembre 2011"
author = "Elie"
+++

<p>
	Protocole CAN :</p>
<p>
	11 bits d&#39;identifiant</p>
<p>
	0 &agrave; 8 octets de donn&eacute;e</p>
<p>
	&nbsp;</p>
<p>
	Protocole UART :</p>
<p>
	[ FD ] [ size | 0 | id10..8 ] [ id7..0] [ M1 ] [ M2] &hellip; [ M8 ] [ BF ]</p>
<p>
	&nbsp;</p>
<p>
	(FD = 11111101)</p>
<p>
	(BF = 10111111)</p>
<p>
	&nbsp;</p>
<p>
	&nbsp;</p>
