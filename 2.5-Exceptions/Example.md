# Приклади коду

## 1. try – catch

```java
public class TryCatchExample {
    public static void main(String[] args) {
        String[] inputs = {"25", "abc"};

        for (int i = 0; i <= inputs.length; i++) {
            try {
                int value = Integer.parseInt(inputs[i]);
                System.out.println("Число: " + value);
            } catch (NumberFormatException e) {
                System.out.println("Не число: " + inputs[i]);
            } catch (ArrayIndexOutOfBoundsException e) {
                System.out.println("Немає елемента " + i);
            }
        }
    }
}
```

## 2. try – catch – finally

```java
public class TryCatchFinallyExample {
    static void process(String packet) {
        System.out.println("Сесію відкрито");
        try {
            int size = Integer.parseInt(packet);
            System.out.println("Розмір пакета: " + size);
        } catch (NumberFormatException e) {
            System.out.println("Некоректний пакет");
        } finally {
            System.out.println("Сесію закрито");
        }
    }

    public static void main(String[] args) {
        process("512");
        process("x12");
    }
}
```

## 3. throw

```java
public class ThrowExample {
    static class Sensor {
        private double threshold;

        void setThreshold(double threshold) {
            if (threshold <= 0 || threshold > 100) {
                throw new IllegalArgumentException("Некоректний поріг: " + threshold);
            }
            this.threshold = threshold;
        }
    }

    public static void main(String[] args) {
        Sensor sensor = new Sensor();
        try {
            sensor.setThreshold(150);
        } catch (IllegalArgumentException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

## 4. throws

```java
public class ThrowsExample {
    static class ChannelBusyException extends Exception {
        ChannelBusyException(String message) {
            super(message);
        }
    }

    static boolean[] busy = {false, true};

    static void connect(int channel) throws ChannelBusyException {
        if (busy[channel]) {
            throw new ChannelBusyException("Канал " + channel + " зайнятий");
        }
        System.out.println("Підключено до каналу " + channel);
    }

    public static void main(String[] args) {
        try {
            connect(0);
            connect(1);
        } catch (ChannelBusyException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

