# Zápis řetězců

Teď se podíváme na zoubek řetězcům.
Už s nimi trochu umíš, tak začneme rekapitulací.

Textový *řetězec* (angl. *string*) je datový typ (druh *hodnot*),
který obsahuje text – třeba slovo nebo větu.

Když řetězec zadáváš do programu, musíš ho označit – uzavřít do
*uvozovek*, buď jednoduchých nebo dvojitých:

```python
'tohle je řetězec'
"tohle taky"
```

Je velký rozdíl mezi `print('cislo')` – vypiš slovo „cislo“ –
a `print(cislo)` – vypiš hodnotu výrazu `cislo`.
Jednou je `cislo` pět konkrétních písmen; podruhé *instrukce* k použití
proměnné.
Počítač, na rozdíl od lidí, rozdíl mezi textem a instrukcí nepozná z kontextu,
a tak je uvozovky potřeba používat důsledně.

{{ figure(
    img=static('quote-comic.svg'),
    alt='(Ilustrační komiks. Člověk říká robotovi: "Řekni Pavlovi, ať mi zavolá!". Robot odpoví: "PAVLOVI AŤ MI ZAVOLÁ!")',
) }}


## Znaky

Texty sestávají z jednotlivých písmenek.
Řetězce víceméně taky, ale aby bylo jasné, co přesně tím *písmenkem*
myslíme, říkáme, že řetězce sestávají ze *znaků* (angl. *characters*).

Takový znak může být písmenko (např. `A`) nebo číslice (`3`),
ale i jiný symbol (`!`).

Každý řetězec má určitý počet znaků.
Kolik, to zjistíš pomocí funkce `len()`.
Třeba řetězec `Ahoj!` má znaků pět:

```pycon
>>> len('Ahoj!')
5
```

Jeden ze zajímavějších znaků je *mezera*.
Je to taky znak. V řetězci se tedy chová stejně jako písmenko:

```pycon
>>> len(' ')
1
>>> len('K ní')
4
>>> len('3 + 2')
5
```

Mimochodem, řetězec může být i prázdný – pak má nula znaků:

```pycon
>>> len('')
0
>>> len("")
0
```


## Uvozovky

K uvození řetězce můžeš použít jednoduché nebo dvojité rovné uvozovky.
Není mezi nimi rozdíl.
Podobně `4.0` a `4.000` jsou dva zápisy téhož čísla,
tak `'slovo'` a `"slovo"` pro Python označuje stejnou
hodnotu, skládající se ze stejných pěti písmen.

Použité uvozovky nejsou součástí hodnoty – python si „nepamatuje“, jakým
způsobem byl řetězec uvozen.
Když má nějaký řetězec vypsat s uvozovkami, jedny si k tomu vybere – většinou
ty jednoduché:

```pycon
>>> "python"
'python'
>>> 'slovo'
'slovo'
```

> [note]
> Předchozí příklad je z interaktivního režimu Pythonu, který ukazuje hodnoty
> výrazů „programátorsky“ – pokud možno tak, jak se zapisují v Pythonu.
> Funkce `print()` vypisuje hodnoty „hezky“, „pro uživatele“ – v případě
> řetězců tedy bez uvozovek.


### Uvozovky v uvozovkách

Proč si při zadávání textu můžeš vybrat mezi dvěma druhy uvozovek?

Občas se stane, že v rámci textu potřebuješ použít samotnou uvozovku (nebo
apostrof).
Pak musíš „kolem“ řetězce použít tu druhou:

```python
print('Zpívala si: "Tralala!"')
print("Byl to Goa'uld, parazit z planety P3X-888")
```

Když v rámci textu použiješ stejnou uvozovku jako „kolem něj“, tak bude Python
naprosto zmatený.

```pycon
>>> len("Zpívala si: "Tralala"")
Traceback (most recent call last)
  File "<>", line 1
    len("Zpívala si: "Tralala"")
                      ^
SyntaxError: invalid syntax
```

Pokud používáš chytrý editor, doporučuju si zvyknout na to, jakou barvou
máš řetězce zvýrazněné.
Často to pomáhá odhalit chybky.


## Sekvence se zpětným lomítkem

Co dělat, když v řetězci potřebuješ *oba* druhy uvozovek,
jako ve větě `Vtom vnuk křik': "Hleď!"`?

Můžeš si pomoci tím, že spojíš dva řetězce:

```pycon
>>> print("Vtom vnuk křik': " + '"Hleď!"')
Vtom vnuk křik': "Hleď!"
```

