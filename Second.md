## Kanji reading practice sheets

### How to

Just enter characters you want to practice into @mykanji array, fill in what characters you already know (not needed) into @iknowkanji array and execute script:

```
perl generate_kanji_list.pl > practice.html
```

### How it works

First it collets all kanji from database into hash. Next, usekanji table is filled with characters from @mykanji and @iknowkanji. usekanji only purpose is to count how many of those characters appear in each word. After that each character from @mykanji is printed inside template with example words and radicals. Example words are choosen based on how many of selected characters are inside them and lenght of the word. 

Radicals printed below character are separated into two types:

1. Radicals
2. Parts

Each character has (AFAIK) only one base radical, but you can also identify it by parts (http://jisho.org/search/%E6%A0%A1%20%23kanji).

There are three variable that control how the result looks like:

1. $words_per_character - how many example words print with each character.
2. $print_radicals - show/hide radicals under characters.
3. $print_suggested_kanji - count kanji that appear in words (excluding @mykanji and @iknokanji) and print them into STDERR.
