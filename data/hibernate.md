# 📦 Hibernate

## Introduction

Hibernate est un framework ORM (Object-Relational Mapping) pour Java qui simplifie la gestion des bases de données en mappant les objets Java aux tables relationnelles. Il permet de réduire le code SQL, d'améliorer la maintenabilité des applications, et de gérer les relations complexes entre les entités. Hibernate est largement utilisé dans les applications Java modernes pour sa flexibilité et ses fonctionnalités avancées.

---

## Concepts clés

### ORM (Object-Relational Mapping)

L'ORM permet de mapper les objets Java aux tables relationnelles, éliminant ainsi le besoin d'écrire du SQL manuel pour les opérations courantes.

### Session et SessionFactory

- **Session** : Une session est utilisée pour interagir avec la base de données. Elle est responsable de la persistance des objets.
- **SessionFactory** : La SessionFactory est une usine qui produit des sessions. Elle est généralement configurée une fois et partagée dans toute l'application.

### Cache

Hibernate offre deux niveaux de cache :

1. **Cache de premier niveau** : Activé par défaut, il est lié à la session.
2. **Cache de second niveau** : Permet de partager les données entre plusieurs sessions.

---

## Commandes essentielles

### Configuration

1. **Créer un fichier `hibernate.cfg.xml`** :

```xml
<hibernate-configuration>
    <session-factory>
        <property name="hibernate.connection.driver_class">org.postgresql.Driver</property>
        <property name="hibernate.connection.url">jdbc:postgresql://localhost:5432/mydb</property>
        <property name="hibernate.connection.username">postgres</property>
        <property name="hibernate.connection.password">password</property>
        <property name="hibernate.dialect">org.hibernate.dialect.PostgreSQLDialect</property>
        <property name="hibernate.show_sql">true</property>
        <property name="hibernate.hbm2ddl.auto">update</property>
    </session-factory>
</hibernate-configuration>
```

2. **Ajouter les dépendances Maven** :

```xml
<dependency>
    <groupId>org.hibernate</groupId>
    <artifactId>hibernate-core</artifactId>
    <version>5.6.15.Final</version>
</dependency>
<dependency>
    <groupId>org.postgresql</groupId>
    <artifactId>postgresql</artifactId>
    <version>42.5.0</version>
</dependency>
```

---

## Exemples pratiques

### Exemple de classe Entity

```java
// filepath: entities/User.java
import javax.persistence.Entity;
import javax.persistence.Id;

@Entity
public class User {
    @Id
    private int id;
    private String name;
    private String email;

    // Getters et setters
    public int getId() {
        return id;
    }
    public void setId(int id) {
        this.id = id;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public String getEmail() {
        return email;
    }
    public void setEmail(String email) {
        this.email = email;
    }
}
```

### Exemple de gestion des sessions

```java
// filepath: main/Main.java
import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.cfg.Configuration;

public class Main {
    public static void main(String[] args) {
        SessionFactory factory = new Configuration()
            .configure("hibernate.cfg.xml")
            .addAnnotatedClass(User.class)
            .buildSessionFactory();

        Session session = factory.getCurrentSession();

        try {
            // Créer un nouvel utilisateur
            User user = new User();
            user.setId(1);
            user.setName("Alice");
            user.setEmail("alice@example.com");

            // Démarrer une transaction
            session.beginTransaction();

            // Sauvegarder l'utilisateur
            session.save(user);

            // Valider la transaction
            session.getTransaction().commit();
        } finally {
            factory.close();
        }
    }
}
```

---

## Bonnes pratiques

1. **Utiliser des annotations** : Préférez les annotations comme `@Entity`, `@Id`, et `@Column` pour définir les entités.
2. **Configurer le cache** : Implémentez un cache de second niveau pour améliorer les performances.
3. **Gérer les transactions** : Utilisez des transactions pour garantir l'intégrité des données.
4. **Modulariser les entités** : Organisez les entités dans des packages dédiés pour une meilleure maintenabilité.
5. **Optimiser les requêtes** : Utilisez des requêtes HQL (Hibernate Query Language) pour des opérations complexes.

---

## Enjeux du développement avec Hibernate

1. **Réduction du code SQL** : Hibernate élimine le besoin d'écrire du SQL manuel pour les opérations courantes.
2. **Gestion des relations complexes** : Hibernate simplifie la gestion des relations entre les entités (ex. `@OneToMany`, `@ManyToOne`).
3. **Performance** : Hibernate offre des fonctionnalités avancées comme le cache de second niveau pour améliorer les performances.
4. **Flexibilité** : Hibernate permet de changer facilement de base de données grâce à sa prise en charge des dialectes.
5. **Scalabilité** : Hibernate est adapté aux applications nécessitant une gestion complexe des données.

---

## Commandes utiles pour Hibernate

### Génération automatique des tables

Configurez `hibernate.hbm2ddl.auto` dans `hibernate.cfg.xml` :

- `create` : Crée les tables à chaque démarrage.
- `update` : Met à jour les tables existantes.
- `validate` : Vérifie la structure des tables sans les modifier.

### Requêtes HQL

```java
String hql = "FROM User WHERE email = :email";
Query<User> query = session.createQuery(hql, User.class);
query.setParameter("email", "alice@example.com");
List<User> users = query.getResultList();
```

---

## Liens utiles

- [Documentation officielle Hibernate](https://hibernate.org/)
- [Tutoriels Hibernate](https://www.baeldung.com/hibernate-tutorial)
- [Exemples de configuration Hibernate](https://docs.jboss.org/hibernate/orm/)
- [Hibernate GitHub](https://github.com/hibernate/hibernate-orm)
