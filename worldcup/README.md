# World Cup

football.db RSSSF (Rec.Sport.Soccer Statistics Foundation) Archive Data for the World Cup







to update pages use:

```
(i) download and convert .html to .txt
$  ruby prepare/prepare.rb worldcup        -u
$  ruby prepare/prepare.rb worldcup_full   -u
$  ruby prepare/prepare.rb worldcup_quali  -u

(ii)  try some format fixes
$  ruby fmtfix/fmtfix.rb worldcup        -u --no-tables --no-top
$  ruby fmtfix/fmtfix.rb worldcup_full   -u --no-tables --no-top
$  ruby fmtfix/fmtfix.rb worldcup_quali  -u --no-tables --no-top
```


for more on the update machinery, see [`/scripts` »](https://github.com/rsssf/scripts)