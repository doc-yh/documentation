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

    @Value("${datasource.readWrite.url}")
    private String urlReadWrite;

    @Value("${datasource.readWrite.username}")
    private String usernameReadWrite;

    @Value("${datasource.readWrite.password}")
    private String passwordReadWrite;

    @Value("${datasource.readOnly.url}")
    private String urlReadOnly;
    
    @Value("${datasource.username.readOnly}")
    private String usernameReadOnly;

    @Value("${datasource.password.readOnly}")
    private String passwordReadOnly;

    @Bean
    public TransactionRoutingDataSource dataSource() {
        TransactionRoutingDataSource routingDataSource = new TransactionRoutingDataSource();
        routingDataSource.setTargetDataSources(Map.of(
                DataSourceType.READ_WRITE, hikariDataSource(urlReadWrite, usernameReadWrite, passwordReadWrite),
                DataSourceType.READ_ONLY, hikariDataSource(urlReadOnly, usernameReadOnly, passwordReadOnly)
        ));
        return routingDataSource;
    }

    protected HikariDataSource hikariDataSource(String url, String username, String password) {
        PGSimpleDataSource dataSource = new PGSimpleDataSource();
        dataSource.setURL(url);
        dataSource.setUser(username);
        dataSource.setPassword(password);
        HikariConfig hikariConfig = new HikariConfig();
        int cpuCores = Runtime.getRuntime().availableProcessors();
        hikariConfig.setMaximumPoolSize(cpuCores * 4);
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
