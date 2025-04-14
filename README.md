
```markdown
# 🏨 Projet de Gestion Hôtelière

## 📘 Description

Ce projet a pour objectif de modéliser un système de gestion hôtelière structuré autour de plusieurs entités telles que les hôtels, les chambres, les employés, les types et les catégories. Il permet de représenter de façon claire la structure de l’établissement, l’organisation des chambres, et la hiérarchie du personnel.

---

## 🧱 Modèle Logique des Données (MLD)

### 📌 Tables et attributs

#### 🔹 `Type`
Contient les types généraux attribués aux hôtels et chambres.

```sql
Type(
    Type_Id INT PRIMARY KEY,
    Type_Name VARCHAR(50)
);
```

#### 🔹 `Category`
Décrit la catégorie d'une chambre (tarif, nombre de lits, etc.).

```sql
Category(
    Category_Id INT PRIMARY KEY,
    Category_Name VARCHAR(50),
    Price INT,
    Beds_Numbers INT
);
```

#### 🔹 `Hotel`
Chaque hôtel appartient à un type.

```sql
Hotel(
    Hotel_Id INT PRIMARY KEY,
    Hotel_Name VARCHAR(50),
    Type_Id INT,
    FOREIGN KEY (Type_Id) REFERENCES Type(Type_Id)
);
```

#### 🔹 `Room`
Les chambres sont associées à un hôtel et à un type.

```sql
Room(
    Room_Id INT PRIMARY KEY,
    Floor VARCHAR(50),
    Hotel_Id INT,
    Type_Id INT,
    FOREIGN KEY (Hotel_Id) REFERENCES Hotel(Hotel_Id),
    FOREIGN KEY (Type_Id) REFERENCES Type(Type_Id)
);
```

#### 🔹 `Employee`
Chaque employé appartient à un hôtel et peut avoir un superviseur (relation récursive).

```sql
Employee(
    Employee_Id INT PRIMARY KEY,
    Employee_Name VARCHAR(50),
    Employee_Speciality VARCHAR(50),
    Hotel_Id INT,
    FOREIGN KEY (Supervisor_Id) REFERENCES Employee(Employee_Id),
    FOREIGN KEY (Hotel_Id) REFERENCES Hotel(Hotel_Id)
);
```

---

## ✅ Objectifs du Projet

- Gérer efficacement la structure des hôtels (types, chambres, étages)
- Organiser les employés avec une hiérarchie (superviseur)
- Relier les entités avec des clés étrangères respectant l'intégrité référentielle

---

## 🛠️ Technologies recommandées

- **Base de données** : MySQL, PostgreSQL, SQLite
- **Modélisation** : DB Designer, Draw.io, SQL Power Architect
- **Backend (optionnel)** : Node.js, Django, Flask
- **Frontend (optionnel)** : React, Vue.js, ou autre

---

## ✍️ Auteur

Projet réalisé par GBOKO AMARA, dans le cadre d’un exercice de modélisation de base de données relationnelle.
