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

Une m??thode annot??e avec @Transactional(readOnly=true) peut effectuer des modifications dans la base de donn??es, sauf si la propri??t?? "enforceReadOnly" de DataSourceTransactionManager est d??finie sur true. Dans ce cas, les modifications de donn??es seront bloqu??es, m??me si la m??thode est annot??e avec @Transactional(readOnly=false). La propri??t?? readOnly de @Transactional est utilis??e pour informer le syst??me de gestion de transaction que cette m??thode est cens??e ??tre utilis??e pour des op??rations de lecture seules. Cependant, cela ne garantit pas que des modifications ne seront pas effectu??es, c'est la propri??t?? enforceReadOnly de DataSourceTransactionManager qui garantit l'immuabilit?? des donn??es.
