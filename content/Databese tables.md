• získávání dat z více tabulek
• druhy spojení

Vazby mezi tabulkami:
Říká se jim relace, či kardinalita vztahu, vyjadřují kolik výskytů jedné tabulky může vstoupit do vztahu s výskytem druhé entity. 
- 1:1 jeden záznam v první tabulce odpovídá druhému záznamu v druhé tabulce. U relace 1:1 by měl být nastaven primární klíč na sloupec, kterým budou obě tabulky propojeny. *Příklad: manžel má 1 manželku, a ta má 1 manžela 1:1*
- 1:n jeden záznam v první tabulce odpovídá druhému záznamu v druhé tabulce. U relace 1:n by měl být zvolen u tabulky 1, a to na sloupec, který bude připojen k druhé tabulce. *Příklad: jeden zaměstnanec může mít N průchodů turniketem, ale jeden průchod odpovídá jednomu zaměstnanci*
- m:n několik záznamů v první tabulce odpovídá několika záznamům v druhé tabulce. U relace m:n primární klíč první tabulky odpovídá cizímu klíči druhé tabulky. *Příklad několik hostů u prostřeného stolu si může sednout na několik židlí a každá židle může být obsazena několika hosty.*

Získávání dat z více tabulek:
Pokud chceme pomocí jednoho dotazu získat data z více tabulek, tak musíme využít funkce spojování tabulek.
- Klauzule WHERE - Jde o nejjednodušší způsob propojení, ale maximálně dvou tabulek. Tabulky jsou propojeny na základě jedné společné hodnoty.

``` SQL
SELECT z.id_zakaznika, z.jmeno, o.id_objednavky, o.cena 
FROM zakaznici z, objednavky o 
WHERE z.id_zakaznika = o.id_zakaznika;
```

- JOIN obecně - Umožnuje více způsobů spojení. Obecně vypadá jeho klauzule následovně
``` SQL
SELECT * [seznam_polozek_vystupni_sestavy] 
FROM prvni_tabulka
JOIN[DRUH_SPOJENI] druha_tabulka [ON podminka_spojeni];
```

- INNER JOIN - výlučné spojení - spojení je provedeno na základě shody jednoho nebo více společných atributů, změnou pořadí tabulek dostaneme stejný výběr, jen se změněným pořadím.
``` SQL
ON z.id_zakaznika = o.id_zakaznika → USING(id_zakaznika)
```

- LEFT JOIN - Z první levé tabulky se ve výpisu objeví všechny řádky, z druhé pravé tabulky pouze řádky splňující podmínku. (jen objednávky, které mají objednavatele/zákazníka)
``` SQL
SELECT z.id_zakaznika, z.jmeno, o.id_objednavky, o.cena 
FROM zakaznici z
LEFT [OUTER] JOIN objednavky o 
ON z.id_zakaznika = o.id_zakaznika;
```

- RIGHT JOIN - Z druhé pravé tabulky se ve výpisu objeví všechny řádky, z první levé tabulky, pouze řádky splňující podmínku.
``` SQL
SELECT z.id_zakaznika, z.jmeno, o.id_objednavky, o.cena 
FROM zakaznici z
RIGHT [OUTER] JOIN objednavky o 
ON z.id_zakaznika = o.id_zakaznika;
```

- NATURAL LEFT JOIN - Jako součást spojení budou použita všechna shodná pole obou zdrojových tabulek.
``` SQL
SELECT z.id_zakaznika, z.jmeno, o.id_objednavky, o.cena FROM zakaznici z
NATURAL LEFT JOIN objednavky o;
```

- FULL JOIN - Vypíše z obou tabulek i řádky, které spojovací kritéria nesplňují.
``` SQL
SELECT z.id_zakaznika, z.jmeno, o.id_objednavky, o.cena 
FROM zakaznici z
FULL JOIN objednavky o 
ON z.id_zakaznika = o.id_zakaznika;
```

```

Příklad
Na tabulkách student, score, grade_event proveďte dotazy, pomocí kterých
získáte následující výpisy (pošlete SQL dotazy):
• jméno, pohlaví a score všech studentů, kteří dostali na zkoušce aspoň 90
bodů
• jméno, pohlaví všech studentů, kteří dostali na zkoušce aspoň 90 bodů
• datum zkoušky, počet studentů na zkoušce, průměrný počet bodů na
zkoušce
• jméno studenta, datum zkoušky, počet bodů, které získal na zkoušce, i
pro zkoušku, na které nebyl žádný student
• jméno studenta, pohlaví, datum zkoušky, typ zkoušky, počet bodů, jen
pro zkoušky, které byly T (testy)

``` MySQL

-- jméno, pohlaví a score všech studentů, kteří dostali na zkoušce aspoň 90 bodů
SELECT name, sex, score.score FROM student
LEFT JOIN score
ON student.student_id = score.student_id
WHERE score.score > 90;

```

``` MySQL

-- jméno, pohlaví všech studentů, kteří dostali na zkoušce aspoň 90 bodů
SELECT name, sex FROM student
LEFT JOIN score
ON student.student_id = score.student_id
WHERE score.score > 90;

```

``` MySQL

-- datum zkoušky, počet studentů na zkoušce, průměrný počet bodů na zkoušce
SELECT grade_event.date, COUNT(score.student_id), AVG(score.score)
FROM grade_event
LEFT JOIN score
ON grade_event.event_id = score.event_id
GROUP BY grade_event.date;

```

``` MySQL

-- jméno studenta, datum zkoušky, počet bodů, které získal na zkoušce, i pro zkoušku, na které nebyl žádný student
SELECT grade_event.date, student.name, score.score
FROM grade_event
LEFT JOIN score
ON grade_event.event_id = score.event_id
LEFT JOIN student
ON score.student_id = student.student_id;

```

``` MySQL

-- jméno studenta, pohlaví, datum zkoušky, typ zkoušky, počet bodů, jen pro zkoušky, které byly T (testy)
SELECT student.name, student.sex, grade_event.date, grade_event.category, score.score
FROM score
LEFT JOIN grade_event
ON score.student_id = grade_event.event_id
LEFT JOIN student
ON score.student_id = student.student_id
WHERE grade_event.category = "T";

```