---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - ads
---

## Bubble Sort $O(n^2)$

Vizualizace: https://www.algoritmy.net/article/3/Bubble-sort

```C#
 static void BubbleSort(int[] arr)
 {
     bool swapped = false;
     for (int i = 0; i < arr.Length - 1; i++)
     {
         swapped = false;
         for (int j = 0; j < arr.Length - i - 1; j++)
         {
             if (arr[j + 1] < arr[j])
             {
                 int tmp = arr[j + 1];
                 arr[j + 1] = arr[j];
                 arr[j] = tmp;
                 swapped = true;
             }
         }
         if (!swapped)
         {
             break;
         }
     }
 }
```

## Insertion sort $O(n^2)$

Vizualizace: https://www.algoritmy.net/article/8/Insertion-sort

``` C#
  public static void InsertionSort(int[] array)
  {
      for (int i = 0; i < array.Length - 1; i++)
      {
          int j = i + 1;
          int tmp = array[j];
          while (j > 0 && tmp < array[j - 1]) // Změněno na tmp < array[j - 1] pro vzestupné třídění
          {
              array[j] = array[j - 1];
              j--;
          }
          array[j] = tmp;
      }
  }
```
