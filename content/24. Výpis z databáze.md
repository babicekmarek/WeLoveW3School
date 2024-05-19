• připojení se k databázi
• výpis dat z databáze

Příklad:
• naprogramujte HTML stránku s formulářem
• formulář bude obsahovat prvek pro vstup textu, do kterého zadáte jméno
studenta
• po zadání jména se připojíte k databázi a z tabulky student vypíšete
informace o všech zkouškách, které daný student absolvoval
• pokud student tohoto jména neexistuje, vypíšete o tom info
• po zadání jména se připojíte k databázi a z tabulky student vypíšete
informace o všech zkouškách, které daný student absolvoval
• pokud student tohoto jména neexistuje, vypíšete o tom info

``` SQL

SELECT grade_event.date, grade_event.category, grade_event.event_id, score.score
FROM grade_event
LEFT JOIN score
ON grade_event.event_id = score.event_id
LEFT JOIN student
ON score.student_id = student.student_id
WHERE student.name = "X"

```

``` HTML

<!DOCTYPE html>
<html>
<body>

<form action="welcome.php" method="POST">
Name: <input type="name" name="name"><br>
<input type="submit">
</form>

</html>


```

``` PHP

<?php
$host = "localhost";
$username = "user";
$password = "password";
$database = "database";


$name = $_POST["name"];
$conn = mysqli_connect($host, $username, $password, $database);

$sql = "SELECT score.event_id FROM score JOIN student ON score.student_id = student.student_id WHERE student.name = '$name'";

$result = mysqli_query($conn, $sql);

if ($result) {
    while ($row = mysqli_fetch_assoc($result)) {
        echo "Event: " . $row["event_id"] . "<br>";
    }
} else {
    echo "Error: " . $sql . "<br>" . mysqli_error($conn);
}

mysqli_close($conn);
?>

```