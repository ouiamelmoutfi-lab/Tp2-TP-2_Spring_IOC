# Spring IoC — Injection de Dépendances avec Annotations

Application Java Maven démontrant les principes d'**Inversion de Contrôle (IoC)** et d'**Injection de Dépendances (DI)** à l'aide du framework Spring, via les annotations `@Component`, `@Autowired` et `@Qualifier`.

---

## 🛠️ Technologies utilisées

- Java 11+
- Spring Framework 6.1.2 (`spring-context`)
- Maven

---

## 📁 Structure du projet

```
src/main/java/com/example/
├── dao/
│   ├── IDao.java          → Interface DAO (contrat : getValue())
│   ├── DaoImpl.java       → Implémentation 1 — retourne 100.0
│   └── DaoImpl2.java      → Implémentation 2 — retourne 150.0
├── metier/
│   ├── IMetier.java       → Interface métier (contrat : calcul())
│   └── MetierImpl.java    → Implémentation métier — injecte IDao et calcule getValue() * 2
└── presentation/
    └── Presentation2.java → Point d'entrée — configure et lance le contexte Spring
```

---

## 📸 Captures d'écran

### Capture 1 — Injection avec `@Autowired` seul (DaoImpl)

![Screenshot 1](Screenshot%202026-10-12%20165904.png)

Dans cette première version, `MetierImpl` utilise uniquement l'annotation `@Autowired` pour injecter une implémentation de `IDao`. Spring choisit automatiquement le bean disponible, ici **`DaoImpl`** (identifiant `"dao"`), qui retourne la valeur `100.0`.

Le résultat affiché en console est :
```
Resultat = 200.0
```
> `DaoImpl.getValue()` retourne `100.0` → `100.0 × 2 = 200.0`

---

### Capture 2 — Sélection explicite avec `@Qualifier("dao2")` (DaoImpl2)

![Screenshot 2](Screenshot%202026-10-12%20170447.png)

Dans cette seconde version, on ajoute l'annotation `@Qualifier("dao2")` aux côtés de `@Autowired` dans `MetierImpl`. Cela indique à Spring d'injecter **`DaoImpl2`** (identifiant `"dao2"`) à la place de `DaoImpl`.

```java
@Autowired
@Qualifier("dao2")
private IDao dao;
```

`DaoImpl2.getValue()` retourne `150.0`, donc le résultat devient :
```
Resultat = 300.0
```
> `DaoImpl2.getValue()` retourne `150.0` → `150.0 × 2 = 300.0`

**Ce changement illustre la puissance de l'IoC** : on modifie le comportement de l'application sans toucher à la logique métier, juste en changeant quelle implémentation Spring doit injecter.

---

## ▶️ Lancer le projet

```bash
mvn clean install
```

Puis exécuter la classe `Presentation2` comme application Java.
