### (Je n'ai pas encore corrigé les fautes d'orthographe divers)
## Général
#### > IP (Internet protocol)
- Identifie chaque appareil sur internet
- Coder sur 4 octets (32 bits)

##### > Les differentes classes d'IP :
- Classe A : (gros réseau)
  - 1 octet pour identifié le réseau
  - 3 octets pour identifié les machines
  - 16 777 214 adresses possible
  - Commence toujours par la suite de bits 0, donc compris entre 0 et 127, mais certaines adresses sont réservées à des usages particuliers.
  - Plage d'adresse de 0.0.0.0 à 127.255.255.255
- Classe B : (réseau moyen)
  - 2 octet pour identifié le réseau
  - 2 octets pour identifié les machines
  - 65535 adresses possible
  - Commence toujours par la suite de bits 10, donc compris entre 128 et 191.
  - Plage d'adresse de 128.0.0.0 à 191.255.255.255
- Classe C : (réseau simple)
  - 3 octet pour identifié le réseau
  - 1 octets pour identifié les machines
  - 256 adresses possible
  - Commence toujours par la suite de bits 110, donc compris entre 192 et 223.
  - Plage d'adresse de 192.0.0.0 à 223.255.255.255
- Classe D : (multicast)
  - Un émeteur vers plusieurs récepteurs
  - Commence toujours par la suite de bits 1110, donc compris entre 224 et 239.
  - Plage d'adresse de 225.0.0.0 à 239.255.255.255
- Classe D : (IANA)
  - Réserver à l'IANA
  - Commence toujours par la suite de bits 1111, donc compris entre 240 et 255.
  - Plage d'adresse de 240.0.0.0 à 255.255.255.255
  
 > Les adresses privées entre les classes :
 > - Classe A : 10.0.0.0 à 10.255.255.255
 > - Classe B : 172.16.0.0 à 172.31.255.255
 > - Classe C : 192.168.1.0 à 192.168.255.255
  
- Résumé :

  | Classe    | Bits de départ | Début     | Fin             | CIDR (Masque) | Masque de sous réseau par défault |
  | --------- | -------------- | --------- | --------------- | ------------- | --------------------------------- |
  | Classe A  | 0              | 0.0.0.0   | 127.255.255.255 | /8            | 255.0.0.0                         |
  | Classe B  | 10             | 128.0.0.0 | 191.255.255.255 | /16           | 255.255.0.0                       |
  | Classe C  | 110            | 192.0.0.0 | 223.255.255.255 | /24           | 255.255.255.0                     |
  | Classe D  | 1110           | 224.0.0.0 | 239.255.255.255 |               | Non définie                       |
  | Classe E  | 1111           | 240.0.0.0 | 255.255.255.255 |               | Non définie                       |
  
---

