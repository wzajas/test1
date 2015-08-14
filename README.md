## Convert JMdict + kanjidic2.xml + kradfile-u into SQLite database

### Content

Only words that have kanji in them go into database, but it's fairly simple to modify the script to generate full dictionary.

### Database structure

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

### Get files

kradfile-u http://www.kanjicafe.com/downloads/kradfile-u.gz

JMdict ftp://ftp.monash.edu.au/pub/nihongo/JMdict.gz

kanjidic2.xml http://www.edrdg.org/kanjidic/kanjidic2.xml.gz

```
wget http://www.kanjicafe.com/downloads/kradfile-u.gz ftp://ftp.monash.edu.au/pub/nihongo/JMdict.gz http://www.edrdg.org/kanjidic/kanjidic2.xml.gz
```

#### Unpack

`
gzip -d *gz
`

### Generate dumps

`
perl generate_dict.pl
`

### Import dumps into sqlite

```
sqlite dictionary.db < database_structure.sql
sqlite dictionary.db < import.sql 
```
