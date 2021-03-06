# Structural patterns

### Decorator \(Wrapper\)

Allows behavior to be added to an individual object, dynamically, without affecting the behavior of other objects from the same class. It is a flexible alternative of subclasses creation practice for functionality extension. Object "doesn't" know that it was "decorated", so  this pattern is perfect for expansion of software systems.

The decorator pattern is often useful for adhering to the Single Responsibility Principle, as it allows functionality to be divided between classes with unique areas of concern.

_When should be used:_ 

* objectives and behavior of objects should be added dynamically;
* concrete implementation should be separated from duties and behaviors;
* objects' extension for the creation of subclasses is impractical or impossible;
* specific functions should not be on the upper levels of the object hierarchy;
* some functionality isn't applicable for all objects and can't be removed if necessary;
* a large number of small objects that have similar implementations aren't permissible.

![](../../../.gitbook/assets/image%20%2854%29.png)

**Component** – a class that defines an interface for objects that can be dynamically assigned additional duties, as well as for future decorators;

**ConcreteComponent** – defines an object to which new states and behavior are added;

**Decorator** – contains a reference to the **component** object and inherits its interface implementation by default. 

**ConcreteDecorator** \(ConcreteDecoratorA, ConcreteDecoratorB\) – concrete decorators.

### **Composite** 

призначений для створення деревоподібної структури для подання ієрархії об’єктів, де кожний об’єкт можна розглядати незалежно або як набір вкладених об’єктів через один інтерфейс. Таким чином, з’являється можливість уніфіковано, однаково поводитися з кожним об’єктом.

_When should be used:_ 

*  у наявності є оригінальна структура, що складається з об’єктів та композицій об’єктів;
* необхідно забезпечити ігнорування клієнтом істотних відмінностей між окремим об’єктом та складеним об’єктом;
* необхідно реалізувати уніфіковану обробку всіх об’єктів.

Але також можна розглядати і такі варіанти:

* шаблон «Декоратор», який містить операції типу Додати \(Add\), Видалити \(Remove\) та Знайти \(Find\)
* шаблон «Пристосуванець» для розділення компонентів за умови, що характеристика «місцезнаходження» може бути проігнорована і всі операції будуть починатися з кореневої вершини композиції об’єктів 
* шаблон «Відвідувач» для локалізації операцій, які на даний момент розподілені між класами Composite та Component

![](../../../.gitbook/assets/image%20%28118%29.png)

  
**Component** – компонент, який задає інтерфейс для об’єктів, котрі компонуються. Також він надає відповідну реалізацію операцій за замовчанням, спільну для всіх класів; об’являє єдиний інтерфейс для доступу до нащадків та керування ними; визначає інтерфейс для доступу до батьківського елемента компонента у рекурсивній структурі та при необхідності реалізує його;

**Leaf** –  компонент без реалізації контейнерних функцій. Визначає листові вершини та не має нащадків. Визначає поведінку примітивних об’єктів у композиції; входить до складу контейнерів; 

**Composite** – складений об’єкт. Визначає поведінку контейнерних об’єктів, у яких є нащадки. Зберігає ієрархію компонентів-нащадків; реалізує операцій, які відносяться до інтерфейсу управління нащадками.

### Bridge \(Handle/Body\)

Дозволяє розділяти абстракцію і реалізацію таким чином, щоб вони могли змінюватися незалежно. Шаблон bridge використовує інкапсуляцію, агрегування та успадкування для того, щоб розділити відповідальність між класами.

_When should be used:_ 

*   потрібно уникнути постійної прив'язки абстракції до реалізації / абстракція та реалізація не повинні бути зв’язаними під час компіляції;
* конкретну реалізацію необхідно вибирати під час виконання програми;
* абстракція та реалізація повинні бути незалежно розширюваними новими підкласами. У такому випадку «Міст» дозволяє комбінувати різні абстракції та реалізації та змінювати їх незалежно;
* зміни в реалізації абстракції не повинні позначатися на клієнтах, тобто клієнтський код не повинен перекомпілювати;
* деталі реалізації повинні бути прихованими від клієнта; 
* кількість класів швидко зростає, що є ознакою того, що ієрархію потрібно розділити на 2 частини.

