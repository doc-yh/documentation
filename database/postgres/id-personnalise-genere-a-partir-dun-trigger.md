# ID personnalisé généré à partir d'un trigger

Fonction trigger qui se déclenche au moment de l'insertion

```sql
create sequence if not exists DATA.SEQ;

CREATE OR REPLACE FUNCTION DATA.next_val() RETURNS trigger AS $next_val$
        BEGIN
            NEW.av_id_piamp := nextval('DATA.SEQ');
    	    RETURN NEW;
	END;
$next_val$ LANGUAGE plpgsql;

CREATE OR REPLACE TRIGGER next_val
  BEFORE INSERT ON DATA.AVIS
  FOR EACH ROW
  EXECUTE FUNCTION DATA.next_val();
```

Exemple d'insertion

```sql
INSERT INTO data.avis (av_id_piamp) values (default)
```
