# Dodanie Power Up-ów

Przed pracą nad taskiem stwórz swojego brancha -> [[Tworzenie Branchy]]

#### Power Upy:
1. zwiększanie życia 
2. zwiększanie szybkości

zdjęcia do obu ulepszeń znajdują się w katalogu **Sprite**
![[Pasted image 20220424235748.png]]

Stwórz 2 nowe prefaby Speed oraz Life.
![[Pasted image 20220425000048.png]]

Będziemy musieli w czasie gry pobierać utworzone prefaby i je tworzyć w kodzie za pomocą metody Instantiate.
Niestety Unity może jedynie pobierać pliki gry z folderu Resource.
By pobrać te prefaby utworzyłem w folderze Resource 2 ScriptableObjecty które będą wskazywać na power-upy 
> Więcej o ScriptableObjectach -> https://docs.unity3d.com/Manual/class-ScriptableObject.html

Teraz trzeba wejść na każdego z ScriptableObjecty i wybrać odpowiadającemu mu prefaba
![[Pasted image 20220425001659.png]]

Teraz możesz pobrać utworzonego power-upa za pomocą polecenia
```CS
Resources.Load<Typ Obiektu>("ścieżka do scriptable obiektu");
```
W przypadku gdy będziemy chcieli pobrać power-upa speed należy użyć
```CS
Resources.Load<GameObject>("Czolgi/Speed");
```
Każdy prefab jest typem GameObject

> Więcej o Resource -> https://docs.unity3d.com/ScriptReference/Resources.Load.html

Następnie implementujemy to w skrypcie

![[Pasted image 20220425002012.png]]