Ale lepší způsob je použít speciální zápis se *zpětným lomítkem*.
Kdykoli se v řetězci objeví sekvence `\'` nebo `\"`, Python dá do řetězce danou
uvozovku.

```pycon
>>> print("Vtom vnuk křik': \"Hleď!\"")
Vtom vnuk křik': "Hleď!"
>>> print('"Jen ho nech," řek\' děd. "Kdo zná líp kraj?"')
"Jen ho nech," řek' děd. "Kdo zná líp kraj?"
```

Ve výsledném řetězci pak ovšem žádné zpětné lomítko *není*.
Sekvence `\'` je jen způsob, jak v Pythonu zadat `'` – jediný znak.
Tomu je celkem důležité porozumět.
Zkus si, zvládneš jestli předpovědět výsledek těchto příkazů:

```python
print(".\".")
len(".\".")
".\"."  # (v interaktivním režimu)
```

{% filter solution %}
```pycon
>>> print(".\".")
.".
>>> len(".\".")
3
>>> ".\"."
'.".'
```
{% endfilter %}


Znaků které se zadávají sekvencí se zpětným lomítkem je více.
Jedna ze zajímavějších je `\t`, představující tabulátor – jediný znak, který
se, když ho vypíšeš, „roztáhne“ na víc mezer.

```pycon
>>> print("a\tb")   # Výpis "pro lidi"
a       b
>>> "a\tb"          # Výpis "pro programátory"
'a\tb'
>>> len("a\tb")     # Počet znaků v řetězci
3
```

Se zpětným lomítkem můžeš zadat jakýkoli znak – včetně *emoji* – podle jména
(`\N{…}`) nebo identifikačního čísla (`\x..`, `\u....`, `\U........`)
standardu Unicode.
Stačí přesné jméno nebo číslo znát (nebo třeba dohledat na internetu).
V následujících řetězcích jsou takové znaky pro přehlednost mezi dvěma
pomlčkami `-`. Délka každého řetězce je tedy celkem 3:

```pycon
>>> print('-\N{GREEK CAPITAL LETTER DELTA}-')
-Δ-
>>> print('-\N{SECTION SIGN}-')
-§-
>>> print('-\N{GRINNING CAT FACE WITH SMILING EYES}-')
-😸-
>>> print('-\x60-')
-`-
>>> print('-\u30C4-')
-ツ-
>>> print('-\U0001F0BD-')
-🂽-
```


### Zpětné lomítko

Zpětné lomítko tedy začíná speciální sekvenci (známou pod anglickým
termínem *escape sequence*), kterou zadáš *jediný znak*.

Tahle vychytávka má jeden, někdy nepříjemný, důsledek: pokud chceš mít jako
součást řetězce zpětné lomítko (třeba ve jménech souborů na Windows),
nemůžeš použít přímo `\`.
Musíš použít speciální sekvenci `\\` – tedy lomítko zdvojit:

```python
print('C:\\PyLadies\\Nový adresář')
```

Podobně jako `\"` je zápis pro uvozovku a `\'` pro apostrof, sekvence `\\`
je zápis pro jedno zpětné lomítko.


### Nový řádek

Někdy potřebuješ řetězce, které obsahují více řádků.
Pythonní řetězce ale můžeš normálně napsat jen na *jeden* řádek.
(Python se tak snaží ulehčit hledání chyby, kdybys koncovou uvozovku
zapoměl{{a}}.)

Můžeš ale do řetězce znak pro nový řádek vložit pomocí sekvence `\n`:

```pycon
>>> print('Haló haló!\nCo se stalo?')
Haló haló!
Co se stalo?
```

Ono `\n` do řetězce vloží znak nového řádku.
Ten při výpisu ukončí stávající řádek a přejde na nový – ale jinak se chová
jako jakýkoli jiný znak:

```pycon
>>> print('-\n-')
-
-
>>> len('-\n-')
3
```


## Trojité uvozovky

Kromě `\n` je i druhý způsob, jak zadat řetězec se znakem nového řádku:
ohraničit ho *třemi* uvozovkami (jednoduchými nebo dvojitými)
na každé straně.
Dají se tak zadávat delší víceřádkové řetězce:

```python
basen = '''Haló haló!
Co se stalo?
Prase kozu potrkalo!'''
```

Pozor na to, že pokud je tenhle řetězec
v odsazeném kódu, každý jeho řádek bude začínat
několika mezerami.

```python
cislo = 4

if cislo > 0:
    print("""
        Výsledek porovnání:

        Číslo je kladné.
    """)
```

