Řídící struktury:

Řídící struktury jsou základní prvky v algoritmizaci. Jde o posloupnost příkazů a větvení kódu a cyklení kódu. Posloupnost příkazů jsou příkazy, které se vykonávají jeden za druhým. 

Větvení programu: program se liší podle reakce na otázku ano či ne.
Vícenásobné větvení: případ, kdy se program liší na více možností.

Logické operátory:
AND logický součin 
OR logický součet
NOT negace

pomocí logických operátorů jsme schopní spojovat podmínky.

druhy cyklů a jejich využití:

for - předem musí být znám počet opakování cyklu, průchod polí
while - předem není znám počet opakování, když chceme provádět činnost než se splní nějaká podmínka
do-while - předem není znám počet opakování, když chceme, aby se cyklus udál alespoň jednou

Příklad:
~~~ Python
# · Naprogramujte cyklus, ve kterém bude uživatel zadávat celá čísla, dokud nezadá nulu
# · Program vám pak vypíše počet sudých a počet lichých čísel, které uživatel zadal  

#prvni verze, hodne jednoducha AI verze
L, S = [], []
while (v := int(input("zadej vstup: "))) != 0:
    (S if v % 2 == 0 else L).append(v)
print("licha:", L, "suda:", S)

#druha verze, jednoducha, nerozsiritelna
L = []
S = []
v = int(input("type input: "))
while v != 0:
    if v != 0:
        if v%2 == 0: S.append(v)
        else: L.append(v)
    v = int(input("zadej vstup: "))
print("licha:",L,"suda:",S)
  
#treti verze, tahle mi prijde nejvic spravna
seznam_licha = []
seznam_suda = []
def cyklus(licha, suda):
    vstup = int(input("zadej cislo: "))
    if vstup != 0:
        if vstup%2 == 0: suda.append(vstup)
        else: licha.append(vstup)
    return vstup

while cyklus(seznam_licha, seznam_suda) != 0:
    print("aktualizovane seznamy: licha:",seznam_licha,"suda:",seznam_suda)
print("licha:",seznam_licha,"\n"+"suda:",seznam_suda)
~~~