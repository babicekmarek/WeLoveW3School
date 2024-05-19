 XML, definice souboru XML ✅
 Export do XML, import z XML ✅
 parsování XML ✅
 JSON ✅

XML (Extensible Markup Language) je značkovací jazyk, který slouží pro uspořádání dat, nejvíce rozšířený společně s JSON, oproti kterému je však jeho struktura větší. Musí mít kořenový element, do kterého lze vkládat další vnořené elementy, jejíchž obsahem jsou data samotná.

``` XML

<?xml version="1.0" encoding="UTF-8"?>
<zamestnanec id=1>
    <jmeno>Jan</jmeno>
    <prijmeni>Novak</prijmeni>
    <plat>35000</plat>
    <datumnarozeni>1.1.2000</datumnarozeni>
</zamestnanec>

<zamestnanec id=2>
	<jmeno>Marek</jmeno>
    <prijmeni>Babicek</prijmeni>
    <plat>3</plat>
    <datumnarozeni>1.1.2001</datumnarozeni>
</zamestnanec>

```

Abychom omezili množinu možných výsledných podob dokumentů XML, používají se takzvané definiční soubory, napři. DTD (.dtd) nebo XML Schema (.xsd).

DTD zastaralý způsob uchovávání dat, současně se používá pouze pro definování jazyka HTML.

``` DTD

<?xml version="1.0"?>  
<!DOCTYPE note [  
<!ELEMENT note (to,from,heading,body)>  
<!ELEMENT to (#PCDATA)>  
<!ELEMENT from (#PCDATA)>  
<!ELEMENT heading (#PCDATA)>  
<!ELEMENT body (#PCDATA)>  
]>  
<note>  
<to>Tove</to>  
<from>Jani</from>  
<heading>Reminder</heading>  
<body>Don't forget me this weekend</body>  
</note>

```

JSON - Java Script Object Notation - soubor s daty, který se většinou používá pro Java Script, výhodou je, že se nemusí uzavírat žádné elementy a jeho velikost je při stejných datech poloviční oproti XML.

``` JSON

{
    "zamestnanec" :[
        {"jmeno":"Jan", "prijmeni":"Novak","plat":35000,"datumnarozeni":"1.1.2000"},
        {"jmeno":"Marek", "prijmeni":"Babicek","plat":1,"datumnarozeni":"1.1.2001"}
    ]
}

```

**Export do XML** je proces, kdy je vygenerován XML soubor s nějakými daty, které zadal uživatel při vyplňování webového formuláře. Tento XML soubor pak může zpracovat jiná aplikace, nebo je uchován jako záloha.

**Import z XML** je proces, kdy je soubor XML někam nahrán/načten a následně (obvykle) parsován, čímž josu z něj data vytažena a mohou být zobrazena nebo uložena do databáze.

**Parsování XML** je proces kdy data postupně načteme/načítáme a zpracováváme(vypisujeme nebo postupně analyzujeme). K souboru XML, který chceme parsovat můžeme přistupovat naráz nebo proudově. 
- Naráz data načteme do operační paměti, kde po celou dobu parsování zabíra místo. Nejjednodušší a nejrychlejší způsob parsování.
- Proudové zpracování, do operační paměti je vždy načtena pouze část a je postupně zpracováván. Nezabírá takové množství v operační paměti, protože je v ní uložena jen daná aktuálně zpracovávaná část.
V PHP je nejsnazší k XML souboru přistupovat tak, že ho převedeme na Objekt a dále s ním pracujeme jako s objektem.