#### > IPv4 et IPv6 :
  - ##### IPv4: (Longueur de 32 bits soit 4 octets)
    La plage d'attribution s'étend de 0.0.0.0 à 255.255.255.255. Elle est prémunie contre la pénuerie d'adresse par la norme RFC 1918. L'obtention d'une de ces adresses se fait soit par l'attribution statique ou automatique. _(Voir dans "UTILS" pour l'expliaction des deux thermes)_
  - ##### IPv6: (Longueur de 128 bits soit 16 octets)
    - 2<sup>128 possibilités d'adresses unique
    - 16 bits sous la forme de quatre chiffres héxadécimaux * 8 séparé par 2 points (":")
    - 64 bits sont réserver pour l'adresse réseau et les 64 autres restent pour fournir des détails sur l'interface réseau de l'hôte
  
    > Exemple :
    > 2001:0DB8:AC10:FE01:0000:0000:0000:0000\
    > Soit :\
    > 0010000000000001:0000110110111000:1010110000001000:1111111000000001:"Les zéros restent des zéro"
  
  - ##### Principales différences entre IPv4 et IPv6
    - espaces d'adressage plus importants en IPv6
    - IPv6 est fait pour rendre le transfert de paquets plus sécurisé
    - Avec l'IPv6, pas de limites géographiques (Actuelement 50% des IP sont réservées au Etats-Unis (car créer par eux))
    - Meilleurs fonctionnalités de multidiffusion dans le cas de l'IPv6
    
  - Objectifs sur le long therme:
    - Passé de l'IPv4 à l'IPv6 (Se fait en douceur grâce au NAT et au CIDR)

---

#### > Adresse broadcast :
Est une adresse par laquelle tout les appareils connectés au réseau peuvent recevoir des datagrames. Un message envoyé à une adresse broadcast peut-être reçu par tout les hôtes connectés au réseau.

---

#### > Différence entre IP privée et IP publique
  ##### - Privée :
  Ces adresses ne sont par sur Internet mais seulement sur réseau privés. Elles renforcent la sécurité car elles ne sont pas directement relié à Internet mais à un routeur, lui relié à Internet. Pour les entreprises etc. elle permet de communiquer sans consommer d'adresses Publique ainsi, deux entreprises différentes qui ne sont pas raccordés ensemble peuvent avoir le même addressage. Pour permettre à une adresse privée d'accéder à Internet, l'adresse doit être traduite en adresse publique appelé NAT _(Voir dans "UTILS" pour la définition et les types)_
  ##### - Publique :
  Ces adresses permetes aux ordinateurs du réseau de communiquer entre eux sur internet. Ces adresses sont fournis par le FAI (fournisseur d'accès à Internet) au moment de l'installation et de la synchronisation de la box. Chaques adresses sont unique au monde, non comprise dans la partie privée.
    
  ##### Exceptions :
  - Le réseau 127.0.0.0 est réservé pour les tests de boucle local conne l'adresse IP 127.0.0.1 ("localhost") qui est une boucle local sur le PC.
  - Le réseau 0.0.0.0 est lui aussi réservé.

---

#### > Masque de sous réseau
Il permet de distinguer la partie de l'adresse utilisée pour le routage et celle utilisable pour numéroter des interfaces (ordinateurs, imprimantes, etc..)\
Étant codé sur 4 octets et constitué d'une suite de 1 puis de 0, il y a 32 possibilité de masque 
- L'adresse de sous-réseau est obtenu en appliquand l'opérateur "ET" binaire entre l'adresse IP et le masque de sous-réseau

  > #### Exemple :
  > Adresse : 192.168.1.2 - Masque : 255.255.255.0\
  > _(Voir dans "UTILS" pour la convertion décimale vers binaire)_\
  > - 0 ET 0 = 0
  > - 1 ET 0 = 0
  > - 0 ET 1 = 0
  > - 1 ET 1 = 0\
  > \
  > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;192&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;168&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2\
  > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 1 0 0 0 0 0 0 . 1 0 1 0 1 0 0 0 . 0 0 0 0 0 0 0 1 . 0 0 0 0 0 0 1 0\
  > ET 1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;. 1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;. 1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;1 1 . 0 0 0 0 0 0 0 0\
  > =&nbsp;&nbsp; 1 1 0 0 0 0 0 0 . 1 0 1 0 1 0 0 0 . 0 0 0 0 0 0 0 1 . 0 0 0 0 0 0 0 0
  > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;192&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;168&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0
  > #### L'adresse de sous-réseau est : 192.168.1.0

- L'adresse de l'hôte à l'intérieur du sous-réseau est obtenu en appliquand l'opérateur "ET" binaire entre l'adresse IP et le "complément à un" _(Voir dans "UTILS" pour la définition)_ du masque

  > #### Exemple :
  > Adresse : 192.168.1.2 - Masque : 255.255.255.0\ avec complément à un 0.0.0.255
  > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;192&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;168&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2\
  > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 1 0 0 0 0 0 0 . 1 0 1 0 1 0 0 0 . 0 0 0 0 0 0 0 1 . 0 0 0 0 0 0 1 0\
  > ET 0 0 0 0 0 0 0 0 . 0 0 0 0 0 0 0 0 . 0 0 0 0 0 0 0  . 1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;1 1\
  > =&nbsp;&nbsp; 1 1 0 0 0 0 0 0 . 1 0 1 0 1 0 0 0 . 0 0 0 0 0 0 0 1 . 0 0 0 0 0 0 0 0
  > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;192&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;168&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0
  > #### L'adresse de l'hôte est : 0.0.0.2

En résumé :

|                        |                 |
| ---------------------- | --------------- |
| La notation            | 91.198.174.2/19 |
| désigne l'adresse IP   | 91.168.174.2    |
| avec le masque         | 255.255.224.0   | 
| avec l'adress SR       | 91.168.160.0    |
| et l'adress hôte       | 0.0.14.2        |

Ça signifie que les 19 premiers bits de l'adresse sont dédiés à l'adresse du sous-réseau et le reste à l'adresse de l'interface hôte à l'intérieur du réseau\
_(Voir dans "UTILS" pour la liste des masques de sous réseau)_

---

### TCP : (Transmission Conctrol Protocol) (Dans la langue de Molière : Protocole de contrôle de transmission)
  Est un protocole de paquet fiable\
  Il utilise un system de handshaking _(Voir dans "UTILS" pour la définition)_
  
#### > Fonctionnement :
  - Etablissement de la connextion
  - Transfert de données
  - Fin de connexion

#### > Connexion entre les appareils :
En règle général un système ouvre une 'socket' (point d'accès à une connexion TCP) et se met en attente passive de connexion d'un autre système. On appel ça l'ouverture passive, utilisé par le côté serveur de la connexion.

#### > Transferts de données : (sécurité)
  - Les numéros de séquence sont utilisés pour ordonner les segments TCP reçus et détecter les données perdues
  - Les sommes de contrôle permettents la détection d'erreur
  - Les acquittements et les temporisations permettent la détection des segments perdue ou retardés
   
&nbsp;
<p><a href="https://commons.wikimedia.org/wiki/File:Tcp_talk.svg#/media/Fichier:Tcp_talk.svg"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/31/Tcp_talk.svg/1200px-Tcp_talk.svg.png" alt="Tcp talk.svg"></a><br>Par <a href="//commons.wikimedia.org/w/index.php?title=User:Skc&amp;action=edit&amp;redlink=1" class="new" title="User:Skc (page does not exist)">Sébastien Koechlin</a> — <span class="int-own-work" lang="fr">Travail personnel</span>, <a href="https://creativecommons.org/licenses/by-sa/3.0" title="Creative Commons Attribution-Share Alike 3.0">CC BY-SA 3.0</a>, <a href="https://commons.wikimedia.org/w/index.php?curid=16887951">Lien</a></p>

#### >  La somme de contrôle :
Sur 16 bits, constituée par le complément à un de la somme complémentée à un de tout les éléments d'un segment TCP (en-tête et données) tout ça calculée par l'émeteur et inclus dans le segment émis. Puis est recalculée par le destinaire. Si elle correspond à la somme de contrôle reçue, on considère que le segment à été reçu intact et sans erreur.

#### > Terminaison d'une connexion :
Chaque et extrémité de la connexion effetue sa terminaison de manière indépendante

#### > Alternative :
Les applications multimédia (audio, vidéo), des jeux multi-joueurs en temps réel, l'échange de fichiers, etc n'ont pas besoin du TCP et peuvent même les limités car il est nécessaire de gérer les pertes et les erreurs plustôt que d'essayer de les éviter.
  - UDP : est souvent utilisé pour le temps réel mais est moins fiable
  - SCTP : comme le TCP, mais permettant la communications multi-cibles comme l'UDP
  - MPTCP : surcouche de TCP, exploiter tous les chemins disponibles en parallèle, et donc améliorer significativement les performances et la fiabilité d'une connexion.
  
#### > Le Modèle TCP/IP (Modèle internet):
  Il utilise des couches réseau _(Voir dans "UTILS" pour la définition)_ :
  1. Application
  2. Transport
  3. Internet
  4. Accès réseau
  
---
  
  ### > UDP : (User Datagram Protocol) (Protocole de datagramme utilisateur)
  Permet l'échange entre deux utilisateur de manière symple, chacun définie par une adresse IP et un port. Il n'est pas nécessaire d'avoir une communication préalable n'est requise pour établir la connexion, contrairement du TCP qui utilise le handshaking _(Voir dans "UTILS" pour la définition)_. Les paquets envoyés en UDP sont préfixer d'une en-tête contenant l'adresse de destination, suffisant pour sont envoie.
  
  #### > Propriétés :
  - Ne retient pas d'informations sur l'état des messages UDP. Il est définie comme un protocole non fiable
  - "Orienté transaction", pratique pour les protocoles simples de type requête-réponse
  - Il fournit des datagrammes utiles pour modeliser d'autres protocoles
  - Il est simple, bon pour le bootstrapping _(Voir dans "UTILS" pour la définition)_, le DHCP et les protocoles simplifié de transfert de fichiers
  - Il est dit sans état, pratique pour le streaming (Télévision sur Tèl./Ordinateur)
  - Absence de délai, pratique pour le temps réel (Chats Vocaux, jeux-vidéo etc.)
  - Efficace pour des communications unidirectionnel
  
---

### Le Model OSI : (Open Systems Interconnection)
  Est une norme de communication, en réseau, pour tout les sytèmes informatique, il à une architecture en couches _(Voir dans "UTILS" pour la définition)_\
  Il est proposé par l'ISO (Internationel Organization for Standardization)
  
<p><a href="https://commons.wikimedia.org/wiki/File:OSI_Model_v1.svg#/media/Fichier:OSI_Model_v1.svg"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/8d/OSI_Model_v1.svg/1200px-OSI_Model_v1.svg.png" alt="OSI Model v1.svg"></a><br>Par <a href="//commons.wikimedia.org/wiki/User:Offnfopt" title="User:Offnfopt">Offnfopt</a> — <span class="int-own-work" lang="fr">Travail personnel</span>, Domaine public, <a href="https://commons.wikimedia.org/w/index.php?curid=39917431">Lien</a></p>

#### > Son architecture :

|                     | PDU        | Couche          | Fonction                                                                  |
| ------------------- | ---------- | --------------- | ------------------------------------------------------------------------- |
| Couches hautes      | Donnée     | 7. Application  | Point d'accès aux services réseau                                         |
|                     |            | 6. Présentation | Fait la conversion entre données manipulées ainsi que des octets transmis |
|                     |            | 5.Session       | Gère la synchronisation entre les échanges, permet l'ouvert et la fermeture de la session | 
|                     | Datagramme | 4. Transport    | Gère la communication de proche en proche, généralement entre machine : routage et adressage des paquets |
| Couches matérielles | Paquet     | 3. Réseau       | Détermine le parcours des données et l'adressage logique (Adresse IP) |
|                     | Trame      | 2. Liaison      | Gère la communication entre 2 machines directement connecter entre elles, ou par commutateur |
|                     | Bit        | 1. Physique     | Gère la transmission des signauc entre les entités. Limité a l'émission et à la reception d'un bit ou d'un train de bit |

#### > Divers :
  - Pas forcement compatible avec la pile IP
  - Le modèle OSI est connu pour ses fonctionnalités permettant de garantir une bonne qualité de service.
  - Il est universelle, on retrouve ce modèle dans beaucoup de système, car il permet une meilleur organisation des normes par rapport au système applicatifs.
  
| Num | Couche       | Norme                                  |
| --- | ------------ | -------------------------------------- |
| 7   | Application  | Web                                    |
| 6   | Présentation | HTML / XML                             |
| 5   | Session      | HTTP / HTTPS                           |
| 4   | Transport    | TCP                                    |
| 3   | Réseau       | IP                                     |
| 2   | Liaison      | Ethernet / xDSL                        |
| 1   | Physique     | RJ45 / RJ11 / RJ12 / Cable cat. 5 et + |

---

## UTILS
#### > Convertion décimale vers binaire : 

On connais la traduction d'un nombre décimale en binaire, en soustraillant des puissances de 2 à notre décimale:\
192 = 2<sup>7</sup> + 2<sup>6</sup> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= 128 + 64\
168 = 2<sup>7</sup> + 2<sup>5</sup> + 2<sup>3</sup> = 128 + 32 + 8\
1 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= 2<sup>0</sup> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= 1\
2 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= 2<sup>1</sup> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= 2
  > Tableau de convertion :\
  > On traduira : 192.168.1.2

| &nbsp;&nbsp;&nbsp; | 2<sup>7</sup> | 2<sup>6</sup> | 2<sup>5</sup> | 2<sup>4</sup> | 2<sup>3</sup> | 2<sup>2</sup> | 2<sup>1</sup> | 2<sup>0</sup> |
| ------------------ | --- | --- | --- | --- | --- | --- | --- | --- |
| Décimale           | 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   |
| 192                | 1   | 1   | 0   | 0   | 0   | 0   | 0   | 0   |
| 168                | 1   | 0   | 1   | 0   | 1   | 0   | 0   | 0   |
| 1                  | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 1   |
| 2                  | 0   | 0   | 0   | 0   | 0   | 0   | 1   | 0   |

---

#### > Calcul du nombre d'hôte possible sur une adresse :
  2<sup>32-CIDR(masque)</sup>-2
  
  > Ainsi pour un masque de 19, on obtient
  > 2<sup>32-19</sup>-2 = 8190 hôtes possible
  
---

#### > Complément à un :

Il s'agit d'ajouter traduire du décimale au binaire puis d'inverser tout les bits de 1 vers 0 et de 0 vers 1
  > Ainsi :\
  > &nbsp;1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;. 1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;. 1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;1 1 . 0 0 0 0 0 0 0 0\
  > Deviens :\
  > &nbsp;0 0 0 0 0 0 0 0 . 0 0 0 0 0 0 0 0 . 0 0 0 0 0 0 0  . 1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;1 1

---

#### > NAT (Network Adresse Translation) : 
  - statique : Correspondance un pour un établie entre les adresses local et gloable
  - dinamique : mappage de plusieurs adresses local vers plusieurs adresses gloables
  - traduction d'adresses de port (PAT) : mappages de plusieurs adresses locales et gloabales vers une seule. Cette méthode est également appelée "surcharge" (Surcharge NAT)

---

#### > Attribution statique :
  - Définit par l'administrateur réseau
  - Permet un bon contrôle mais à faire que sur des petites structure car sinon la surcharge de travail peut-être trop importante
  - Utile pour les routeurs et les firewall
  
#### > Attribution automatique :
  - Définit par le serveur DHCP

---

#### > Handshaking :
  - Principe sur lequel deux entités entreprènes d'abbord une "négociation" avant une communication
 
#### > Bootstrapping :
  - Est un compilateur écrit dans son propre langage

---

#### > Les couches réseau :
  - Fonctionnalités nécessaire à la communication et l'organisation des fonctions
