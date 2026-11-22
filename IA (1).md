# IA.md — Problèmes rencontrés et solutions (TP 2 – Application Web)

## 1. Dépendances Maven (`pom.xml`)

**Problème rencontré :** La propriété `${langchain4j.version}` apparaissait en rouge dans le fichier `pom.xml`. Les dépendances du projet devaient également être vérifiées pour respecter les consignes du TP.

**Solution appliquée :** Vérification de la section `<properties>` et déclaration de la version de LangChain4j utilisée. Les dépendances ont été comparées avec la configuration du TP précédent qui fonctionnait, puis limitées à celles nécessaires au TP 2.

## 2. Rôle système et mémoire de conversation

**Problème rencontré :** Il fallait s'assurer que le rôle choisi par l'utilisateur soit bien pris en compte par l'assistant et qu'il ne soit pas mélangé avec le contexte d'une conversation précédente.

**Solution appliquée :** Lors du changement de rôle, l'ancienne mémoire de conversation est vidée, puis le nouveau rôle est ajouté sous forme de message système. Des essais ont permis de vérifier que l'assistant respecte le rôle sélectionné.

## 3. Variable d'environnement Gemini

**Problème rencontré :** La clé API Gemini n'était pas directement accessible depuis la configuration de lancement Payara dans IntelliJ.

**Solution appliquée :** Création de la variable d'environnement Windows `GEMINI_KEY`, puis redémarrage d'IntelliJ afin que l'IDE récupère cette variable. La clé est ainsi lue depuis l'environnement avec `System.getenv()` au lieu d'être écrite directement dans le code.

## 4. Liaison du projet à GitHub

**Problème rencontré :** Lors du push, IntelliJ affichait le message « Define remote », car aucun dépôt distant n'était encore associé au projet local.

**Solution appliquée :** Création du dépôt GitHub `tp2-web`, puis association du projet local à ce dépôt. Après cette configuration, les commits locaux pouvaient être envoyés sur GitHub avec un push.

## 5. Tests de l'application

**Problème rencontré :** Il fallait vérifier que le rôle système était respecté pendant plusieurs messages et que le changement de rôle modifiait bien le comportement de l'assistant.

**Solution appliquée :** Réalisation de tests avec le rôle « Traducteur Anglais-Français », puis avec le rôle « Guide touristique ». Les réponses obtenues ont permis de vérifier la traduction de plusieurs messages, la conservation du rôle pendant la conversation et le changement de comportement après sélection d'un nouveau rôle.

## 6. Vérification des dépendances et de la compilation

**Problème rencontré :** Le professeur a signalé une erreur possible dans les dépendances du projet.

**Solution appliquée :** Exécution des commandes `mvnw.cmd clean package` et `mvnw.cmd dependency:tree` pour vérifier la compilation et les dépendances. La commande de compilation s'est terminée avec le résultat `BUILD SUCCESS` et les dépendances ont été résolues. L'erreur signalée n'ayant pas été reproduite, son origine n'a pas pu être confirmée.

## 7. Nombre de commits Git

**Problème rencontré :** Le professeur a indiqué que le dépôt ne contenait que deux commits, alors que quatre étapes de suivi étaient attendues.

**Solution appliquée :** Vérification de la différence entre un dépôt GitHub et un commit. Un dépôt contient le projet, tandis qu'un commit enregistre un état du projet. Les quatre étapes à enregistrer séparément sont : la page JSF, le backing bean, l'intégration des fonctionnalités demandées et les tests. 
