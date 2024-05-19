Do formulářů lze zapisovat pomocí adresy, a nebo HTTP dotazu. Do databází zapisujeme, protože potřebujeme data uložit na server např.: objednávka na eshop.

GET Veškerá data jsou odesílána jako součást URL adresy: *?id=11154&product=6448*. Všechna data se odešlou tímto způsobem, oddělená pomocí & proměnná a hodnota. Není vhodné odesílat pomocí takto přístupného dotazu cokoliv co je tajné, jako jsou hesla.

POST Odesílá data v hlavičkách HTTP dotazu. Data nejsou viditelná, ale jsou stále přístupná. Tento způsob je bezpečnější než GET způsob. Můžeme odesílat i soubory, ani jejich délka není tolik omezená jako u metody GET. 

Zabezpečení uživatelského vstupu.
Data můžeme kontrolovat již na straně uživatele, ale to nemusí být efektivní a ani účinné, a tak je lepší data kontrolovat na straně serveru. Je dobré zkontrolovat jestli jsou data ve správném formátu a odpovídají správnému typu. 

SQL injection. 
Pomocí formuláře můžeme odeslat SQL dotaz v poli, které není pro SQL dotaz přizpůsobeno a nevědomky si spustíme SQL dotaz na straně serveru, tohle může mít fatální důsledky, jako na VŠE, kde při vyplňování testu v papírové podobě a následném skenování testu, byla vyřazena školní databáze a byly smazány všechny známky studentů. Pole musí být nastaveno tak, aby pracovalo s případným dotazem jako textem a ne SQL dotazem.
Potřebujeme použít filtry, ty se používají ve tvaru regulérních výrazů. *bind_param("ssi", $a, $b, $c)*. Ověří, zda jsou proměnné string, string a integer.

Některé databáze se proti SQL injectům brání samotné.

~~~ HTML
naprogramujte HTML stránku s formulářem
• formulář bude obsahovat prvky pro vstup informací o nové zkoušce
(datum a kategorie zkoušky (enum! - viz struktura tabulky)) ✅
• po zadání hodnot se připojíte k databázi a údaje přidáte do tabulky
grade_event


<form action="welcome.php" method="POST">
    <label>Date</label>
    <input type="datetime" id="date" name="date"><br>
    <label>Category</label>
    <input type="text" id="category" name="category"><br>
    <label>id</label>
    <input type="number" id="id" name="id"><br>

    <input type="submit" value="Submit">
</form> 

~~~ 

``` PHP

<?php
$servername = "localhost";
$username = "user";
$password = "password";
$dbname = "database";

$date = $_POST["date"];
$id = $_POST["id"];
$category = $_POST["category"];


$conn = mysqli_connect($servername, $username, $password, $dbname);

if (!$conn) {
  die("Connection failed: " . mysqli_connect_error());
}

$sql = "INSERT INTO grade_event (date, category, event_id)
VALUES ('$date', '$category', '$id')";

if ($conn->query($sql) === TRUE) {
  echo "New record created successfully";
} else {
  echo "Error: " . $sql . "<br>" . $conn->error;
}
?> 

```