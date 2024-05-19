SQL - Structured Query Language, jedná se o neprocedurální jazyk - sdělujeme, co chceme, ale ne jak to získat. Dotaz i odpověď jsou textové řetězce. Nezáleží na velikosti písmen příkazů. Jazyk lze s menšími změnami použít ve většině databázových systémů.

DDL - Data Definition Language - definuje struktury, příkaz CREATE
DML - Data Manipulation Language - umožňuje výběr, vkládání, mazání řádků a aktualizace SELECT, INSERT, DELETE
DCL - Data Control Language - Speciální příkazy pro řízení provozu a údržbu databáze.

SELECT vybírá z databáze nějaká data, doplněný o místo odkud FROM vybíráme.

Projekce: Vymezuje/upravuje, která data chceme vybrat z dané tabulky.

Restrikce, pomáhá nám omezit výběr dat, která z příkazu dostat, jedná se o primitivní podmínku. Můžeme používat logické operátory AND, OR, NOT a kulatých závorek. Operátor LIKE vyhledá podobné řetězce.
- 1 restrikce: WHERE, před seskupováním
- 2 restrikce: HAVING, po seskupování

Agregace, shlukování, databáze nabízí spoustu agregačních funkcí. Agregační funkce jsou ty, které zpracovávají několik hodnot a jako výsledek vrátí jednu hodnotu. Agregační funkce se používají přímo při použití příkazu SELECT. Funkce se nad řádky vykoná a výsledek je SELECTem vrácen. Stejně jako v jiných programovacích jazycích, nají tyto funkce závorky a případné parametry.

``` SQL

-- prezidenti, kteří mají ve jméně w nebo v
SELECT * FROM president 
WHERE president.first_name LIKE "%W%" OR president.first_name LIKE "%V%"; 

```

``` SQL

-- posledních 20 prezidentů podle abecedy, seřazeni podle příjmení a pak podle křestního jména
SELECT * FROM president
ORDER BY president.last_name DESC
LIMIT 20;

```

``` SQL

-- měsíc, počet prezidentů, kteří se v daném měsíci narodili
SELECT MONTH(president.birth), COUNT(president.id_president)
FROM president
GROUP BY MONTH(president.birth);

```

``` SQL

-- jako předchozí, ale jen měsíce s více jak 3 narozenými prezidenty
SELECT MONTH(president.birth), COUNT(president.id_president) AS pocet
FROM president
GROUP BY MONTH(president.birth)
HAVING pocet > 3;

```

``` SQL

-- na tabulce score: id studenta, id zkoušky, score na zkoušce, ale jen proscore, které je nadprůměrné (větší než celkový průměr bodů na všechzkouškách) = vnořený dotaz
SELECT student.student_id, grade_event.event_id, score.score
FROM student
LEFT JOIN score 
ON student.student_id = score.student_id
LEFT JOIN grade_event 
ON score.event_id = grade_event.event_id
WHERE score.score > (SELECT AVG(score.score) FROM score);

```
