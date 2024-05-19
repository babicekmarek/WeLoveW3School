 Šifrování (princip, funkce)
 Hashování (princip, funkce)

**Rozdíl mezi šifrováním a hashováním**: Zašifrovaná data jsme schopni získat zpátky obráceným postupem, tím, že použijeme klíč a data odkryjeme, oproti tomu hashování dat je nezvratný způsob ukrytí dat. Šifrování se používá k ukrývání dat, zatímco hashování se používá pro ověření integrity dat a autentizaci.

Typy šifer: 
- Transpoziční šifra - Nemění se znaky, ze kterých se text skládá, pouze se posune jejich význam, pro rychlé operace s šifrou lze využít tabulka.
- Substituční šifra - Konkrétní znaky jsou nahrazeny jinými znaky.
- Symetrické šifrování - K šifrování a dešifrování zprávy je používán jeden klíč. 
- Asymetrické šifrování - K šifrování a dešifrování se používají odlišné klíče, které jsou spolu matematický svázány.
- Hashování - Využije se hashovací tabulky.

Příklad: Napište v javě statickou metodu, která zašifruje text tak, že každý znak
nahradí jeho ASCII hodnotou, mezi čísly vloží „*“ a mezi slovy nechá mezeru.
``` Python

def hashovacimetoda(text):
    zaheslovano = ""
    for i in text:
        if i == " ":
            zaheslovano += " "
        else:
            zaheslovano += str(ord(i)) + "*"
    return zaheslovano[0:-1]
    
print(hashovacimetoda("abcd kocka"))

```

``` Java

class Hashovani{
    public static String zahashovat(String slovo){
        String zasifrovano = "";
        char[] Array = slovo.toCharArray();
        for (int i = 0; i < slovo.length(); i++){
            if (((int) Array[i]) == 32){
                zasifrovano +=(" ");
            }
            else {
                zasifrovano += ((int) Array[i]);
                if (i != slovo.length() - 1){
                    zasifrovano += "*";
                }
            }
        }
        return zasifrovano;
    }

    public static void main(String[] args) {
        System.out.println(zahashovat("abcd kocka"));
    }
}

```