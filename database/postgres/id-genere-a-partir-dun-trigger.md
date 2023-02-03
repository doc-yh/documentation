# ID généré à partir d'un trigger

Fonction trigger qui se déclenche au moment de l'insertion

<pre class="language-sql"><code class="lang-sql">create sequence if not exists DATA.SEQ;

CREATE OR REPLACE FUNCTION DATA.next_val() RETURNS trigger AS $$
        BEGIN
            NEW.av_id_piamp := nextval('DATA.SEQ');
    	    RETURN NEW;
	END;
<strong>$$ LANGUAGE plpgsql;
</strong>
CREATE OR REPLACE TRIGGER next_val
  BEFORE INSERT ON DATA.AVIS
  FOR EACH ROW
  EXECUTE FUNCTION DATA.next_val();
</code></pre>

Exemple d'insertion

```sql
INSERT INTO data.avis (av_id_piamp) values (default)
```
