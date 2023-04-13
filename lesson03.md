# Урок 3. Булева алгебра. Конструкції, що керують потоком.

## Булеві змінні

Змінна типу 'bool' може містити тільки два значення: **True** або **False**, при чому це не рядки, не числа, а саме поняття істинності та хибності. 

Назва "Булеві величини" походять від винахідника математичної логіки ("Булевої алгебри") - британського математика ХІХ століття - Джорджа Буля.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6c/George_Boole.jpg/267px-George_Boole.jpg)

## Булева алгебра (логічні оператори)

Існують наступні логічні оператори:

* and - та 
* or - або
* xor - або, що виключається (підключається окремо)
* not - НЕ not означає НЕ, і, бувши поставленим перед типом bool, змінює його значення на зворотне, тобто **'not True'** стає **'False'**, **'not False'** стає **'True'** Далі приведена таблиця, що демонструє роботу операторів :

| Оператори  | 0 to 0| 0 to 1| 1 to 0 | 1 to 1|
|------------|:-----:|:-----:|:------:|:-----:|
| and        |   0   |   0   |    0   |   1   |
| or         |   0   |   1   |    1   |   1   |
| xor        |   0   |   1   |    1   |   0   |


## Умовний оператор if (оператор розгалуження)

В python до версії 3.10 існував тільки один умовний операторʼ `if -> elif -> else`. Починаючи з версії мови 3.10 був доданий оператор порівняння шаблонів `match/case`, який також можна використовувати схожим чином, але він не є предметом розгляду даного уроку. Якщо вам цікаво, як це працює, в кінці уроку є посилання на відповідну статтю. 

Приклад оператору розгалуження `if`:

```python
print ("Give it to me!")
number = int(input())

if (number >= 100):
    print ("Thanks, man!")
elif ((number > 10) and (number < 100)):
    print ("OK :(")
else:
    print ("WHAAAAT????")

if (number > 1000):
    print ("!!!!WOOOOWWWW!!!")

```

Зверніть увагу, ми вперше стикаємося з блоком операторів. Так само працюють і цикли, і функції, і класи зі своїми методами. Блок операторів починається зі свого оператора (наприклад, зараз це блок оператора if), після оператора йде двокрапка, потім усі дії, які програміст хоче виконати в рамках цього блоку. Всі дії потрібно писати з додатковим відступом у чотири пробіли (так, саме чотири пробіли, а не одну табуляцію - це важливо). Якщо відступа не буде, python буде сприймати це як код поза блоком.

Є можливість використовувати оператор if в декількох варіантах. Нижче наведено список усіх варіантів:
#'Неповне розгалуження'
* if (умова) дія
* if (умова) (блок дій у кілька рядків)
#'Повне розгалуження'
* if (умова) (блок дій у декілька рядків) else дія
* if (умова) (блок дій у кілька рядків) else (блок дій у кілька рядків)
#'Багатогілкове розгалуження'
* if (умова) (блок дій у кілька рядків) elif (умова) (блок дій у декілька рядків) else дію
* if (умова) (блок дій у кілька рядків) elif (умова) (блок дій у декілька рядків) else (блок дій у декілька рядків)

**Між if та else може бути скільки завгодно elif.**

**Між if і else може бути скільки завгодно elif.**

Слід мати на увазі той факт, що надмірне використання операторів розгалуження у програмах відчутно уповільнюють швидкість їх виконання. Тому, при побудові дерева розгалужень слід ретельно перевірити їх логіку і за можливості скоротити, наприклад пішовши від противного. Також існує метод застосування ключів словників (хеш-таблиць) для виклику відповідних дій, але подібні приклади ми будемо розглядати під час вивчення відповідного типу даних та їх застосування.

## Оператори порівняння та пріоритети операцій

На відміну від мови С, в Python оператори порівняння мають однаковий пріоритет.
Результатом порівняння є відповідь типу `bool` -  `True` або `False`.
Python пропонує використовувати ланцюги операторів порівняння, тобто класичне для програмування подвійне порівняння може бути замінено ланцюгом:


```python
>>> x = 5
>>> y = 10
>>> z = 15

>>> (x < y) and (y <= z)
True

>>> x < y <= z
True
```

До операторів порівняння відносяться наступні:

```
"<"      - менше 
">"      - більше
"=="     - дорівнює
">="     - більше або дорівнює
"<="     - менше або дорівнює
"!="     - не дорівнює
"not"    - не є чимось
"is"     - є тим самим
"is not" - не є тим самим
"in"     - є частиною чогось
"not in" - не є частиною чогось

```

Останні чотири оператори потребують додаткового пояснення.

Оператор `is` перевіряє, чи є обидва операнди одним і тим самим об'єктом у пам'яті, тоді як просте порівняння на рівність `==` перевіряє тільки на відповідність вмісту двох операндів, але не перевіряє, чи є вони тим самим об'єктом.


```python
>>> l1 = [1, 2, 3]
>>> l2 = [1, 2, 3]
>>> l1 == l2
True
>>> l1 is l2
False
>>> l1 is not l2
True
```

Оператор `in` перевіряє, чи операнд зліва є частиною операнда справа:

```python
>>> l1 = [1, 2, 3]
>>> 3 in l1
True
>>> 4 in l1
False
>>> 5 not in l1
True
```

## Альтернативний синтаксис if, заміна тернарному оператору

