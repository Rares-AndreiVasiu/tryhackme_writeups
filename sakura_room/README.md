# Sakura

## INTRODUCTION
- type __Let's go!__ as the answer

***

## TIP-OFF
- in order to find the username of the the attacker, I have downloaded the .svg
image.
- then perform a simple _strings sakurapwnedletter.svg | head_ command in your
terminal emulator of choice.
- ![screenshot for results](images/attacker_username.png)
- therefore, the attacker's username is ~~SakuraSnowAngelAiko~~

## RECONNAISSANCE
- if we levrege our google dorking skills, we may search for the username 
as follows _intext:"SakuraSnowAngelAiko"_.
- skimming through the results, we stumble across a her github profile (https://github.com/sakurasnowangelaiko?tab=repositories)
- in her github pinned repos we observe a __PGP__ entitled project.
- the attacker managed to store their public key in the repository
- a PGP key ( Pretty Good Privacy) is an encryption system using both a public
and private key. It ensures secure communication by allowing only the wanted
recicipients to read the conversations.
- then we copy paste this text into _cyberchef.org_ and select __From Base64__
recipe.
- ![screenshot from cyberchef](images/attacker_email.png) 
- and we got the attacker's email: ~~SakuraSnowAngel83@protonmail.com~~
