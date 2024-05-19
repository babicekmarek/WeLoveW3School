V textu bych vám rád vysvětlit a následně předvedl k čemu se používá **upcasting** a **downcasting** v Java. Základní koncept se pokusím vysvětlit na obrázku. Kde z *rodiče* pomocí **downcastingu** vytvoříme *dítě* a z *dítěte* pomocí **upcastingu** vytvoříme *rodiče*.

![](Diagram%20downcasting%20a%20upcasting.png)

**K čemu se vlastně upcasting a downcasting používá?**
- **Upcasting** (odhození směrem nahoru) používáme pokud chceme vytvořit třídu a následně využívat pouze třídu jí nadřazenou. Moc často se s touto potřebou nesetkáváme, ale je důležité tuto možnost mít. Tento proces může sloužit k vynucenému použití, přetížení určité metody. Z objektu *dítěte* vytváříme objekt *rodiče*.
- **Downcasting** používáme pokud chceme z nadřazené třídy vytvořit podtřídu. Při použití **downcastingu** převezmeme objekt a přiřadíme ho objektu podtřídy. Nejčastěji se s **downcastingem** setkáváme, když z instance nadtřídy potřebujeme získat přístup k metodám podtřídy. Z objektu *rodiče* vytváříme objekt *dítěte*.

Tyto důležité funkce v Java jsou velice vhodné, i když se s nimi setkáváme velice zřídka. **Upcasting** můžeme použít vždycky, avšak při používání **downcastingu** musíme dbát na bezpečnost (musíme použít ***instanceof***), protože si potřebujeme ověřit, že se jedná o instanci podtřídy.

**Příklad upcastingu**:
```java
class Vehicle {
    void drive() {
        System.out.println("Driving a vehicle");
    }
}

class Car extends Vehicle {
    private int fuelLevel;

    int getFuelLevel() {
        return fuelLevel;
    }
}

public class Main {
    public static void main(String[] args) {

        Vehicle myCar = new Car(); //UPCASTING

        Car myCar2 = new Car();
        Vehicle vehicle = myCar2; //UPCASTING
    }
}
```

**Příklad downcastingu:**
```java
class Vehicle {
    void drive() {
        System.out.println("Driving a vehicle");
    }
}

class Car extends Vehicle {
    void accelerate() {
        System.out.println("Car is accelerating");
    }
}

public class Main {
    public static void main(String[] args) {
        Vehicle vehicle = new Car(); // UPCASTING

        if (vehicle instanceof Car) { // CHECKING WHETHER IT IS AN INSTANCE
            Car anotherCar = (Car) vehicle; // DOWNCASTING
            anotherCar.accelerate();
        } else {
            System.out.println("Vehicle is not a Car");
        }
    }
}
```
