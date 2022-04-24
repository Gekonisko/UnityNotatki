# Dodanie Spirali Śmierci

Przed pracą nad taskiem stwórz swojego brancha -> [[Tworzenie Branchy]]

co pewien okres czasu twórz skrzynki po spirali na całej mapie
![[Pasted image 20220425004116.png]]
![[Pasted image 20220425004256.png]]
i tak dalej.

Możesz zrobić to w już istniejącym generatorze. Co 1 sekundę twórz skrzynki. Użyj do tego Corutyn 
> o corutynach -> https://docs.unity3d.com/Manual/Coroutines.html
lub zwiększaj zmienną w metodzie update o wartość `Time.deltaTime`


Pamiętaj by umieścić stworzoną klase w namespace Czolgi
![[Pasted image 20220425000504.png]]