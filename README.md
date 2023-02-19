# Streams-en-Java
Descripción de Streams en Java y casos de uso prácticos para uso didáctico.

Stream en Java
En Java, un Stream es una secuencia de elementos que se procesan de manera funcional. Los elementos pueden ser de diferentes tipos como objetos, primitivas, arrays y más. Los Streams se utilizan para realizar operaciones en colecciones, como filtrar elementos, mapearlos, reducirlos y más.

¿Cómo funcionan los Streams en Java?
Los Streams en Java funcionan a través de una serie de pasos que se aplican a los elementos de una colección. Estos pasos se realizan de forma secuencial y cada uno puede producir un nuevo Stream o un resultado final. Los pasos comunes en una operación de Stream son los siguientes:

Creación de un Stream: se crea un Stream a partir de una colección como una lista, un array, un set, entre otros.
Filtrado: se eliminan los elementos que no cumplen una condición definida.
Transformación: se realiza una operación sobre cada elemento del Stream, como cambiar su tipo o calcular una propiedad.
Reducción: se combinan los elementos del Stream en un solo resultado, como sumarlos o concatenarlos.
Los Streams en Java son inmutables, lo que significa que no se puede modificar la colección original y se debe crear un nuevo Stream para cada operación.

Métodos de Stream en Java
A continuación, se presentan algunos de los métodos más comunes que se pueden usar en un Stream en Java:
```
1. filter(Predicate<T>)
Este método se utiliza para filtrar los elementos de un Stream basándose en una condición 
definida en un objeto Predicate. Devuelve un Stream con los elementos que cumplen la condición.

2. map(Function<T, R>)
Este método se utiliza para transformar los elementos de un Stream mediante una operación 
definida en un objeto Function. Devuelve un Stream con los elementos transformados.

3. flatMap(Function<T, Stream<R>>)
Este método se utiliza para transformar los elementos de un Stream en otro 
Stream mediante una operación definida en un objeto Function. 
Devuelve un Stream plano (sin anidamiento) con los elementos transformados.

4. sorted()
Este método se utiliza para ordenar los elementos de un Stream en orden natural.

5. distinct()
Este método se utiliza para eliminar los elementos duplicados de un Stream.

6. limit(long n)
Este método se utiliza para limitar el número de elementos de un Stream a un número máximo definido.

7. skip(long n)
Este método se utiliza para saltar los primeros n elementos de un Stream.

8. forEach(Consumer<T>)
Este método se utiliza para realizar una operación en cada elemento de un Stream.

9. reduce(BinaryOperator<T>)
Este método se utiliza para combinar los elementos de un Stream en un 
solo resultado mediante una operación definida en un objeto BinaryOperator.

10. collect(Collector<T, A, R>)
Este método se utiliza para coleccionar los elementos de un Stream en 
una colección específica definida en un objeto Collector.

11. anyMatch(Predicate<T>)
Este método se utiliza para verificar si algún elemento de un Stream 
cumple con una condición definida en un objeto Predicate.

12. allMatch(Predicate<T>)
Este método se utiliza para verificar si todos los elementos de un Stream 
cumplen con una condición definida en un objeto Predicate.

13. noneMatch(Predicate<T>)
Este método se utiliza para verificar si ninguno de los elementos de un 
Stream cumple con una condición definida en un objeto Predicate.

14. findFirst()
Este método se utiliza para obtener el primer elemento de un Stream, si existe.

15. findAny()
Este método se utiliza para obtener cualquier elemento de un Stream, si existe.

16. count()
Este método se utiliza para contar el número de elementos en un Stream.

17. min(Comparator<T>)
Este método se utiliza para obtener el elemento mínimo de un Stream 
basado en un orden definido en un objeto Comparator.

18. max(Comparator<T>)
Este método se utiliza para obtener el elemento máximo de un Stream 
basado en un orden definido en un objeto Comparator.

19. toArray()
Este método se utiliza para convertir un Stream en un array.
```

## Ejemplos de uso de Stream en HashMap
Supongamos que tenemos un HashMap<String, Integer> que representa el 
número de ventas que ha tenido cada producto en una tienda en línea. 
Aquí te van algunos ejemplos de uso de Stream para procesar este HashMap:

1. Calcular la suma de todas las ventas:

```
int totalSales = salesMap.values().stream().mapToInt(Integer::intValue).sum();

```

2. Encontrar el producto con más ventas:
```
Optional<String> bestSeller = salesMap.entrySet().stream()
        .max(Map.Entry.comparingByValue())
        .map(Map.Entry::getKey);

```
3. Filtrar los productos con menos de 10 ventas:
```
Map<String, Integer> topSellers = salesMap.entrySet().stream()
        .filter(entry -> entry.getValue() >= 10)
        .collect(Collectors.toMap(Map.Entry::getKey, Map.Entry::getValue));

```
4. Encontrar los productos que tienen "phone" en su nombre:
```
List<String> phoneProducts = salesMap.keySet().stream()
        .filter(name -> name.contains("phone"))
        .collect(Collectors.toList());

```
5. Calcular el promedio de ventas de todos los productos:
```
OptionalDouble averageSales = salesMap.values().stream()
        .mapToInt(Integer::intValue)
        .average();
```
6. Convertir el HashMap en una lista de objetos "Product":
```
List<Product> products = salesMap.entrySet().stream()
        .map(entry -> new Product(entry.getKey(), entry.getValue()))
        .collect(Collectors.toList());

```

## Ejemplso de uso de Stream en ArraList
Supongamos que tenemos un ArrayList<Integer> que representa el puntaje que obtuvieron los estudiantes en un examen. Aquí te van algunos ejemplos de uso de Stream para procesar este ArrayList:

1. Calcular la suma de todos los puntajes:
```
int totalScore = scores.stream().mapToInt(Integer::intValue).sum();

```
2. Encontrar el puntaje más alto:
```
OptionalInt highestScore = scores.stream().mapToInt(Integer::intValue).max();

```
3. Filtrar los puntajes mayores a 70:
```
List<Integer> passingScores = scores.stream()
        .filter(score -> score > 70)
        .collect(Collectors.toList());

```
4. Encontrar el promedio de puntajes:
```
OptionalDouble averageScore = scores.stream().mapToInt(Integer::intValue).average();

```

5. Contar la cantidad de estudiantes que obtuvieron más de 80 puntos:
```
long count = scores.stream().filter(score -> score > 80).count();

```
