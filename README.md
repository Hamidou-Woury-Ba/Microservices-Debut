# Microservices-Debut

# Base de donnée postgres
* Créer l'utilisateur avec mot de passe
```
CREATE USER microservicedebutuser WITH PASSWORD 'votre_mot_de_passe_secure';
```
* Créer les bases avec le bon propriétaire
```
CREATE DATABASE students OWNER microservicedebutuser;
CREATE DATABASE schools OWNER microservicedebutuser;
```

* Donner tous les droits (même si OWNER les a déjà)
```
GRANT ALL PRIVILEGES ON DATABASE students TO microservicedebutuser;
GRANT ALL PRIVILEGES ON DATABASE schools TO microservicedebutuser;
```

* Configurer les schémas (pour chaque base)
```
\c students
CREATE SCHEMA IF NOT EXISTS students_schema;
GRANT ALL ON SCHEMA students_schema TO microservicedebutuser;
ALTER DEFAULT PRIVILEGES IN SCHEMA students_schema GRANT ALL ON TABLES TO microservicedebutuser;
```

```
\c schools
CREATE SCHEMA IF NOT EXISTS schools_schema;
GRANT ALL ON SCHEMA schools_schema TO microservicedebutuser;
ALTER DEFAULT PRIVILEGES IN SCHEMA schools_schema GRANT ALL ON TABLES TO microservicedebutuser;
```