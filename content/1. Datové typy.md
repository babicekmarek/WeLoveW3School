Statické a dynamické typování ✅
Uložení dat v paměti ✅
práce s primitivními a neprimitivními datovými typy ✅
příklad ✅

**Datové typy:** Datový typ určuje druh hodnoty, která je uložená v proměnné.

**Rozlišujeme tyto datové typy:** Boolean (true/false), integer (), float (), string ().

**Statické typování:** Na začátku kódu se nastaví hodnota, tuto hodnotu bude mít celou dobu, setkal jsem se statickým typováním v Java. Chybu v špatném typu proměnné odhalí již kompilátor.

**Dynamické typování**: Na začátku se nastaví hodnota, ale tuto hodnotu můžeme změnit, třeba když ji uložíme do proměnné hodnotu jiného typu. Problém nemusí být tak jednoduché odhalit, minimálně kompilátor si této chyby nevšimne.

**Uložení dat v paměti:** Proměnná vznikne svojí deklarací, její typ se nastaví určením datového typu deklarované proměnné. Při vytvoření proměnné, při deklaraci je ve fyzické paměti vyhrazené uložiště o určené velikosti. (dynamické datové typy můžou změnit velikost)

| Datový typ | délka   | Rozsah hodnot                   |
| ---------- | ------- | ------------------------------- |
| boolean    | 1 bit   | 0 až 1                          |
| char       | 1 bajt  | 0 až 255                        |
| long       | 4 bajty | 0 až 4 294 967 295              |
| int        | 4 bajty | -2 147 483 648 až 2 147 483 647 |
| float      | 4 bajty | 1E-37 až 1E+37                  |
| double     | 8 bajtů | 1E-307 až 1E+308                |

**Primitivní datové typy:** booleaan, integer, float, char, nebo enum. Primitivní datové typy obsahují jeden prvek. Jsou zabudované přímo do jádra programovacího jazyka.

**Neprimitivní datové typy:** string, array, object. Neprimitivní datové typy obsahují í více prvků. Nejsou zabudované přímo do jádra programovacího jazyka, musíme importovat (např. v Java import array). Nejsou uložené přímo, ale odkazuje se na ně odkazem.

**Generické typy:** Generické datový typ znamená, že může zastupovat více datových typů. V Java je příkladem ArrayList, uložíme několik datových typů do jednoho pole. 

Příklad:

~~~ java
// o Napište generickou třídu Pole<E>, datová složka jsou data (prvky pole) a počet prvků v poli (ne kapacita pole). ✅
// o Pole nesmí mít prázdné prvky uprostřed, jen na konci. ✅
// o Napište metody pro:
        // o přidání prvku konec pole (+ potřebné kontroly) ✅
        // o odebrání prvku z libovolného místa (+ posun + vrácení hodnoty + potřebné kontroly)✅
// o Vytvořte jednu instanci této třídy ✅

// nevím jestli to můžu udělat takhle, podle mě nemůžu použít ArrayList

public class datovetypy<E> {
    private E[] seznam;
    private int pocetPrvku;

    
    @SuppressWarnings("unchecked")
    public datovetypy(int initialCapacity) {
        this.seznam = (E[])new Object[initialCapacity];
        this.pocetPrvku = 0;
    }

    public void pridej(E prvkek) {
        if (pocetPrvku < seznam.length) {
            seznam[pocetPrvku] = prvkek;
            pocetPrvku++;
        } else {
            System.out.println("Seznam je plný, prvek nebyl přidán.");
        }
    }

    public String odeber(int index) {
        if (index >= 0 && index < pocetPrvku) {
            for (int i = index; i < pocetPrvku - 1; i++) {
                seznam[i] = seznam[i + 1];
            }
            seznam[pocetPrvku - 1] = null;
            pocetPrvku--;
            return "Z místa s indexem " + index + " byl odstraněn prvek.";
        }
        return "Nic nebylo odstraněno";
    }

    @Override
    public String toString() {
        StringBuilder sb = new StringBuilder("Pole [seznam=");
        for (int i = 0; i < pocetPrvku; i++) {
            sb.append(seznam[i]);
            if (i < pocetPrvku - 1) sb.append(", ");
        }
        sb.append(", pocetPrvku=").append(pocetPrvku).append("]");
        return sb.toString();
    }

    public static void main(String[] args) {
        datovetypy<Integer> pole = new datovetypy<>(5);
        pole.pridej(5);
        pole.pridej(10);
        pole.pridej(15);
        pole.pridej(20);
        pole.pridej(25);
        System.out.println(pole);
        System.out.println(pole.odeber(3));
        System.out.println(pole);
    }
}
~~~
