# Creational patterns

### Prototype



_When should be used:_ 

*  система не повинна залежати від способу створення та реалізації об’єктів, які до неї входять;
* класи, які породжуються, визначаються під час виконання програми, наприклад, за допомогою динамічного завантаження;
* бажано уникнути успадкування створювача об’єкта \(тоді “Прототип” є конкуретном “Абстрактної фабрики”\);
* екземпляри класу можуть знаходитися в одному зі станів, кількість яких є невеликою. Тому може бути зручніше встановити відповідну кількість прототипів та клонувати їх, а не створювати об’єкт кожного разу в потрібному стані; 
* створення об’єкта заново \(new + встановлення значень полів\) є “дорогим”.

![](../../../.gitbook/assets/image%20%28111%29.png)


**Prototype** — визначає інтерфейс для клонування самого себе;

**ConcretePrototype** — реалізує операцію клонування самого себе;

**Client** — створює новий об’єкт, звертаючись до прототипу з запитом клонувати себе, потім, користуючись його інтерфейсом, виконує з отриманим клоном потрібні маніпуляції.

### **Factory method**



Це шаблон рівні класу, а не об’єкта!

Відомий ще під назвою “Віртуальний конструктор \(Virtual Constructor\)”.

Шаблон “Фабричний метод” часто застосовується в інструментальних бібліотеках і каркасах.

_When should be used:_ 

* класу наперед невідомо, об’єкти яких класів йому потрібно створювати, оскільки планується багато різних варіантів функціонування;
* клас спроектовано таким чином, щоб специфікація породжуваного об’єкту визначається тільки в нащадках;
* клас делегує свої обов’язки одному з декількох допоміжних підкласів і планується локалізувати знання про те, який клас приймає ці обов’язки на себе; 
* це дозволяє використовувати у коді програми не специфічні класи, а маніпулювати абстрактними об’єктами на більш високому рівні.

![](../../../.gitbook/assets/image%20%283%29.png)

**Product** — продукт, абстрактний клас; визначає інтерфейс об’єктів, створюваних фабричним методом;

**ConcreteProduct** — конкретний продукт, клас; реалізує інтерфейс Product;

**Creator** — творець; оголошує фабричний метод, що повертає об’єкт типу Product; може викликати реалізацію за замовчанням Фабричного методу, який повертає об’єкт ConcreteProduct; може викликати Фабричний метод для створення об’єкту Product;

**ConcreteCreator** —конкретний творець; заміщує фабричний метод, що повертає об’єкт ConcreteProduct.

### 

Дозволяє змінювати поведінку системи, варіюючи створювані об’єкти, але при цьому залишаючи незмінніми інтерфейси. Надає інтерфейс для створення сімейств взаємнопов’язаних або незалежних об’єктів, не визначаючи при цьому їх конкретних класів.

_When should be used:_ 

*  система не повинна залежати від того, яким чином створюються, компонуються та подаються вхідні об’єкти;
* конкретний варіант бажаної поведінки системи визначають не окремі об’єкти, а ціле сімейство пов’язаних об’єктів. Об’єкти одного сімейства повинні використовуватися разом;
* на вхід системи подається тільки ціле сімейство об’єктів, система конфігурується одним із сімейств;
* виконуються певні умови конфіденційності, коли небажано надавати весь API бібліотеки об’єктів, їх реалізацію. Замість цього надаються тільки їх інтерфейси.

![](../../../.gitbook/assets/image%20%28106%29.png)

**AbstractFactory** – визнчає загальний інтерфейс для операцій створення абстрактних об’єктів – продуктів. Надалі в програмі замість абстрактних будуть створюватися вже конкретні об’єкти певного сімейства;

**ConcreteFactory\[N\]** – визначає, реалізує операції, які створюють всі об’єкти одного конкретного сімейства;

**AbstractProduct\[A-Z\]** – визначає загальний інтерфейс; для типу об’єкта-продукта. A-Z в даному випадку – множина таких продуктів, які складають абстрактне сімейство;

**ConcreteProduct\[A-Z\]\[N\]** - визначає конкретний об’єкт-продукт типу \[A-Z\], створюваний відповідною конкретною фабрикою; 

**Client** – програмний модуль, який віддає команди на отримання конкретного сімейства продуктів, користуючись виключно відомими інтерфейсами класів  AbstractFactory та AbstractProduct.

### **Singleton**



Найбільш поширений спосіб використання шаблона “**Одинак**” - використання його як місця для зберігання та підтримки доступу до глобальних змінних.

_When should be used:_ 

* повинен бути рівно один екземпляр певного класу, легко доступний для всіх клієнтів;
* єдиний екземпляр повинен розширюватися шляхом породження підкласів, і клієнтам потрібно мати можливість працювати з розширеним екземпляром без модифікації свого коду.

Якщо створення та надання глобального доступу до єдиного об’єкту класу, час і способи створення даного об’єкту не є проблемними питаннями, розглядання шаблона “Одинак” не є актуальним.

![](../../../.gitbook/assets/image%20%2822%29.png)

**Singleton** — одинак:  визначає операцію\(статичний метод\) Instance, яка дозволяє клієнтам отримувати доступ до єдиного екземпляру; може нести відповідальність за створення та маніпулювання власним унікальним екземпляром;

клієнти отримують доступ до екземпляру класу Singleton тільки через його операцію Instance \(публічний статичний метод класу\); 

всі конструктори класу мають бути protected або private.

### The Builder



_When should be used:_ 

* клієнт повинен створювати складені об’єкти. При цьому процес створення об’єкта можна розділити на етапи;
* алгоритм створення складного об’єкта не повинен залежати від того, з яких частин  складається об’єкт і яким чином вони між собою з’єднані; 
* процес конструювання повинен забезпечувати створення різних видів подання об’єкта, що конструюється.

![](../../../.gitbook/assets/image%20%2851%29.png)

**Builder** – містить перелік **всіх можливих абстрактних** методів  для створення та поєднання частин різноманітних об’єктів \(продуктів\);

**ConcreteBuilder** – конкретний будівельник, який займається створенням **якогось одного** об’єкту \(продукту\):  онструює та зв’язує разом частини продукту за допомогою реалізації тільки тих абстрактних методів інтерфейсу **Builder**, які потрібні для створення частин цього продукту; визначає внутрішнє подання цього складного об’єкту та надає інтерфейс для отримання останнього;

**Director** – розпорядник: фіксований, єдиний алгоритм створення будь-яких продуктів, для яких є у наявності відповідний **Builder**; конструює продукт, користуючись загальним інтерфейсом **Builder-а**;

**Product** – кінцевий продукт, побудований за допомогою конкретного **Builder-а**: являє собою складний конструйований об’єкт; 

**ConcreteBuilder** будує внутрішнє подання продукта та визначає процес його збирання. Крім цього може включати класи, які визначають складові частини \(у т.ч. інтерфейси\) для збірки кінцевого результату з частин
