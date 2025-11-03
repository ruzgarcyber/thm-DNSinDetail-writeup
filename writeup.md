## TryHackMe DNS in Detail
> Merhaba millet! Bugün sizlere çözmüş olduğum **DNS in Detail** Lab'ını writeup şeklinde sunacağım.

## Bilgiler.
- Lab adı: **DNS in Detail**
- Zorluk: **Kolay**
- Writeup yazarı: **Rüzgar Umut Gündoğan**
- Writeup yazılma tarihi: **3.11.2025**

## Lab'dan öğrendiklerim.
- DNS(Domain Name System)'in ne olduğunu öğrendim.
- Domain Hierarchy'inin ne olduğunu ve türlerini öğrendim(Subdomain, Second-Level Domain, TLD (Top-Level Domain)).
- DNS Record Types, yani DNS Rekor Türlerini öğrendim(A, AAAA, CNAME, MX, TXT)

## Lab Sırasında yaptıklarım.
*1.* TryHackMe'inin içindeki web siteyi açtım.

*2.* İlk olarak, shop.website.thm adlı websiteyi CNAME Record'u ile sorguladım. Ve shops.myshopify.com adlı siteyi bularak Flag'i bulmuş oldum.[CEVAP; shops.myshopify.com]
> Komut; user@thm:~$ nslookup --type=CNAME shop.website.thm
Server: 127.0.0.53
Address: 127.0.0.53#53
Non-authoritative answer:
shop.website.thm canonical name = shops.myshopify.com

*3.* Sonrasında, website.thm adlı sitenin TXT Record'unu sorguladım. Ve FLAG'i bulmuş oldum [CEVAP; THM{7012BBA60997F35A9516C2E16D2944FF}].
> Komut; user@thm:~$ nslookup --type=TXT website.thm
Server: 127.0.0.53
Address: 127.0.0.53#53
Non-authoritative answer:
website.thm text = "THM{7012BBA60997F35A9516C2E16D2944FF}"

*4.* Ondan sonra, website.thm adlı websitenin sayısal öncelik değerini buldum [CEVAP; 30].
> Komut; 
user@thm:~$ nslookup --type=MX website.thm
Server: 127.0.0.53
Address: 127.0.0.53#53
Non-authoritative answer:
website.thm mail exchanger = 30 alt4.aspmx.l.google.com

*5.* En son olarak, www.website.thm adlı websitenin **A Record**'unu alarak IP adresini bulmuş oldum [CEVAP; 10.10.10.10].
> Komut;
user@thm:~$ nslookup --type=A www.website.thm
Server: 127.0.0.53
Address: 127.0.0.53#53
Non-authoritative answer:
Name: www.website.thm
Address: 10.10.10.10

## Referanslar.
- [TryHackMe](https://www.tryhackme.com)
- [TryHackMe | DNS in Detail](https://tryhackme.com/room/dnsindetail)

## Teşekkür.
> Buraya kadar gelip yazmış olduğum writeup'ı okuduğunuz için çok teşekkür ederim. Tekrardan farklı bir Writeup'da görüşmek üzere...
