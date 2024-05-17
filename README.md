# Les Jointures en SQL pour Débutants

## Introduction

En SQL, les jointures permettent de combiner des données de plusieurs tables en fonction d'une relation entre elles. Cela est très utile quand les informations que nous voulons analyser ou afficher sont réparties sur plusieurs tables dans une base de données.

## Clé Primaire et Clé Étrangère

### Clé Primaire (Primary Key)
- Une clé primaire est un identifiant unique pour chaque enregistrement dans une table.
- Par exemple, dans une table `Etudiants`, la colonne `EtudiantID` peut être définie comme clé primaire car elle identifie de manière unique chaque étudiant.

### Clé Étrangère (Foreign Key)
- Une clé étrangère est une colonne qui établit un lien entre les données de deux tables.
- Par exemple, si nous avons une table `Cours` et une table `Inscriptions`, la colonne `EtudiantID` dans la table `Inscriptions` peut être une clé étrangère, qui fait référence à la colonne `EtudiantID` de la table `Etudiants`.

## Types de Jointures

### 1. INNER JOIN (Jointure Interne)
- Affiche uniquement les lignes qui ont des correspondances dans les deux tables.

### 2. LEFT JOIN (Jointure à Gauche)
- Affiche toutes les lignes de la table de gauche, et les lignes correspondantes de la table de droite. Si aucune correspondance n'est trouvée, les résultats de la table de droite seront `NULL`.

### 3. RIGHT JOIN (Jointure à Droite)
- Affiche toutes les lignes de la table de droite, et les lignes correspondantes de la table de gauche. Si aucune correspondance n'est trouvée, les résultats de la table de gauche seront `NULL`.

### 4. FULL JOIN (Jointure Complète)
- Affiche toutes les lignes lorsqu'il y a une correspondance dans une des tables. Si une ligne dans une table n'a pas de correspondance dans l'autre table, les résultats contiendront `NULL` pour les colonnes de l'autre table.

## Exemples de Requêtes avec Jointures

### Tables Exemple:

#### 1. Table `Etudiants`:
| EtudiantID | Nom     |
|------------|---------|
| 1          | Alice   |
| 2          | Bob     |
| 3          | Charlie |

#### 2. Table `Cours`:
| CoursID | Intitule      |
|---------|---------------|
| 101     | Mathématiques |
| 102     | Histoire      |

#### 3. Table `Inscriptions`:
| EtudiantID | CoursID |
|------------|---------|
| 1          | 101     |
| 2          | 102     |
| 3          | 101     |

### 1. INNER JOIN:

Pour obtenir la liste des étudiants inscrits et les cours auxquels ils sont inscrits:
```sql
SELECT Etudiants.Nom, Cours.Intitule
FROM Etudiants
INNER JOIN Inscriptions ON Etudiants.EtudiantID = Inscriptions.EtudiantID
INNER JOIN Cours ON Inscriptions.CoursID = Cours.CoursID;
```

### 2.LEFT JOIN:
Pour obtenir tous les étudiants, y compris ceux qui ne sont inscrits à aucun cours:

```sql
Copier le code
SELECT Etudiants.Nom, Cours.Intitule
FROM Etudiants
LEFT JOIN Inscriptions ON Etudiants.EtudiantID = Inscriptions.EtudiantID
LEFT JOIN Cours ON Inscriptions.CoursID = Cours.CoursID;
```

### 3.RIGHT JOIN:
Pour obtenir tous les cours, y compris ceux qui n'ont pas d'étudiants inscrits:

```sql
Copier le code
SELECT Etudiants.Nom, Cours.Intitule
FROM Etudiants
RIGHT JOIN Inscriptions ON Etudiants.EtudiantID = Inscriptions.EtudiantID
RIGHT JOIN Cours ON Inscriptions.CoursID = Cours.CoursID;
```

### 4.FULL JOIN:
Pour obtenir tous les étudiants et tous les cours, y compris ceux sans correspondances:

```sql
Copier le code
SELECT Etudiants.Nom, Cours.Intitule
FROM Etudiants
FULL JOIN Inscriptions ON Etudiants.EtudiantID = Inscriptions.EtudiantID
FULL JOIN Cours ON Inscriptions.CoursID = Cours.CoursID;
```

## Conclusion

Les jointures sont des outils puissants en SQL qui permettent de combiner des données de plusieurs tables pour répondre à des questions complexes. En comprenant comment utiliser les clés primaires et étrangères, ainsi que les différents types de jointures, vous pouvez manipuler et analyser efficacement les données dans une base de données relationnelle.
