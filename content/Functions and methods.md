 argumenty a návratová hodnota funkce 
 přetížené metody: funkce se stejným názvem a jiným počtem/typem argumentů
 rekurze funkce: volá samu samotnou

funkce a metody: Funkce jsou takřka samostatné části kódu. Vždy jsou určen pro vykonávání nějaké jedné činnosti, řeší jeden určitý problém. Proměnné, které jsou funkci předány jako argument můžeme ve funkci používat jinak ne, pokud ve funkci vytvoříme proměnnou, můžeme s ní pracovat pouze v rámci funkce. Pokud chceme pracovat s proměnnou i v funkci i mimo, tak musíme vytvořit globální proměnnou.

Argumenty jsou nepovinnou součástí funkce. Prostřednictvím argumentů předáváme funkci nějaké hodnoty, které jsou v ní následně zpracovatelné pod názvem argumentu. Někdy musí být součástí argumentu taky datový typ argumentu. 

Funkce vrací hodnotu pomocí return.

Přetěžování metod je způsob, kdy je definována metoda se stejným názvem, ale s jiným počtem nebo typem argumentů.

Rekurze je způsob programování, při němž funkce volá sama sebe, avšak obvykle s jinými hodnotami parametrů.



``` Java

class Petka {
    private static int mocnina(int number, int exponent) {
        int result = 1;
        if (exponent == 0){
            return result;
        }
        else if (exponent > 0){
            for (int i = 0; i < exponent; i++) {
                result *= number;
            }
            return result;
        }
        else {
            exponent = -exponent;
            for (int i = 0; i < exponent; i++) {
                result *= number;
            }
            System.out.println("1/"+result);
            return 0;
        }
    }

    private static float mocnina(float number, float exponent) {
        if (exponent == 0) {
            return 1;
        } 
        else if (exponent > 0) {
            return number * mocnina(number, exponent - 1);
        } 
        else {
            return 1 / mocnina(number, -exponent);
        }
    }

    public static void main(String[] args) {
        System.out.println(mocnina(2, -4));
        System.out.println(mocnina(2f, -4f));
    }
}

```