### Général
#### > IP (Internet protocol)
- Identifie chaque appareil sur internet
- Coder sur 4 octets (32 bits)

---

#### > Masque de sous réseau
Il permet de distinguer la partie de l'adresse utilisée pour le routage et celle utilisable pour numéroter des interfaces (ordinateurs, imprimantes, etc..)\
Étant codé sur 4 octets et constitué d'une suite de 1 puis de 0, il y a 32 possibilité de masque 
- L'adresse de sous-réseau est obtenu en appliquand l'opérateur "ET" binaire entre l'adresse IP et le masque de sous-réseau

  > #### Exemple :
  > Adresse : 192.168.1.2 - Masque : 255.255.255.0\
  > _(Voir dans "UTILS" pour la convertion décimale vers binaire)_\
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
