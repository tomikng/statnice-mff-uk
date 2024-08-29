---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - ads
---

## Quick Sort

```C#
namespace ConsoleApp1
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int[] array = { 33, 10, 55, 71, 29, 15, 67 };
            Console.WriteLine("Original Array: " + string.Join(", ", array));

            Quicksort(array, 0, array.Length - 1);

            Console.WriteLine("Sorted Array: " + string.Join(", ", array));

            // Original Array: 33, 10, 55, 71, 29, 15, 67
            // Sorted Array: 10, 15, 29, 33, 55, 67, 71
        }

        public static void Quicksort(int[] array, int left, int right)
        {
            if (left < right)
            {
                int boundary = left;
                for (int i = left + 1; i <= right; i++)
                {
                    if (array[i] < array[left])
                    {
                        Swap(array, i, ++boundary);
                    }
                }
                Swap(array, left, boundary);
                Quicksort(array, left, boundary - 1);     // Exclude the pivot element
                Quicksort(array, boundary + 1, right);    // Start sorting after the pivot element
            }
        }

        private static void Swap(int[] array, int left, int right)
        {
            int tmp = array[right];
            array[right] = array[left];
            array[left] = tmp;
        }
    }
}

```

- **(Best Case)**: $O(n log(n))$ (Když je pivot vždy vybrán tak, že rozdělí pole na dvě přibližně stejně velké části)

- **(Worst Case)**: $O(n^2)$ (Když je pole již seřazeno (buď vzestupně nebo sestupně) a pivot je vždy vybrán jako největší nebo nejmenší prvek)

- **Prostorová složitost**: $O(\log n)$ v průměrném a nejlepším případě, což odpovídá hloubce rekurze.

- **V nejhorším případě** (např. při degeneraci na $O(n)$), může prostorová složitost vzrůst až na $O(n)$ kvůli hloubce rekurze.