# TP2 — Spring Boot : Gestion des Produits & Introduction à JPA

Ce projet correspond au **TP2** du module Spring Boot.  
L’objectif est de mettre en pratique les notions de **Spring Boot**, **JPA**, **H2 / MySQL**, et **Spring Data**, en suivant les étapes démontrées dans les vidéos ci-dessous.


###  Création de l’entité `Product`
Dans le package `entities`, créer la classe `Product` avec les attributs suivants :

```java
@Entity
@Data
@NoArgsConstructor
@AllArgsConstructor
public class Product {
    @Id @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private double price;
    private int quantity;
}
```

---

###  Configuration de la base de données

#### ➔ `application.properties` (H2)
```properties
spring.datasource.url=jdbc:h2:mem:products-db
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.h2.console.enabled=true
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

---

###  Création du Repository

```java
public interface ProductRepository extends JpaRepository<Product, Long> {
    List<Product> findByNameContains(String keyword);
}
```

---

###  Opérations CRUD à tester

Depuis le contrôleur ou un `CommandLineRunner`, tester :

-  Ajouter des produits  
-  Consulter tous les produits  
-  Consulter un produit par son `id`  
-  Rechercher des produits par mot-clé  
-  Mettre à jour un produit  
- Supprimer un produit  

*(Tester via Postman, H2 console, ou navigateur.)*

---

###  Migration vers MySQL

Modifier `application.properties` :

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/products_db?createDatabaseIfNotExist=true
spring.datasource.username=root
spring.datasource.password=
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
```

---

###  Étendre le projet (bonus des vidéos)
Reprendre les exemples de gestion de :
-  **Patient**
-  **Médecin**
- **Rendez-vous**
-  **Consultation**
-  **Users & Roles**

Ces entités permettront d’explorer :
- Les relations **OneToMany**, **ManyToOne**, **ManyToMany**
- La **sécurité Spring Security**
- L’utilisation de **JPA Repositories** avancés.

---

##  Technologies utilisées

| Outil / Technologie | Rôle |
|----------------------|------|
| **Java 17+** | Langage principal |
| **Spring Boot 3+** | Framework principal |
| **Spring Data JPA** | Gestion de la persistance |
| **H2 / MySQL** | Bases de données |
| **Lombok** | Simplification du code |
| **IntelliJ IDEA Ultimate** | IDE |
| **Git / GitHub** | Gestion de versions |



##  Auteur

**Anouar Mohamed**  
Projet académique — TP2 Spring Boot  
Encadré par *[nom de l’enseignant si applicable]*

---

##  Statut du projet

 Terminé — Migré vers MySQL et testé avec Postman.

