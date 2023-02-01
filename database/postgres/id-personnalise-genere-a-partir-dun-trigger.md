# ID personnalisé généré à partir d'un trigger

Fonction trigger qui se déclenche au moment de l'insertion

```sql
create sequence if not exists DATA.S_AVIS_PIAMP;

-- La fonction assure le redémarrage de la séquence DATA.S_AVIS_PIAMP chaque année.
-- De plus, elle initialise la variable av_id_piamp à chaque nouvelle insertion dans la table DATA.AVIS, en utilisant le format "AA-SEQ",
-- où "AA" représente l'année en cours et "SEQ" représente la valeur actuelle de la séquence DATA.S_AVIS_PIAMP.
CREATE OR REPLACE FUNCTION DATA.reset_s_avis_piamp_by_year() RETURNS trigger AS $reset_s_avis_piamp_by_year$
	DECLARE
	  current_year INTEGER;
	  last_year INTEGER;
	  next_id INTEGER;
        BEGIN
	    current_year := date_part('year', CURRENT_DATE);
	    SELECT max(date_part('year',to_date(substring(av_id_piamp::text, 1, 2), 'YY'))) INTO last_year FROM DATA.AVIS;
   	    IF last_year IS NULL OR current_year != last_year THEN
               perform setval('DATA.s_avis_piamp', 1);
               next_id := currval('DATA.s_avis_piamp');
            ELSE
               next_id := nextval('DATA.s_avis_piamp');
            END IF;
            NEW.av_id_piamp := to_char(date_trunc('year', CURRENT_DATE), 'YY-') || cast(next_id as text);
    	    RETURN NEW;
	END;
$reset_s_avis_piamp_by_year$ LANGUAGE plpgsql;

CREATE OR REPLACE TRIGGER reset_s_avis_piamp_by_year
  BEFORE INSERT ON DATA.AVIS
  FOR EACH ROW
  EXECUTE FUNCTION DATA.reset_s_avis_piamp_by_year();
```

Exemple d'insertion

```sql
INSERT INTO data.avis (av_id_piamp) values (default)
```
