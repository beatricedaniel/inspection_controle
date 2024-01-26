# INSPECTION_CONTROLE
Processus de mise-à-jour des tableaux de bord https://arssante.opendatasoft.com/pages/inspection-controle/

## préparation des fichiers sources (extractions SIICEA)
### pour mission_EHPAD
- type de cible = "Etablissements et Services pour Personnes Agées"
- type de mission != Audit ; Audit franco-wallon
- date réelle de visite >= début du programme d'IC
- statut de mission != "abandonné" et "reporté"
### pour mission_EHPAD_prog
- type de cible = "Etablissements et Services pour Personnes Agées"
- - type de mission != Audit ; Audit franco-wallon
- statut de mission != "abandonné"
- date réelle de visite = NULL
- date provisoire de visite >= date de l'extraction
### pour SICEA_export_missions_Decisions_suivis
- RAS
### pour t_finess_500
- https://www.data.gouv.fr/fr/datasets/referentiel-finess-t-finess/
- etat = "ACTUEL"
- categ_code = 500

## import des fichiers en BDD
prérequis : convertir les fichiers .xlsx en .csv via le script convert_excel_to_csv.py 

### missions réalisées
table destination : mission_EHPAD

### missions prévisionnelles
table destination : mission_EHPAD_prog

### décisions
table destination : SICEA_export_missions_Decisions_suivis

### finess
table destination : t_finess_500

### modifications a posteriori sur DWH
- DWH_MISSIONS_AGG_COMMUNE:
*Normandie
*Saint-Pierre
*Guadeloupe
*Guadeloupe
- 
### communes
table destination : ref_insee_communes

## préparation des fichiers output
- export des requêtes vers des tables : 1 table / fichier
- dans chaque table remplacer les libellés régions
- dans chaque table remplacer niveaux géo en NC

## traitements dans ODS
- attention spécifique dernière version : filtre date réelle de visite <01/01/2024
