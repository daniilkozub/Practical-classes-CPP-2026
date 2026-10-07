# Приклади коду

## 1. ArrayList

```java
import java.util.ArrayList;
import java.util.List;

public class ArrayListExample {
    public static void main(String[] args) {
        List<String> callSigns = new ArrayList<>();

        callSigns.add("Сокіл");
        callSigns.add("Беркут");
        callSigns.add("Яструб");
        callSigns.add(1, "Орел");

        System.out.println(callSigns);
        System.out.println("Розмір: " + callSigns.size());
        System.out.println("Перший: " + callSigns.get(0));
        System.out.println("Є Беркут? " + callSigns.contains("Беркут"));
        System.out.println("Індекс Яструб: " + callSigns.indexOf("Яструб"));

        callSigns.set(0, "Сапсан");
        callSigns.remove("Орел");
        callSigns.remove(0);

        System.out.println(callSigns);
    }
}
```

## 2. LinkedList

```java
import java.util.LinkedList;

public class LinkedListExample {
    public static void main(String[] args) {
        LinkedList<String> messages = new LinkedList<>();

        messages.addLast("Звіт 1");
        messages.addLast("Звіт 2");
        messages.addFirst("ТЕРМІНОВО");

        System.out.println(messages);
        System.out.println("Перше: " + messages.getFirst());
        System.out.println("Останнє: " + messages.getLast());

        String processed = messages.removeFirst();
        System.out.println("Оброблено: " + processed);
        System.out.println(messages);
    }
}
```

## 3. Перебір колекції та Iterator

```java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

public class IterationExample {
    public static void main(String[] args) {
        List<Integer> scores = new ArrayList<>();
        scores.add(85);
        scores.add(40);
        scores.add(92);
        scores.add(55);

        for (int i = 0; i < scores.size(); i++) {
            System.out.println(i + ": " + scores.get(i));
        }

        int sum = 0;
        for (int s : scores) {
            sum += s;
        }
        System.out.println("Сума: " + sum);

        Iterator<Integer> it = scores.iterator();
        while (it.hasNext()) {
            if (it.next() < 60) {
                it.remove();
            }
        }
        System.out.println("Після видалення: " + scores);
    }
}
```

## 4. HashSet, LinkedHashSet, TreeSet

```java
import java.util.HashSet;
import java.util.LinkedHashSet;
import java.util.Set;
import java.util.TreeSet;

public class SetExample {
    public static void main(String[] args) {
        String[] ips = {"10.0.0.5", "10.0.0.1", "10.0.0.5", "10.0.0.9", "10.0.0.1"};

        Set<String> hashSet = new HashSet<>();
        Set<String> linkedSet = new LinkedHashSet<>();
        Set<String> treeSet = new TreeSet<>();

        for (String ip : ips) {
            hashSet.add(ip);
            linkedSet.add(ip);
            treeSet.add(ip);
        }

        System.out.println("HashSet:       " + hashSet);
        System.out.println("LinkedHashSet: " + linkedSet);
        System.out.println("TreeSet:       " + treeSet);

        boolean added = hashSet.add("10.0.0.5");
        System.out.println("Додано повторно? " + added);

        Set<Integer> a = new TreeSet<>();
        Set<Integer> b = new TreeSet<>();
        for (int i = 1; i <= 5; i++) a.add(i);
        for (int i = 4; i <= 8; i++) b.add(i);

        Set<Integer> union = new TreeSet<>(a);
        union.addAll(b);
        Set<Integer> intersection = new TreeSet<>(a);
        intersection.retainAll(b);
        Set<Integer> difference = new TreeSet<>(a);
        difference.removeAll(b);

        System.out.println("Об'єднання: " + union);
        System.out.println("Перетин:    " + intersection);
        System.out.println("Різниця:    " + difference);
    }
}
```

## 5. HashMap

```java
import java.util.HashMap;
import java.util.Map;

public class HashMapExample {
    public static void main(String[] args) {
        Map<String, String> phoneBook = new HashMap<>();

        phoneBook.put("Черговий", "101");
        phoneBook.put("Штаб", "102");
        phoneBook.put("Медпункт", "103");
        phoneBook.put("Штаб", "202");

        System.out.println(phoneBook.get("Штаб"));
        System.out.println(phoneBook.get("Склад"));
        System.out.println(phoneBook.getOrDefault("Склад", "немає"));
        System.out.println(phoneBook.containsKey("Медпункт"));

        phoneBook.remove("Медпункт");

        for (Map.Entry<String, String> entry : phoneBook.entrySet()) {
            System.out.println(entry.getKey() + " -> " + entry.getValue());
        }

        String[] words = {"ціль", "база", "ціль", "ціль", "база", "маршрут"};
        Map<String, Integer> counts = new HashMap<>();
        for (String w : words) {
            counts.put(w, counts.getOrDefault(w, 0) + 1);
        }
        System.out.println(counts);
    }
}
```

