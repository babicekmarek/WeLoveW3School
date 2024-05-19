 abstraktní třídy ✅
 rozhraní ✅
 kolekce objektů příbuzných tříd✅
 polymorfismus, downcasting ✅

- abstraktní třídy - Abstraktní třída je metoda, má předdefinované metody a proměnné, která má alespoň jednu metodu abstraktní (není nijak vyplněná). Objekt, ze kterého další objekt dědí se nazývá rodič a ten, který dědí, tak se nazývá potomek. Potomek může dědit pouze z jednoho rodičovského objektu.

- rozhraní - Rozhraní definuje hlavičky metod. Nutič metod, rozhraní má pouze abstraktní metody. Objekt potomek, který implementuje rodičovský objekt musí implementovat všechny metody rodiče. 

- Kolekce objektů příbuzných tříd - Třídy, které spolu úzce souvisí můžeme spojovat do kolekcí, díky kolekcím můžeme s objekty efektivněji pracovat. Namísto zapsání samostatného kódu po zpracování každého jednotlivého objektu je tak možné použít stejný kód ke zpracování všech prvků kolekce.

- Polymorfismus je volání metod z různých tříd konajíc stejnou funkci v rámci třídy, z níž byla volána.

- **Upcasting** (odhození směrem nahoru) používáme pokud chceme vytvořit třídu a následně využívat pouze třídu jí nadřazenou. Moc často se s touto potřebou nesetkáváme, ale je důležité tuto možnost mít. Tento proces může sloužit k vynucenému použití, přetížení určité metody. Z objektu *dítěte* vytváříme objekt *rodiče*.

- **Downcasting** používáme pokud chceme z nadřazené třídy vytvořit podtřídu. Při použití **downcastingu** převezmeme objekt a přiřadíme ho objektu podtřídy. Nejčastěji se s **downcastingem** setkáváme, když z instance nadtřídy potřebujeme získat přístup k metodám podtřídy. Z objektu *rodiče* vytváříme objekt *dítěte*.


``` Java

public interface IPlaceniRestaurace {
    float vypocetCenySDPH();
}

```

``` Java

public class Jidlo implements IPlaceniRestaurace{
    public float cena;

    public Jidlo(float cena) {
        this.cena = cena;
    }

    @Override
    public float vypocetCenySDPH() {
        return this.cena * 1.1f;
    }
}

```

``` Java

public class Napoje implements IPlaceniRestaurace {
    public float cena;
    public boolean alkoholicke;

    public Napoje(float cena, boolean alkoholicke) {
        this.cena = cena;
        this.alkoholicke = alkoholicke;
    }

    @Override
    public float vypocetCenySDPH() {
        if (this.alkoholicke){return this.cena * 1.21f;}
        return this.cena * 1.1f;
    }
}

```

``` Java

import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<IPlaceniRestaurace> objednavka = new ArrayList<IPlaceniRestaurace>();

        Jidlo jidlo1 = new Jidlo(100);
        Napoje napoj1 = new Napoje(50, true);
        Napoje napoj2 = new Napoje(50, false);

        objednavka.add(jidlo1);
        objednavka.add(napoj1);
        objednavka.add(napoj2);

        Float soucet = 0f;

        for (IPlaceniRestaurace i : objednavka){soucet+=(i.vypocetCenySDPH());}
        System.out.print(soucet);
    } 
}

```