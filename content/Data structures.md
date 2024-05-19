pole ✅, lineární seznam ✅, strom ???
· fronta ✅, zásobník ✅
· slovník ✅, množina✅
Příklad ✅

Data se organizují do datových struktur v paměti počítače, díky tomu jsou více efektivně používané zdroje paměti. Datová struktura ukládá data, která spolu logicky souvisejí.

**Pole:** Taková datová struktura, která seskupuje prvky stejného datového typu. K prvkům v poli přistupujeme pomocí indexů. Velikost pole se nemění. Většinou se  jedná o primitivní (abstraktní) datový typ. Vícerozměrné pole je praktické využití pole v poli, jednoduchá 2D struktur.
~~~ python
# pole v python
mylist = ["apple", "banana", "cherry"]
~~~

~~~ java
// pole v Java
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
~~~

**Lineární seznam:** Tato datová struktura se chová podobně jako pole, ale není mu moc podobné z programátorského hlediska. V paměti se neuloží celý seznam, ale uloží se vždy jeden prvek s odkazem na další prvek, těmto částem Lineárního seznamu se říká uzly.
~~~ java
// lineární seznam v Java (LinkedList)
import java.util.LinkedList;
LinkedList<String> cars = new LinkedList<String>();
~~~
Něco mezi polem a lineárním seznamem je dynamické pole. 
**Dynamické pole:** Tato datová struktura funguje na principu, kdy se uloží pole o určité délce, pokud dojde tomuto poli kapacita, vytvoří se nové pole o větší kapacitě.
~~~ Java
// dynamické seznam v Java (ArrayList)
import java.util.ArrayList;
ArrayList<String> cars = new ArrayList<String>();
~~~

**Strom:** ?

**Fronta:** Toto je typ datové struktury, typ toho jak se ukládají a jak se pracuje s daty. Tento typ datové struktury funguje tak, že prvek, který je uložen jako první je vybrán jako první. *FIFO - first in first out*.

**Zásobník:** Toto je typ datové struktury, typ toho jak se ukládají a jak se pracuje s daty. Tento typ datové struktury funguje tak, že prvek, který je uložen jako první je vybrán jako poslední. *LIFO - last in first out.*

**Slovník:** Tato datová struktura funguje na principu asociací, každý z dvojice klíče a hodnoty tvoří jeden prvek v seznamu. V rámci jednoho slovníku musí být klíče jedinečné a neměnné, zároveň může být klíčem každý datový typ.
~~~ Python
# slovník v Python
thisdict = {"brand": "Ford", "model": "Mustang", "year": 1964}
~~~

~~~ Java
// slovník v Java
import java.util.HashMap;
import java.util.Map;
Map<String, String> slovnik = new HashMap<>();
slovnik.put("jablko", "apple");
~~~
**Množina:** Taková datová struktura, která obsahuje nesetříděné hodnoty, pořadí hodnot se může jakkoliv změnit, žádná z těchto hodnot se nesmí opakovat. 
~~~ Python
planety = set(("Země", "Mars", "Jupiter", "Saturn", "Uran", "Neptun"))
~~~

Příklad:
~~~ Java
// o Naprogramujte třídu FIFO (Fronta) jako třídu, kde datovou strukturou pro ukládání dat bude pole reálných čísel.
// o Délka pole bude zadaná při vytváření instance pomocí argumentu konstruktoru.
// o Bude obsahovat metody pro:
//      o Přidání prvku
//      o Odebrání prvku
//      o toString()

import java.util.Arrays; 

class FIFO {
    private Float[] seznam;
    private int delka;
    private int obsazene;

    public FIFO(int delka) {
        this.delka = delka;
        this.obsazene = 0;
        seznam = new Float[delka];
    }

    public void pridani(Float prvek){
        if (delka > obsazene){
            seznam[obsazene] = prvek; obsazene+=1;
        }
    }

    public void odebrani(int index){
        if (index > obsazene-1){System.out.println("FIFO index out of range");}
        else if (index < obsazene){
            seznam[index] = null; obsazene-=1;
        }
    }

    @Override
    public String toString() {
        return "FIFO [seznam=" + Arrays.toString(seznam) + ", delka=" + delka + ", obsazene=" + obsazene + "]";
    }

    public static void main(String[] args) {
        FIFO fronta = new FIFO(5);
        fronta.pridani(5.0f);
        fronta.pridani(10.0f);
        fronta.pridani(15.0f);
        fronta.pridani(20.0f);
        fronta.pridani(25.0f);
        fronta.pridani(30.0f);
        System.out.println(fronta);
        fronta.odebrani(0);
        fronta.odebrani(3);
        fronta.odebrani(2);
        fronta.odebrani(1);
        System.out.println(fronta);
    }
}
~~~