# Questions

Répondez ici aux questions théoriques en détaillant un maxium vos réponses :

1) Expliquer la procédure pour réserver un nom de domaine chez OVH avec des captures d'écran (arrêtez-vous au paiement) :

2. Comment faire pour qu'un nom de domaine pointe vers une adresse IP spécifique ?
3. Comment mettre en place un certificat SSL ?

# Questions

Répondez ici aux questions théoriques en détaillant un maxium vos réponses :

1) Expliquer la procédure pour réserver un nom de domaine chez OVH avec des captures d'écran (arrêtez-vous au paiement) :

1. je vais sur **ovhcloud.com → Domains**.
2. je tape nom dans la barre de recherche, choisis l’extension (.fr, .com, …), vérifie la disponibilité, puis **Ajouter au panier**.
3. Dans le panier, choisis **durée 1 an** (classique pour commencer). Laisse la **protection WHOIS** activé si proposé par défaut.
4. je me connecte ou crée mon compte et on vérifie mon identité
5. je laisse les DNS par défaut d’OVH (je pourrai changer après).


2. Comment faire pour qu'un nom de domaine pointe vers une adresse IP spécifique ?


1. **Web Cloud → Noms de domaine → [mon-domaine] → Zone DNS**.
2. **Ajouter un enregistrement** → **A** → Sous-domaine `@` → Cible = mon IPv4 → Valider.
3. (Optionnel) **Ajouter AAAA** pour IPv6.
4. **www** → CNAME → Cible `mon-domaine.tld.` → Valider.
5. Attends la propagation (quelques minutes en général).

3. Comment mettre en place un certificat SSL ?
1. **Web Cloud → Hébergements → [mon hébergement] → Informations générales**.
2. Bloc **Configuration** → **… → Commander un certificat SSL** → on choisi **Let’s Encrypt (gratuit)**.
3. Ensuite, dans **Multisite**, j'active la colonne **SSL** pour chaque (sous-)domaine, attends l’émission (quelques minutes).
4. Force le HTTPS (via ton CMS ou un .htaccess). Quand c’est prêt, tu verras **Yes – LETSENCRYPT – DV**. 