# Задача "Исследование JVM через VisualVM"
```
18:19:49.080330400: loading io.vertx
18:19:49.666397900: loaded 529 classes
```
![](/Classes1.png)
Были загружены 529 классов библиотеки io.verx.
![](/Metaspace1.png)
При загрузке классов библиотеки размер используемой и зарезервированной памяти Metaspase увеличились до 15 МБ.
![](/Heap1.png)
При загрузке классов размер используемой памяти в куче увеличился до 36 МБ, зарезервированный размер памяти кучи равен 192 МБ и не изменился при подгрузке классов.

```
18:19:52.675852700: loading io.netty
18:19:54.052062400: loaded 2117 classes
```
![](/Classes2.png)
Были загружены 2117 классов библиотеки io.netty.
![](/Metaspace2.png)
При загрузке классов библиотеки размер используемой и зарезервированной памяти Metaspase увеличились до 20-21 МБ.
![](/Heap2.png)
При загрузке классов размер используемой памяти в куче увеличился до 99 МБ, зарезервированный размер памяти кучи остался равен 192 МБ и не изменился при подгрузке классов.

```
18:19:57.066120100: loading org.springframework
18:19:57.556784300: loaded 869 classes
```
![](/Classes3.png)
Были загружены 869 классов из внешней библиотеки org.springframework.
![](/Metaspace3.png)
При загрузке классов библиотеки размер используемой и зарезервированной памяти Metaspase увеличились до 30-31 МБ.
![](/Heap3.png)
При загрузке классов размер используемой памяти в куче увеличился до 77 МБ (значение ниже того, что было в предыдущем пункте, тк успел отработать сборщик мусора и удалить часть неиспользуемых классов), зарезервированный размер памяти кучи остался равен 192 МБ и не изменился при подгрузке классов.


```
18:20:00.567209: now see heap
18:20:00.567209: creating 5000000 objects
18:20:00.874647: created
```
![](/Classes4.png)
Был загружен 1 базовый класс Object.
![](/Metaspace4.png)
При загрузке класса библиотеки размер используемой и зарезервированной памяти практически не изменился.
![](/Heap4.png)
При создании 5 млн объектов размер используемой памяти в куче увеличился до 186 МБ, зарезервированный размер памяти кучи остался равен 192 МБ и не изменился при подгрузке объектов.

```
18:20:03.879020500: creating 5000000 objects
18:20:04.166891400: created
```
Количество классов и объем памяти Metaspase больше не притерпевают изменений, тк новые классы не передаются, а производится только создание объектов "Object".
![](/Heap5.png)
При создании еще 5 млн объектов размер используемой памяти в куче увеличился до 430,5 МБ, зарезервированный размер памяти кучи был увеличен до 1069 МБ.

```
18:20:07.226420800: creating 5000000 objects
18:20:07.471283100: created
```
![](/Heap6.png)
При создании еще 5 млн объектов размер используемой памяти в куче увеличился до 686,5 МБ, зарезервированный размер памяти кучи не был изменен и остался равен 1069 МБ.

На приведенном ниже скриншоте отображена работа сборщика мусора, который удалял неиспользуемые объекты из кучи.
![](/GC.png)