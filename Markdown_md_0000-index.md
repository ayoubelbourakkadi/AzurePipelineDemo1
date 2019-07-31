[Table des matières](./9999-toc.md) | [Suivant >](./0300-vueFonctionnelle.md)

# Application Information Document (AID) CANEL

Version : 0.4  
Date : 16/04/2018  
Statut : Draft  
[Version PDF](./site.pdf)  

## Historique des modifications
| Version | Date       | Auteur        | Description de la modification |
|---------|------------|---------------|--------------------------------|
|   0.1  | 05/04/2018 |  Nawfal El Bouzidy | Version initiale           |
|   0.2  | 12/06/2018 |  Nawfal El Bouzidy | Version à valider          |        

## Révisions

| Version | Description des changements | Date |
|---|---|---|
| 0.1 | Revue par Hervé | 05/04/2018 |
| 0.2 | Prise en compte des remarques + maj | 09/04/2018|
| 0.3 | Prise en compte remarque Yannick (schéma)| 10/04/2018|
| 0.4 | Intégration de l’application WSCandidat| 16/04/2018|
| 0.5 | Prise en compte des remarques EMLyon| 29/10/2018|


## Auteurs
| Rôle        | Nom           | Société |
|-------------|---------------|---------|
| Développeur | Nawfal El Bouzidy   | IBM     |


## Approbations
Ce document a été approuvé par les personnes suivantes :

| Rôle        | Nom           | Société |
|-------------|---------------|---------|
| [Rôle]      | [Auteur]      | [Société]     |

## Applications concernées
Ce document regroupe les applications listées dans le tableau ci-dessous :

| Application       |
|-----------------------------|
| CANEL     |
| WSCANDIDAT     |
| CANBEL     |

## Table des matières

