### Gros merci à Mazoise (mchardin) pour la correction de l'ortographe 👌
#### Abonne toi, lache un like, active la cloche tout ça tout ça :star2:
## Général
#### > IP (Internet protocol)
- Identifier chaque appareil sur internet
- Coder sur 4 octets (32 bits)

##### > Les différentes classes d'IP :
- Classe A : (gros réseau)
  - 1 octet pour identifier le réseau
  - 3 octets pour identifier les machines
  - 16 777 214 adresses possibles
  - Commence toujours par la suite de bits 0, donc compris entre 0 et 127, mais certaines adresses sont réservées à des usages particuliers.
  - Plage d'adresse de 0.0.0.0 à 127.255.255.255
- Classe B : (réseau moyen)
  - 2 octets pour identifier le réseau
  - 2 octets pour identifier les machines
  - 65535 adresses possibles
  - Commence toujours par la suite de bits 10, donc compris entre 128 et 191.
  - Plage d'adresse de 128.0.0.0 à 191.255.255.255
- Classe C : (réseau simple)
  - 3 octets pour identifier le réseau
  - 1 octet pour identifier les machines
  - 256 adresses possibles
  - Commence toujours par la suite de bits 110, donc compris entre 192 et 223.
  - Plage d'adresse de 192.0.0.0 à 223.255.255.255
- Classe D : (multicast)
  - Un émetteur vers plusieurs récepteurs
  - Commence toujours par la suite de bits 1110, donc compris entre 224 et 239.
  - Plage d'adresse de 225.0.0.0 à 239.255.255.255
- Classe D : (IANA)
  - Réservé à l'IANA
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
    La plage d'attribution s'étend de 0.0.0.0 à 255.255.255.255. Elle est prémunie contre la pénurie d'adresses par la norme RFC 1918. L'obtention d'une de ces adresses se fait par attribution statique ou automatique. _(Voir dans "UTILS" pour l'explication des deux termes)_
  - ##### IPv6: (Longueur de 128 bits soit 16 octets)
    - 2<sup>128 possibilités d'adresses uniques
    - 16 bits sous la forme de quatre chiffres hexadécimaux * 8 séparés par 2 points (":")
    - 64 bits sont réservés pour l'adresse réseau et les 64 autres restent pour fournir des détails sur l'interface réseau de l'hôte
  
    > Exemple :
    > 2001:0DB8:AC10:FE01:0000:0000:0000:0000\
    > Soit :\
    > 0010000000000001:0000110110111000:1010110000001000:1111111000000001:"Les zéro restent des zéro"
  
  - ##### Principales différences entre IPv4 et IPv6
    - espaces d'adressage plus importants en IPv6
    - IPv6 est fait pour rendre le transfert de paquets plus sécurisé
    - Avec l'IPv6, pas de limite géographique (Actuellement 50% des IP sont réservés aux États-Unis (car créés par eux))
    - Meilleures fonctionnalités de multidiffusion dans le cas de l'IPv6
    
  - Objectifs sur le long terme :
    - Passer de l'IPv4 à l'IPv6 (Se fait en douceur grâce au NAT et au CIDR)

---

#### > Adresse broadcast :
Est une adresse par laquelle tous les appareils connectés au réseau peuvent recevoir des datagrammes. Un message envoyé à une adresse broadcast peut être reçu par tous les hôtes connectés au réseau. Elle est l'adresse IP la plus haute selon l'adresse réseau

---

