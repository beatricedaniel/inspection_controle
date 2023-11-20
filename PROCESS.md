# INSPECTION_CONTROLE
Processus de mise-à-jour des tableaux de bord https://arssante.opendatasoft.com/pages/inspection-controle/

## critères de l'extraction SIICEA
- date de début = date début du plan d'IC sur date réelle de visite
- pas de date de fin
- type d'établissement = EHPAD
- statut de mission = tous

## préparation des fichiers sources (extractions SIICEA)

### fichier missions
- missions réalisées
type de cible = ehpad
date réelle de visite comprise entre la date de début du plan d'IC et la date de fin d'extraction demandée par la DGCS (fin du trimestre)
statut = maintenu ou clôturé
- missions prévisionnelles
type de cible = ehpad
date réelle de visite = null
date provisoire de visite > date choisie en date de fin pour le fichier des missions réalisées
statut = maintenu ou reporté (?)

### fichier décisions
ras

### t_finess
filtrer sur caégorie = 500

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

### communes
table destination : ref_insee_communes

## préparation des fichiers output
- export des requêtes vers des tables : 1 table / fichier
- dans chaque table remplacer les libellés régions
- dans chaque table remplacer niveaux géo en NC

