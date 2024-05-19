• tabulky databáze mysql
• přidání uživatele databáze, práva, role
• zamykání tabulek, transakceexitů
• pohledy, uložené procedury, triggery

Databáze musí být řádně zabezpečená před přístupem neoprávněných osob. K tomu slouží práva uživatelů, kteří pak v databázi smějí dělat pouze to, co jim je povolené.

Tabulky jsou jedním ze základních databázových objektů. Slouží k přímému uložení dat do prostoru relační databáze. Má pevně daný počet sloupců, které určují typ a význam hodnot v takovém sloupci uložených. Není možné, aby dva různé záznamy v tabulce měly odlišný počet položek, nebo obsahovaly ve stejné položce různé datové typy.

Přídání uživatele do databáze, použíjeme příkaz CREATE USER

``` SQL

CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';

```
Takový uživatel nemá žádná práva a je nutné mu je prvně přidělit.

Pokud chceme práva přidat použijeme příkaz GRANT a pokud je chceme odebrat použijeme příkaz REVOKE

``` SQL

-- Přidání povolení na SELECT a INSERT pro všechny tabulky v databázi website.
GRANT SELECT, INSERT ON website.* TO 'username'@'localhost';

-- Přidání všech oprávnění pro všechny databáze a jejich tabulky.
GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost';

-- Odebrání oprávnění na DROP pro všechny databáze a jejich tabulky.
REVOKE DROP ON *.* TO 'username'@'localhost';

-- Přidání oprávnění měnit oprávnění uživatelů (může přidělovat prává, která sám má).
GRANT USAGE ON *.* 'username'@'localhost' WITH GRANT OPTION;

```

Role - můžeme přidělovat role, skupina uživatelů se stejnými právy.

``` SQL

CREATE ROLE 'app_developer', 'app_read', 'app_write';
GRANT ALL ON app_db.* TO 'app_developer';
GRANT SELECT ON app_db.* TO 'app_read';
GRANT INSERT, UPDATE, DELETE ON app_db.* TO 'app_write';
CREATE USER 'dev1'@'localhost' IDENTIFIED BY 'dev1pass';
CREATE USER 'read_user1'@'localhost' IDENTIFIED BY 'read_user1pass';
CREATE USER 'read_user2'@'localhost' IDENTIFIED BY 'read_user2pass';
CREATE USER 'rw_user1'@'localhost' IDENTIFIED BY 'rw_user1pass';
GRANT 'app_developer' TO 'dev1'@'localhost';
GRANT 'app_read' TO 'read_user1'@'localhost', 'read_user2'@'localhost';
GRANT 'app_read', 'app_write' TO 'rw_user1'@'localhost';

```

Zamykání tabulek, jsme schopní zamknout tabulku, když s ní potřebujeme pracovat, provést nějakou transakci.

Pohledy, způsob vytvoření, nebo předpřipravení nové tabulky pomocí nějakého dotazu, po vytvoření pohledu můžeme s tabulkou pracovat jako s normální tabulkou.

Procedury jsou prakticky funkce v SQL, předpřipravíme si ji dopředu a později ji můžeme zavolat s nějakým argumentem.

Trigger je pak nějaká uložená procedura, která se spouští automaticky v souvislosti s provedením nějakého akčního dotazu v tabulce. Dále se od uložených procedur liší nemožností předávat nějaké vstupní parametry nebo něco vracet. Výhoda je, že trigger pracuje ještě s neupravenými daty tabulek.

Příklad
• Vytvořte pohled: jméno studenta, datum zkoušky, počet bodů, které
získal na zkoušce pro případy, kdy student získal více jak 50 bodů.
Vysvětlete na příkladu vlastnosti pohledu (view)

``` SQL

CREATE VIEW pohled20 AS
SELECT student.name, grade_event.date, score.score
FROM student
LEFT JOIN score
ON student.student_id = score.student_id
LEFT JOIN grade_event
ON score.event_id = grade_event.event_id
WHERE score.score > 50;

```

• jak byste udělali proceduru, která by měla stejnou funkčnost jako tento
trigger, ale minimální počet bodů by byl jako argument této procedury

``` SQL

DELIMITER //
CREATE PROCEDURE procedura (IN minimalniHodnota INT)
BEGIN
    SELECT student.name, grade_event.date, score.score
    FROM student
    LEFT JOIN score ON student.student_id = score.student_id
    LEFT JOIN grade_event ON score.event_id = grade_event.event_id
    WHERE score.score > minimalniHodnota;
END //
DELIMITER ;

CALL procedura(50);


	```