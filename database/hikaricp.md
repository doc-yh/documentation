# HikariCP

HikariCP est une bibliothèque de pools de connexions pour les bases de données qui vise à être plus légère et plus rapide que les autres bibliothèques de pools de connexions couramment utilisées.

Un pool de connexions est une collection de connexions pré-établies à une base de données qui peuvent être réutilisées par les applications pour éviter de créer de nouvelles connexions pour chaque requête. Lorsqu'une application a besoin d'une connexion à une base de données, elle en demande une au pool au lieu de créer une nouvelle connexion. Si une connexion est disponible dans le pool, elle est donnée à l'application, sinon une nouvelle connexion est créée pour répondre à la demande.

Un pool de connexions HikariCP utilise les fonctionnalités suivantes :

* Taille maximale du pool : le nombre maximal de connexions qui peuvent être maintenues dans le pool à tout moment. Lorsque le pool atteint sa taille maximale, les demandes supplémentaires de connexions sont mises en file d'attente jusqu'à ce qu'une connexion soit libérée.
* Temps d'attente : le temps maximum que l'application doit attendre pour obtenir une connexion du pool lorsque le pool est plein. Si un temps d'attente est dépassé, une exception est levée.
* Temps d'inactivité : le temps après lequel une connexion inutilisée sera automatiquement fermée. Cela permet de libérer les ressources utilisées par les connexions inutilisées.
* Validation des connexions : des vérifications régulières pour s'assurer que les connexions dans le pool sont valides et fonctionnelles.

En résumé, un pool de connexions HikariCP est une collection de connexions pré-établies à une base de données qui peuvent être réutilisées pour éviter de créer de nouvelles connexions pour chaque requête. Il utilise une stratégie de gestion de la taille du pool, des temps d'attente, un temps d'inactivité et une validation des connexions pour gérer efficacement les connexions.
