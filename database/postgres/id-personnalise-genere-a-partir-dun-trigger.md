# ID personnalisé généré à partir d'un trigger

Fonction trigger qui se déclenche au moment de l'insertion

```sql
create sequence if not exists DATA.S_AVIS_PIAMP;

CREATE OR REPLACE FUNCTION data.reset_s_avis_piamp_by_year() RETURNS trigger AS $reset_s_avis_piamp_by_year$
	DECLARE
	  current_year INTEGER;
	  last_year INTEGER;
    BEGIN
		current_year := date_part('year', CURRENT_DATE);
		SELECT max(date_part('year',to_date(substring(av_id_piamp::text, 1, 2), 'YY'))) INTO last_year FROM DATA.AVIS;
        IF last_year IS NULL OR current_year != last_year THEN
			RAISE NOTICE 'Restarting s_avis_piamp sequence for year %', current_year;
            ALTER SEQUENCE DATA.S_AVIS_PIAMP RESTART WITH 1;
		ELSE
			RAISE NOTICE 'current year %', current_year;
        END IF;
		NEW.av_id_piamp := to_char(date_trunc('year', CURRENT_DATE), 'YY') || '-' || cast(nextval('data.s_avis_piamp') as text);
    	RETURN NEW;
	END;
$reset_s_avis_piamp_by_year$ LANGUAGE plpgsql;

CREATE OR REPLACE TRIGGER reset_s_avis_piamp_by_year
  BEFORE INSERT ON data.avis
  FOR EACH ROW
  EXECUTE FUNCTION data.reset_s_avis_piamp_by_year();

ALTER FUNCTION data.reset_s_avis_piamp_by_year() OWNER TO piamp_api;
```

Exemple d'insertion

```sql
INSERT INTO data.avis (av_id_piamp) values (default)
```
