
 metody pro vyhledávání v nesetříděném poli
 rekurzivní metody pro vyhledávání v setříděném poli

Vyhledávací algoritmy se snaží najít nějaký prvek v poli (pokud je pole setříděné, je vyhledávání jednoduší).

Metoda vyhledávání v nesetříděném poli:
lineární sekvenční vyhledávání: jediný způsob jak vyhledávat v nesetříděné datové struktuře, procházíme jeden prvek po prvku a zjišťujeme jestli to není právě ten, který hledáme. Časová náročnost a složitost je n=n.

Metody pro vyhledávání v setříděném poli: 
- Binární vyhledávání: pole rozdělujeme od prostředka, postupně se přibližujeme konci, kde najdeme hledaný prvek, nebo tam nebude.
- Binární vyhledávací strom: binární vyhledávání, ale přiřazujeme uzly.
- B-strom: binární vyhledávání s uzly, ale v každém uzlu může být více hodnot.
- Hashovací tabulka: 


``` Java
// Příklad:
// Napište statickou metodu, která vám v nesetříděném poli studentů (instance
// třídy Clovek s vlastnostmi jméno a příjmení) najde prvního člověka s daným
// jménem a příjmením a vrátí jeho pořadí.

class Clovek {
    private String jmeno;
    private String prijmeni;

    public Clovek(String jmeno, String prijmeni) {
        this.jmeno = jmeno;
        this.prijmeni = prijmeni;
    }

    private String getJmeno(){
        return this.jmeno;
    }

    private String getPrijmeni(){
        return this.prijmeni;
    }

    public static int najdiStudenta(Clovek[] pole, String jmeno, String prijmeni){
        for (int i = 0; i < pole.length; i++) {
            if (pole[i].getJmeno().equals(jmeno) && pole[i].getPrijmeni().equals(prijmeni)){
                return i;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        Clovek[] lide = new Clovek[3];
        lide[0] = new Clovek("Antonin", "Zirac");
        lide[1] = new Clovek("Beata", "Yranova");
        lide[2] = new Clovek("Cyril", "Xaver");

        System.out.println("Student ma index: " + najdiStudenta(lide, "Cyril", "Xaver"));
        
    }
}

```