![](../../../.gitbook/assets/image%20%28114%29.png)

**Abstraction** визначає інтерфейс абстракції і агрегує \(зберігає посилання\) на об'єкт типу Implementor;

**Refined Abstraction** \(опціонально\) - це більш специфічний підклас основної абстракції, який розширює інтерфейс, визначений нею;

**Implementor** визначає інтерфейс для класів реалізації. Він не зобов'язаний точно відповідати інтерфейсу класу Abstraction, більше того обидва інтерфейси можуть бути абсолютно різні. Зазвичай інтерфейс класу Implementor надає тільки примітивні операції, а клас Abstraction визначає операції більш високого рівня, що базуються на цих примітивах; 

**ConcreteImplementor** - один з конкретних \(платформо-залежних\) виконавців.

### Proxy

забезпечує створення заступника об’єкта для контролю доступу до останнього через перехоплення всіх викликів.

Надає об’єкт-заступник \(surrogate\) або об’єкт-замінник \(placeholder\).

Обгортаючи доступ до реального компонента, «Заступник»зменшує складність роботи з ним.

_When should be used:_ 

*  створення об’єкту є “дорогою” операцією – можна створювати об’єкт тільки при першому зверненні до нього;
* потрібно контролювати доступ до об’єкту: для різних об’єктів можна встановлювати різні рівні доступу;
* потрібно організувати віддалений функціонал – заступник надає  локального представника замість цільового об’єкта, що знаходиться в іншому адресному просторі; 
* потрібно виконувати додаткові дії при доступі до об'єкта – «розумне посилання».

Види шаблону:

* **віртуальний заступник**: управляє створенням одного об’єкта через інший тоді, коли цей об’єкт реально потрібний \(доцільно у випадках, якщо процес створення досить повільний або може бути визнаним непотрібним\). Має назву ще **lazy loading, on-demand loading, just-in-time loading.** Може кешувати частину інформації про реальний Суб’єкт, щоб відкласти його створення;
* **заступник для аутентифікації \(заступник-захисник\)**: перевіряє правильність умов доступу до об’єкту;
* **віддалений заступник**: забезпечує зв’язок з Суб’єктом, який знаходиться у іншому адресному просторі \(домені застосунку, процесі чи комп’ютері\); кодує/декодує повідомлення, які надсилаються мережею;
* **розумний заступник:** додає щось до запиту перед його надсиланням до мережі або змінює запит; 
* **кешуючий заступник**: забезпечує тимчасове зберігання результатів розрахунків до надсилання їх клієнтам, які можуть розділити ці результати.

![](../../../.gitbook/assets/image%20%28146%29.png)

**Proxy :**

* зберігає посилання, яке дозволяє йому звертатися до реального суб'єкту, використовуючи інтерфейс класу Subject;
* надає інтерфейс, ідентичний інтерфейсу Subject, тому заступник завжди може бути підставлений замість реального суб'єкта;
* контролює доступ до реального суб'єкту і може відповідати за його створення і видалення;
* виконує інші обов'язки, які залежать від виду заступника \(remote proxies, virtual proxies, protection proxies etc.\);

**Subject** – визначає спільний для **RealSubject** і **Proxy** інтерфейс, так що клас **Proxy** можна використовувати скрізь, де очікується **RealSubject;** 

**RealSubject** – визначає реальний об'єкт, який подається за допомогою заступника.

### Fasade

структурує об’єкти, надаючи до них всіх доступ через єдиний шлюз. Надає єдиний, уніфікований інтерфейс до всієї підсистеми замість набору окремих та багаточисельних інтерфейсів. Фактично, “Фасад” визначає інтерфейс більш високого рівня, який спрощує використання системи.

_When should be used:_ 

*  є необхідність у наданні простого інтерфейсу доступу до складної системи;
* між клієнтами та класами реалізації абстракції існує багато залежностей і треба зменшити їхню кількість; 
* є необхідність розкласти підсистему на окремі шари, створити різні рівні доступу до підсистеми,  розшарувати її.

![](../../../.gitbook/assets/image%20%2878%29.png)

**Facade** – фасад:

