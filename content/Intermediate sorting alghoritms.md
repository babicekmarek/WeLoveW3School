Quick sort: Dva způsoby, první principiální a druhý programátorsky komplexně logicky.
Důležitý je zmínit, že si vybereme pivota, ten se většinou vybírá mediánem tří, ale můžeme si zvolit poslední číslo.
Maximální možnost pokusů je n = n$^2$. Po prvním průběhu máme správně zařazený první pivot a pole rozdělené na větší a menší.
- Tady je to vysvětlený, že se určí pivot a následně se rozděluje na větší a menší půlky, vysvětluje to Skot: https://youtu.be/XE4VP_8Y0BU?si=lg1PQfXoBSiEYEwn
- Tady je to vysvětlený s logikou se kterou by se to mělo kódovat: https://youtu.be/WprjBK0p6rw?si=LMTbxbUfiJOdLHup
Zvolil bych ten druhý způsob, protože se u toho blýskneš jako hvězda, ale zmínit oba a asi je fajn oba ukázat.

![](Pasted%20image%2020240514151823.png)

``` Text

(3 -1 0 7 -2 8 1 5) { pivot = 5 }
(3 -1 0 -2 1 )|5| (7 8){ rozdělím na dvě pole }
(3 -1 0 -2 1) { pivot = 1 } a (7 8) { pivot = 8 }
(-1 -2 0 |1| 3) |5| (7 |8|) { rozdělím na další pole }
(-1 -2 |0|) |3| |5| |7| |8| { určím pivot -2 }
(-2 -1) |0| |3| |5| |7| |8| { rozdělím na další pole }
|-1| (-2) |0| |3| |5| |7| |8| { poslední pole }
|-2| |-1| |0| |3| |5| |7| |8| { uspořádané pole }

```

Merge sort: Funguje na principu slévání. Pole se postupně rozdělí a následně se znova spojuje zpátky, při spojování zpátky se porovnávají prvky, menší doleva, větší doprava.
Maximální časová náročnost je n = n log n ve všech případech.

https://youtu.be/5Z9dn2WTg9o?si=ivDXZFdtChlR8EzC

``` Text 

(3 -1 0 7 -2 8 1 5) 
(3 -1 0 7) (-2 8 1 5) { rozděluju na dvě pole }
(3 -1) (0 7) (-2 8) (1 5) { rozděluju na čtyři pole }
(3) (-1) (0) (7) (-2) (8) (1) (5) { rozděluju na 8 polí }
(-1 3) (0 7) (-2 8) (1 5) { slévám na 4 pole }
(-1 0 3 7) (-2 1 5 8) { slévám na 2 pole }
(-2 -1 0 1 3 5 7 8) { slévám dohromady }


```