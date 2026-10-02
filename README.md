# Enseignes des stations-service françaises

Table de correspondance entre le **numéro officiel d'une station-service**
(celui du site [prix-carburants.gouv.fr](https://www.prix-carburants.gouv.fr/)
et du jeu de données « Prix des carburants en France ») et son **enseigne**
(TotalEnergies, Intermarché, E.Leclerc…).

Les prix officiels ne donnent que l'adresse des stations. Cette table sert à
l'application **Le Plein du Jour** (Freebox Player) pour afficher le nom de
chaque station.

| | |
|---|---|
| Stations | 9669 |
| Enseignes distinctes | 422 |
| Données OpenStreetMap du | 2026-10-02 15:22 (UTC) |

## Fichiers

- `enseignes.csv` : UTF-8, séparateur virgule, en-tête `id,enseigne`, trié par numéro.
- `enseignes.json` : objet `{ "numéro": "enseigne" }`.

## Comment elle est construite

1. Extraction OpenStreetMap (Overpass) de toutes les stations françaises
   `amenity=fuel` qui portent l'étiquette `ref:FR:prix-carburants` : le
   rapprochement se fait par ce numéro, jamais par la position.
2. Enseigne lue dans `brand`, sinon `name` (24 caractères au plus), sinon
   `operator`. Les valeurs sans information (« Independent », « Station
   service »…) sont ignorées.
3. Graphies fusionnées : Total → TotalEnergies, E. Leclerc → E.Leclerc,
   Système U / U / La Station U → Station U, Agip → Eni, AVIA → Avia, etc.
4. Seuls les numéros présents ce jour-là dans le flux officiel des prix sont
   gardés.

## Licences et attribution

**© les contributeurs d'OpenStreetMap.** Cette table est une base de données
dérivée d'[OpenStreetMap](https://www.openstreetmap.org/copyright), mise à
disposition sous la licence **Open Database License (ODbL) 1.0** : voir
[LICENSE](LICENSE). Toute réutilisation doit citer OpenStreetMap et ses
contributeurs, et une base dérivée de celle-ci doit rester sous ODbL.

Les numéros de stations proviennent du jeu de données « Prix des carburants
en France — flux instantané » du ministère de l'Économie
([data.economie.gouv.fr](https://data.economie.gouv.fr/explore/dataset/prix-des-carburants-en-france-flux-instantane-v2/)),
sous Licence Ouverte 2.0.
