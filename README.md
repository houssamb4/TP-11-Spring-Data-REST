# 🏦 Spring Data REST - Application Bancaire
### TP 11 – API REST automatisée avec Spring Data REST

Cette application **Spring Boot** expose automatiquement une API REST pour gérer des **clients** et leurs **comptes bancaires** grâce à **Spring Data REST**.

---

## 🚀 Lancer l'application

```bash
mvn spring-boot:run
```

L'application démarre sur le port **8080**.

Base path API : `/api`

## 📋 Endpoints disponibles

### 🔍 Projections

Les projections permettent de personnaliser les informations retournées dans les réponses JSON.

#### Projection "solde"

Affiche uniquement le solde du compte :

```
GET http://localhost:8080/api/comptes/1?projection=solde
```

#### Projection "mobile"

Affiche le solde et le type du compte :

```
GET http://localhost:8080/api/comptes/1?projection=mobile
```

#### Projection "clientDetails"

Affiche uniquement le nom et l'email d'un client :

```
GET http://localhost:8080/api/comptes/1/client?projection=clientDetails
```

### 📄 Pagination et tri

Spring Data REST supporte automatiquement la pagination et le tri.

#### Pagination

Affiche les comptes avec pagination (2 comptes par page) :

```
GET http://localhost:8080/api/comptes?page=0&size=2
```

#### Tri

Trie les comptes par solde en ordre décroissant :

```
GET http://localhost:8080/api/comptes?page=0&size=2&sort=solde,desc
```

Tri en ordre croissant :

```
GET http://localhost:8080/api/comptes?sort=solde,asc
```

### 🔗 Relations entre entités

Les relations entre Client et Compte sont automatiquement exposées comme liens REST.

#### Comptes d'un client

Récupère tous les comptes associés à un client :

```
GET http://localhost:8080/api/clients/1/comptes
```

#### Client d'un compte

Récupère les informations du client associé à un compte :

```
GET http://localhost:8080/api/comptes/1/client
```

Avec projection :

```
GET http://localhost:8080/api/comptes/1/client?projection=clientDetails
```

### 🔎 Recherche personnalisée

#### Recherche par type de compte

Recherche tous les comptes de type EPARGNE :

```
GET http://localhost:8080/api/comptes/search/byType?t=EPARGNE
```

Recherche tous les comptes de type COURANT :

```
GET http://localhost:8080/api/comptes/search/byType?t=COURANT
```
