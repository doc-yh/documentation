# Search Path

Le `search_path` est une variable d'environnement dans PostgreSQL qui détermine l'ordre dans lequel les schémas de la base de données sont recherchés lorsqu'une requête fait référence à des objets sans spécifier leur schéma.

Plus précisément, le `search_path` définit la liste des schémas de base de données dans l'ordre dans lequel ils doivent être cherchés lorsqu'une requête fait référence à un objet non qualifié par un nom de schéma explicite. Par exemple, si le `search_path` est défini à `public, sales`, et qu'une requête fait référence à une table nommée "orders", PostgreSQL va d'abord chercher la table dans le schéma "public", puis dans le schéma "sales".

La variable `search_path` peut être configurée au niveau de l'utilisateur ou de la session. Par défaut, le `search_path` est défini sur `"$user", public`, ce qui signifie que PostgreSQL va d'abord chercher les objets dans le schéma portant le nom de l'utilisateur actuel, puis dans le schéma public.

Le `search_path` est utile pour simplifier l'écriture des requêtes en évitant de devoir spécifier le nom complet des objets de la base de données à chaque fois. Cela facilite également la maintenance de la base de données en permettant de déplacer les objets d'un schéma à un autre sans avoir à modifier toutes les requêtes qui les utilisent.

```sql
ALTER ROLE my_user IN DATABASE my_database SET search_path TO schema_a, schema_b, schema_c, public
```
