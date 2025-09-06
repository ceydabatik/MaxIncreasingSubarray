using System;
using System.Collections.Generic;
using System.Text.Json;

namespace MaxlncreasingSubArray
{
    internal class Program
    {
        public static string MaxIncreasingSubarrayAsJson(List<int> numbers)
        {
            if (numbers == null || numbers.Count == 0)
                return "[]";

            List<int> best = new();   // En iyi alt dizi
            int bestSum = int.MinValue;

            List<int> current = new(); // Şu anki alt dizi
            int currentSum = 0;

            current.Add(numbers[0]);
            currentSum = numbers[0];

            for (int i = 1; i < numbers.Count; i++)
            {
                if (numbers[i] > numbers[i - 1]) // Artış devam ediyor
                {
                    current.Add(numbers[i]);
                    currentSum += numbers[i];
                }
                else
                {
                    if (currentSum > bestSum)
                    {
                        best = new List<int>(current);
                        bestSum = currentSum;
                    }

                    current.Clear();
                    current.Add(numbers[i]);
                    currentSum = numbers[i];
                }
            }

            if (currentSum > bestSum)
            {
                best = new List<int>(current);
            }

            return JsonSerializer.Serialize(best);
        }

        public static void Main()
        {
            Console.WriteLine(MaxIncreasingSubarrayAsJson(new List<int> { 1, 2, 3, 1, 2 }));
            Console.WriteLine(MaxIncreasingSubarrayAsJson(new List<int> { 2, 5, 4, 3, 2, 1 }));
            Console.WriteLine(MaxIncreasingSubarrayAsJson(new List<int> { 1, 2, 2, 3 }));
            Console.WriteLine(MaxIncreasingSubarrayAsJson(new List<int> { 1, 3, 5, 4, 7, 8, 2 }));
            Console.WriteLine(MaxIncreasingSubarrayAsJson(new List<int>()));
        }
    }
}
