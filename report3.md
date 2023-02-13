

# Lab Report 3 - Researching Commands

In this blog post, I will research the various use cases of `grep`

## `-E` - pattern matching
This command turns the string input of grep into a regex string which has many useful filtering options. Our first example is 
```
find written_2/ > f.txt
grep -E “Bahamas|China” f.txt
```
![e1 example](/assets/report3/e1.png)

These commands search for files that contain either Bahamas or China in the filename. This is a powerful tool when we want to have multiple search terms in our grep command; something that is easy to do with regex. 

The second example will be `grep -E ".*k.*" f.txt` which searches for any filenames that contain the letter ‘k’.
![e2 example](/assets/report3/e2.png)

As we can see, the pattern matching capabilities of -E are extremely useful when we want to not only just search for simple strings.

## `-w` - word search
This command searches for the input as a word, not as a fragment. This means that the word must be in isolation (aka surrounded by non-letter characters or at the beginning/end of a line).
For example, 
```
cd written_2/travel_guides/berlitz2/
grep -w "El" Barcelona-WhatToDo.txt
```

![w1 example](/assets/report3/w1.png)
In this command, we searched for every instance of “El” as a word, so only space-separated instances of “El” came up in our response

```
grep "at" California-History.txt > g.txt
wc g.txt
grep -w “at" California-History.txt > g.txt
wc g.txt
```
![w2 example](/assets/report3/w2.png)

This second example clearly illustrates how powerful -w can be. The word “at” may appear in many other words such as “cat”, “attack”, and “lateral”. However, with -w, only *at* the word will appear in our output.

## `-v` - inverted
The grep command gets inverted by -v and searches for every line that is *not* matching the input string. 

Example on .txt files:
`grep -v "e" Costa-History.txt`

![v1 example](/assets/report3/v1.png)
In this command, we searched for every line of Costa-History.txt that did not contain the letter e. This was not very common, and there was only one line that matched this response.

Example on directory names:
```
find written_2 > f.txt
grep -v ".txt" f.txt > g.txt
```
![v2 example](/assets/report3/v2.png)

This second example searches for any path that does not contain “.txt” which eliminates all the text files from the output.

