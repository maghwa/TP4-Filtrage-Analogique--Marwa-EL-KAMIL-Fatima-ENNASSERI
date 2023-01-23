# TP4-Filtrage-Analogique--Marwa-EL-KAMIL-Fatima-ENNASSERI
#### Réalisé par: 
- Fatima  Ennassiri (Filière: Cyber Security)
- Marwa El Kamil(Filière: Artficial Intelligence)
### Encadré par:
- Mr Alae Ammour

### Objectifs:
- Appliquer un filtre réel pour supprimer les composantes indésirables d’un signal. 
- Améliorer la qualité de filtrage en augmentant l’ordre du filtre.
### Introduction-Diagramme de Bode:

Le diagramme de Bode permet de représenter sous forme graphique le gain en dB (G=20 log et 
la phase ( d'une fonction de transfert, en fonction de w. Il permet de voir le 
comportement d'un filtre ou d'un système asservi linéaire

## 1.Filtrage et diagramme de Bode
Sur le réseau électrique, un utilisateur a branché une prise CPL (Courant Porteur en 
Ligne), les signaux utiles sont de fréquences élevées. Le réseau électrique a 
cependant sa propre fréquence (50 hz). Le boiter de réception doit donc pouvoir 
filtrer les basses fréquences pour s'attaquer ensuite à la démodulation du signal utile.
Schématiquement :

<img width="227" alt="Screenshot 2023-01-22 231718" src="https://user-images.githubusercontent.com/87017143/213946683-1878ef96-a156-41be-b6e5-190498338af3.png">

Mathématiquement, un tel filtre fournit un signal de sortie en convoluant le signal 
d'entrée par la réponse temporelle du filtre :
y(t) = x(t) * h(t)
### Notre manipulation
Nous souhaitons appliquer un filtre passe-haut pour supprimer la composante à 50Hz. Soit notre signal d'entrée :

x(t) = sin(2.pi.f1.t) + sin(2.pi.f2.t) + sin(2.pi.f3.t)
Avec f1 = 500 Hz,
f2 = 400 Hz 
et f3 = 50 Hz
 #### 1.2- Définition de signal x(t) et Traçage de signal x(t) et sa transformé de Fourrier:
 
 Le code:
 
<img width="308" alt="Screenshot 2023-01-22 233550" src="https://user-images.githubusercontent.com/87017143/213946889-2b1e8574-2e50-4acf-ac2a-c2ae096f98b9.png">
 
 L'affichage:
 
 <img width="810" alt="Screenshot 2023-01-22 233523" src="https://user-images.githubusercontent.com/87017143/213946924-a1ff48c9-2eff-4cf5-9dd4-fe370b81895e.png">
La fonction H(f) (transmittance complexe) du filtre passe haut de premier ordre est 
donnée par :
H(f) = (K.j.w/wc) / (1 + j. w/wc)
Avec K le gain du signal, w la pulsation et wc la pulsation de coupure.
On se propose de tracer le diagramme de Bode de ce filtre et de l'appliquer au 
signal.
#### 1. Traçage de module de la fonction H(f) avec K=1 et wc = 50 rad/s:

-Le code:

<img width="298" alt="Screenshot 2023-01-23 003622" src="https://user-images.githubusercontent.com/87017143/213947014-995a64e0-657e-4666-a422-1f3f1da351bd.png">

 -L'affichage en utilisant plot:
 
<img width="398" alt="Screenshot 2023-01-23 003212" src="https://user-images.githubusercontent.com/87017143/213947146-4b3b289a-46d1-44f5-9c8a-cf6506c8da63.png">

-L'affichage en utilisant semilogx:

<img width="371" alt="Screenshot 2023-01-23 003448" src="https://user-images.githubusercontent.com/87017143/213947273-f588594b-947b-4b71-8c2b-cf058c352975.png">

#### 2. Traçage 20.log(|H(f)|) pour différentes pulsations de coupure wc:

-Le code:

<img width="331" alt="Screenshot 2023-01-23 011258" src="https://user-images.githubusercontent.com/87017143/213948048-8907a672-b764-4027-ba9c-7d0be73aff5f.png">
 
 -L'affichage:
 
 <img width="398" alt="Screenshot 2023-01-23 010845" src="https://user-images.githubusercontent.com/87017143/213948094-e42294f3-deaf-4633-add0-9eb073ac7710.png">

-En tracant 20.log(|H(f)|) pour différentes pulsations de coupure wc, on observe qu'il y a une coupure de fréquence à la pulsation de coupure choisie. Cela signifie que les fréquences inférieures à la pulsation de coupure sont transmises avec un gain élevé tandis que les fréquences supérieures à la pulsation de coupure sont atténuées.
#### 3. Le Choix de différentes fréquences de coupure :
En choisissant différentes fréquences de coupure et en appliquant le filtrage dans l'espace des fréquences, on observe que les fréquences inférieures à la fréquence de coupure sont transmises avec un gain élevé tandis que les fréquences supérieures à la fréquence de coupure sont atténuées.
###  application de  ce filtrage dans l'espace des fréquence:
Le code:

<img width="520" alt="Screenshot 2023-01-23 015427" src="https://user-images.githubusercontent.com/87017143/213950073-94c4f654-df6f-4e04-a79d-559ec081ccee.png">


Affichage:

<img width="410" alt="Screenshot 2023-01-23 014119" src="https://user-images.githubusercontent.com/87017143/213949639-54c74178-693b-4ee7-9dc5-0ac5d635f94e.png">

#### 4.Le choix de wc optimal:
Le choix de wc optimal dépend des besoins spécifiques du signal et de l'application. Il est important de choisir une fréquence de coupure qui sépare les fréquences souhaitées des fréquences non souhaitées.

## 2.Dé-bruitage d'un signal sonore

