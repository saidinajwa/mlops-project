# Réflexion — TP2

1. Quel est le meilleur des 3 modèles ? Peut-on le prouver ?
   -> 

2. Peut-on redonner exactement le modèle de l'Essai 1 ?
   -> 

3. Un camarade peut-il reproduire notre travail sur une autre machine ?
   -> 

# Réflexion — TP3

1. Quel est le meilleur modèle, et peut-on le prouver ?
   -> J'ai enregistré mes trois essais comme trois runs dans MLflow, avec leurs paramètres et leurs métriques. En les triant par f1, `essai-1` et `essai-3` arrivent à égalité (0.889), et `essai-2` est nettement plus faible (0.333). J'ai retenu `essai-3` parce qu'à performance égale, il vaut mieux garder le modèle le plus simple (il n'utilise pas la colonne salaire). Le f1 est plus fiable que l'accuracy ici, car très peu de clients partent. Le résultat est daté, conservé et visible dans l'interface.


2. Peut-on redonner exactement le modèle de l'Essai 1 ?
   ->  Oui. MLflow garde le modèle de chaque run, rangé sous l'identifiant du run. Avec `mlflow.sklearn.load_model("runs:/<id>/model")`, je recharge le modèle exact d'un essai sans le ré-entraîner. Je l'ai vérifié avec le script `charger_modele.py`, qui recharge le meilleur modèle et prédit sur un nouveau client.


3. Un camarade peut-il reproduire notre travail sur une autre machine ?

   ->Pas entièrement. Il récupère le code avec Git, et chaque run note les paramètres et les versions des bibliothèques. Mais les dossiers `mlruns/` et `mlflow.db` restent sur ma machine (ils sont dans le `.gitignore`), donc il ne voit pas mes runs et doit relancer les scripts. Son environnement peut aussi différer du mien.