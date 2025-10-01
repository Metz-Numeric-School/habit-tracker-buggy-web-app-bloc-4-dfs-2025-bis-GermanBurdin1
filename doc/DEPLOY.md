# Procédure de Déploiement

Décrivez ci-dessous votre procédure de déploiement en détaillant chacune des étapes. De la préparation du VPS à la méthodologie de déploiement continu.

- Je mets à jour la machine (`apt update && apt upgrade`), et je vérifie ce qu'il y a déjà sur le serveur
- je télécharge aapanel
- Sécurité de base : UFW (ouvrir 22, 80, 443)
- DNS du domaine → IP du VPS (A/AAAA). Un Nginx “propre” devant (reverse-proxy), ça aide.
- Variables d’env dans `.env` Bref, le minimum vital.


## Préparation du VPS

- Connexion SSH en root et vérification des services clés: Nginx, PHP-FPM, MariaDB/MySQL, ports 80/443/3306 ouverts localement
- Contrôle des droits et de l’utilisateur actif, configuration basique du shell et alias utiles
- Installation d’aaPanel sur le VPS, accès à l’interface web sécurisée
- Ouverture des ports nécessaires dans le pare-feu aaPanel: c'est déjà fait normalement mais je vérifie quand même

## Méthode de déploiement

- Installation des stacks via aaPanel App Store: Nginx, PHP 8.x, MariaDB
- Création de la base de données applicative et d’un utilisateur limité, configuration du .env
- Création du site: définition du Website Path et du Running directory vers public/, vérification du vhost Nginx
- Dépôt du code dans /www/wwwroot/www.burdin-dfsgr2.local/, installation des dépendances Composer côté serveur
- Ajustement des droits pour www/www-data sur les répertoires d’écriture
- Tenté Option “push-to-deploy”: repo bare + hook post-receive pour checkout, composer install et reload PHP-FPM mais pas eu le temps