## 6. HashMap, LinkedHashMap, TreeMap

```java
import java.util.HashMap;
import java.util.LinkedHashMap;
import java.util.Map;
import java.util.TreeMap;

public class MapOrderExample {
    public static void main(String[] args) {
        Map<String, Integer> hashMap = new HashMap<>();
        Map<String, Integer> linkedMap = new LinkedHashMap<>();
        TreeMap<String, Integer> treeMap = new TreeMap<>();

        String[] names = {"Петренко", "Андрієнко", "Коваль", "Бондар"};
        int[] scores = {78, 95, 64, 88};

        for (int i = 0; i < names.length; i++) {
            hashMap.put(names[i], scores[i]);
            linkedMap.put(names[i], scores[i]);
            treeMap.put(names[i], scores[i]);
        }

        System.out.println("HashMap:       " + hashMap);
        System.out.println("LinkedHashMap: " + linkedMap);
        System.out.println("TreeMap:       " + treeMap);
        System.out.println("Перший ключ:   " + treeMap.firstKey());
        System.out.println("Ключі:         " + treeMap.keySet());
        System.out.println("Значення:      " + treeMap.values());
    }
}
```

## 7. Черга і стек (ArrayDeque)

```java
import java.util.ArrayDeque;
import java.util.Deque;
import java.util.Queue;

public class DequeExample {
    public static void main(String[] args) {
        Queue<String> queue = new ArrayDeque<>();
        queue.offer("Запит 1");
        queue.offer("Запит 2");
        queue.offer("Запит 3");

        System.out.println("Наступний: " + queue.peek());
        while (!queue.isEmpty()) {
            System.out.println("Обробка: " + queue.poll());
        }

        Deque<String> stack = new ArrayDeque<>();
        stack.push("Крок 1");
        stack.push("Крок 2");
        stack.push("Крок 3");

        System.out.println("Вершина: " + stack.peek());
        while (!stack.isEmpty()) {
            System.out.println("Скасовано: " + stack.pop());
        }
    }
}
```

## 8. PriorityQueue

```java
import java.util.PriorityQueue;

public class PriorityQueueExample {
    public static void main(String[] args) {
        PriorityQueue<Integer> distances = new PriorityQueue<>();
        distances.offer(450);
        distances.offer(120);
        distances.offer(800);
        distances.offer(300);

        while (!distances.isEmpty()) {
            System.out.println(distances.poll());
        }
    }
}
```

## 9. equals() і hashCode() у HashSet

```java
import java.util.HashSet;
import java.util.Objects;
import java.util.Set;

public class EqualsHashCodeExample {
    static class Point {
        private final int x;
        private final int y;

        Point(int x, int y) {
            this.x = x;
            this.y = y;
        }

        @Override
        public boolean equals(Object o) {
            if (this == o) return true;
            if (!(o instanceof Point)) return false;
            Point p = (Point) o;
            return x == p.x && y == p.y;
        }

        @Override
        public int hashCode() {
            return Objects.hash(x, y);
        }

        @Override
        public String toString() {
            return "(" + x + ", " + y + ")";
        }
    }

    public static void main(String[] args) {
        Set<Point> points = new HashSet<>();
        points.add(new Point(1, 2));
        points.add(new Point(1, 2));
        points.add(new Point(3, 4));

        System.out.println(points.size());
        System.out.println(points.contains(new Point(3, 4)));
    }
}
```

## 10. Comparable, Comparator, Collections

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

public class SortingExample {
    static class Cadet implements Comparable<Cadet> {
        private final String name;
        private final double average;

        Cadet(String name, double average) {
            this.name = name;
            this.average = average;
        }

        public String getName() { return name; }
        public double getAverage() { return average; }

        @Override
        public int compareTo(Cadet other) {
            return this.name.compareTo(other.name);
        }

        @Override
        public String toString() {
            return name + " " + average;
        }
    }

    static class ByAverageDesc implements Comparator<Cadet> {
        @Override
        public int compare(Cadet a, Cadet b) {
            return Double.compare(b.getAverage(), a.getAverage());
        }
    }

