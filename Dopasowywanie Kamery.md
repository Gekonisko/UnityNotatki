# Dopasowywanie Kamery
Tworzymy skryp CameraAdjustment a następnie przypisujemy go do Głównej kamery, a następnie czamy, aż magia zrobi swoje
![[Pasted image 20220405135404.png]]
``` CS
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class CameraAdjustment : MonoBehaviour
{
    private Camera _cam;
    Resolution res;

    private void Start()
    {
        _cam = GetComponent<Camera>();
        res = Screen.currentResolution;

        var (center, size) = CalculateOrtoSize();
        _cam.transform.position = center;
        _cam.orthographicSize = size;
    }

    private void Update()
    {
        if (res.width != Screen.width || res.height != Screen.height)
        {

            var (center, size) = CalculateOrtoSize();
            _cam.transform.position = center;
            _cam.orthographicSize = size;

            res = Screen.currentResolution;
        }
    }

    private (Vector3 center, float size) CalculateOrtoSize()
    {
        var bounds = new Bounds();
        foreach (var col in FindObjectsOfType<Collider2D>()) bounds.Encapsulate(col.bounds);
        bounds.Expand(1);

        var vertical = bounds.size.y;
        var horizontal = bounds.size.x * Screen.safeArea.height / Screen.safeArea.width;

        var size = Mathf.Max(horizontal, vertical) * 0.5f;
        var center = bounds.center + Vector3.back;

        return (center, size);
    }
}
```
