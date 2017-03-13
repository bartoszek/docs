Introduction
============

Notre projet est basé sur l'implémentation et le déploiement d'un réseau VLAN 10Go de premier ordre qui prendra le relais de notre actuel réseau de style 'empilé' , qui a été assemblé au fil des années, et qui est maintenant à la limite extrême de sa capacité d'expansion. Ce qui nécessite une refonte majeure accompagnée une mise à jour du matériel qui va non seulement accroître la vitesse d'accès au réseau mais aussi permettre une croissance efficace, logique et économique pour l'avenir.

Une fois la nouvelle infrastructure réseau en place, nous pourrons aborder la seconde phase de ce projet : le déploiement d'un système de Stockage NAS de dernière génération.

Une architecture de ce type est aujourd’hui la norme des systèmes d’informations des entreprises.

Les stratégies antisinistres font aussi aujourd'hui partie des schémas directeurs de ces architectures et propose des technologies Raid0 a Raid6.
Nous prevoyons d'installer , hors nodal , un systeme leger de type QNAP qui permettra de sauvegarder de maniere incrémentale les données du serveur principal.En cas de sinistre dans le nodal , par exemple , nous disposerons alors d'une sauvegarde disponible.

Notre réseau actuel ayant été conçu au cours des années, a atteint ses capacités maximales en termes de performance et d'extension. Nous avons donc besoin de rebâtir entièrement notre réseau sur de nouvelles bases totalement indépendantes, et en faisant ainsi, de nous mettre au niveau de nos concurrents ou même de les dépasser. Cela nous permettra d’étendre notre capacité à chercher et à obtenir des projets plus importants.

Description du Projet
=====================

La société s'est équipée début 2011 d'un serveur NAS de type BlueArc d'une capacité de 15 Téraoctets.Ce serveur centralise distribue ses données a un ensemble de clients hétérogènes (Mac/Windows/Linux) a travers un réseau 1 Gigabit.

La societe BlueArc a ete rachete peu apres par la societe Hitachi.Aujourd'hui les produits BlueArc ne sont plus maintenus par Hitachi (Hds) rendant ce materiel peu a peu obsolete.

Ce projet consiste aujourd'hui a : 

- renouveler notre serveur de stockage centralisé NAS et en accroître la capacité a 40Teraoctets.
- upgrader l'ensemble du réseau a un débit de 10 Gigabits.
- mettre en place un serveur de Backup de type QNAP mini NAS permettant de sécuriser l'ensemble des données.

Phases du projet
================

- Analyse et étude du réseau actuellement en place afin d'établir une topologie schématique

- Recherche et conception d'un réseau complexe adapté aux besoins techniques exigeants de l'entreprise.

- Préparation, à l'aide des résultats obtenus précédemment, du plan de mise en place de la nouvelle infrastructure 

- Installation du nouveau matériel et du câblage associé

- Migration des clients du réseau vers le nouveau matériel, test et stress-test du réseau

- Préparation du plan de mise en place du nouveau stockage.

- Réception et installation du nouveau serveur

- Migration des données du stockage actuel vers le nouveau système

- tests et développement/migration des outils de gestion et d'archivage

R&D :Integration et mise a niveau des outils logiciels
======================================================

Nous prévoyons d'attribuer des ressouces d'ingénieur de Développement Système  afin d'adapter l'ensemble de nos outils a la nouvelle infrastructure et a l'automatisation des taches d'archivage et de backup.

Aspect Environemental de la solution choisie
============================================

Le prestataire choisi (APY micro) choisit ses composants dans un souci de consommation électrique le plus faible possible.Il est aussi sensible au recyclage des emballages (cartons ferrailles , plastique) des composants utilisés.Ils limitent notament l'utilisation de materiel sur-emballé par l'achat de composants OEM/bulk.
