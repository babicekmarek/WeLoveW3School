• způsoby autentizace a autorizace
• cookie proměnné
• session proměnné

Příklad:
• naprogramujte 2 provázané stránky
• jedna z nich bude vytvářet 2 session proměnné s vámi zvoleným
libovolným jménem i obsahem
• ve druhé se bude existence 1. session proměnné kontrolovat a hodnota 2.
session proměnné se pak zobrazí
• pokud session neexistují, vypíše se o tom informace
• mezi stránkami přecházejte libovolným způsobem


``` HTML

<!DOCTYPE html>
<html lang="cs">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>jedna</title>
</head>
<body>
    <h1>jedna</h1>
    <button onclick="createSessionVariables()">Vytvoř Session Proměnné</button>
    <br>
    <a href="dva.html">Přejít na dva</a>

    <script>
        function createSessionVariables() {
            sessionStorage.setItem("sessionVar1", "nastavena");
            sessionStorage.setItem("sessionVar2", "blabla");
            alert("Session proměnné byly vytvořeny.");
        }
    </script>
</body>
</html>


```

``` HTML

<!DOCTYPE html>
<html lang="cs">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>dva</title>
</head>
<body>
    <h1>dva</h1>
    <div id="message"></div>
    <br>
    <a href="jedna.html">Zpět na jedna</a>

    <script>
        window.onload = function() {
            var sessionVar1 = sessionStorage.getItem("sessionVar1");
            var sessionVar2 = sessionStorage.getItem("sessionVar2");
            var messageElement = document.getElementById("message");

            if (sessionVar1) {
                messageElement.textContent = "Hodnota druhé session proměnné: " +sessionVar2;
            } else {
                messageElement.textContent = "Session proměnné neexistují.";
            }
        }
    </script>
</body>
</html>

```