#### > Différence entre IP privée et IP publique
  ##### - Privée :
  Ces adresses ne sont pas sur Internet mais seulement sur les réseau privés. Elles renforcent la sécurité car elles ne sont pas directement reliées à Internet mais à un routeur, lui relié à Internet. Pour les entreprises etc. elle permet de communiquer sans consommer d'adresses publiques. Ainsi, deux entreprises différentes qui ne sont pas raccordées ensemble peuvent avoir le même adressage. Pour permettre à une adresse privée d'accéder à Internet, l'adresse doit être traduite en adresse publique appelée NAT _(Voir dans "UTILS" pour la définition et les types)_
  ##### - Publique :
  Ces adresses permettent aux ordinateurs du réseau de communiquer entre eux sur internet. Ces adresses sont fournies par le FAI (fournisseur d'accès à Internet) au moment de l'installation et de la synchronisation de la box. Chaque adresse est unique au monde, non comprise dans la partie privée.
   
  ##### Exceptions :
  - Le réseau 127.0.0.0 est réservé pour les tests de boucle locale comme l'adresse IP 127.0.0.1 ("localhost") qui est une boucle locale sur le PC.
  - Le réseau 0.0.0.0 est lui aussi réservé.

---

#### > Masque de sous réseau
Il permet de distinguer la partie de l'adresse utilisée pour le routage et celle utilisable pour numéroter des interfaces (ordinateurs, imprimantes, etc..)\
Étant codé sur 4 octets et constitué d'une suite de 1 puis de 0, il y a 32 possibilités de masque 
- L'adresse de sous-réseau est obtenu en appliquant l'opérateur "ET" binaire entre l'adresse IP et le masque de sous-réseau

  > #### Exemple :
  > Adresse : 192.168.1.2 - Masque : 255.255.255.0\
  > _(Voir dans "UTILS" pour la conversion decimal vers binaire)_\
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

- L'adresse de l'hôte à l'intérieur du sous-réseau est obtenue en appliquant l'opérateur "ET" binaire entre l'adresse IP et le "complément à un" _(Voir dans "UTILS" pour la définition)_ du masque

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
| avec l'adresse SR      | 91.168.160.0    |
| et l'adresse hôte      | 0.0.14.2        |

Ça signifie que les 19 premiers bits de l'adresse sont dédiés à l'adresse du sous-réseau et le reste à l'adresse de l'interface hôte à l'intérieur du réseau\
_(Voir dans "UTILS" pour la liste des masques de sous réseau)_

---

### TCP : (Transmission Control Protocol) (Dans la langue de Molière : Protocole de contrôle de transmission)
  Est un protocole de paquet fiable\
  N'est pas orienté datagramme
  Il prend en charge la diffusion (multicast)
  Il utilise un system de handshaking _(Voir dans "UTILS" pour la définition)_
  
#### > Fonctionnement :
  - Etablissement de la connexion
  - Transfert de données
  - Fin de connexion

#### > Connexion entre les appareils :
En règle générale, un système ouvre une 'socket' (point d'accès à une connexion TCP) et se met en attente passive de connexion d'un autre système. On appel ça l'ouverture passive, utilisé par le côté serveur de la connexion.

#### > Transferts de données : (sécurité)
  - Les numéros de séquence sont utilisés pour ordonner les segments TCP reçus et détecter les données perdues
  - Les sommes de contrôle permettent la détection d'erreur
  - Les acquittements et les temporisations permettent la détection des segments perdus ou retardés
   
&nbsp;
<p><a href="https://commons.wikimedia.org/wiki/File:Tcp_talk.svg#/media/Fichier:Tcp_talk.svg"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/31/Tcp_talk.svg/1200px-Tcp_talk.svg.png" alt="Tcp talk.svg"></a><br>Par <a href="//commons.wikimedia.org/w/index.php?title=User:Skc&amp;action=edit&amp;redlink=1" class="new" title="User:Skc (page does not exist)">Sébastien Koechlin</a> — <span class="int-own-work" lang="fr">Travail personnel</span>, <a href="https://creativecommons.org/licenses/by-sa/3.0" title="Creative Commons Attribution-Share Alike 3.0">CC BY-SA 3.0</a>, <a href="https://commons.wikimedia.org/w/index.php?curid=16887951">Lien</a></p>

#### >  La somme de contrôle :
Sur 16 bits, constitués par le complément à un de la somme complémentée à un de tous les éléments d'un segment TCP (en-tête et données) tout ça calculé par l'émetteur et inclus dans le segment émis. Puis est recalculé par le destinataire. Si elle correspond à la somme de contrôle reçue, on considère que le segment a été reçu intact et sans erreur.

#### > Terminaison d'une connexion :
Chaque extrémité de la connexion effectue sa terminaison de manière indépendante

#### > Alternative :
Les applications multimédia (audio, vidéo), des jeux multi-joueurs en temps réel, l'échange de fichiers, etc n'ont pas besoin du TCP et peuvent même les limiter car il est nécessaire de gérer les pertes et les erreurs plutôt que d'essayer de les éviter.
  - UDP : est souvent utilisé pour le temps réel mais est moins fiable
  - SCTP : comme le TCP, mais permettant la communication multi-cibles comme l'UDP
  - MPTCP : surcouche de TCP, exploite tous les chemins disponibles en parallèle, et donc améliore significativement les performances et la fiabilité d'une connexion.
  
#### > Le Modèle TCP/IP (Modèle internet):
  Il utilise des couches réseau _(Voir dans "UTILS" pour la définition)_ :
  1. Application
  2. Transport
  3. Internet
  4. Accès réseau
  
---
  
  ### > UDP : (User Datagram Protocol) (Protocole de datagramme utilisateur)
  Permet l'échange entre deux utilisateur de manière simple, chacun défini par une adresse IP et un port. Il n'est pas nécessaire d'avoir une communication préalable pour établir la connexion, contrairement au TCP qui utilise le handshaking _(Voir dans "UTILS" pour la définition)_. Les paquets envoyés en UDP sont préfixés d'une en-tête contenant l'adresse de destination, suffisant pour son envoi.
  
  #### > Propriétés :
  - Ne retient pas d'information sur l'état des messages UDP. Il est défini comme un protocole non fiable
  - "Orienté transaction", pratique pour les protocoles simples de type requête-réponse
  - Il fournit des datagrammes utiles pour modéliser d'autres protocoles
  - Il est simple, bon pour le bootstrapping _(Voir dans "UTILS" pour la définition)_, le DHCP et les protocoles simplifiés de transfert de fichiers
  - Il est dit sans état, pratique pour le streaming (Télévision sur Tel./Ordinateur)
  - Absence de délai, pratique pour le temps réel (Chats Vocaux, jeux-vidéo etc.)
  - Efficace pour des communications unidirectionnelles
  
---

### Le Model OSI : (Open Systems Interconnection)
  Est une norme de communication, en réseau, pour tous les systèmes informatiques, il a une architecture en couches _(Voir dans "UTILS" pour la définition)_\
  Il est proposé par l'ISO (International Organization for Standardization)
  
<p><a href="https://commons.wikimedia.org/wiki/File:OSI_Model_v1.svg#/media/Fichier:OSI_Model_v1.svg"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/8d/OSI_Model_v1.svg/1200px-OSI_Model_v1.svg.png" alt="OSI Model v1.svg"></a><br>Par <a href="//commons.wikimedia.org/wiki/User:Offnfopt" title="User:Offnfopt">Offnfopt</a> — <span class="int-own-work" lang="fr">Travail personnel</span>, Domaine public, <a href="https://commons.wikimedia.org/w/index.php?curid=39917431">Lien</a></p>

#### > Son architecture :

|                     | PDU        | Couche          | Fonction                                                                  |
| ------------------- | ---------- | --------------- | ------------------------------------------------------------------------- |
| Couches hautes      | Donnée     | 7. Application  | Point d'accès aux services réseau                                         |
|                     |            | 6. Présentation | Fait la conversion entre données manipulées et octets transmis |
|                     |            | 5.Session       | Gère la synchronisation entre les échanges, permet l'ouverture et la fermeture de la session | 
|                     | Datagramme | 4. Transport    | Gère la communication de proche en proche, généralement entre machine : routage et adressage des paquets |
| Couches matérielles | Paquet     | 3. Réseau       | Détermine le parcours des données et l'adressage logique (Adresse IP) |
|                     | Trame      | 2. Liaison      | Gère la communication entre 2 machines directement connectées entre elles, ou par commutateur |
|                     | Bit        | 1. Physique     | Gère la transmission des signaux entre les entités. Limité  à l'émission et à la réception d'un bit ou d'un train de bit |

#### > Divers :
  - Pas forcément compatible avec la pile IP
  - Le modèle OSI est connu pour ses fonctionnalités permettant de garantir une bonne qualité de service.
  - Il est universel, on retrouve ce modèle dans beaucoup de système, car il permet une meilleur organisation des normes par rapport aux systèmes applicatifs.
  
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

### > Serveur et protocole DHCP :
  Est un service qui délivre des adresses IP aux ordinateurs qui se connectent au réseau
  Le serveur va délivrer un bail DHCP à l'ordinateur qui comprend :
  - La durée de vie du bail (Libère l'adresse au bout d'un moment. Si l'ordinateur est encore connecté il lui redonnera une nouvelle adresse IP. Ce système permet de faire tourner les adresses IP)
  - Une adresse IP (Adresse dynamique : attribution statique)
  - Et les paramètres réseau (Adresse passerelle, Adresse du DNS)

---

### > Serveur et protocole DNS :
  Permet de traduire les noms de domaines en adresse IP

---

### > Configuration minimale pour faire communiquer deux adresses en utilisant l'IP :
  Ordinateur    ->   Passerelle   ->   Internet   ->   Passerelle   ->   Serveur\
  172.18.3.82        172.18.0.253

---

### > Une passerelle :
  Dispositif permettant de relier deux réseaux informatiques, de type différent, ensemble :
  - Répéteur          (niveau 1)
  - Pont              (niveau 2)
  - Relais / Routeur  (niveau 3)
  
  Une passerelle est plus communément appelée modem-routeur ou box, relie un réseau local à Internet. Elle sert également de pare-feu, de proxy, et effectue la qualité de service. Une passerelle par défaut est une passerelle qui gère le routage au niveau IP.

---

### Routage d'IP :
  Sélection des chemins, dans un réseau, par lesquels on va faire acheminer les données, de l'expéditeur vers le ou les destinataire(s).
  
---

### Ports :

  - 0 à 1023 : Controlés et assignés par l'IANA, appelés Well Known Ports
  - 1024 à 49156 : Ports enregistrés
  - 49152 à 65535 : Ports dynamiques
  
  Une adresse IP + un port = un socket : Chemin par lequel transitent des paquets

---
## UTILS
#### > Conversion décimal vers binaire : 

On connaît la traduction d'un nombre décimal en binaire, en soustrayant des puissances de 2 à notre décimale:\
192 = 2<sup>7</sup> + 2<sup>6</sup> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= 128 + 64\
168 = 2<sup>7</sup> + 2<sup>5</sup> + 2<sup>3</sup> = 128 + 32 + 8\
1 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= 2<sup>0</sup> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= 1\
2 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= 2<sup>1</sup> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= 2
  > Tableau de conversion :\
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
  > 2<sup>32-19</sup>-2 = 8190 hôtes possibles
  
---

#### > Complément à un :

Il s'agit de convertir du décimal au binaire puis d'inverser tous les bits de 1 vers 0 et de 0 vers 1
  > Ainsi :\
  > &nbsp;1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;. 1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;. 1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;1 1 . 0 0 0 0 0 0 0 0\
  > Deviens :\
  > &nbsp;0 0 0 0 0 0 0 0 . 0 0 0 0 0 0 0 0 . 0 0 0 0 0 0 0  . 1 1 &nbsp;1 1 &nbsp;1 1 &nbsp;1 1

---

#### > NAT (Network Adresse Translation) : 
  - statique : Correspondance un pour un établie entre les adresses locales et globales
  - dynamique : mappage de plusieurs adresses locales vers plusieurs adresses globales
  - traduction d'adresses de port (PAT) : mappages de plusieurs adresses locales et globales vers une seule. Cette méthode est également appelée "surcharge" (Surcharge NAT)

---

#### > Attribution statique :
  - Défini par l'administrateur réseau
  - Permet un bon contrôle mais à faire que sur des petites structures car sinon la surcharge de travail peut être trop importante
  - Utile pour les routeurs et les firewall
  
#### > Attribution automatique :
  - Défini par le serveur DHCP

---

#### > Handshaking :
  - Principe sur lequel deux entités entreprennent d'abord une "négociation" avant une communication
 
#### > Bootstrapping :
  - Est un compilateur écrit dans son propre langage

---

#### > Les couches réseau :
  - Fonctionnalités nécessaires à la communication et l'organisation des fonctions

