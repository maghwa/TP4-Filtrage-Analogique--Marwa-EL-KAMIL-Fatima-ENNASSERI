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
Dans son petit studio du CROUS, un mauvais futur ingénieur a enregistré une 
musique en « .wav » avec un très vieux micro. Le résultat est peu concluant, un bruit strident s'est ajouté à sa musique. Heureusement son voisin, expert en traitement du signal est là pour le secourir :
« C'est un bruit très haute fréquence, il suffit de le supprimer. » dit-il sûr de lui.
#### 1. une méthode pour supprimer ce bruit sur le signal

<img width="408" alt="Screenshot 2023-01-27 100251" src="https://user-images.githubusercontent.com/87017143/215048448-e4b08fc2-0a20-47cd-8c7f-ab25008e08ec.png">

On Observe  que dans le spectre suivant il y a une fréquence entre 4000 et 6000 d'amplitude 2 qui constitue le bruit, pour l'éiminer on doit appliquer un filtre passe bas qui nous permettra de diminuer l'intensité du bruit.

==>Une méthode courante pour supprimer un bruit haute fréquence d'un signal est d'utiliser un filtre passe-bas. 

==>Lors de l'attenuation du bruit, on arrive pas à filtrer le signal avec une transmittance complexe d'ordre 1 sans affecter le signal.Par conséquent un filtre pass-bas de premier ordre n'est pas eeficace pour eliminer le bruit.Par suite, il faut opter pour un filtre d'ordre supérieur nommé un filtre "Butterworth" en augmentant le n:

<img width="282" alt="Screenshot 2023-01-27 102332" src="https://user-images.githubusercontent.com/87017143/215052470-fe5fb6d9-a412-40e6-9442-4dfcb159876a.png">

#### 2.Le paramètre K influence sur la rapidité de la transition entre la bande passante et la bande stop. Plus K est élevé plus la transition sera rapide.

<img width="415" alt="Screenshot 2023-01-27 101920" src="https://user-images.githubusercontent.com/87017143/215054880-92d34b70-771e-4043-841e-5548be1ba0d5.png">


<img width="412" alt="Screenshot 2023-01-27 101854" src="https://user-images.githubusercontent.com/87017143/215055047-fd886660-24ff-42d8-b7cf-f312ba6b72b6.png">

on crée un filtre Butterworth d'ordre 100 qui est un type de filtre passe-bas qui utilise une fonction de transfert caractéristique de Butterworth pour atténuer les fréquences élevées au-dessus d'une fréquence de coupure spécifiée. L'ordre du filtre détermine la rapidité avec laquelle les fréquences élevées sont atténuées au-delà de la fréquence de coupure. Un ordre élevé signifie une atténuation plus rapide des fréquences élevées.

<img width="386" alt="Screenshot 2023-01-27 104020" src="https://user-images.githubusercontent.com/87017143/215055374-1506f19c-8d6a-46c8-a3a0-5409cb2d46f7.png">
 On remarque qu'on a pu filtrer la musique en eliminant le bruit,
 (voir la figure ci-dessous) et et grâce à la commande Sound().
 
<img width="410" alt="Screenshot 2023-01-27 105030" src="https://user-images.githubusercontent.com/87017143/215057582-fe1ac487-3f16-4cde-9cb0-e76c51449d78.png">

le code:

<img width="365" alt="Screenshot 2023-01-27 105147" src="https://user-images.githubusercontent.com/87017143/215057638-4c814a82-a536-4272-8474-14d1c8ab5021.png">