Víceřádkové řetězce se často používají jako dokumentační řetězce funkcí.
U nich nevadí, že jsou na začátku řádků mezery.


## Formátovací řetězce

Tato sekce byla vyčleněna ven, viz [Formátovací řetězce](../fstring)


## Výběr znaků

Už umíš spojovat dohromady kratší řetězce:

```python
spojeny_retezec = 'a' + 'b'
dlouhy_retezec = 'ó' * 100
```
Teď se podíváme na opačný proces: jak z dlouhého
řetězce dostat kratší součásti.
Začneme jednotlivými znaky.
Dělá se to operací *vybrání prvku* (angl. *subscripting*),
která se píše podobně jako volání funkce, jen s hranatými závorkami:

```python
pate_pismeno = 'čokoláda'[5]

print(pate_pismeno)
```

Funguje to? Dostal{{a}} jsi opravdu páté písmeno?

{% filter solution %}
Nedostal{{a}} – dostal{{a}} jsi *šesté* písmeno.
{% endfilter %}

Jak sis možná už všiml{{a}}, programátoři počítají od nuly.
„První“ prvek má vždy číslo nula, druhý číslo jedna a tak dál.

Stejně je to i s písmeny v řetězcích: první písmeno má číslo nula,
druhé jedna, ... a osmé písmeno má číslo sedm.

Proč je tomu tak?
K úplnému pochopení důvodů by ses potřeboval{{a}}
naučit něco o ukazatelích a polích,
což nebude hned, takže pro teď nám bude
stačit vědět,
že programátoři jsou prostě divní.

A nebo že mají rádi divná čísla jako nulu.

```plain
   [0] [1] [2] [3] [4] [5] [6] [7]

  ╭───┬───┬───┬───┬───┬───┬───┬───╮
  │ Č │ o │ k │ o │ l │ á │ d │ a │
  ╰───┴───┴───┴───┴───┴───┴───┴───╯
```


A když už jsme u divných čísel,
co se asi stane, když budu chtít vybírat písmena
pomocí záporných čísel?

{% filter solution %}
```python
print('Čokoláda'[-1])  # → a
print('Čokoláda'[-2])  # → d
print('Čokoláda'[-3])  # → á
print('Čokoláda'[-4])  # → l
```

Záporná čísla vybírají písmenka od konce.

```plain
   [0] [1] [2] [3] [4] [5] [6] [7]
   [-8][-7][-6][-5][-4][-3][-2][-1]
  ╭───┬───┬───┬───┬───┬───┬───┬───╮
  │ Č │ o │ k │ o │ l │ á │ d │ a │
  ╰───┴───┴───┴───┴───┴───┴───┴───╯
```
{% endfilter %}

Řetězce umí i jiné triky.
Třeba můžeš zjistit, jak je řetězec dlouhý
nebo jestli v sobě obsahuje daný menší řetězec.

<table class="table">
    <tr>
        <th>Zápis</th>
        <th>Popis</th>
        <th>Příklad</th>
    </tr>
    <tr>
        <td><code>len(r)</code></td>
        <td>Délka řetězce</td>
        <td><code>len('čokoláda')</code></td>
    </tr>
    <tr>
        <td><code>x&nbsp;in&nbsp;r</code></td>
        <td>True pokud je řetězec <code>x</code> obsažen v <code>r</code></td>
        <td><code>'oko' in 'čokoláda'</code></td>
    </tr>
    <tr>
        <td><code>x&nbsp;not&nbsp;in&nbsp;r</code></td>
        <td>Opak <code>x in r</code></td>
        <td><code>'dub' not in 'čokoláda</code></td>
    </tr>
</table>

Řetězce vždy berou v potaz velikost písmen,
takže např. `'ČOKO' in 'čokoláda'` je `False`.
Kdybys chtěl{{a}} porovnávat bez ohledu na velikost písmen,
musel{{a}} bys oba řetězce převést třeba na malá písmena
a pak je porovnat.

A jak se převádí na malá písmena?
K tomu budeme potřebovat další novou vlastnost Pythonu: metody.

## Metody

*Metoda* (angl. *method*) je jako funkce – něco, co se dá zavolat.
Na rozdíl od funkce je svázaná s nějakým *objektem* (hodnotou).
Volá se tak, že se za objekt napíše tečka,
za ní jméno metody a za to celé se, jako u funkcí, připojí závorky
s případnými argumenty.

Řetězcové metody `upper()` a `lower()`
převádí text na velká, respektive malá písmena.

