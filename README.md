## GeoCall-BF - Évolution V1 à V9

**V1 - Base** 
Version de départ avec juste `Text("Hello Android!")` centré. Objectif : vérifier que le projet Compose compile et s’affiche sans erreur sur un téléphone Android. Pas de bouton, pas de permission. 

**V2 - Bouton URGENCE** 
Ajout d’un gros bouton rouge de 200dp avec le texte `URGENCE` en blanc, taille 24sp. Le `onClick` est vide pour l’instant. C’est l’interface de base qui sera utilisée pour déclencher l’alerte. 

**V3 - Permissions** 
Ajout des 2 permissions critiques dans `AndroidManifest.xml` : `SEND_SMS` pour envoyer l’alerte et `ACCESS_FINE_LOCATION` pour récupérer la position GPS. Sans ça, les versions suivantes ne fonctionnent pas. 

**V4 - Contacts d’urgence** 
Interface avec 3 `OutlinedTextField` pour enregistrer les numéros 1, 2 et 3. Utilise `SharedPreferences` pour sauvegarder avec les clés `n1`, `n2`, `n3`. Bouton `Sauver` pour valider. C’est le cœur de l’app : sans contacts, pas d’alerte. 

**V5 - Carte Google Maps** 
Intégration de `com.google.maps.android:maps-compose:4.3.3`. Affiche une `GoogleMap` centrée sur Ouagadougou `LatLng(12.3714, -1.5197)` zoom 15f. Ajout d’un `Marker` intitulé `Tu es ici`. Permet de voir la position avant envoi. 

**V6 - Historique** 
Ajout d’une `LazyColumn` pour lister les alertes envoyées. `historique` est un `mutableStateOf(listOf("Aucune alerte"))`. À chaque alerte, on ajoute `Alerte $timestamp` en haut de liste et on garde les 10 dernières. Utile pour les preuves. 

**V7 - Mode SMS sans internet** 
Vérification réseau avec `ConnectivityManager`. Si pas d’internet, l’app affiche `Mode SMS activé - Pas d'internet` et force l’envoi par SMS uniquement. Important pour les zones rurales du Burkina avec mauvaise connexion. 

**V8 - Multilingue** 
Gestion de toutes les langues parlées au Burkina Faso. Variable `langue` en `mutableStateOf("fr")`. Bouton pour changer. Le texte du bouton `URGENCE` s’adapte. Rend l’app accessible à tous. 

**V9 - Design Burkina Faso** 
Application des couleurs du drapeau : `vertBF = Color(0xFF009E60)` et `rougeBF = Color(0xFFEF2B2D)`. Le bouton `URGENCE` a un fond rouge et texte vert. Donne une identité nationale forte à l’appli. 
