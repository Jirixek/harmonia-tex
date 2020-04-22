# harmonia-tex
Šablona zavádějící styl harm.cz

## Popis a použití
Toto šablona (harmstyle.tex) slouží ke generování PDF dokumentů ve stylu mojí stránky Harmonia. Jako ukázku užitečnosti jsem zkonvertoval stránku [Melodické vedení](http://harm.cz/maturita/klasika/melodicke_vedeni), která obsahuje všechny konstrukce (popsané níže).

## Konstrukce/makra
Jako hlavní fontovou rodinu šablona používá `TG Adventor`. Poté ještě importuje fonty `Noto Sans ExtraLight` a `Noto Serif`, které se používají pro `\lead` a harmonické funkce.

### Sloupce vedle sebe
Makra `\twocols`, `\threecols` a `\fourcols` berou dva, tři či čtyři parametry. Vytvoří *n* sloupců vedle sebe, které jsou zarovnané k vršku.

### Barevné boxy
`\bluebox`, `\greenbox` a `\redbox` berou jeden parametr. Obsah parametru obalí barevným rámečkem.

### Zadávání not
`\onestaff` a `\twostaff` vytvoří prostředí pro zadávání not. Jejich výhoda spočívá hlavně v tom, že není třeba zadávat stejné informace pořád dokola.

`\notefnk` slouží pro zadávání funkce danému souzvuku. Parametr se zarovná pod notovou osnovu.

### Tabulky
`\tableto{size}{atr}{value}` vytvoří tabulku daného rozměru.
`\crx` ukončí řádek tabulky a obarví ho modře.
`\crlig` ukončí řádek tabulky a vloží mezi řádky šedou čáru.
Jako inspiraci jsem použil [OPMac Tricks](http://petr.olsak.net/opmac-tricks.html#crx).

### Miscellaneous
`\sup` vloží horní index v textovém módu.
`\sub` vloží spodní index v textovém módu.
`\supsub{sup}{sub}` vloží oba dva indexy nad sebe v textovém módu.
`\footer` vloží dodatek po vzoru stylu [Harmonia](harm.cz).

## Generování pdf dokumentu
PDF se třeba generovat na dvakrát, protože MusixTex si potřebuje ujasnit, kde mu začínají a končí osnovy, aby následně mohl provést cut na požadovaný `\hsize`. Lze využít následující postup nebo použít `tex.sh`, který tohle udělá za Vás. 
```
luatex -fmt pdfcsplain "$compileFile"
musixflx "$compileFile"
luatex -fmt pdfcsplain "$compileFile"
```
