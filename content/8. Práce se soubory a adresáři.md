 procházení adresáře ✅
 čtení souboru, zápis do souboru ✅
 nahrávání souboru ✅
 serializace objektů ✅

Všechny soubory jsou jak ve Windows, tak Linux a ostatních OS upořádány do adresáře, v případě Linux může nastat případ jediného adresáře, ale stále je procházet soubory. Každá aplikace potřebuje přistupovat k souborům. V Javě používáme k přistupování k souborům třídu File, stejně přistupujeme k souboru i adresáři. Přístup k adresářám a souborům v Java není ideální řešení, je funkční pouze v rámci možností.

Procházení adresáře: Adresář lze procházet například rekurzivně, taková funkce bude mít pravděpodobně jeden argument, argument s cestou k adresáři.

Čtení souboru, zápis do souboru: Ukládá data uživatelů, jde o primární způsob ukládání dat. Metody pro přístup k souborům jsou přímo implementovány v programovacích jazycích. 
- FileReader – metoda read()- pro čtení souboru
- FileWriter – metoda write()- pro zápis do souboru
- close() – metoda pro uzavření relace (práce se souborem) – musíme volat po dokončení čtení nebo zápisu

Nahrávání souborů: Proces, kdy soubor je nahraný na vzdálený server, na vzdáleném serveru je soubor zpracován a uložen. O proces přenosů se v rámci internetu stará protokol http(s). Pro upload se používá metoda POST, soubor se postupně nahrává do předdefinovaného adresáře, pokud je přenos v pořádku a nevyskytne se žádný problém, tak je přesunut do zadaného umístění

**Serializace objektů:** uložení objektu, tak abychom se k němu kdykoliv mohli vrátit, konverze objektu na proud bitů a následné uložení do paměti v podobě souboru. 
**Deserializace objetků:** obnovení bitů reprezentující nějaký objekt ze souboru do tvaru objektu.

``` Java 

import java.io.Serializable;

public class Person implements Serializable{
    private String name;
    private int age;

    public Person(String name, int age){
        this.name = name;
        this.age = age;
    }  

    @Override
    public String toString() {
        return "Person [name=" + name + ", age=" + age + "]";
    }
}

```

``` Java

import java.io.*;

public class SerializationPerson {
    public static void main(String[] args) {
        Person person1 = new Person("Frantisek", 25);

        // Serialization
        try (FileOutputStream fileOut = new FileOutputStream("personSerialized.txt");
            ObjectOutputStream objectOut = new ObjectOutputStream(fileOut)) {
            objectOut.writeObject(person1);
            System.out.println("Serialized");
        } catch (IOException e) {
            e.printStackTrace();
        }

        // Deserialization
        try (FileInputStream fileIn = new FileInputStream("personSerialized.txt");
            ObjectInputStream objectIn = new ObjectInputStream(fileIn)) {
            Person deserializedPerson = (Person) objectIn.readObject();
            System.out.println("Deserialized: " + deserializedPerson);
        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
}

```

``` Text serializovaný objekt

���sr�Person�<X��Bh�I�ageL�namet�Ljava/lang/String;xp���t� Frantisek

```

Příklad:
A. Napište metodu, která bude rekurzivně procházet zadaný adresář
(argument metody) a vypisovat název každého vnitřního souboru a
informaci, jestli je to adresář nebo obyčejný soubor.

``` Python
# Příklad:
# A. Napište metodu, která bude rekurzivně procházet zadaný adresář
# (argument metody) a vypisovat název každého vnitřního souboru a
# informaci, jestli je to adresář nebo obyčejný soubor.

import os

def rekurze(dirList,index,delka):
    if index < delka:
        if os.path.isfile("../"+dirList[index]):
            print("├─F──"+dirList[index])
        else:
            print("├─A──"+dirList[index])
        index += 1
        rekurze(dirList,index,delka)

def prochazeni(adresar):
    print("D:")
    dirList = os.listdir(adresar)
    rekurze(dirList,0,len(dirList))
    
prochazeni("..")

```

B. Napište metodu, ve které budete číst z jednoho souboru (1. argument
metody) text a do druhého souboru (2. argument metody) uložíte
všechna slova kratší než 3. argument metody, každé na samostatný řádek.

``` Python

# Příklad:
# B. Napište metodu, ve které budete číst z jednoho souboru (1. argument
# metody) text a do druhého souboru (2. argument metody) uložíte
# všechna slova kratší než 3. argument metody, každé na samostatný řádek.

def metoda(souborcteni,souborzapis,delka):
    dlouhaSlova = ""
    with open(souborcteni, "r") as f:
        obsah_souboru = f.read()
        slova = obsah_souboru.split()
    for slovo in slova:
        if len(slovo) < delka:
            dlouhaSlova += slovo + "\n"
    f = open(souborzapis, "w+")
    f.write(dlouhaSlova)
    f.close()
    
metoda("soubor.txt","souborZapis.txt",4)

```