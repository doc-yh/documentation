# Auto-commit

Auto-commit est une fonctionnalité de certaines bases de données qui permet de valider automatiquement les transactions après chaque instruction SQL exécutée. Cela signifie que chaque instruction SQL est considérée comme une transaction individuelle qui est automatiquement validée (commitée) après son exécution. Cela peut être pratique pour certaines applications, mais peut causer des problèmes pour les applications qui nécessitent des transactions plus complexes.

Désactiver l'auto-commit permet de conserver plus de contrôle sur les transactions, car les développeurs peuvent décider explicitement quand une transaction doit être validée. Cela permet également de regrouper plusieurs instructions SQL en une seule transaction, ce qui peut améliorer les performances.

En résumé, dans cette méthode, l'auto-commit est désactivé, ce qui permet de regrouper plusieurs instructions SQL en une seule transaction et de conserver plus de contrôle sur les transactions.

## @Tranctional et l'auto-commit

L'annotation @Transactional de Spring permet de désactiver l'auto-commit. Lorsqu'une méthode est marquée avec @Transactional, Spring crée automatiquement une transaction pour cette méthode et toutes les opérations de base de données exécutées dans cette méthode sont regroupées dans cette transaction. Les opérations ne sont pas automatiquement validées après chaque instruction, mais plutôt lorsque la méthode est terminée avec succès. Si une exception est levée dans la méthode, la transaction est annulée (rollback).

En utilisant l'annotation @Transactional, vous pouvez facilement gérer les transactions de manière déclarative, sans avoir à gérer explicitement les transactions dans le code. Il vous permet de définir le niveau de isolation et de gérer les rollbacks automatiquement.

Voir le `doBegin()` de `DataSourceTransactionManager`