- [Objectifs](./0000-index.md#objectifs)
- [Terminologie et Acronymes](./0000-index.md#terminologie-et-acronymes)
- [Vue Fonctionnelle](./0300-vueFonctionnelle.md)
- [Architecture Technique Générale](./0400-archiTechnique.md)
- [Bases de Donnees et Dossiers](./0500-baseDonnees.md)
- [Interfaces / services](./0600-interfacesServices.md)
- [Batchs Jobs](./0700-batchs.md)
- [Interfaces Utilisateurs](./0800-interfacesUtilisateurs.md)
- [Environnement](0900-environnement.md)
- [Procédure De Backup](./1000-procedureDeBackup.md)
- [Procédure De Deploiment](./1100-procedureDeploiement.md)
- [Activites Périodiques](./1200-activitesPeriodiques.md)
- [Normes Et Conventions](./1300-normesEtConventions.md)
- [Contact métier / AMOA](./1400-contactsmetierAmoa.md)
- [Historique de l'Application](./1500-historiqueApplication.md)
- [Documents De Référence](./1600-documentsReference.md)

#	Objectifs

L'objectif du document descriptif d’application (AID) est de fournir aux membres de l'équipe une vue d'ensemble de l'application CANEL.  L'AID décrit la fonction de l'application, la structure des applications, la configuration de l’application et l'environnement technique. Ce document pourra faire référence à n'importe quelle documentation existante.
L'équipe de delivery tiendra l'AID à jour durant toute la vie de l'application CANEL.


# Terminologie et Acronymes
Les acronymes et la terminologie spécifiquement utilisés dans ce document sont décrits ci-dessous.  D'autres acronymes utilisés généralement peuvent être trouvés dans l'ASCP.

| Numéro       |     Terminologie/acronymes	Définition     |        Définition |
| :------------: | :-------------: | :-------------: |
| 1       |     AID     |        Document descriptif d’application |
| 2       |     SME     |        Expert applicatif |
| 3	| ASTF|	Admission sur titre français  
| 4 |	M.S.|	Les mastères spécialisés
| 5	| iMBA|	International MBA
| 6	| GLUX|	MSc in Luxury Management and Marketing
| 7	| EMM|	European Master in Management
| 8	| GEP	|Global Entrepreneurship Program
| 9	| SOIM|	MSc in Sports and Outdoor Industry Management
| 10	| IDEA|	Msc in Innovation, Design, Entrepreneurship & Arts
| 11	| PGM	|Programme Général de Management
| 12	| DUA|	Diriger une activité
| 13	| AMP|	Advanced Management Programme
| 14	| EMBA|	Executive MBA
| 15	| CANEL| Candidature en Ligne
|16|	Concours |	Concours d’entrée, chaque programme est associé à un ou plusieurs concours d’entrée
|17|	Session|	Chaque concours peut être proposé une ou plusieurs fois dans l’année. Une session correspond donc à une plage datée d’ouverture d’un concours
|18|	Candidat intégré | C’est le statut ultime pour un candidat. Il est passé par le statut « admissible », puis « admis » et il a confirmé son admission en payant notamment les arrhes. Il devient alors « intégré » ce qui représente la dernière action réalisée coté Back Office. |
|19|	Phase |	Chaque session présente une ou plusieurs phases, qui sont des périodes datées. On retrouve très souvent la suite de phases suivante : candidature en ligne, remise des pièces annexes, selon le concours éligibilité, admissibilité, admission et intégration. Ceci n’est pas une obligation, le nombre de phases et leur enchainement doit pouvoir être paramétré au sein du concours
|20 |	Back-office |	Accès administratif aux dossiers de candidatures, réservé à un personnel identifié. Cet accès permet toute action sur les dossiers et leur qualification. Il permet également l’accès aux opérations globales de calcul, extraction, édition, changement de statut, reporting et statistiques ….|
| 21	| Front-office |	Accès au remplissage des dossiers de candidatures pour les candidats et à la visibilité d’avancement de son dossier une fois transmis à EMLYON. |
| 22|	Candidat|	Internaute ayant fait une demande d’ouverture de dossier de candidature. Attention, il peut y avoir méprise de signification car il y a deux façons de voir les choses. Appellation usuelle : Quand un internaute démarre un dossier de candidature on l’appelle candidat …. Mais, Appellation officielle : Il n’est vraiment candidat que lorsque nous avons reçu son véritable dossier « papier » avec toutes les pièces annexes officielles.
|23 |	Noyau (du dossier) |	C’est la partie du dossier de candidature commune à tous les concours et concerne directement le candidat. Elle regroupe la partie « état civil », la partie « Coordonnées » et la partie « Diplôme ». Cette partie est commune pour tous les dossiers de candidatures sur lesquels un même candidat postule. Note : Un candidat peut effectivement présenter en parallèle plusieurs dossiers de candidature de types différents (c.à.d. de famille de concours différents)|
|24 |	Partie paramétrée du dossier (dite « dossier dynamique ») |	Le dossier dynamique représente une ossature ‘vierge’ d’un dossier de candidature que doivent remplir les candidats, entièrement en ligne. Il est potentiellement différent pour chaque concours. Ce dossier n’est pas figé dans le temps, mais peut évoluer d’exercice en exercice. Il reste fixe (au moins en termes de zones de saisie) une fois la 1ère session du concours ouverte sur l’exercice en cours. Dans les faits, on tente de minimiser le nombre de dossiers dynamiques différents en affectant le même modèle au plus grand nombre possible de concours. |
|25 |	Campus	| Site géographique géré par EMLYON pour accueillir des étudiants en formation. Actuellement EMLYON dispose de 2 campus : 1 à Ecully (23 avenue Guy de Collonges) appelé aussi « Campus Europe », 1 à Shanghai, appelé aussi « Campus Asie ». Les choses peuvent évidemment évoluer et les campus se multiplier, on parle alors de multi-campus.
| 26	|AESCRA|	AESCRA est le nom juridique de la maison mère EMLYON. Cela signifie Association pour l’Enseignement Supérieur Commercial en Rhône-Alpes.
| 27	| Grande Ecole |	C’est le nom qui regroupe les programmes de formation initiale. |
| 28	| Programmes Master’s |	Il s’agit de l’ensemble des programmes de formation au sein de la Grande Ecole qui délivrent le grade Master. |
| 29|	CDME|	CDME est le nom juridique de la filiale de formation continue. |
| 30	| Executive Development |	C’est le nom commercial de la filiale de formation continue. |
|31  |	Programme |	Formation particulière à laquelle un participant s’inscrit et qu’il va suivre durant une période déterminée. EMLYON compte environ 30 programmes dans la Grande Ecole et 10 dans Executive Development. Tous ne sont pas concernés par l’application de gestion des concours dont nous parlons dans ce document.
|32|	Application de mise en ligne des résultats	| Application WEB existante qui permet d’afficher sur nos sites le résultat des candidats à nos concours en fonction des phases d’admissibilité ou d’admission. |
| 33 |	Application d’inscriptions aux oraux |	Application WEB existante qui permet à un Back Office de renseigner une suite de dates d’oral possibles par concours (avec des plafonds d’accueil pour chaque date) et aux candidats de s’inscrire sur une date particulière pour venir passer ses épreuves orales (sur 1 journée). |
|34 |	Dossier complet |	Dossier complètement renseigné, validé par le candidat et dont toutes les pièces annexes ont été transmises et réceptionnées par le service de sélection.|
|35|	Dossier incomplet|	Dossier complètement renseigné, validé par le candidat et dont au moins une des pièces annexes n’a pas encore été réceptionnée par le service de sélection.|
|36|	Dossier non éligible	|Candidature ne pouvant être retenue pour passer la phase d’amissibilité et/ou d’amission (mauvais diplôme, note insuffisante, …)|
|37|	Admissibilité |	Etape (phase) du concours qui concerne les épreuves écrites. Ces épreuves arrivent généralement avant les épreuves orales et permettent une première sélection. Le candidat déclaré non admissible, arrête là son parcours de candidat. Celui déclaré admissible peut poursuivre en se présentant à l’oral. |
|38|	Admission |	Etape (phase) du concours qui concerne les épreuves orales. Le candidat déclaré non admis, arrête là son parcours de candidat. Celui déclaré admis peut immédiatement nous préciser s’il accepte d’être intégré à l’Ecole. Une dernière possibilité réside dans l’admission sur liste supplémentaire. En fonction du nombre d’admis qui va décliner l’intégration on fait appel aux candidats sur cette liste là qui passent alors de admis en liste supplémentaire à admis. |
|39 |	Candidat intégré	| C’est le statut ultime pour un candidat. Il est passé par le statut « admissible », puis « admis » et il a confirmé son admission en payant notamment les arrhes. Il devient alors « intégré » ce qui représente la dernière action réalisée coté Back Office. |
|40|	Concours liés	| Il s’agit de concours ayant les mêmes principes d’admission et le même MDDC. Pour de tels concours, il est possible pour le candidat de mentionner un concours de « substitution » (donc un programme de substitution), si sa candidature au 1er concours n’est pas pertinente. A l’heure actuelle, seuls les 12 concours des Mastères Spécialisés sont considérés comme liés mais cela pourrait être étendu.|

[Table des matières](./9999-toc.md) | [Suivant >](./0300-vueFonctionnelle.md)
