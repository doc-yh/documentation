# Read-write and read-only transaction routing

Source : [https://vladmihalcea.com/read-write-read-only-transaction-routing-spring/](https://vladmihalcea.com/read-write-read-only-transaction-routing-spring/)

<figure><img src="../../.gitbook/assets/Read-Write-Read-Only-Spring-Transaction-Routing.png" alt=""><figcaption></figcaption></figure>

```java
public enum DataSourceType {
    READ_WRITE,
    READ_ONLY
}
```

```java
@Configuration
public class MultiDataSourceConfiguration {

    @Value("${datasource.driverClassName}")
    private String driverClassName;

    @Value("${datasource.url}")
    private String url;

    @Value("${datasource.username}")
    private String username;

    @Value("${datasource.password}")
    private String password;

    @Value("${datasource.username.readOnly}")
    private String usernameReadOnly;

    @Value("${datasource.password.readOnly}")
    private String passwordReadOnly;

    @Value("${datasource.hikari.maximumPoolSize}")
    private int hikariMaximumPoolSize;

    @Bean
    public TransactionRoutingDataSource dataSource() {
        TransactionRoutingDataSource routingDataSource = new TransactionRoutingDataSource();
        routingDataSource.setTargetDataSources(Map.of(
                DataSourceType.READ_WRITE, hikariDataSource(DataSourceBuilder.create()
                        .driverClassName(driverClassName)
                        .url(url)
                        .username(username)
                        .password(password)
                        .build()),
                DataSourceType.READ_ONLY, hikariDataSource(DataSourceBuilder.create()
                        .driverClassName(driverClassName)
                        .url(url)
                        .username(usernameReadOnly)
                        .password(passwordReadOnly)
                        .build())
        ));
        return routingDataSource;
    }

    protected HikariDataSource hikariDataSource(DataSource dataSource) {
        HikariConfig hikariConfig = new HikariConfig();
        hikariConfig.setMaximumPoolSize(hikariMaximumPoolSize);
        hikariConfig.setDataSource(dataSource);
        return new HikariDataSource(hikariConfig);
    }

}
```

```java
public class TransactionRoutingDataSource extends AbstractRoutingDataSource {

    @Override
    protected Object determineCurrentLookupKey() {
        return TransactionSynchronizationManager.isCurrentTransactionReadOnly() ?
                DataSourceType.READ_ONLY :
                DataSourceType.READ_WRITE;
    }

}
```

```java
@Configuration
@EnableTransactionManagement
public class TransactionManagerConfiguration {
    
    @Bean
    public DataSourceTransactionManager dataSourceTransactionManager(DataSource dataSource) {
        DataSourceTransactionManager dataSourceTransactionManager = new DataSourceTransactionManager(dataSource);
        dataSourceTransactionManager.setEnforceReadOnly(true);
        return dataSourceTransactionManager;
    }

}
```

Une méthode annotée avec @Transactional(readOnly=true) peut effectuer des modifications dans la base de données, sauf si la propriété "enforceReadOnly" de DataSourceTransactionManager est définie sur true. Dans ce cas, les modifications de données seront bloquées, même si la méthode est annotée avec @Transactional(readOnly=false). La propriété readOnly de @Transactional est utilisée pour informer le système de gestion de transaction que cette méthode est censée être utilisée pour des opérations de lecture seules. Cependant, cela ne garantit pas que des modifications ne seront pas effectuées, c'est la propriété enforceReadOnly de DataSourceTransactionManager qui garantit l'immuabilité des données.
