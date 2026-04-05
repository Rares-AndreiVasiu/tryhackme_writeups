# Personal solution

## 1. Which VPN service was used to send the anonymous email from the .eml file?
- Opening `exhibit_a.eml` and reading the full header chain, the email was sent from `notmyname2847@gmail.com` to `redakce@novinybrno.cz` (a Czech news outlet).
 
- The critical header is the SMTP handshake line recorded by Gmail's servers:
 
```
Received: from [193.32.249.132] ([193.32.249.132])
        by smtp.gmail.com with ESMTPSA id
        4fb4d7f45d1cf-66e02d37620sm407278a12.2.2026.03.27.23.14.55
        for <redakce@novinybrno.cz>
```
 
- This is the IP address the sender's device used to authenticate with Gmail → before Gmail's own relay infrastructure takes over. This is the for real ip.

- All other `Received:` hops show Google infrastructure (`209.85.220.41`, etc.) and are just useless.
 
- Looking up this ip `193.32.249.132`:
 
- **ASN:** AS39351
- **Organisation:** 31173 Services AB
- **Geolocation:** Amsterdam, Netherlands
- **Flags:** VPN exit node detected
 
> [IPinfo.io — 193.32.249.132](https://ipinfo.io/193.32.249.132)
 
- 31173 Services (AS39351) is a Swedish hosting and network company.
- Searching for their known customers shows a  partnership with **Mullvad VPN**
 
- Mullvad hosts many of its owned servers through 31173 Services
- The `193.32.249.0/24` subnet is part of Mullvad's server infrastructure in Amsterdam
 
>  [Mullvad — About our servers](https://mullvad.net/en/help/server-list)  
>  [BusinessWire — Mullvad & 31173 Services partnership](https://www.businesswire.com/news/home/20160814005016/en/Mullvad-Amagicom-AB-Mullvad-emphasizes-VPN-security-with-server-upgrades)  
>  [bgp.tools — AS39351](https://bgp.tools/as/39351)  
>  [Scamalytics — 31173 Services AB](https://scamalytics.com/ip/isp/31173-services-ab)

## 2. What is the full street address of the petrol station where the missing vehicle was last seen?

-At first I searched for the orlean website to find out about official petrol stations (https://www.orlen.cz/stanice), because on google maps there might be some of them missing. So i filtered them based on LPG, as confirmed through the picture. 

- I searched across _D1_ for existing ones, but none matched the dash cam picture due to the lack of existance of the road sign with Brno and Olomouc.

![Dash cam footage](./exhibit_b.png)

- So i decided to investigate further the files provided in the archive. Consequently I stumbled upon the ecta_memo.pdf file, where i found out this interesting insight: **_March 2026, a dashcam SD card was recovered from a vehicle stopped for an unrelated traffic matter near Hulín._**. This is our lead, so I opened up
google maps and searched for orlen  petrol stations. Luckily there was only one in that region:

![Orlen Hulin](./orlen.png)

- Then i copied the address from google maps.
