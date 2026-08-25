# JOURNAL-IA — Mini-TP 3 : Cycle de vie & Intents

## Outil IA utilisé
Kiro (assistant IA intégré dans le Kiro IDE)

## Tâche confiée à l'IA
Diagnostiquer le crash suivant :

```
java.lang.RuntimeException: Unable to start activity
  ComponentInfo{mg.itu.cycledevie/mg.itu.cycledevie.MainActivity}:
  java.lang.NullPointerException: findViewById(R.id.btnPartage) must not be null
    at mg.itu.cycledevie.MainActivity.onCreate(MainActivity.kt:29)
```

Ligne 29 : `findViewById<Button>(R.id.btnPartage).setOnClickListener { partagerCollecte() }`

## Diagnostic produit par l'IA

- **Ligne** : MainActivity.kt:29 — `findViewById<Button>(R.id.btnPartage)` retourne `null` et le `.setOnClickListener` provoque le NullPointerException.
- **Cause** : L'identifiant `R.id.btnPartage` n'existe pas dans le layout `activity_main.xml`. Le vrai identifiant déclaré dans le XML est `@+id/btnPartager` (avec un « r » final). La faute de frappe empêche Android de trouver la vue, `findViewById` retourne `null`, et l'accès immédiat plante l'app au démarrage dans `onCreate`.
- **Correction** : Remplacer `R.id.btnPartage` par `R.id.btnPartager` à la ligne 29.

---

## VERDICT

Je suis d'accord avec le diagnostic.
L'IA pointe la bonne ligne (29) et la bonne cause : en ouvrant activity_main.xml, le bouton est bien déclaré `btnPartager` — le `r` final manque dans la variante crashée, ce que l'IA a correctement identifié.
La correction (renommer l'ID) est suffisante et vérifiable directement dans le layout.
