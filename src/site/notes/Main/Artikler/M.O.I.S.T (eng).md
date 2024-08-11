---
{"dg-publish":true,"permalink":"/main/artikler/m-o-i-s-t-eng/","title":"M.O.I.S.T (eng)","tags":["Principles"],"created":"2024-06-19T08:43:14.420+02:00"}
---


> [!tldr] 
> The **MOIST** principles provide a balanced approach to writing code that prioritizes **clarity**, **maintainability**, and **readability**. While the *DRY* principle focuses on minimizing repetition, **MOIST** acknowledges the practical need for some redundancy to achieve these goals.

> [!summary] 
> **Meaningful**: Ensure that the code has purpose and context, even if it means some repetition to enhance clarity.
> 
>**Organized**: Keep the code well-structured and easy to navigate, which might involve some necessary redundancy.
>
>**Intentional**: Be deliberate with repetitions, understanding when they serve a functional or communicative purpose.
>
>**Simplified**: Advocating for simplicity and clarity in code design and implementation.
>
>**Transparent**: Make the code's intentions clear, even if this means duplicating logic to make it more understandable.
# Meaningful
Ensure that the code serves a clear **purpose** and is provided with **context**, while avoiding unnecessary repetition that could obscure its intent. 
Meaningful code is characterized by well-chosen names for variables, functions, and classes, promoting readability and aiding other developers in understanding its purpose. 

Following Robert Martin's Clean [Code philosophy](https://gist.github.com/wojteklu/73c6914cc446146b8b533c0988cf8d29), emphasis is placed on self-explanatory code, enhancing clarity and purposefulness. By keeping related behavior localized, the code becomes easier to understand without requiring developers to jump across the codebase.
```C#
// Meaningful
// Example of meaningful code with clear purpose and context
public class Rectangle
{
    public double Length { get; }
    public double Width { get; }

    public Rectangle(double length, double width)
    {
        Length = length;
        Width = width;
    }

    public double CalculateArea()
    {
        return Length * Width;
    }
}

```
# Organized
Maintain a **well-structured** codebase that is easy to navigate, minimizing redundancy where possible. 

Organized code follows a logical structure with distinct separations of concerns, reducing the need for duplicated setup or initialization code across different modules. 

Martin Fowler's iterative approach suggests [refining the code's structure over time](https://martinfowler.com/books/refactoring.html), starting with initial organization that may include redundancy, which is then fine-tuned during refactoring. 

By keeping related functions and data close together, the code becomes more understandable and easier to reason about.
```C#
// Organized
// Example of organized code with a clear structure
public class Rectangle
{
    public double Length { get; }
    public double Width { get; }

    public Rectangle(double length, double width)
    {
        Length = length;
        Width = width;
    }

    public double CalculateArea()
    {
        return Length * Width;
    }
}

```
# Intentional
Be deliberate in the use of **repetitions**, understanding when they serve a functional or communicative purpose. 

**Intentional repetition** ensures that redundant code is included for a reason, such as enhancing readability or aiding future maintainers in understanding the code. 

While Clean Code advises against unnecessary repetition, it also emphasizes that readability should not be sacrificed solely to avoid redundancy. Intentional repetition aligns with this nuanced approach, allowing for initial clarity before refactoring to eliminate unnecessary duplications while preserving intent. 

By keeping related logic together, intentional repetition makes behavior more localized and easier to follow.
```C#
// Intentional
// Example of intentional repetition for clarity
public class Greeting
{
    public void Greet(string name)
    {
        Console.WriteLine($"Hello, {name}!");
        Console.WriteLine($"Welcome to our website, {name}!");
    }
}

```
# Simplified
Maintain simplicity in the code structure, *even if it occasionally results in redundant segments* to enhance clarity and ease of maintenance. 

**Simplified code** prioritizes readability by reducing complexity and avoiding unnecessary abstractions. 

Robert Martin advocates for simplicity as a core principle of Clean Code, encouraging straightforward and understandable solutions. 

By minimizing cognitive overhead for developers, simplified code supports maintainability, making it easier to debug, refactor, and extend. Starting with straightforward implementations and refining them over time fosters a better understanding of the system's behavior and facilitates collaboration among developers.
```C#
// Simplified
// Example of simplified code with reduced complexity
public class PrimeChecker
{
    public bool IsPrime(int n)
    {
        if (n <= 1)
            return false;

        for (int i = 2; i <= Math.Sqrt(n); i++)
        {
            if (n % i == 0)
                return false;
        }

        return true;
    }
}

```
# Transparrent
Ensure clarity in the code structure and logic, even if it requires duplicating certain aspects to enhance understandability and ease of maintenance. 

**Transparent code** makes its purpose and behavior explicit, prioritizing understandability for anyone reading it. By reducing cognitive load, transparent code makes it easier to **comprehend**, **debug**, and **modify**. 
Supporting the [principle of locality of behavior](https://htmx.org/essays/locality-of-behaviour/), transparent code keeps related logic together and ensures the purpose of each code segment is evident. 

By aligning with principles such as self-documenting code and expressive programming, transparent codebases are easier to maintain, understand, and extend over time.
```C#
// Transparent
// Example of transparent code with clear logic and purpose
public class PriceCalculator
{
    public double CalculateTotalPrice(double[] prices, int[] quantities)
    {
        double total = 0;
        for (int i = 0; i < prices.Length; i++)
        {
            total += prices[i] * quantities[i];
        }
        return total;
    }
}

```

### Conclusion

Following the **MOIST principles** provides a balanced approach to writing code that prioritizes **clarity**, **maintainability**, and **readability**. While acknowledging the need for some redundancy, **MOIST** ensures that clarity and intentionality are maintained throughout the codebase. By adhering to **MOIST** principles, developers can create code that is both clear and maintainable, promoting collaboration and reducing the risk of errors.

| Source                                                                                | Description                                           |
| ------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| [Clean code gist](https://gist.github.com/wojteklu/73c6914cc446146b8b533c0988cf8d29)  | A resumé of the clean code principles                 |
| [martin Flowers book on refactoring](https://martinfowler.com/books/refactoring.html) | A wonderful book by Martin Flower                     |
| [Locality of Behaviour](https://htmx.org/essays/locality-of-behaviour/)               | A description of the principle: Locality of Behaviour |
| [KISS](https://www.interaction-design.org/literature/topics/keep-it-simple-stupid)    | A description about the acronym KISS                  |
| [YAGNI](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it)                     | A wiki description about the acronynm YAGNI           |