    public static void main(String[] args) {
        List<Cadet> group = new ArrayList<>();
        group.add(new Cadet("Мельник", 4.2));
        group.add(new Cadet("Іваненко", 4.8));
        group.add(new Cadet("Литвин", 3.9));

        Collections.sort(group);
        System.out.println("За прізвищем: " + group);

        group.sort(new ByAverageDesc());
        System.out.println("За балом: " + group);

        List<Integer> nums = new ArrayList<>();
        Collections.addAll(nums, 7, 3, 9, 3, 1);
        System.out.println("max = " + Collections.max(nums));
        System.out.println("min = " + Collections.min(nums));
        System.out.println("3 зустрічається: " + Collections.frequency(nums, 3));
        Collections.reverse(nums);
        System.out.println("reverse: " + nums);
    }
}
```

## 11. enum

```java
import java.util.EnumMap;
import java.util.Map;

public class EnumExample {
    enum Rank {
        PRIVATE("Солдат", 1),
        SERGEANT("Сержант", 2),
        LIEUTENANT("Лейтенант", 3),
        CAPTAIN("Капітан", 4);

        private final String title;
        private final int level;

        Rank(String title, int level) {
            this.title = title;
            this.level = level;
        }

        public String getTitle() { return title; }
        public int getLevel() { return level; }

        public boolean isOfficer() {
            return level >= 3;
        }
    }

    public static void main(String[] args) {
        for (Rank r : Rank.values()) {
            System.out.println(r.ordinal() + " " + r.name() + " " + r.getTitle() + " офіцер: " + r.isOfficer());
        }

        Rank rank = Rank.valueOf("SERGEANT");
        System.out.println(rank == Rank.SERGEANT);

        switch (rank) {
            case PRIVATE:
                System.out.println("Рядовий склад");
                break;
            case SERGEANT:
                System.out.println("Сержантський склад");
                break;
            default:
                System.out.println("Офіцерський склад");
        }

        Map<Rank, Integer> count = new EnumMap<>(Rank.class);
        count.put(Rank.CAPTAIN, 1);
        count.put(Rank.PRIVATE, 25);
        count.put(Rank.SERGEANT, 4);
        System.out.println(count);
    }
}
```

## 12. Узагальнені класи

```java
public class GenericClassExample {
    static class Box<T> {
        private T value;

        public void set(T value) { this.value = value; }
        public T get() { return value; }
        public boolean isEmpty() { return value == null; }
    }

    static class Pair<K, V> {
        private final K key;
        private final V value;

        Pair(K key, V value) {
            this.key = key;
            this.value = value;
        }

        public K getKey() { return key; }
        public V getValue() { return value; }

        @Override
        public String toString() {
            return key + "=" + value;
        }
    }

    public static void main(String[] args) {
        Box<String> textBox = new Box<>();
        textBox.set("Секретно");
        String text = textBox.get();
        System.out.println(text);

        Box<Integer> numberBox = new Box<>();
        System.out.println(numberBox.isEmpty());

        Pair<String, Integer> p = new Pair<>("Порт", 8080);
        System.out.println(p.getKey() + " " + p.getValue());
        System.out.println(p);
    }
}
```

## 13. Узагальнені методи

```java
import java.util.ArrayList;
import java.util.List;

public class GenericMethodExample {
    static <T> void printAll(List<T> list) {
        for (T item : list) {
            System.out.print(item + " ");
        }
        System.out.println();
    }

    static <T> T getFirst(List<T> list) {
        if (list.isEmpty()) {
            return null;
        }
        return list.get(0);
    }

    static <T extends Comparable<T>> T max(List<T> list) {
        T best = list.get(0);
        for (T item : list) {
            if (item.compareTo(best) > 0) {
                best = item;
            }
        }
        return best;
    }

    static double sum(List<? extends Number> list) {
        double total = 0;
        for (Number n : list) {
            total += n.doubleValue();
        }
        return total;
    }

    public static void main(String[] args) {
        List<String> names = new ArrayList<>();
        names.add("Коваль");
        names.add("Бондар");
        names.add("Шевчук");

        List<Integer> nums = new ArrayList<>();
        nums.add(4);
        nums.add(17);
        nums.add(9);

        printAll(names);
        printAll(nums);
        System.out.println(getFirst(names));
        System.out.println(max(names));
        System.out.println(max(nums));
        System.out.println(sum(nums));
    }
}
```
