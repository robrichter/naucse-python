# Instalace editoru

Editor, program na úpravu textu, je základní pomůckou každého programátora.
A tak je dobré do něj investovat trochu času.

Je víceméně jedno, který programátorský editor budeš používat.
Pokud už nějaký oblíbený máš, stačí ho jen nastavit;
jestli ne, nějaký ti doporučíme.
Pokud ale používáš Poznámkový blok (Notepad) z Windows,
nebo TextEdit (editor předinstalovaný v macOS),
nebude ti stačit.
Stejně tak nejsou vhodné programy jako Word či Writer.


## Co programátorský editor umí

Editor pro programátory ti umožňí upravovat *prostý text* – písmenka.
Na rozdíl od programů jako Word, Writer či Pages neumožňuje text *formátovat*,
tedy dělat nadpisy, obarvovat, zvětšovat font pro jednotlivá slova,
vkládat obrázky a podobně.

Pomocí editoru budeš zadávat počítači příkazy, takže formátování nepotřebuješ.
Porovnej {{ gnd('sám', 'sama') }}, jaký je rozdíl mezi následujícími příkazy
pro někoho, kdo se jimi má řídit:

* Nakresli mi beránka!
* <font color="green">Nakresli <big><big>mi</big> <u>beránka</u>!</big></font>

Naše editory neumí formátování, ale neznamená že to jsou úplně „hloupé“
nástroje.
Aby se ti programy upravovaly pohodlněji, mají několik vychytávek:

Podpora více souborů
:   Větší projekty sestávají z více souborů, které můžeš mít v editoru
    otevřené všechny najednou.

Číslování řádků
:   Před každým řádkem se ukazuje číslo.
    To se bude velice hodit, až Python bude nadávat, že chyba je na řádku 183. 

Odsazování
:   V Pythonu je důležité, kolika mezerami řádek začíná.
    Správně nastavený editor nám odsazování značně zjednoduší.

Obarvování
:   Ačkoli nemůžeme u jednotlivých písmenek nastavovat barvu přímo, editor nám
    obarvením může napovědět, jak našim instrukcím bude počítač rozumět.
    Ale je to jenom nápověda:
    programátor s jinak nastaveným editorem může mít stejný soubor obarvený
    docela jinak.

> [note]
>
> Pro ilustraci, takhle může v editoru vypadat kousek kódu:
>
> ```python
>     1  @app.route('/courses/<course:course>/')
>     2  def course_page(course):
>     3      try:
>     4          return render_template(
>     5              'course.html',
>     6              course=course,
>     7              plan=course.sessions,
>     8          )
>     9      except TemplateNotFound:
>    10          abort(404)
> ```


## Volba a nastavení editoru

Pro náš workshop budeme používat editor Visual Studio Code. Klikni na jeho jméno a dostaneš se na
instrukce ke stažení a nastavení.
(Na tuhle stránku se pak už nemusíš vracet.)

* [Visual Studio Code]({{ subpage_url('vscode') }}) – doporučený editor pro
  Windows a macOS (a vhodný i pro Linux).
  V poslední době je to asi nejpopulárnější editor kódu.
  Nabízí mnoho funkcí a má velkou základnu uživatelů a vývojářů,
  takže se neustále vylepšuje.

  V poslední době toho umí víc a víc – a dokonce i věci,
  které ze začátku trochu překážejí.
  Neboj se editor přizpůsobit nebo něco vypnout.

  
