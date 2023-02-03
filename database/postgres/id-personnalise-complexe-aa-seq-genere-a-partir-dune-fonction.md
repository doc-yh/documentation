# ID personnalisé complexe (AA-SEQ) généré à partir d'une fonction

La fonction `DATA.get_av_id_piamp` génère un identifiant de format `AA-SEQ` en concaténant l'année courante (obtenue grâce à la fonction `DATA.get_av_id_piamp_year`) et la valeur actuelle de la séquence `DATA.S_AVIS_PIAMP_ID`. La séquence `DATA.S_AVIS_PIAMP_ID` est réinitialisée à chaque nouvelle année.

<pre class="language-plsql"><code class="lang-plsql">create sequence if not exists DATA.S_AVIS_PIAMP_ID;
create sequence if not exists DATA.S_AVIS_PIAMP_YEAR;

CREATE OR REPLACE FUNCTION DATA.get_av_id_piamp_year() RETURNS INTEGER AS $$
    DECLARE
        current_year INTEGER;
      last_year INTEGER;
    BEGIN
    current_year := cast(to_char(date_trunc('year', CURRENT_DATE), 'YY') as integer);
    SELECT last_value INTO last_year FROM DATA.S_AVIS_PIAMP_YEAR;
   IF current_year != last_year THEN
      perform pg_advisory_lock(hashtext('DATA.get_av_id_piamp_year'));
      SELECT last_value INTO last_year FROM DATA.S_AVIS_PIAMP_YEAR;
      IF current_year != last_year THEN
         perform setval('DATA.S_AVIS_PIAMP_YEAR', current_year);
         perform setval('DATA.S_AVIS_PIAMP_ID', 1, false);
      END IF;
      perform pg_advisory_unlock(hashtext('DATA.get_av_id_piamp_year'));
   END IF;
    RETURN current_year;
    END;
<strong>$$ LANGUAGE plpgsql;
</strong>
CREATE OR REPLACE FUNCTION DATA.get_av_id_piamp() RETURNS varchar(20) AS $$
    BEGIN
    RETURN DATA.get_av_id_piamp_year() || '-' || cast(nextval('DATA.s_avis_piamp') as text);
    END;
$$ LANGUAGE plpgsql;
</code></pre>

```sql
SELECT DATA.get_av_id_piamp();
```
