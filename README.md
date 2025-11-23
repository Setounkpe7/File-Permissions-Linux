# File Permissions in Linux  
Projet issu du Google Cybersecurity Professional Certificate

## Objectif du projet  
Ce projet consiste à vérifier, analyser et mettre à jour les permissions de fichiers et répertoires dans un environnement Linux.  
Les objectifs étaient :

- Inspecter les permissions existantes.  
- Comprendre le format des permissions sous Linux.  
- Modifier les permissions avec `chmod` pour appliquer un modèle d’accès sécurisé.  
- Appliquer les règles de moindre privilège définies par l’organisation.

---

## Contexte du projet  
L’équipe de recherche de l’entreprise stocke plusieurs projets dans un dossier Linux. Les autorisations actuelles ne respectaient pas les règles de sécurité souhaitées.  
Le travail demandé incluait :

1. Examiner les permissions avec `ls -la`  
2. Identifier les niveaux d’accès requis  
3. Ajuster les permissions en conséquence  
4. Vérifier les résultats obtenus  

---

## Analyse des permissions  
Le projet commence par l’inspection des permissions avec :

```bash
ls -la
```

Les permissions Linux sont représentées par une chaîne de 10 caractères :

- 1er caractère : type (`-` fichier / `d` répertoire)  
- 2e à 4e : droits **utilisateur**  
- 5e à 7e : droits **groupe**  
- 8e à 10e : droits **autres**  

Exemple analysé dans le projet :

```
-rw-rw-r--
```

- utilisateur : lecture/écriture  
- groupe : lecture/écriture  
- autres : lecture  

---

## Modifications réalisées

### Suppression du droit d’écriture pour “other”
Pour empêcher quiconque hors du propriétaire et du groupe d’écrire sur `project_k.txt` :

```bash
chmod o-w project_k.txt
```

Vérification :

```bash
ls -la
```

---

### Mise à jour d’un fichier caché  
Le fichier caché `.project_x.txt` devait :

- ne plus être modifiable par personne  
- rester lisible par l’utilisateur et le groupe  

Commandes utilisées :

```bash
chmod u-w .project_x.txt
chmod g-w .project_x.txt
chmod g+r .project_x.txt
```

---

### Restriction d’accès à un répertoire  
Le répertoire `drafts` devait être accessible uniquement par `researcher2`.  
Le bit d’exécution (`x`) est donc retiré du groupe et des autres :

```bash
chmod g-x drafts
chmod o-x drafts
```

Résultat : seul `researcher2` peut entrer dans le répertoire.

---

## Compétences développées  
- Lecture et interprétation des permissions Linux  
- Utilisation avancée de `chmod`  
- Application du principe **Least Privilege**  
- Manipulation des fichiers cachés  
- Gestion des droits sur les répertoires (bit d’exécution)  
- Vérification des autorisations avec `ls -la`  

---

## Outils utilisés  
- Terminal Linux  
- Commandes :  
  - `ls`, `ls -la`  
  - `chmod`

---

## Conclusion  
Ce projet démontre la capacité à :  
- examiner les permissions système,  
- analyser des cas d’usage organisationnels,  
- appliquer correctement les droits Linux pour contrôler l’accès aux fichiers et répertoires.

C’est une compétence essentielle pour les rôles **SOC Analyst L1**, **Cybersecurity Analyst**, **Sysadmin**, et **Linux Security**.

---

## Ajouter le rapport PDF au repo  

```markdown
[Voir le rapport PDF complet](./file-permissions-linux.pdf)
```
