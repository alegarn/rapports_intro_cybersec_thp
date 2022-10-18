# Cybersécurité - Jour 1

## Objectif
- Pouvoir hacker notre premier email: baptiste.fraikinfranklin@laposte.net

## Méthodologie
- Utiliser les ressources de l'osint framework
- HaveIBeenPwnd
- google.com / autre moteur de recherche

## Ressources
- https://osintframework.com/: Open-source intelligence framework, contient des ressources gratuites ou payantes ouvertes permettant de trouver des informations sur un ensemble de brêches.
- https://haveibeenpwned.com/: Check if your email or phone is in a data breach

## Etapes
1 - ';--have i been pwned?
- à l'aide du site https://haveibeenpwned.com/, ajouter baptiste.fraikinfranklin@laposte.net sur le formulaire de la page d'accueil 
- Faire un clic sur le bouton "pwned?"

Les informations obtenues:

- baptiste.fraikinfranklin@laposte.net apparaît sur 3 brêches:
	- le nom: ce qui est compromis
	- Armor Games (2019): Bios, Dates of birth, Email addresses, Genders, Geographic locations, IP addresses, Passwords, Usernames
	- Coupon Mom / Armor Games (2014): Email addresses, Passwords
	- MindJolt: Dates of birth, Email addresses, Names
- il faut chercher les fichiers de Coupon Mom / Armor Games, qui contiennent des mots de passes.

2 - osintframework
- Page principale https://osintframework.com/, suivre les liens Email Address -> Breach Data (Brêches)
	- Tester les sites: ajouter baptiste.fraikinfranklin@laposte.net aux barres de recherches (Intelligence X)

- Intelligence X(https://intelx.io/):
	- Found 5 Text Files, 3 CSV Files: Zabugour.rar/185.txt; armorgames.com_2019.01.rar/ArmorGames.com_01-2019.csv ; Database.txt; Armorgames.com7.7kk.txt; Couponmom.com/couponmom2014.txt; ArmorGames.7z/ArmorGames.csv ; domain-split-combos.zip/combos.vip-laposte.net.txt ; MindJolt.7z/Data/Mindjolt.csv

3 - Où trouver les données?
- Moteur de recherche: utiliser les données pour faire des recherches.

- écrire "download breach armor games 2014", valider
	- site: https://phcracker.net/tags/leaked/ -> plusieurs liens vers certains fichiers à télécharger, celui qiui fonctionne: nitroflare
		- 
- écrire "Coupon Mom / Armor Games Database Leaked 8 February 2014 - Free Download", valider
	- https://thejavasea.com/threads/coupon-mom-armor-games-database-leaked-8-february-2014-free-download.1693/: -> plusieurs liens: ddownload / nitroflare (télécharger les données à partir d'un des liens)
	- https://breached.to/Thread-Armor-Games-Database-Leaked-Download: leak d'armor games 2019, il faut s'inscrire et télécharger

- écrire "Armor Games Database breach download", valider
	- https://github.com/hacxx-underground/Files/blob/main/ArmorGames.com%20-%20Full%20Dehashed%20-%20Leaked%20June%202019%20-%20FREE%20Download: un lien nitroflare
- résultats:
	- https://phcracker.net/tags/leaked/
- s'incrire sur breached.to
	- chercher avec "leak Coupon Mom Armor Games"
	- https://breached.to/Thread-Coupon-Mom-Armor-Games-11M-2014-Leak--21547?highlight=armor+games: CouponMom-ArmorGames-2014.txt

4 - Trouver un mot de passe

Utiliser le fichier: CouponMom-ArmorGames-2014.txt

Pour l'ouvrir: télécharger Notepad ++ si vous n'arrivez pas à l'ouvrir avec Bloc-Note

Dans le fichier:
	- CTRL + F: baptiste.fraikinfranklin@laposte.net
	- cela révèle son mot de passe

Se rendre sur le site: https://armorgames.com/login
- Rentrer son login: baptiste.fraikinfranklin@laposte.net / mot de passe


5 - Sur quel autre site?

Page principale https://osintframework.com/, suivre les liens Email Address -> Email Verification
	- https://emailrep.io/ -> Simple Email Reputation: ajouter baptiste.fraikinfranklin@laposte.net aux barres de recherches
		- il y a un compte twitter
