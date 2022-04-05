# Unity Kamera
Jest urządzeniem, kótre przechwytuje obraz i wyświetla go na użytwkownikowi. Unity daję możliwoś tworzenia wiele kamer które moża wykorzystać np. jako lustra w grze. Czy też dodawaś przeróżne efekty do nich jak rozmycie, zwężenia widzenia, neonowy styl, ... znwane także efektami Post Procesingu.
## Tryb Orthographic
Jest to jeden z rodzaji generowania ebrazu przez kamere, tryb orhographiczny tworzy obraz bez perspektywy przez co jest przydatny przy tworzniu gier 2D.
![[Pasted image 20220405005000.png]]

Mamy tu także do dyspozycji 3 zmienne:
- **Size** - Rozmiar kamery podawany w unity jednostach.Oznacza on wysokość kamery od środka w górę i od środka w dół. np. zdefiniujemy że zmienna *size = 3*, przez do będziemy mieli *3 jednoski od środka do dolnej krawędzi* i *3 jednostki od środka do górnej krawędzi*. ***Wysokość kamery*** jest zawsze stał, nie zależy od rodzelczości. 
![[Pasted image 20220405010306.png]]
  Jedynie co się będzie zmianiać to ***szerokość kamery***, która zależy od rodzelczości ekranu.
  Jeżeli ekran będze miał rozdzielczość *800x480* to docelową szerokośc można obliczyć wzorem:
  $$Szerokość Kamery = \frac{SzerokośćEkranu}{WysokośćEkranu} \cdot Wsyokość Kamery$$
    $$Wsyokość Kamery = 3$$
  $$Szerokość Kamery = \frac{800}{480} \cdot 3 = 5$$

  ![[Pasted image 20220405011435.png]]
  Przy rozdzielczości *2160x1080* kamera szerokość kamery będzie wynosiła:
  $$Szerokość Kamery = \frac{2160}{1080} \cdot 3 = 6$$
  ![[Pasted image 20220405011950.png]]
  > [[Dopasowywanie Kamery|Tutaj]] zobaczysz skrypt dopasowujący kamere do rozdzielczoście ekranu.
  
- **ClipingPlanes Near** - jak obiekt ma być blisko kamery by go renderować.
  domyślnie ta wartość jest mała 0.3 ale jak ją zaczniemy większać to niektóre obiekty mogą ziknąć z pola widzenia kamery. Np. skrzynka widoczna na nagraniu jest oddalona o *10 jednostek unity* przez co gdy wartoś przekroczy liczbę dziesięć to skrzyna zniknie z gry. *Pozycja kamery to (0,0,-10)*, *pozycja skrzynki (0,0,0)*. W grach 2D zmienna near wpływa na obiekty znajdujące się na osi Z.
  ![[bandicam 2022-04-05 01-34-12-316.mp4]]
- **ClipingPlanes Far** - jak daleko ma być obiekt by został on zrenderowany. To jest to samo co ***ClipingPlanes Near*** tylko, że zmiana idze w drugą stronę. Zmienna ***ClipingPlanes Far*** nie może  być mniejsza od zmiennej **ClipingPlanes Near** ![[bandicam 2022-04-05 01-42-19-414.mp4]]