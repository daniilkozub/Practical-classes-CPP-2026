# Згадаймо: обробка винятків

## Ієрархія

```
Throwable
├── Error                  — збої JVM, не обробляємо
└── Exception              — checked
    ├── IOException ...
    └── RuntimeException   — unchecked
        ├── NullPointerException
        ├── ArithmeticException
        ├── ArrayIndexOutOfBoundsException
        └── IllegalArgumentException
            └── NumberFormatException
```

## Checked vs unchecked

| Checked | Unchecked |
|---|---|
| `extends Exception` | `extends RuntimeException` |
| Компілятор **вимагає** обробити або оголосити | Компілятор не перевіряє |
| Зовнішня, передбачувана ситуація | Помилка в коді |

## try – catch – finally

```java
try {
    // небезпечний код
} catch (NumberFormatException e) {   // спочатку конкретний тип
    // обробка
} catch (RuntimeException e) {        // потім загальний
    // обробка
} finally {
    // виконується ЗАВЖДИ
}
```

## throw і throws

```java
void setAge(int age) {
    if (age < 0) throw new IllegalArgumentException("age < 0");  // викидаємо
}

void load(String path) throws IOException { ... }               // оголошуємо
```

## Власний виняток

```java
class AccessDeniedException extends Exception {
    AccessDeniedException(String message, Throwable cause) {
        super(message, cause);        // cause — першопричина
    }
}
```

## Питання

1. Чим checked відрізняється від unchecked?
2. Що буде, якщо `catch (Exception e)` поставити першим?
3. Коли виконується `finally`?
4. `throw` чи `throws` — що де пишемо?
5. Від якого класу наслідуємося для checked-винятку? А для unchecked?

