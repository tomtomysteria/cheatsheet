# 📦 Hibernate

## Introduction

Hibernate est un framework ORM (Object-Relational Mapping) pour Java qui simplifie la gestion des bases de données en mappant les objets Java aux tables relationnelles. Il permet de réduire le code SQL et d'améliorer la maintenabilité des applications.

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

1. **Utiliser des annotations** : Préférez les annotations comme `@Entity` et `@Id` pour définir les entités.
2. **Configurer le cache** : Implémentez un cache de second niveau pour améliorer les performances.
3. **Gérer les transactions** : Utilisez des transactions pour garantir l'intégrité des données.

---

## Liens utiles

- [Documentation officielle Hibernate](https://hibernate.org/)
- [Tutoriels Hibernate](https://www.baeldung.com/hibernate-tutorial)
- [Exemples de configuration Hibernate](https://docs.jboss.org/hibernate/orm/)
