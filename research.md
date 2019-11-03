### Général
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
  
- Résumé :

  | Classe   | Bits de départ | Début     | Fin             | Notation CIDR | Masque de sous réseau par défault |
  | -------- | -------------- | --------- | --------------- | ------------- | --------------------------------- |
  | Classe A | 0              | 0.0.0.0   | 127.255.255.255 | /8            | 255.0.0.0                         |
  | Classe B | 10             | 128.0.0.0 | 191.255.255.255 | /16           | 255.255.0.0                       |
  | Classe C | 110            | 192.0.0.0 | 223.255.255.255 | /24           | 255.255.255.0                     |
  | Classe D | 1110           | 224.0.0.0 | 239.255.255.255 |               | Non définie                       |
  | Classe E | 1111           | 240.0.0.0 | 255.255.255.255 |               | Non définie                       |

##### > Adresse broadcast :
Est une adresse par laquelle tout les appareils connectés au réseau peuvent recevoir des datagrames. Un message envoyé à une adresse broadcast peut-être reçu par tout les hôtes connectés au réseau.

##### > Différence entre IP privée et IP publique
  ##### - Privée :
  Ces adresses ne sont par sur Internet mais seulement sur réseau privés. Elles renforcent la sécurité car n'étant pas directement relié à Internet mais à un routeur, lui relié à Internet. Pour les entreprises etc. elle permet de communiquer sans consommer d'adresses Publique ainsi, deux entreprises différentes qui ne sont pas raccordés ensemble peuvent avoir le même addressage. Pour permettre à une adresse privée d'accéder à Internet, l'adresse doit être traduite en adresse publique appelé NAT _(Voir dans "UTILS" pour la définition et les types)_
  ##### - Publique :
  Ces adresses permetes aux ordinateurs du réseau de communiquer entre eux sur internet. Ces adresses sont fournis par le FAI (fournisseur d'accès à Internet) au moment de l'installation et de la synchronisation de la box. Chaques adresses sont unique au monde, non comprise dans la partie privée.\
  Exceptions :\
    - Le réseau 127.0.0.0 est réservé pour les tests de boucle local conne l'adresse IP 127.0.0.1 ("localhost") qui est une boucle local sur le PC.\
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

### UTILS
#### > Convertion décimale vers binaire : 

On connais la traduction d'un nombre décimale en binaire, en soustraillant des puissances de 2 à notre décimale:\
192 = 2<sup>7</sup> + 2<sup>6</sup> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= 128 + 64\
168 = 2<sup>7</sup> + 2<sup>5</sup> + 2<sup>3</sup> = 128 + 32 + 8\
1 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= 2<sup>0</sup> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= 1\
2 &nbsp;&nbsp;&nbsp;&nbsp;= 2<sup>1</sup> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= 2
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
