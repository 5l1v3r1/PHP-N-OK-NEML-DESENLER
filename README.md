# PHP-N-OK-NEML-DESENLER
Mail Yakalama --- URL Yakalama --- Tarih Yakalama --- Plaka Yakalama --- Style Atlama --- Telefon Numarası Yakalama
<!DOCTYPE html>
<html lang="tr-TR">
<head>
	<meta http-equiv="Content-Type" content="text/html ; charset=utf-8">
	<meta http-equiv="Content-Language" content="tr">
	<meta charset="utf-8">

	<script type="text/javascript" src="javaeklentisi.js" language="javascript"></script>
	<title></title> 
</head>

<body>

	<?php

	echo "*******************ÖRNEK 1*******************<br/><br/>";

	$metin = "<span style='color:red'>Hasan Kacar</span>";
	$desen = "/<\/?[^>]+>/";
	$degisen = "";
	$sonuc = preg_replace($desen, $degisen, $metin);

	echo "Metin : " . $metin . "<br/>";
	echo "Yeni Metin : " . $sonuc;


	echo "<br/><br/>*******************ÖRNEK 2*******************<br/><br/>";

	$metin2 = "Hasan Kacar Tel : 0536 706 32 30";
	$desen2 = "/ 0?[0-9]{3}\s?[0-9]{3}\s?[0-9]{2}\s?[0-9]{2}/";

	preg_match_all($desen2, $metin2, $sonuc2);

	echo "Metin : " . $metin2 . "<br/>";
	echo "<pre>";
	print_r($sonuc2);
	echo "</pre>";

	echo "<br/><br/>*******************ÖRNEK 3*******************<br/><br/>";

	$metin3 = "0536 706 32 30";
	$desen3 = "/^0?[0-9]{3}\s?[0-9]{3}\s?[0-9]{2}\s?[0-9]{2}$/";//^ ve $ => Başında veya sonunda rakam dışında bir şey varsa telefon numarası degildir demesini sağlar.

	$sonuc3 = preg_match_all($desen3 , $metin3);

	if($sonuc3 == 1)
	{
		echo "Girilen Deger (" . $metin3 . ") Bir Telefon Numarasıdır.";
	}
	else
	{
		echo "Girilen Deger (" . $metin3 . ") Bir Telefon Numarası Degildir.";
	}
	

	echo "<br/><br/>*******************ÖRNEK 4*******************<br/><br/>";

	$metin4 = "Hasan Kacar . Dogum Tarihi : 01.01.1999 dur.";
	$desen4 = "/ \d{1,2}\.\d{1,2}\.\d{4} /";

	preg_match_all($desen4, $metin4, $sonuc4);

	echo "Metin : " . $metin4 . "<br/>";
	echo "<pre>";
	print_r($sonuc4);
	echo "</pre>";


	echo "<br/><br/>*******************ÖRNEK 5*******************<br/><br/>";

	$metin5 = "Hasan Kacar . Araç Plakası : 35 AU 6490 dır.";
	$desen5 = "/ \d{2}\s?[A-Z]{1,3}\s?\d{2,4} /";

	preg_match_all($desen5, $metin5, $sonuc5);

	echo "Metin : " . $metin5 . "<br/>";
	echo "<pre>";
	print_r($sonuc5);
	echo "</pre>";

	echo "<br/><br/>*******************ÖRNEK 6*******************<br/><br/>";

	$metin6 = "Hasan Kacar PAÜ , Denizli , Domain : https://www.HasanKacar.com.tr adresidir.";
	$desen6 = "/ (http(s)?:\/\/.)?(www\.)?[a-zA-Z0-9\.\:\+\~\#\-\_\+\@\=]{2,256}\.[a-z]{2,6}\b([a-zA-Z0-9\.\:\+\~\#\-\_\+\@]*)+ /";//Web de en çok kullanılan URL deseni....

	preg_match_all($desen6 , $metin6, $sonuc6);

	echo "Metin : " . $metin6 . "<br/>";
	echo "<pre>";
	print_r($sonuc6);
	echo "</pre>";

	echo "<br/><br/>*******************ÖRNEK 7*******************<br/><br/>";

	$metin7 = "Hasan Kacar . E-Mail : HFBKacar_1907@gmail.com.tr adresidir.";
	$desen7 = "/ (\w+)@([a-z]+)\.([a-z]{2,})(\.[a-z]{2}|) /";

	preg_match_all($desen7, $metin7, $sonuc7);

	echo "Metin : " . $metin7 . "<br/>";
	echo "<pre>";
	print_r($sonuc7);
	echo "</pre>";

	echo "<br/><br/>*******************ÖRNEK 8*******************<br/><br/>";

	$metin8 = "Hasan Kacar . E-Mail : HFBKacar_1907@gmail.com.tr adresidir.";
	$desen8 = "/\s+(([^<>()[\]\\.,;:\s@\"]+(\.[^<>()[\]\\.,;:\s@\"]+)*)|(\".+\"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))\s+/";

	//Hasan.Kacar_1907@gmail.com.tr

	/*

	****************DESEN AÇIKLAMASI****************

	Hasan için Grup;
	***[^<>()[\]\\.,;:\s@\"]+

	.Kacar_1907 için Grup;
	***(\.[^<>()[\]\\.,;:\s@\"]+)*)|(\".+\"))

	@ İşaretini Koyduk....

	
	gmail.com.tr için Grup;
	***((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))

	\s+ => 1 vaye 1 den fazla başta veya sonda boşluk varsa onlar için konulmuştur.....

	*/

	preg_match_all($desen8, $metin8, $sonuc8);

	echo "Metin : " . $metin8 . "<br/>";
	echo "Desen : " . $desen8 . "<br/>";//BU DESEN ÇOK ÖNEMLİ EN İYİ VE EN ÇOK KULLANILAN E-MAİL YAKALAMA DESENİDİR.....
	echo "<pre>";
	print_r($sonuc8);
	echo "</pre>";


	?>

</body>
</html>
