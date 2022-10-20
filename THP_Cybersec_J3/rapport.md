# Cybersécurité - Jour 3 (résumé)

## Objectif
- Vous allez devoir craquer le hash d'un mot de passe grâce à un mot de passe que vous connaissez déjà et une attaque par dictionnaire.

## Méthodologie
- Méthodes de crackage de mot de passe

## Outils
- John the Ripper (tester les hash)
- wordlist-generator
- bopscrk (faire une liste, utilisant des infos qui sont personnelles, recombiner les mots)

## Ressources
- https://fr.planetcalc.com/7956/
- https://www.tunnelsup.com/hash-analyzer/
- https://md5decrypt.net/en/HashFinder/
- https://www.dcode.fr/hash-identifier
- https://github.com/clem9669/wordlists/blob/master/Web/decouverte.txt
- https://github.com/openwall/john / https://linuxhint.com/john_ripper_ubuntu/
- https://realpython.com/python-virtual-environments-a-primer/#how-can-you-work-with-a-python-virtual-environment
- https://github.com/r3nt0n/bopscrk
- https://hashes.com/en/generate/hash

## Etapes
1 - échauffement
- https://fr.planetcalc.com/7956/ -> puis écrire le hash 

2 - python venv / bopscrk
- https://github.com/r3nt0n/bopscrk
- bopscrk -i -> "Some other relevant words (comma-separated) >>> tigres"


3 - J.t.R.
- john --wordlist=decouverte.txt --rules  password.txt --format=whirlpool --fork=8
- john --show password.txt 
