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

             .----------.
             | radicals |       .-------------.      .------------.
             |----------|       |    kanji    |      | kanjiwords |
      .----->| id       |       |-------------|      |------------|
      |      | radical  |     .>| id          |<-----| kanji_id   |
      |      | meaning  |     | | character   |      | word_id    |-----.
      |      '----------'     | | reading_on  |      '------------'     |
      |                       | | reading_kun |                         |
      |   .---------------.   | | meaning     |  .------------------.   |
      |   | kanjiradicals |   | '-------------'  |      words       |   |
      |   |---------------|   |                  |------------------|   |
      |   | kanji_id      |---'                  | id               |<--'
      '---| radical_id    |                      | kanji_reading    |
          '---------------'                      | hiragana_reading |
                                                 | meaning          |
                                                 | length           |
                                                 '------------------'
