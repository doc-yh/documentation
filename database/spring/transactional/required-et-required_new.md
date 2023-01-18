# REQUIRED et REQUIRED\_NEW

Les deux propriétés "propagation" `REQUIRED` et `REQUIRED_NEW` dans l'annotation `@Transactional` de Spring sont utilisées pour gérer les transactions dans les méthodes appelées.

La propriété de propagation `REQUIRED` signifie que si une transaction est déjà en cours, cette méthode utilisera la même transaction. Sinon, une nouvelle transaction est créée pour cette méthode. Cela signifie que si vous appelez une méthode marquée avec `@Transactional(propagation = Propagation.REQUIRED)` depuis une méthode déjà marquée avec `@Transactional`, les deux méthodes utiliseront la même transaction.

La propriété de propagation `REQUIRED_NEW` signifie qu'une nouvelle transaction est créée pour cette méthode, indépendamment de si une transaction est déjà en cours ou non. Cela signifie que si vous appelez une méthode marquée avec `@Transactional(propagation = Propagation.REQUIRED_NEW)` depuis une méthode déjà marquée avec `@Transactional`, les deux méthodes auront des transactions distinctes.

En général, il est préférable d'utiliser `REQUIRED` lorsque vous voulez regrouper plusieurs opérations de base de données dans une seule transaction, tandis que `REQUIRED_NEW` est utile lorsque vous voulez séparer les transactions pour éviter des conflits ou des problèmes de verrouillage.
