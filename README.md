# IA PROJET 8

Cette API utilise un modèle de deep learning pour effectuer la segmentation sémantique d'images. Elle est construite avec Flask et TensorFlow.

## Fonctionnalités

Segmentation sémantique d'images
Utilisation d'un modèle ResNet34 FPN pré-entraîné
Génération de masques de segmentation colorés

## Prérequis

Python 3.x
Flask
TensorFlow
Pillow
NumPy
Matplotlib

## Installation

Clonez ce dépôt
Installez les dépendances :
Copypip install flask tensorflow pillow numpy matplotlib

Assurez-vous que le modèle pré-entraîné est présent dans le répertoire du projet :
Copyresnet34_fpn_0.5v2_jaccard_loss_augTrue.tf


## Utilisation

Démarrez le serveur Flask :
app.py

L'API sera accessible à l'adresse http://localhost:5000

Routes

/ : Page d'accueil de l'API
/predict_mask : Endpoint pour la segmentation d'image (méthode POST)

Exemple d'utilisation
Pour segmenter une image, envoyez une requête POST à /predict_mask avec l'image dans le corps de la requête :
import requests

url = "http://localhost:5000/predict_mask"
files = {"image": open("chemin/vers/votre/image.jpg", "rb")}
response = requests.post(url, files=files)

with open("masque_segmentation.png", "wb") as f:
    f.write(response.content)
Fonctionnement

L'image est redimensionnée à 256x128 pixels (taille d'entrée du modèle).
Le modèle prédit un masque de segmentation.
Le masque est converti en une image RGB colorée.
L'image résultante est renvoyée au client.

## Classes de segmentation

0 : void (vide)
1 : flat (plat)
2 : construction
3 : object (objet)
4 : nature
5 : sky (ciel)
6 : human (humain)
7 : vehicle (véhicule)

## Remarques

Le modèle utilisé est resnet34_fpn_0.5v2_jaccard_loss_augTrue.tf.
Les dimensions d'entrée du modèle sont fixées à 256x128 pixels.
Les résultats de la segmentation sont temporairement stockés dans tmp.png.

Contribuer
Les contributions sont les bienvenues ! N'hésitez pas à ouvrir une issue ou à soumettre une pull request.# IA_projet08
