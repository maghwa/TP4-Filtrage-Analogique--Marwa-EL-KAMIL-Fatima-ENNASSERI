# TP4-Filtrage-Analogique--Marwa-EL-KAMIL-Fatima-ENNASSERI
#### Réalisé par: 
- Fatima  Ennassiri (Filière: Cyber Security)
- Marwa El Kamil(Filière: Artficial Intelligence)
### Encadré par:
- Mr Alae Ammour

### Objectifs:
- Appliquer un filtre réel pour supprimer les composantes indésirables d’un signal. 
- Améliorer la qualité de filtrage en augmentant l’ordre du filtre.
### Diagramme de Bode:

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
 
