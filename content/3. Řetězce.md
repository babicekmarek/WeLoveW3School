Řetězce jsou datové typy, slouží k uložení znaků. Řetězce jsou konstantní (nezměnitelné), staticky alokovaným prostorem (omezená maximální délka), dynamicky alokovaným prostorem (omezené pouze velikostí paměti). ASCII tabulka obsahovala historicky 128, později byla rozšířená na 256 znaků, dnes používáme kódování UTF-8, v Asijských zemích UTF-16/UTF-32.

Řetězec je datový typ, který ukládá posloupnost znaků. Řetězec může být konstantní nebo dynamicky alokovaný.

Kódování znaků je způsob prezentování binárně zapsaných znaků v aplikaci či v operačním systému. Existuje velká spousta různých kódování, dnes je nejpoužívanější UTF-8.

Regulérní výrazy jsou speciálně zapsané řetězce, využívají se pro kontrolu, zda nějaký řetězec je v požadovaném tvaru.

Kódování znaků
~~~ Python
# o Napište formulář pro uživatelský vstup emailové adresy studenta a jeho třídy
# o Pomocí regulárních výrazů zkontrolujte
#     o Emailová adresa musí mít koncovku: .cz nebo .edu nebo .com
#     o Před @ smí být jen malá písmena a tečky, tj. například ve tvaru prijmeni.jmeno@gmail.com,
#     o Třídy budou splňovat naše značení (V1A, L3B, I4, …), spojené třídy neuvažujte

import re

def overeni_mail(mail):
    if re.match("^[a-z.]+@[a-z]+\.(cz|com|edu)",mail):
        print("souhlasi")
    else:
        print("nesouhlasi")

mail = input("zadej emailovou adresu: ")
overeni_mail(mail)


def overeni_trida(trida):
    if re.match("^[V|E|I|P|K|S|L|M]+[1-4]+[A-C]*$",trida):
        print("souhlasi")
    else:
        print("nesouhlasi")
        
trida = input("zadej tridu: ")
overeni_trida(trida)
~~~