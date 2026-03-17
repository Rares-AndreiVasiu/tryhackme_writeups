# Dev Diaries
I had to find hidden traces of a website developed by a freelancer who disappeared into thin air and let only the primary domain: **marvenly.com**

___

## Here is how I solved this challenge.
- At first I searched for this exact website in the AttackBox, but no luck.
- Then I tried to perform an analysis on the domain in the terminal

```bash
whois marvenly.com
```

- And got the following output (simplified): 
Domain created: January 8, 2026
Last updated: January 29, 2026
Registrar: NameCheap

> This means that the domain registered development in January this year.

- Okay then I tried to enumerate the dns with the main domain:

```bash
dig marvenly.com A
dig marvenly.com AAAA
dig marvenly.com MX
```
> No results for A, nor AAAA, but I got 5 responses for mail servers which means the root domain has no web hosting running.

- I tried to find certificate logs to find something:

```bash
curl "https://crt.sh/?q=marvenly.com&output=json"
```

> Oh boy, I hit the jackpot. I got 2 subdomains active: **admin.marvenly.com** and **uat-testing.marvenly.com**. A simple search in the web browser and both open nicely.

- Scrolling to the bottom of the page i get the username for copyright: notvibecoder23.
- I searched on github for this usernam and found it, only one result at this moment.
- I found the repository: **marvenly_site** on this github profile.
- Then I search through the commits and found the flag THM{}.
- Also the commit for the "removing the source code" was also hidden in plain sight, so no trouble so far.
- I cloned the project locally, ran the website in my browser and I have looked in the consolve, storage and so on to find the email.
- Then I checked the logs (lucky me someone commented this on that commit) with

```bash
git log
```
> Scrolling through this extensive output i found the email of the freelancer.
