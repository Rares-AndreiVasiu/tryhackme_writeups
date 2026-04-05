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

## 3. At what time did the suspicious action take place in the route planning system on March 25th, 2026?

- We check the .csv file `access_log.csv` and look at the timestamps on 25th of March.
- We notice the following odd action of *Export* from user BR-0291 of a sensitive route pdf file
- All other actions performed by other users was of type view/edit.
- User **BR-0291** took this action at 22, which is another red flag in our pursuit. Who exports a routing file at that time in night?
- So this user planned ahead of time his criminal actions, because at the head of the csv file he failed to authenticate on the 24th of March.
- Then, on the 27th maybe an admin restricted access to this file.

*22:14:09*

## 4. What is the employee ID of the person who sent the anonymous email?

- BR-0312 was in the system at 23:41 on March 25, just after BR-0291's suspicious EXPORT at 22:14
- BR-0312 is a Dispatch Operator in the employees.csv file
- BR-0312 was also active very late on 24th of March at23:12, suggesting they regularly work late shifts and would notice after-hours anomalies.
- there is also the sense of untrust in the internal system, so as a non it person he went straight to the local press: _I do not know who to trust inside the company right now._
  
## 5. What is the employee ID of the employee responsible for leaking the shipment details?

From the 3rd question in our investigation the culprit is BR-0291
