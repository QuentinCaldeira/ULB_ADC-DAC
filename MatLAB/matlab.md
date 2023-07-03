# Contraintes Data Acquisition Toolbox et NI PCIe 6323

## Spécifications de la carte NI PCIe 6323

### Entrées analogiques

- Sample Rate maximal de 250 kS/s
- Taille de la mémoire FIFO de 4095 échantillons
- Transfert de données DMA

### Sorties analogiques

- Sample Rate de 900 kS/s maximum si une sortie active
- Sample Rate de 840 kS/s maximum si deux sorties actives
- Sample Rate de 775 kS/s maximum si trois sorties actives
- Sample Rate de 719 kS/s maximum si quatre sorties actives
- Taille de la mémoire FIFO de 8191 échantillons répartis entre les quatre sorties
- Transfert de données DMA

## Fonctions utilisées de la Data Acquisition Toolbox


- `daq` qui permet de créer un objet DataAcquisition
- `addinput` qui permet d'ajouter des entrées
- `addoutput` qui permet d'ajouter ddes sorties
- `start` qui permet de lancer une acquisition en arrière plan
- `read` qui permet de récupérer les données acquises
- `flush` qui permet de vider les buffers

## Test réalisé

Pour tester la carte, on génère un signal PWM continu sur `ctr0`, le pin 2 de la carte. On connecte un bouton poussoir sur `ai3`, le pin 30 de la carte. On visualise le signal PWM généré à l'oscilloscope. On souhaite avoir un signal PWM avec un rapport cyclique de 0,2. Si le bouton est enclenché, le rapport cyclique passe a 0,8.

## Observations et explications

- Le signal PWM est correctement généré. Sa fréquence peut montée à 100 kHz sans problèmes
- La détection du bouton ne se fait pas correctement. Il s'avère que le SampleRate par défaut est de 1000 échantillons par seconde, ce qui fais une période de 1 ms. Hors, le temps d'exécution de la fonction `read` pour receuillir un échantillons est supérieur à 1 ms. La mise à jour des échantillons n'est donc pas perçue par le programme.
- Un SampleRate plus faible permet de détecter l'actualisation du bouton. Il faut que la mise à jour des échantillons soit plus rapide que le temps d'exécution de la lecture
- Lire un plus gros paquet d'échantillons permet une meilleure détection. En effet, la carte stocke 4095 données puis les envoi au PC. En faisant une lecture simple, on lui demande de faire un transfert pour seulement 1 échantillon. 

## Solutions envisagées

- Réduire le SampleRate pour atteindre des temps inférieur au temps d'exécution de la fonction `read`. Le problème est qu'il ne sera pas possible d'agir rapidement sur un procédé (temps de réaction facilement supérieur à la dizaine voir centaine de ms)
- Prendre plus d'échantillons et les moyenner. L'acquisition se fera plus rapidement. Le problème est que ça rajoute du temps de processing des données après l'acquisition, et perte de précision de la mesure en faisant un moyennage sur plusieurs échantillons
- Trouver une fonction plus **bas-niveau** afin de gagner en temps d'exécution sur la lecture d'un échantillon. Cela permettra de pouvoir augmenter le SampleRate.