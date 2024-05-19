 druhy chyb, ošetřování chyb ✅
 výjimky a jejich zpracování✅
 jednotkové testy ✅

*Chyba byla jít na tuhle školu, představ si, že bys byl na gymplu, kde se učíš společenskovědní seminář, zeměpis, matematiku, angličtinu a češtinu k maturitě. To by ti bylo dobře, všechno by ti bylo jedno, prostě by ses učil, nevymýšlel tyhle nesmysly.*

Chyba je okamžik, kdy program směřuje někam, kam vývojář nezamýšlel, abychom předešli fatálním stavům, tak musíme tyto případné stavy ošetřit.

Druhy chyb:
- Syntaktická - Tuto chybu nám oznámí kompilátor při spuštění programu, chyba je spuštěna špatnou syntaxí, špatný zápis programovacího jazyku.
- Sémantická - Program funguje, kompilátor nenajde žádnou chybu, ale program se ubírá směrem, který programátor nepředpokládal. Během běhu programu není vyvolána žádná chyba, kompilátor předpokládá, že žádná chyba nenastala, tuhle chybu může odhalit pouze pogramátor.
- Neočekávaná událost - 

Ošetření chyb, program se může dostat do oblastní, které programátor neplánuje, může nastat chyba, a tak je důležité kód opatřit výjimkami, ty můžou zabránit nevhodnému zásahu uživatele.

Výjimky a jejich zpracování
- Try - Toto je blok programu, kde očekáváme, že nastane výjimka, pokud nenastane, program běží dál, ale pokud nastane, musí vyvolat další blok kódu, který se nazývá catch.
- Catch / except - Do tohoto bloku se program musí dostat pokud nastane výjimka.
- Finally - Tento blok se provede vždy na závěr bloku výjímek, nezáleží jestli k chybě dojde, nebo ne.

Jednotkové / UNIT testy
Jednotkové testy testují izolovanou část kódu, ověřují jeho funkčnost nezávisle na zbytku kódu. Většinou testujeme nějakou třídu nebo metodu.

***Příklad: Pomocí výjimek ošetřete konzolový vstup od uživatele.
• V prvním vstupu požadujete, aby uživatel zadal textový řetězec, který
začíná číslicí. Vstup, který tuto podmínku nesplňuje, vyhodí vaši vlastní
výjimku.
• Druhým uživatelským vstupem bude číslo v rozsahu 0 až 10; kontrolujete,
zda je vstup opravdu číslo v tomto rozsahu. Pokud všechny vstupy
projdou, text i číslo se vypíší. Ohlídejte i jiné případné chyby vstupu.***

``` Python

def prvni(text):
    try:
        int(text[0])
        print("First character is a number")
    except:
        print("First Character is not a number")

a = input("zadej text zacinajici cislici: ")
prvni(a)

def druhy(cislo):
    try:
        cislo = int(cislo)
        if cislo >= 0 and cislo <= 10:
            print("Number",cislo,"is in range")
        else:
            print("Number is out of range")
    except ValueError:
        print("Input is not a number")

b = input("Zadej cislo od 0 do 10: ")
druhy(b)

```