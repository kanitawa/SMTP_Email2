# SMTP_Email2
LabVIEWから.NETを利用してSMTPプロトコルでメール送信をおこなうVI

## 概要
[LabVIEW](http://www.ni.com/ja-jp/shop/labview.html)の「開発システム」以上のエディションには、「データ通信」->「プロトコル」->「[SMTP Eメール](http://zone.ni.com/reference/ja-XX/help/371361P-0112/lvcomm/smtp_client/)」VIがあり（以下、これを「組み込みのSMTP EメールVI」と呼ぶ）、LabVIEWからSMTPサーバにEメールを送信することができます。

しかし、この「組み込みのSMTP EメールVI」には、
1. [「```Date```」ヘッダの曜日がおかしい](http://bananawani-mc.blogspot.jp/2018/01/n.html)
2. 本文がテキストしか含まなくても「```Content-Type: multipart/mixed```」になる

という問題点があります（*2015*, *2015 sp1* および *2017* で確認）。

ほとんどのSMTPサーバプログラムは不正なヘッダを上書きしてくれますので、上記1が目に見える形で問題になることはないでしょう。
また、ほとんどのメールクライアントはMIMEマルチパートを正しく表示してくれますので、上記2も問題にはなりません。

ただ、***あまり気分の良いものではありません*** :-P

そこで、.NET Frameworkを利用して、上記問題のないSMTP Eメール送信VI「***SMTP_Email2***」を作成しました。

## 環境
+ LabVIEW2015 sp1（32bit 日本語版）
+ Windows10 pro（64bit）
+ .NET Framework（ver.4以上）

使用している.NETクラスは「[SmtpClient クラス](https://msdn.microsoft.com/ja-jp/library/system.net.mail.smtpclient(v=vs.110).aspx)」と「[MailMessage クラス](https://msdn.microsoft.com/ja-jp/library/system.net.mail.mailmessage(v=vs.110).aspx)」の２つです。これらは.NET ver.2からのクラスですので、古い.NETにも移植できると思います。

## インストール
「src-ja」以下のVIをコピーするだけです。各VIに依存関係はありませんので、必要なVIだけをコピーすることができます。

## 使い方
「組み込みのSMTP EメールVI」と、構成・制御記名・端子位置を互換にしてありますので、迷うこと無く使えると思います。

![簡単な使用例](https://user-images.githubusercontent.com/26862256/35136585-c414a53c-fd27-11e7-9c2d-fc217e7e681b.png)


## ライセンス
これらのVIはMITライセンスに則り公開されています（LICENSE.txtを参照）。
