---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - ads
---

## Bubble Sort $O(n^2)$

Vizualizace: https://www.algoritmy.net/article/3/Bubble-sort

```JS
var swapped = false;

function bubbleSort(array a)
    for i in 1 -> a.length - 1 do

        swapped = false;

        for j in 1 -> a.length - i - 1 do
            if a[j] < a[j+1]:
                prohoď(a[j], a[j+1]); 
                swapped = true;

        if(!swapped){
            končíme
        }
```

## Insertion sort $O(n^2)$

Vizualizace: https://www.algoritmy.net/article/8/Insertion-sort

``` JS
function insertionSort(array a)
    for i in 0 -> a.length - 2 do
        j = i + 1
        tmp = a[j]
        while j > 0 AND tmp > a[j-1] do //uvolni misto hodnote
            a[j] = a[j-1]
            j--
        a[j] = tmp //vloz hodnotu
```