* проінформований про те, яким складовим системи потрібно переадресовувати запит;
* делегує запити клієнтів відповідним об’єктам всередині підсистеми;

**Класи підсистеми**:

* реалізують функціональність підсистеми;
* виконують дії, які потребує «Фасад» і які, в свою чергу, «Фасад» отримав від одного з клієнтів;
* нічого не “знають” про існування самого «Фасаду» \(не зберігають посилань на нього\); 
* реалізація компонентів підсистеми закрита та не видна зовнішнім компонентам.

### **Adapter** 

призначений для організації використання функцій об'єкта, недоступного для модифікації, через спеціально створений інтерфейс.

«Адаптер» забезпечує спільну роботу класів з несумісними інтерфейсами шляхом створення спільного об’єкта, через який вони можуть взаємодіяти.

«Адаптер» – шаблон, що уніфікує класи та об’єкти.

_When should be used:_ 

*  існуючий клас підтримує необхідні дані і поведінку, але має інтерфейс, який не відповідає певним вимогам \(наприклад, при використанні існуючої бібліотеки, до класів якої немає доступу\);
* необхідно створити повторно використовуваний клас, який повинен взаємодіяти із зазделегідь невідомими або непов’язаними з ним класами, які мають несумісні інтерфейси; 
* необхідно об’єднати інтерфейси декількох класів, причому в наявності можуть бути тільки об’єкти-підкласи кожного з цих класів, а не примірники цих класів.

![](../../../.gitbook/assets/image%20%28169%29.png)

**Target** - цільовий інтерфейс. Визначає інтерфейс, який залежить від предметної області і яким користується **Client**;

**Client** - взаємодіє з об'єктами, що задовольняють інтерфейсу **Target**;

**Adaptee** - адаптований інтерфейс. Визначає існуючий інтерфейс класу \(бібліотеки\), який потребує адаптації; 

**Adapter** - клас, що адаптує інтерфейс **Adaptee** до інтерфейсу **Target.**

### Flyweight

структурує об'єкти таким чином, що з них створюється лише обмежений набір екземплярів замість великої множини об’єктів. Полегшує повторне використання багатьох малих об’єктів, роблячи використання великої кількості об’єктів більш ефективною.

_When should be used:_ 

*   у додатку використовується велика кількість подібних об'єктів, при цьому накладні витрати на їх зберігання є високими \(може не вистачити пам’яті для їх одночасного розміщення в режимі runtime\);
* більшу частину станів об'єктів можна винести назовні \(у зону відповідальності клієнтів, які створюють і використовують ці об'єкти\);
* багато нероздільних \(unshared\) об'єктів можна замінити невеликою кількістю поділюваних \(shared\) об'єктів, оскільки їх стан винесено назовні;
* ідентичність кожного об’єкту не має значення.

![](../../../.gitbook/assets/image%20%28124%29.png)

**Flyweight** визначає інтерфейс, за допомогою якого пристосуванці можуть отримувати зовнішній стан або певним чином на нього впливати;

**ConcreteFlyweight** реалізує інтерфейс **Flyweight** та додає при необхідності внутрішній стан.  Об’єкт класу **ConcreteFlyweight** повинен бути розділюваним \(shared\). Будь-який збережуваний ним стан повинен бути внутрішнім, тобто таким, що не залежить від контексту;

**UnsharedConcreteFlyweight** – нерозділюваний \(unshared\) конкретний пристосуванець. Не всі підкласи **Flyweight** обов’язково повинні бути shared. Інтерфейс **Flyweight** допускає розділення, але не нав’язує його. Часто у об’єктів **UnsharedConcreteFlyweight** на деякому рівні структури пристосуванця є нащадки у вигляді об’єктів класу **ConcreteFlyweight;**

**FlyweightFactory** створює об’єкти-пристосуванці та управляє ними. Забезпечує необхідне розділення пристосуванців. Коли клієнт звертається до пристосуванця, об’єкт **FlyweightFactory** надає існуючий екземпляр або створює новий, якщо готового ще немає;

**Client** зберігає посилання на одного або декількох пристосуванців.  Обчислює або зберігає зовнішній стан пристосуванців.

