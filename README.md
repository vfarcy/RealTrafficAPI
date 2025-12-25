# RealTrafficAPI

## Présentation

Ce projet propose une suite de scripts Python pour interagir avec l’API RealTraffic, permettant d’obtenir et d’exploiter des données aéronautiques en temps réel : trafic aérien, météo, informations aéroportuaires, etc. Il s’adresse aux passionnés d’aviation, développeurs, chercheurs ou toute personne souhaitant analyser ou visualiser le trafic aérien mondial.

## Fonctionnalités principales
- **Authentification** à l’API RealTraffic (gestion de licence).
- **Récupération du trafic aérien** autour d’un point ou d’un aéroport.
- **Recherche de vols** (callsign, numéro de vol, immatriculation, etc.).
- **Récupération des METAR/TAF** (météo) pour les aéroports proches.
- **Affichage graphique** des avions sur une carte (matplotlib/cartopy).
- **Diffusion des données** sur le réseau local via UDP.
- **Analyse des pistes actives**, du vent, et des mouvements d’avions (arrivées/départs).
- **Exploration de la base de données aéroportuaire** locale (SQLite).

## Structure du projet
- `API_tester.py` : Script principal, illustre toutes les fonctionnalités de l’API, diffusion UDP, affichage graphique, etc.
- `API_traffic.py` : Récupère et affiche le trafic aérien.
- `API_weather.py` : Récupère et affiche la météo (METAR, TAF).
- `API_airportinfo.py` : Informations détaillées sur un aéroport.
- `API_sigmet.py` : Récupère les SIGMET (bulletins météo dangereux).
- `API_search.py` : Recherche de vols par différents critères.
- `API_nearestmetar.py` : Trouve les METAR les plus proches d’un point.
- `API_active_runway.py` : Analyse des pistes actives et du vent.
- `requirements.txt` : Dépendances Python nécessaires.
- `.gitignore` : Fichiers/dossiers à exclure du versionnement.

## Installation

1. **Cloner le dépôt** :
   ```bash
   git clone <url-du-repo>
   cd RealTrafficAPI
   ```
2. **Créer un environnement virtuel** :
   ```bash
   python -m venv .venv
   .venv\Scripts\activate  # Windows
   # ou
   source .venv/bin/activate  # Linux/Mac
   ```
3. **Installer les dépendances** :
   ```bash
   pip install -r requirements.txt
   ```

## Utilisation


### Prérequis
- Une licence RealTraffic valide (fichier `RealTraffic.lic` ou clé à fournir en argument).
- La base de données aéroportuaire fournie avec RealTraffic (`navdb.s3db`).

#### Où se trouve le fichier `navdb.s3db` ?

- **Windows** : `C:\\Users\\<VotreNom>\\AppData\\Roaming\\InsideSystems\\navdb.s3db`
- **Mac/Linux** : `~/Documents/.InsideSystems/navdb.s3db`

Vous pouvez aussi spécifier son emplacement avec l’option `-d` ou `--dbdir` lors de l’exécution des scripts.

### Exemples de commandes

- **Trafic autour d’un aéroport :**
  ```bash
  python API_tester.py -a LFPG -l VOTRE_LICENCE
  ```
- **Trafic autour d’une position :**
  ```bash
  python API_tester.py --lat 48.85 --lon 2.35 -l VOTRE_LICENCE
  ```
- **Affichage graphique en temps réel :**
  ```bash
  python API_tester.py -a LFPG --livemap -l VOTRE_LICENCE
  ```
- **Recherche de vol :**
  ```bash
  python API_search.py -l VOTRE_LICENCE -p Callsign -s AF123
  ```

### Paramètres courants
- `-a`, `--airport` : Code ICAO de l’aéroport
- `--lat`, `--lon` : Latitude/longitude du centre de la zone
- `-l`, `--license` : Clé de licence RealTraffic
- `--livemap` : Affichage graphique en temps réel
- `-r`, `--radius` : Rayon de recherche (km)
- `-d`, `--dbdir` : Dossier contenant la base navdb.s3db

Voir chaque script pour la liste complète des options (utiliser `-h`).

## Conseils pédagogiques
- Lisez le code source pour comprendre la structure des requêtes API et le traitement des réponses.
- Les scripts sont conçus pour être facilement modifiables et réutilisables.
- Les exemples fournis couvrent la plupart des cas d’usage de l’API RealTraffic.
- Utilisez l’affichage graphique pour visualiser le trafic en temps réel.
- Les erreurs sont loguées dans des fichiers texte pour faciliter le debug.

## Dépendances principales
- requests
- psutil
- matplotlib
- cartopy
- textalloc
- numpy

## Limitations et remarques
- L’API RealTraffic nécessite une licence valide.
- Certaines fonctionnalités requièrent la base de données aéroportuaire locale.
- Les scripts sont fournis à titre d’exemple et peuvent être adaptés à vos besoins.

## Licence
Ce projet est fourni à des fins pédagogiques. Respectez les conditions d’utilisation de l’API RealTraffic.
