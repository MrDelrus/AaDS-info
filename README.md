# Информация про ревью 

Алгоритм сдачи задач.

1) Создаете приватный репозиторий на GitHub и добавляете меня (MrDelrus) в коллабораторы (Settings -> Collaborators). 
   
2) В файле README.md пишите свою фамилию, имя и номер группы.
   
3) Для каждой задачи создаете отдельную ветку (создавать новые ветки нужно из ветки main) с названием вида “NX”, где N - номер контеста, X - номер задачи. Например: "1B".
   
4) Внутри ветки создаете файл с названием вида “NX.cpp” (в обозначениях выше).
   
5) Создаете Merge Request (с соответствующим названием) в main и добавляете меня во вкладку Reviewers. В комментарии к MR прикрепляете ссылку на соответствующую посылку (в качестве подтверждения, что ваш код работает). При этом такая посылка может быть отправлена после дедлайна (например, если вам пришлось исправлять замечания к задаче, или вы переписали код на более красивый уже после завершения контеста). Одобрять этот MR и, тем более, сливать с веткой main самостоятельно не надо!
    
6) Если вы видите комментарии с замечаниями внутри MR, то следует их исправить и переотправить решение на ревью.
    
7) Если MR одобрен, то вы все сделали правильно!

С любыми вопросами (в частности, по советам ниже) можно писать мне в Telegram (@vozmuvseros).

**Важно:** все задачи должны быть написаны на языке С++ с соблюдением кодстайла!

Основные советы по кодстайлу: 

1. Не пишите ```using namespace std;```. Вместо этого, если вы часто используете какой-то контейнер/пр., можно написать, например, ```using std::vector```. Также не стоит придумывать свои названия уже имеющимся типам (в частности, в задачах на ревью не следует писать ```using ll = long long;```).

2. Не пишите ```#include <bits/stdc++.h>```, вместо этого лучше отдельно прописать include для каждого контейнера/пр. 

3. По названиям переменных должно быть понятно, за что они отвечают. Исключение: если вы пишите цикл ```for (int i = 0; i < ...```, то в таком случае однобуквенное название допускается. Также однобуквенные названия допускаются, если эти переменные описаны в задаче (таким образом, для них не нужно придумывать новые названия). Названия констант лучше начинать с символа `k`, а затем уже само название (например, ```kModule```). Не сокращайте названия переменных, это ухудшает читабельность (например, не следует писать ```cur``` вместо ```current```). 

4. Всегда ставьте фигурные скобочки, если пишите ```if```, ```else```, ```for``` или ```while```.

5. Для названий классов и переменных вы можете выбрать любой стиль (например, ```PascalCase``` или ```snake_case```), однако в рамках задачи придерживаетесь ровно одного из них. Если название состоит из нескольких слов, то стоит как-либо их разделить (например, ```QuickSelect``` вместо ```Quickselect``` или ```quick_select``` вместо ```quickselect```).

6. Ваш код должен быть написан в одном стиле. Ставьте пробелы между операторами и операндами (например, ```a + b``` вместо ```a+b```). Ставьте пробелы перед круглыми и фигурными скобочками, когда пишите ```if```, ```else``` и т.д., не переносите ```else``` на новую строку. Например, ваш код может выглядеть так
```
if ( ... ) {
  ...
} else {
  ...
}
```

7. Строчки не должны иметь слишком большую длину (например, после 100 символов можете переносить часть кода на следующую строку).

8. Не дублируйте код! Вместо этого, попробуйте вынести повторяющиеся куски в отдельную функцию.

9. Разделяйте решение между классами, функциями и main. Например, если вы пишите сортировку, то стоит в ```main``` считать данные, вызвать написанную функцию ```sort(...)``` и вывести данные назад. В основном для ввода/вывода данных лучше использовать функцию ```main```, для алгоритмов/вспомогательных действий - функции, а для структур данных - классы/структуры. При этом структуры обычно заводят для маленьких объектов, которые являются вспомогательными для чего-то другого (например, структура ```Point``` или ```Segment``` в геометрии), а классы в остальных случаях (например, ```Stack```, ```Queue``` и т.д.).

10. Функции не должны быть слишком большими (иначе, скорее всего, их стоит разделить на несколько функций). В частности поэтому не стоит писать все решение в ```main```, постарайтесь разделить его между разными функциями. Также не стоит писать следующее:

```
int main() {
  solve();
}
```

Это никак не решает проблему декомпозиции задачи.

11. Используйте полученные на курсе С++ знания. Например, не следует делать все переменные внутри класса публичными - скорее всего вы хотите не этого. Полезно сразу писать класс так, чтобы вы могли его переиспользовать в другой задаче без существенных изменений. Не делайте копирований больших объектов (например, контейнеры стоит передавать в функции по ссылке). При передаче в функцию используйте константную ссылку, если это можно сделать (иногда это помогает найти ошибку, если ваш код не работает). Однако передавать мелкие объекты (например, ```int``` или ```long long```) по ссылке не следует.

12. Не используйте глобальные переменные (исключение: какие-то параметры из задачи, которые логично сделать общими, например ```const long long kModule = 998'244'353;```), а также магические заклинания по типу ```const_cast``` и пр. без особой причины. Если вы не знаете, что лучше использовать для приведения типов, то вероятнее всего вам нужен именно ```static_cast``` (в частности, ```static_cast``` лучше C-style каста).

13. Избавляйтесь от повторяющихся магических чисел и констант. Вместо этого, лучше завести соответствующие переменные и использовать их (например, ```const int kModule = 998'244'353```). Если у вас есть несколько состояний, которые вы хотите кодировать цифрами, то лучше завести соответствующий ```enum```.

14. Используйте вашу память рационально. На каждый ```new``` должен найтись свой ```delete```. Если вы пишите свой контейнер, часто лучше сделать ```new``` в конструкторе, а ```delete``` в деструкторе. Кроме того, не следует выделять большое количество память на куче без необходимости для этого (например, если в задаче есть ограничение на размер входного массива, следует завести вектор, а не выделять массив размера N, поскольку на вход могут приходить и маленькие массивы).

15. Если вы хотите перенести строку, скорее всего вам нужно ```'\n'``` вместо ```std::endl``` (см. https://stackoverflow.com/questions/213907/stdendl-vs-n).

16. Реализацию больших методов класса стоит делать вне него (желательно после функции main). Пример хорошего кода:

```
class Stack {
  private:
    ...
  public:
    Stack(...);
    void push(...);
    ...
};

int main() {
  ...
}

Stack::Stack(...) : ... {
  ...
}

void Stack::push(...) {
  ...
}
```

17. Если вы передаете в конструктор класса значения, которые хотите присвоить полям вашего класса, скорее всего вам нужны списки инициализиции.

18. Если при написании собственного класса вы любите писать ```new``` и ```delete``` вместо использования векторов/других стандартных контейнеров, то не забывайте про правило трёх.
