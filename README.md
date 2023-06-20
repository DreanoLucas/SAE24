# SAE 24
## **Developpement d'attaque MiTM et de sécurisation du réseau**
### MITM
Fichier mitm/atk.py

#### ARP
Nous allons appliquer chacune des fonctions expliquées précédemment à un cas concret. Nous avons l’attaquant, le client et le serveur. Le client aura l’adresse IP 192.168.56.1 et le serveur 192.168.56.106. 
Nous utilisons donc notre script « script.py » qui permet d’utiliser les fonctions avec des arguments rentrées en option.  Nous commençons donc par l’utilisation de l’empoisonnement arp entre le client et le serveur, alors on envoie des paquets continuellement aux deux.  

![image](https://github.com/DreanoLucas/SAE24/assets/49568908/b625f15e-44e8-4176-a0a8-601eecf2f75e)

#### DHCP
Pour la fonction d’empoisonnement DHCP il suffit de lancer la fonction DHCP dans le fichier atk.py sans aucune entrée. On écoute le trafic, et lorsque l’on recoit une trame DHCP avec comme option discover nous y répondons avec une offer :

![image](https://github.com/DreanoLucas/SAE24/assets/49568908/488a44a4-5b20-4862-91ce-3cf915067654)

### Ecoute du réseau
Fichier mitm/listen.py

#### HTTP
Nous pouvons en parallèle sur un deuxième terminal écouter le client avec la fonction http nous obtiendrons alors pendant 10 secondes par défaut ou le temps rentré en option. Une lecture de toutes les requêtes http effectuées par le client vers le serveur est alors faite et nous pouvons les observées ici. 

![image](https://github.com/DreanoLucas/SAE24/assets/49568908/b6f03e6c-f002-4d23-bc6e-bee62bfc7c94)

#### SAUVEGARDE HTTP
Nous pouvons observer ces mêmes résultat dans les fichiers capture.json et capture.db comme expliquer dans leurs parties respectives.

![image](https://github.com/DreanoLucas/SAE24/assets/49568908/ab412cc4-6817-4714-a121-7bafbb371177)

![image](https://github.com/DreanoLucas/SAE24/assets/49568908/2c11f4bf-7b4f-4aa0-bed4-17102af2a036)

#### DNS
Nous pourrons maintenant utiliser l’écoute du trafic DNS qui nous donnera les noms de domaine demandé par le client avec la commande host 

![image](https://github.com/DreanoLucas/SAE24/assets/49568908/f44b48f2-d1c4-4d3f-88e6-8b4582863b98)

Notre client étant sur Windows ici nous avons inversé client et serveur pour cette étape. Avec la fonction DNS nous pourrons donc observer l’adresse demandée par le client : 

![image](https://github.com/DreanoLucas/SAE24/assets/49568908/e7fda5d5-c30a-4629-b768-7e06a55b5386)