У багатьох мовах програмування (С++, Java, PHP...) існує тернарний оператор, тобто спеціальний оператор умов, який повертає один із двох результатів, залежно від того, виконується його умова чи ні.  Виглядає він так:

```php
print ($input == 1) ? "One!" : "Not One!";
```

Тернарні оператори часто застосовуються, коли варіантів дій всього два і кожен вимагає виконання лише однієї команди, бо такий запис коротше аналогічного з if. Однак, на жаль, можна зустріти зв'язок if-ів й тернарних операторів, який є важким для розуміння. Інакше кажучи, надмірне застосування цієї конструкції може стати причиною погіршення розуміння коду.

У python немає окремого тернарного оператора, але, починаючи з версії мови 3.6 є можливість його імітувати за допомогою `if`:

```python
test = True
result = 'Test is True' if test else 'Test is False'
# result = 'Test is True'
```

Це можна використовувати з будь-якими функціями. Як-от із друком:

```python
test = True
print ('ttt' if test else 'fff') # виведе ttt
```
Слід зазначити, що подібна синтаксична конструкція зазвичай використовується лише при повному розгалуженні, й блок команд після else є обов'язковим. Тому, у випадку застосування подібного оператора для неповного розгалуження, в одній з гілок варто використовувати команду-заглушку `pass`.

```python
test = True
result = 'Test is True' if test else pass
# result = 'Test is True'
```

## Особливості порівняння об'єктів

У мові Python все є об'єктом. Коли ми говоримо про число, рядки, функції, класи, список і т.д. - ми говоримо про об'єкти.
Python вважає, що якщо об'єкт не пустий, він `True`, а не `False`. `False` - це власне сам `False`, 0 і пустий рядок. Таким чином, якщо нам необхідно порівняти рядок з пустим рядком, або число з нулем, а також дізнатися, чи є пустим той, чи інший об’єкт, замість того, щоб написати умови в стилі старих мов:


```python
if s !='':
    pass

if bool('value'):
    pass
    
if 8 % 2 != 0:
    pass
```
Часто, використання надмірної кількості таких порівнянь призводить до уповільнення виконання вашого коду. Але у таких випадках ми очікуємо лише один результат - 'True' або 'False'. Тому нема жодного сенсу робити повне порівняння, якщо ми можемо передати змінну напряму і умовний оператор сам визначить значення змінної:

```python
if s:
    pass
    
if 8 % 2:
    pass
```

Це значно скорочує і спрощує код.

## Ще одна альтернатива тернарному оператору

Застосування `and` до кількох виразів не просто повертає `True` або `False`. Воно повертає перший `False` вираз, або останній з виразів, якщо всі вони `True`.

Аналогічно, операція `or` повертає перше істинне значення, або останнє, якщо жодне з них не True.

Використовуючи цю особливість python, тернарний оператор можна реалізувати ще більш оригінальним способом:

```python
test = True
result = test and 'Test is True' or 'Test is False'
```

В нашому випадку test = `True`, `and` його пропускає і повертає нам останнє істинне значення, з яким працював, тобто вираз «Test is True' or 'Test is False». Or повертає перший зустрічний True вираз, йому більше нічого не цікаво. Якщо замінити рядки наближеним змістом і використати псевдокод, отримаємо:

```python
result = true1 and true2 or true3
result = true2 or true3
result = true2
```

Що стосується пріоритету операцій, `not` пріоритетніше `and`, `and` пріоритетніше `or`. Тобто спочатку виконується `not`, потом `and`, потом `or`. Пріоритети всіх операцій шукайте в посиланнях.



## Практика

1. Перевірити, чи є введене число парним.
2. Перевірити, чи є число не парним, ділиться чи на три і на п'ять одночасно, але так, щоб не ділитися на 10.
3. Ввести число, вивести усі його дільники.
4. Ввести число, вивести його розряди та їх множники.


## Корисні посилання

[Пріоритети операцій в Python](https://docs.python.org/3/reference/expressions.html#operator-precedence)

[Match/case на Хабрі](https://habr.com/ru/post/585216/)

[Чейнінг операторів порівнянь](https://www.geeksforgeeks.org/chaining-comparison-operators-python/)

## Домашнє завдання

**Перший рівень ("if"):**
Набрати всі приклади посимвольно і змусити їх працювати, розібратися у роботі.

**Другий рівень ("if-elif-else"):**
Завершити практики з уроку.
Придумати власні приклади на альтернативні варіанти if і активне використання булевої алгебри.

**Третій рівень ("Містер Буль. Джордж Буль!"):**
Розвʼязати задачу:

Задача fizz-buzz:

Ви маєте три числа, вони вводяться з консолі. Перше число називається fizz, друге називається buzz. До третього необхідно дорахувати від одиниці. Дивлячись на поточне число, якщо воно кратне fizz – треба виводити F замість числа. Якщо число кратне buzz – треба виводити B замість числа. Якщо число кратне і fizz, і buzz, треба виводити FB. Якщо воно не кратне нічому, виводимо число. І так - поки не буде досягнуто третього введеного числа.

Приклад умови та результату:
Введено числа 2, 5, 18
Висновок має бути таким:
1 F 3 F B F 7 F 9 FB 11 F 13 F B F 17 F

Всі свої рішення треба зібрати в папочку з номером уроку, додати до свого локального репозиторію з домашками та залити на github, посилання викладач буде збирати по формі.