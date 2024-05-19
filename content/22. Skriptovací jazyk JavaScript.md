 skriptování na straně klienta ✅
 technologie AJAX ✅
 TypeScript ✅
 Node.js ✅

Javacript je objektově orientovaný skriptovací jazyk. Snaží se webové aplikace vytvořit funkční, přispívá k rozmachu webových aplikací. Propojuje frontend s backend. Jeho syntaxe je podobná Javě, ale nefungují stejně. 

Skriptování na straně klienta probíhá po stažení webové stránky. Může nastat problém, že uživatel nemá Javascript povolený, a tím zabrání správné funkčnosti webové stránky. PHP je jiný typ skriptovacího jazyku, který pracuje na straně serveru, není potřeba mít nic staženého, ale programátor v PHP nemá stejné možnosti jako programátor v Javacsript.

AJAX (Asynchronic Javascript And XML) je technologie, která dělá Javascript asynchronní, nemusíme čekat až se stránka obnoví. Díky AJAX komunikuje klient se serverem a jsou schopni přenášet data. Díky technologii AJAX jsme schopni vyvíjet dynamické a asynchronní webové aplikace. AJAX obsahuje HTML, CSS, DOM, JSON a XML, Javascript tyto technologie propojuje.

TypeScript je nadstavba Javascript, je funkčnější, obsahuje vylepšené (pořádný třídy, rozhraní). Vývojáři jsou schopní psát funkční kód, zpětně se kompiluje do Javascript. Využívá se při práci s Frameworky a při vývoji webových aplikací.

Node.js je nástroj, který funguje na principu vyvolávání asynchronních událostí, zpracuje více požadavků současně, zrychlí odezvu webové aplikace. Využívá se pro real-time webové aplikace jako jsou chatovací, streamovací aplikace.


``` Javascript

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <input type="text" id="vstup">
    <button onclick="funkce()">otoc</button>
    <input type="text" id="vystup">
    <script>
        function funkce(){
            var reversedtext = "";
            var text = document.getElementById("vstup").value;
            for(var i = text.length-1; i >= 0; i--){
                reversedtext += text[i];
            }
            document.getElementById("vystup").value = reversedtext;
            }
    </script>
</body>
</html>

```