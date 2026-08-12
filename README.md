# SunuDiag

**SunuDiag** est un outil intelligent de pré-diagnostic pédagogique du paludisme.

---

## Présentation

SunuDiag est une application web développée dans le cadre du **Master 1 Intelligence Artificielle et Big Data (UAHB)**.

L’application utilise un modèle de **Machine Learning** pour estimer le risque de paludisme à partir de quelques informations simples sur le patient.

L’objectif n’est pas de donner un diagnostic médical. L’outil sert principalement à **faire une première estimation et à orienter l’utilisateur**, notamment dans un contexte pédagogique.

**Auteur : DEGUENE Fall**

---

## Modèle utilisé

SunuDiag utilise un modèle de **Random Forest** pour effectuer les prédictions.

Le modèle a été entraîné avec le jeu de données **DataSANTE-221**.

Sur les données de test, le modèle obtient une **AUC d’environ 0,66**.

---

## Informations utilisées

Pour faire une estimation, l’application utilise cinq informations :

* **Âge**
* **Température**
* **Glycémie**
* **Hémoglobine**
* **Saison** : saison des pluies ou saison sèche

Ces informations sont envoyées à l’API, qui les transmet ensuite au modèle pour obtenir une estimation.

---

## Comment comprendre le résultat ?

Le résultat est présenté sous forme de niveau de risque :

* **Moins de 30 %** → risque faible
* **De 30 % à moins de 50 %** → risque à surveiller
* **50 % ou plus** → il est recommandé de consulter un professionnel de santé

Ces valeurs servent uniquement à **interpréter le résultat du modèle**. Elles ne constituent pas un diagnostic médical.

---

## Organisation du projet

Le projet est organisé en plusieurs parties :

```text
SunuDiag/
│
├── api/          → API FastAPI qui permet d'utiliser le modèle
├── frontend/     → Interface web utilisée par l'utilisateur
├── models/       → Modèle de Machine Learning sauvegardé
├── train.py      → Script utilisé pour entraîner le modèle
├── Dockerfile    → Configuration utilisée pour le déploiement
└── README.md     → Documentation du projet
```

Cette organisation permet de **séparer les différentes parties de l'application** et de faciliter sa maintenance.

---

## Fonctionnement général

Le fonctionnement de SunuDiag est simple :

1. L’utilisateur ouvre l’application.
2. Il renseigne les cinq informations demandées.
3. Le frontend envoie les données à l’API FastAPI.
4. L’API vérifie les données reçues.
5. Le modèle Random Forest analyse les informations.
6. Le modèle retourne une estimation du risque.
7. L’application affiche le résultat à l’utilisateur.

---

## Déploiement

L’application est déployée sur **Render**.

Le **Dockerfile** permet de préparer l’application et son environnement afin de pouvoir la déployer sur le serveur.

L’API FastAPI permet ensuite au frontend de communiquer avec le modèle de Machine Learning.

---

## Avertissement

⚠️ **SunuDiag est uniquement un outil pédagogique.**

Il ne remplace pas un médecin, un professionnel de santé ou un test biologique.

Le résultat donné par l’application est seulement une **estimation basée sur un modèle de Machine Learning**. En cas de doute ou de symptômes, il est important de consulter un professionnel de santé.

---

## Licence

Ce projet est distribué sous licence **MIT**.

**© 2026 DEGUENE Fall**

🌐 **Tester l’application :** https://sunudiag-jx86.onrender.com/
