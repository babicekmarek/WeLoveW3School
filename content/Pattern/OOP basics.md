 třída ✅, objekt ✅
 statické a instanční proměnné ✅
 statické a instanční metody ✅

Třída: Je konkrétní forma, ze které lze vytvořit objekt. Třída reprezentuje skupinu objektů, které nesou kvalitativně stejné vlastnosti. Všechny objekty třídy Person mají vlastnost name. Konkrétní použití třídy se nazývá objekt / instance. Jakmile třídu použijeme, tak ji nazýváme objekt. 

Objekt / Instance třídy: Je konkrétní instance nějaké třídy, když třída je bábovka, tak objekt je její konkrétní otisk. Odpovídá struktuře třídy a může používat metody třídy. Pro konkrétní objekt nabývají vlastnosti deklarované třídou konkrétních hodnot.

Statické proměnné a statické metody: To jsou takové proměnné a metody, ke kterým lze přistupovat, a které lze volat odkudkoliv z kódu. Nejsou vázány na třídu. 

Instanční proměnné a instanční metody: To jsou takové proměnné a metody, ke kterým lze přistupovat, a které lze volat pouze v rámci dané třídy, potažmo daného konkrétního objektu, jehož vlastnosti v sobě nesou. S těmito metodami lze pracovat pouze v rámci třídy, resp, s jehož daty takové metody typicky pracují.



``` Java

// Příklad:
// Napište třídu Student, která bude mít vlastnosti a metody:
// • každý student má jméno a příjmení a seznam svojí klasifikace (jen
// hodnoty známek)
// • navrhněte vhodnou statickou proměnnou pro počet studentů
// • metodu pro přidání nové klasifikace
// • metodu pro výpočet průměru z klasifikace
// • metodu pro vypsání počtu studentů (instancí)

import java.util.ArrayList;

class Student {
    String jmeno;
    String prijmeni;
    ArrayList<Integer> znamky = new ArrayList<Integer>();
    float prumer;
    static int pocetStudentu = 0;

    public Student(String jmeno, String prijmeni) {
        this.jmeno = jmeno;
        this.prijmeni = prijmeni;
        pocetStudentu++;
    }

    public boolean pridejZnamku(int znamka){
        this.znamky.add(znamka);
        return false;
    }

    public float vypocitejPrumer(){
        for (int i = 0; i < znamky.size(); i++){
            this.prumer += znamky.get(i);
        }
        this.prumer = prumer / znamky.size();
        return 0f;
    }

    public static String vypisPocetStudentu(){
        return "Pocet studentu je: " + pocetStudentu;
    }

    @Override
    public String toString() {
        return "Student [jmeno=" + jmeno + ", prijmeni=" + prijmeni + ", znamky=" + znamky + ", prumer=" + prumer + "]";
    }

    public static void main(String[] args) {
        Student studenJenda = new Student("Maturant", "Babicek");
        studenJenda.pridejZnamku(1);
        studenJenda.pridejZnamku(1);
        studenJenda.pridejZnamku(1);
        studenJenda.pridejZnamku(1);
        studenJenda.pridejZnamku(1);
        studenJenda.vypocitejPrumer();
        System.out.println(studenJenda);
        Student prosimJedna = new Student("Marek", "Babicek");
        System.out.println(prosimJedna);

        System.out.println(vypisPocetStudentu());
    }
}

```