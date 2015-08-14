## Convert JMdict ( + kanjidic2.xml and kradfile-u) into SQLite database

### Database structure

```sql
CREATE TABLE kanji (
 id integer,
 character varchar(1),
 reading_on varchar(255),
 reading_kun varchar(255),
 meaning varchar(255)
);
```
