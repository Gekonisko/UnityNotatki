# Unity Prefabs
Prefab to inaczej kopia obiektu w grze, która jest trzymana w plikach gry. Możemy ją później wykorzystać w tworzeniu nowych obiektów podczas rozgrywki np. wrogowie, ulepszenia.
Np. chcesz stworzyć grę w której czołgiem napierdalasz przeciwników, ale też chcesz by przeciwnicy się co chwilę respić. Dzięki prefabą możesz zrobić kopie wrogiego czołgu w plikach gry a następnie przypisać go do skryptu, który stworzy jego obiekty w trakcie rozgrywki.

### Prefaba tworzymy poprzez zwykłe przeciągnięcie obiektu do plików gry

![[bandicam 2022-04-03 16-00-15-242.mp4]]

Po stworzeniu prefaba obiekt w grze powinien wyglądać jak niebieska kostka

---

### Teraz w inspektorze tego obiektu powinniśmy widzieć 3 dodatkowe pola
![[Pasted image 20220403162528.png]]
- **Open** - otwiera edycję prefaba 
- **Select** - pokazuje ci położenie prefaba w plikach gry
- **Overrides** - pozwala na dodanie zmian aktualnego obiektu do prefaba.
  np. Po dodaniu pustego obiektu *"miecz"* moja Hierarchia będzie wyglądała tak:
![[Pasted image 20220403163257.png]]
By dodać obiekt *"miecz"* mogę kliknąć na przycisk Override a następnie wybrać interesujące mnie działanie.
![[Pasted image 20220403163617.png]]

  ##### Mam tu do dyspozycji parę możliwości:
  1. Możemy działać na wszystkich obiektach jednocześnie i wybrać:
	  - **Apply All** - dodaje wszystkie obiekty do prefaba
	   - **Revert All** - usuwa wszystkie obiekty które nie należą do prefaba
  2. Możemy działać na poszczególnych obiektach i je dodawać lub usuwać w zależności od upodobania:
      - **Apply** - dodaje wybrany obiekt do prefaba
      - **Revert** - usuwa wybrany obiekt z prefaba

---

### Sama edycja obiektu w grze nie zmieni prefaba. 
- #### By został on zmieniony musimy wejść w tryb edycji poprzez kliknięcie w ">" obok obiektu.
![[bandicam 2022-04-03 16-19-12-370.jpg]]
- #### Lub zaaplikować zmiany na obiekcie do prefaba poprzez funkcję override.
   ![[Pasted image 20220403164609.png]]

---

## Wykorzystanie Prefabów w Rozgrywce
Mamy już stworzony prefab ***mimika***(Potwór imitujący skrzynie), teraz trzeba go wykorzystać  w kodzie. Do tego stworzę osobny obiekt *"Game Manager"* oraz dodam do niego skrypt *"Mimic Generator"* , który będzie tworzył ***mimiki***.

``` CS
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
public class MimicGenerator : MonoBehaviour
{
    [SerializeField] private GameObject mimic;
    private float timer = 0;
    private float timeToResp = 1; // czas w sekundach
    private Camera cam;
    private float cameraWidth,cameraHeight;

    private void Start()
    {
        cam = Camera.main; // Pobieram główna kamere, można ją także pobrać przez metode FindObjectOfType<Camera>();
        cameraHeight = cam.orthographicSize;
        cameraWidth = Screen.width/Screen.height * cam.orthographicSize;
    }
    private void Update()
    {
        timer += Time.deltaTime;
        if (timer > timeToResp)
        {
            timer = 0;
            Instantiate(mimic, new Vector3(Random.Range(-cameraWidth, cameraWidth),
            Random.Range(-cameraHeight, cameraHeight), 0), Quaternion.identity);
        }
    }
}

```
Tworzę tutaj publiczną zmienną *mimic* typu *GameObject*, która będzie naszym prefabem.
Następnie inicjalizuje zmienną *timer* oraz *TimieToResp*, które będą odpowiadać odstępy czasu w tworzeniu prefabów. Potrzebuję także kamery by dowiedzieć się na jakiej pozycji stworzyć prefaba by kamera wciąż go widziała.

Do tworzenia prefabów służy metoda **Instantiate**, której składnia wygląda tak.
``` CS
Instantiate("Prefab(GameObject)", "Pozycja w jakiej ma się znajdować(Vector 3)", "W jaką stronę ma być obrucony(Quaternion)");
```
Użyłem funkcji random do losowania pozycji mimika, oraz nadałem mu rotację z stałej Quaternion.identyty, która wyrównuje obiekt idealnie ze światem.

> By dowiedzieć się więcej na temat Kamery i tego jak tworze mimiki w polu widzenia kamery należy zaglądnąć [[Unity Kamera|tutaj]];

#### Po przeciągnięciu  prefaba mimika do skryptu rozgrywka będzie wyglądała tak:
![[Pasted image 20220403172402.png]]
![[bandicam 2022-04-03 17-25-14-910.mp4]]

Niektóra mimiki są widoczne w całości przez to, że biorę tylko pod uwagę punkt środkowy obiektu a nie jego cała zdjęcie. Przez co przy tworzeniu takiego mimika na krawędzi ekranu będzie widać tylko jego połowę
![[Pasted image 20220403173058.png]]