```python
retezec = 'Ahoj'
print(retezec.upper())
print(retezec.lower())
print(retezec)
```

> [note]
> Všimni si, že původní řetězec se nemění; metoda vrátí nový řetězec, ten
> starý zůstává.
>
> To je obecná vlastnost řetězců v Pythonu: jednou existující řetězec se už
> nedá změnit, dá se jen vytvořit nějaký odvozený.


### Iniciály

Pro procvičení metod a vybírání znaků si zkus napsat program,
který se zeptá na jméno, pak na příjmení
a pak vypíše iniciály – první písmena zadaných jmen.

Iniciály jsou vždycky velkými písmeny
(i kdyby byl uživatel líný mačkat Shift).

{% filter solution %}
```python
jmeno = input('Zadej jméno: ')
prijmeni = input('Zadej příjmení ')
inicialy = jmeno[0] + prijmeni[0]
print('Iniciály:', inicialy.upper())
```

Způsobů, jak takový program napsat, je více.
Lze například zavolat `upper()` dvakrát – zvlášť na jméno a zvlášť na příjmení.

Nebo to jde zapsat i takto –
metoda se dá volat na výsledku jakéhokoli výrazu:

```python
jmeno = input('Zadej jméno: ')
prijmeni = input('Zadej příjmení ')
print('Iniciály:', (jmeno[0] + prijmeni[0]).upper())
```

Doporučuji spíš první způsob, ten se smysluplnými názvy proměnných.
Je sice delší, ale mnohem přehlednější.
{% endfilter %}

Řetězcových metod je celá řada.
Nejužitečnější z nich najdeš v [taháku](https://pyvec.github.io/cheatsheets/strings/strings-cs.pdf), který si můžeš stáhnout či vytisknout.

A úplně všechny řetězcové metody jsou popsány v [dokumentaci Pythonu](https://docs.python.org/3/library/stdtypes.html#string-methods) (anglicky; plné věcí, které ještě neznáš).

Všimni si, že `len` není metoda, ale funkce; píše se `len(r)`, ne `r.len()`.
Proč tomu tak je, to za nějakou dobu poznáš.


## Sekání řetězců

Teď se vrátíme k vybírání kousků řetězců.
Zkus, co dělá tenhle program:

```python
retezec = 'čokoláda'
kousek = retezec[5:]
print(kousek)
```

{% filter solution %}
Zápis `retezec[5:]` vybere *podřetězec* od znaku číslo 5 dál.
{% endfilter %}


Dá se použít i `retezec[:5]`,
který vybere všechno *až po* znak číslo 5.
Ale ne znak 5 samotný, takže `retezec[:5] + retezec[5:] == retezec`.


Co asi udělá `retezec[2:5]`?

A co `retezec[-4:]`?

```python
retezec = 'čokoláda'
print(retezec[:4])
print(retezec[2:5])
print(retezec[-4:])
```

Určování vhodných čísel, *indexů*, občas vyžaduje trochu zamyšlení.

U podobného „sekání“ (angl. *string slicing*)
je lepší si číslovat „hranice“ mezi znaky.
Člověk tomu pak lépe rozumí:

{{ anchor('slicing-diagram') }}
```plain
  ╭───┬───┬───┬───┬───┬───┬───┬───╮
  │ Č │ o │ k │ o │ l │ á │ d │ a │
  ├───┼───┼───┼───┼───┼───┼───┼───┤
  │   │   │   │   │   │   │   │   │
  0   1   2   3   4   5   6   7   8
 -8  -7  -6  -5  -4  -3  -2  -1

  ╰───────────────╯
  'čokoláda'[:4] == 'čoko'

          ╰───────────────╯
        'čokoláda'[2:6] == 'kolá'

                      ╰───────────╯
                      'čokoláda'[-3:] == 'áda'
```

## Cvičení

Jaká je délka těchto řetězců?

Výsledek zjistíš snadno, zkus se ale zamyslet a Python použít jen pro ověření.

{# Highlighted as plain text to avoid spoilers #}
```plain
{# 2, 3, 4, 5 -#}
print(len('ahoj'))
print(len("""Ahoj!"""))
print(len('a b'))
print(len( ' a b ' ))
print(len('\N{SNOWMAN}ové'))
print(len('a\nb'))
print(len('a\tb'))
print(len('"\'"'))

{# 3, 4, 5, 6 #}
print(len("""
abc"""))

{# 3, 5, 7, 9 #}
if True:
    print(len("""a
    b"""))

{# 7, 8, 9, more #}
print(len('C:\new_dir'))

print(len(f'{print}'))
```
