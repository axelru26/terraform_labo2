# Explications de l’attaque
## Choses à savoir
Nous partons du principe que nous savons déjà le nom et l’ip de la machine en question.
La vulnérabilité est un id/mdp faible. Nous procèderons donc à un attaque brute force par dictionnaire.

## Etapes de l'attaque
1) Nous utiliserons Metasploit (sous kali linux) qui est un logiciel permettant de faire une multitude d’attaque répertorié par les vulnérabilités cve
2) Une fois Metasploit ouvert, nous paramètrerons :
* L’attaque à 3 threads afin de ne pas trop saturer la machine de requête et risquer d’être bloqué.
* La machine hôte (rhosts) à l’ip de la machine cible
* « STOP ON SUCCESSE », sur TRUE afin d’arrêter l’attaque dès qu’elle réussit.
* « VERBOSE », sur TRUE afin d’afficher toutes output créer par l’attaque
* le userpasse_file qui est le file directory d’un dictionnaire texte d’une paire d’id et mdp
3) Dès que ces paramètres sont mis en place, nous lancerons l’attaque.
4) Une fois l’attaque terminée nous obtenons la confirmation de succès de l’attaque , l’id , le mdp trouvé et une connexion établie avec la vm.
