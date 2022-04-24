# Dodanie Minutnika do gry

Przed pracą nad taskiem stwórz swojego brancha -> [[Tworzenie Branchy]]

 Licznik ma być  położony w prawym górnym rogu ekranu.

![[Pasted image 20220424232327.png]]

 Dodaj go do Canvases jako Text Mesh Pro.
![[Pasted image 20220424233543.png]]
 Wyrównaj go do prawej górnej krawędzi.
![[Pasted image 20220424234421.png]]
Kliknij zaznaczony element z klawiszem **alt**. Dzięki teu teks sam c przeskoczy w prawy górny róg
![[Pasted image 20220424234342.png]]
Będziesz musiał zmienić rozmiar textu. Przeskaluj go w zakładce **scene** do odpowiedniego rozmiaru
![[Pasted image 20220424234023.png]]


Teraz wystarczy napisać skrypt który będzie zmieniał licznik co sekundę.
Możesz do tego użyć Corutyn
https://docs.unity3d.com/Manual/Coroutines.html

albo w metodzie update dodawać do zmiennej 
`Time.deltaTime`

Pamiętaj by umieścić stworzoną klase w namespace Czolgi
![[Pasted image 20220425000504.png]]

