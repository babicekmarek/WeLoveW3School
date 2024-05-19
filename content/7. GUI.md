 grafické prvky ✅
 layouty ✅
 událostmi řízené programování ✅

GUI = Graphic User Interface, přidává programům vizuální a estetickou funkci, díky GUI nepotřebujeme znalosti programátora, bez kterých dokážeme ovládat aplikaci pomocí grafického designu. 

Na rozdíl od webových aplikací, které jsou od základu vytvářeny pomocí značkovacího jazyka, který se má zobrazovat uživateli, programovací jazyky potřebují nějaké rozšíření, které umožní grafické rozhraní (Java, JavaFX, SceneBuilder, InteliJStudio).

Grafické prvky slouží k uživatelské interakci s programem, díky nim je programátor schopný vytvořit asynchronní aplikaci. Mezi grafické prvky patří tlačítka, textová pole, vstupní pole, Labely, posuvníky, check boxy, select boxy. Každý programátor má možnost stylovat grafické prvky, jsou předdefinované, ale lze je jednoduše změnit.

Layout
Absolutní pozice layout: předem definované pozice v px, nezohledňuje se žádný responzivní design, všechny velikosti jsou předem nastavené.
Relativní pozice layout: velikost a pozice se udává v %, zohledňuje se postavení vůči ostatním prvků aplikace, můžeme počítat s možností zvětši/zmenšit aplikaci, na tohle bude reagovat design. Dneska se převážně používají výlučně relativní pozice a zohledňuje se rozlišnost velikostí a poměru stran monitorů.

Událostmi řízené programování
Aplikace a program čeká na akci ze strany uživatele, tato akce vyvolá daný proces. Aplikace reagují na stisknutí tlačítek, najetí myší, a podobně.

``` Python

# Příklad: Napište v GUI formulář pro zadání textu a čísla a výstupu do labelu.
# • Do labelu vypíšete text, který vznikne zřetězením vstupního textu za sebe
# tolikrát, kolik bylo zadané číslo. Jako oddělovač použijte *
# • Odevzdejte jen soubor .fxml a .java (controller)

import tkinter as tk

def generate_text():
    input_text = text_entry.get()
    input_number = number_entry.get()
    text = ""
    for i in range(int(input_number)):
        text = text + input_text + "*"
        i -= 1
    output_label.config(text=text[0:-1])
    
root = tk.Tk()

text_entry = tk.Entry(root)
number_entry = tk.Entry(root)
generate_button = tk.Button(root, text="Generovat", command=generate_text)
output_label = tk.Label(root, text="")



#tohle je pomyslný FXML soubor
text_entry.grid(row=0, column=0)
number_entry.grid(row=1, column=0)
generate_button.grid(row=2, column=0, columnspan=2)
output_label.grid(row=3, column=0, columnspan=2)



root.mainloop()

```