 práce s pointery (pointerová aritmetika ✅, zobrazení adres ✅)
 procházení pole pomocí pointerů ✅

Není OOP, neobsahuje GUI, přímý přístup do paměti, nízkoúrovňoví.

Programovací jazyk C má tu výhodu, že může pracovat s pointery a s proměnnými v rámci celé paměti, lze v něm pracovat na nižší úrovni, tato výhoda se může stát velmi rychle nevýhodou, nesmíme si přepsat žádnou z důležitých systémových proměnných.

Pointer je proměnná, která odkazuje na fyzické místo v paměti.

Pointerová aritmetika je způsob práce v C, kdy provádíme operace jako sčítání a odčítání za pomoci pointerů.
Když se budeme pohybovat v paměti, vzhledem k tomu s jakým typem pointerů pacujeme, například u INT o 4 Bajty. 

Zobrazení adres v C provedeme tím, že na operátor ukážeme pomocí & -> &variable
Adresy jsou obvykle v hexadecimálním formátu.

``` text
Adresa proměnné variable: 0x7fff4e4e5ef4
Hodnota pointeru: 0x7fff4e4e5ef4
Po posunutí o jeden int: 0x7fff4e4e5ef8
```

``` C
#include <stdio.h>

int main()
{
    int data[5] = {5,10,15,20,25};
    for (int i = 0; i < 5; i++) {
        printf("%d\n", data[i]);
        printf("%p\n", &data[i]);
    }
    
    return 0;
    
}

```