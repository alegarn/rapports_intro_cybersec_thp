# Intro à la cybersécurité - 2

## Objectif
- hacker sur un site de blog: 
a. Découvrir un site qui parle de sécu qui est rattaché à THP.
b. Ensuite se connecter sur ce blog en tant qu'utilisateur.
 
## Outils
- DNS crawling/discovery (Google dorks / crt.sh)
- Fuzzing 

## Etapes

1 - thehackingproject.org

Pas de contenu sur la cybersécurité qui apparaît.

2 - Crawler les DNS thehackingproject.org

Google Dork:
- à l'adresse: google.com, mettre dans la barre de recherche: "site:*.@thehackingproject.org -www"
Tous les sous-domaines à l'adresse thehackingproject.org, que google a référencé seront présents.

L'alternative:
- Naviguateur: ajouter "https://crt.sh/?q=thehackingproject.org" puis valider dans la barre de recherche.
Plein de sous-domaines, contenant aussi : "secu.thehackingproject.org"

3 - Comment trouver un utilisateur

Pas de lien pour se login, juste un article.
Trouver des articles sur le site, "https://secu.thehackingproject.org/adminsys3euetzx/la-vie-est-dangereuse-quand-elle-nest-pas-securise/".
Dans l'article, 0 nom d'utilisateur, 0 indice... Le lien donne l'indice "adminsys3euetzx/nom-de-l-article", nous faisant penser "ce pourrait être l'utilisateur en question".

4 - Comment utiliser ce nom d'utilisateur pour se connecter

Sans lien de login, c'est compliqué. 
Technique de recherche: fuzzing. En envoyant des requêtes sur le serveur "secu.thehackingproject.org", pour tester la présence de pages cachées, l'étude des réponses renvoyées (200, 404, 302...) pourrait nous donner ce que nous cherchons.
Outils: gobuster
- L'installer: (linux/ubuntu) dans le terminal "sudo apt  install golang-go" puis "sudo apt install gobuster"
- Utilisation: pour tester de manière automatique s'il y a une page cachée, télécharger une "wordlist", le fichier texte avec plein de mots afin de tester un maximum de possibilitées. 
- Utiliser un des liens:
	- https://blog.sec-it.fr/en/2021/03/02/web-wordlists/
	- https://wordlists.assetnote.io/
	- https://raw.githubusercontent.com/aels/subdirectories-discover/main/dsstorewordlist.txt
	- https://github.com/galehrizky/wp-brute-xmlrpc/blob/master/wordlist.txt
	- https://github.com/clem9669/wordlists/blob/master/Web/discovery.txt
- Pour utiliser gobuster: utiliser le terminal "gobuster -u secu.thehackingproject.org  -w  path/allant/à/discovery.txt"
- Un des résultats: "/jeanette (Status: 302)"
- écrire "https://secu.thehackingproject.org/jeanette" (barre de recherche, votre naviguateur) Voici sa page de connexion!
- Lorsque l'on teste "adminsys3euetzx" (username), et "cequonveut" (son mot de passe): "Erreur : ce mot de passe ne correspond pas à l’identifiant adminsys3EuEtzX." adminsys3EuEtzX: le nom d'un utilisateur!

5 - Maintenant notre mot de passe

Technique de recherche: fuzzing.
Outils: gobuster
- lors de l'utilisation du fuzzing, il y a un lien intéressant: https://secu.thehackingproject.org/sitemap.xml : réponse 200 (il répond)
- https://secu.thehackingproject.org/sitemap.xml -> ouvrir le lien: https://secu.thehackingproject.org/addl-sitemap.xml -> cliquer sur "https://pastebin.com/BfewKTSd"
- Ce site contient: Login : adminsys3EuEtzX / Mot de passe : c3Kpa8c!mf2HQ%NM6w$kvyo*
- Sur https://secu.thehackingproject.org/jeanette, mettre adminsys3EuEtzX (login), c3Kpa8c!mf2HQ%NM6w$kvyo* (mot de passe)
- Bien joué!
