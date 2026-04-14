# football.db RSSSF (Rec.Sport.Soccer Statistics Foundation) archive data from around the world 

what?

find rsssf (tables) pages 
(automatically) converted via `fmtfix`  from .txt (see [/tables](https://github.com/rsssf/tables)), that is, the original .html pages only in .txt, 
to a format that gets you closer to the structured football.txt format 
by applying a series of "autofixes" e.g.

(i) converting "plain" round headers to football.txt-style round headers 
enclosed in square (`▪`) markers e.g.

```
Round 1                   =>     ▪ Round 1 ▪
Round 38                  =>     ▪ Round 38 ▪
Fifth Round               =>     ▪ Fifth Round ▪
Quarterfinals             =>     ▪ Quarterfinals ▪
Semifinals                =>     ▪ Semifinals ▪
Final                     =>     ▪ Final ▪
```

(ii) converting date headers in brackets (`[...]`) to football.txt-style "plain" dates and normalizing the date format for "single "dates 
or date ranges, legs & lists e.g.

```
[Aug 7]                       => _ Aug 7 _
[Aug 8]                       => _ Aug 8 _   
[Mar 21,22]                   => _ Mar 21 & 22 _
[Mar 21-23]                   => _ Mar 21-23 _
[Aug 30,31; Sep 1]            => _ Aug 30,31; Sep 1 _
```

note:  the underscores (`_`) are only used for "visual" debugging 
and not required (for parsing) in the football.txt format.

- (iii) converting "combined" round & date headers and more header variants e.g.

```
Round 24 [Mar 21]                     =>  ▪ Round 24 ▪  Mar 21
Round 24 [Mar 21,22]                  =>  ▪ Round 24 ▪  Mar 21 & 22
Round 24 [Mar 21-23]                  =>  ▪ Round 24 ▪  Mar 21-23
Round 7 [Aug 30,31; Sep 1]            =>  ▪ Round 7 ▪  Aug 30,31; Sep 1
Final [Jun 10, 2004, Imst]            =>  ▪ Final ▪  Jun 10 2004 @ Imst
Final [May 20]                        =>  ▪ Final ▪  May 20
Final [May 29, Wembley; att: 11,689]  =>  ▪ Final ▪  May 29 @ Wembley; att: 11,689
[Apr 11 2021, Brasília]               =>  _ Apr 11 2021 _ @ Brasília
```

(iiii) converting goal lines enclosed in brackets (`[...]`) - following a match line with a score - into football.txt-style enclosed in parentheses (`()`).  

<!--
aside - in the football.txt format text enclosed in brackets `[...]` is used (reserved) for notes.
-->

```
Arsenal        2-1 Leicester
  [Dennis Bergkamp 56, Trevor Sinclair 90og; Tony Cottee 57]
Chelsea        4-0 Sunderland
  [Gustavo Poyet 20, 78, Gianfranco Zola 32, Tore Andre Flo 77]
Coventry       0-1 Southampton
  [Ostenstad 85]
Watford        2-3 Wimbledon
  [Peter Kennedy 17pen, Michael Ngonge 71; Carl Cort 10, Marcus Gayle 28,
   Johnson 78og]

=>

Arsenal        2-1 Leicester
  (Dennis Bergkamp 56, Trevor Sinclair 90og; Tony Cottee 57)
Chelsea        4-0 Sunderland
  (Gustavo Poyet 20, 78, Gianfranco Zola 32, Tore Andre Flo 77)
Coventry       0-1 Southampton
  (Ostenstad 85)
Watford        2-3 Wimbledon
  (Peter Kennedy 17pen, Michael Ngonge 71; Carl Cort 10, Marcus Gayle 28,
   Johnson 78og)
```

and much more.


see [/scripts](https://github.com/rsssf/scripts) for more.





## all together now.  show don't tell. 

to get a better sense about the applied (format) autofixes via `fmtfix` -
look at some real-world samples with all changes all together now. 


before (in "classic" rsssf style)

```
Round 1
[Aug 7]
Arsenal        2-1 Leicester
  [Dennis Bergkamp 56, Trevor Sinclair 90og; Tony Cottee 57]
Chelsea        4-0 Sunderland
  [Gustavo Poyet 20, 78, Gianfranco Zola 32, Tore Andre Flo 77]
Coventry       0-1 Southampton
  [Ostenstad 85]
Leeds          0-0 Derby
Middlesbrough  0-1 Bradford
  [Saunders 90]
Newcastle      0-1 Aston Villa
  [Julian Joachim 75]
Sheffield W.   1-2 Liverpool
  [Carbone 88; Robbie Fowler 75, Titi Camara 84]
Watford        2-3 Wimbledon
  [Peter Kennedy 17pen, Michael Ngonge 71; Carl Cort 10, Marcus Gayle 28,
   Johnson 78og]
West Ham       1-0 Tottenham
  [Frank Lampard 45]
[Aug 8]
Everton        1-1 Man Utd
  [Jaap Stam 87og; Dwight Yorke 7]
```


after (in structured football.txt style for easy parsing and conversion to json, csv, sql & friends)

```
▪ Round 1 ▪
_ Aug 7 _
Arsenal        2-1 Leicester
  (Dennis Bergkamp 56, Trevor Sinclair 90og; Tony Cottee 57)
Chelsea        4-0 Sunderland
  (Gustavo Poyet 20, 78, Gianfranco Zola 32, Tore Andre Flo 77)
Coventry       0-1 Southampton
  (Ostenstad 85)
Leeds          0-0 Derby
Middlesbrough  0-1 Bradford
  (Saunders 90)
Newcastle      0-1 Aston Villa
  (Julian Joachim 75)
Sheffield W.   1-2 Liverpool
  (Carbone 88; Robbie Fowler 75, Titi Camara 84)
Watford        2-3 Wimbledon
  (Peter Kennedy 17pen, Michael Ngonge 71; Carl Cort 10, Marcus Gayle 28,
   Johnson 78og)
West Ham       1-0 Tottenham
  (Frank Lampard 45)
_ Aug 8 _
Everton        1-1 Man Utd
  (Jaap Stam 87og; Dwight Yorke 7)
```



and so on.




note - do NOT expect magic - the `fmtfix` applied autofixes get you closer to the structured football.txt format (that you can automatically parse and convert to json, csv, sql & friends) depending on the ad-hoc rsssf input format variant    

BUT expect some edge cases that you have to fix "by-hand" 
or with one-off search & replace scripts 
or why not? use a.i. and your llms of choice
