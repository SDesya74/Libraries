## **BowLib**
BowLib - библиотека, упрощающая создание собственного лука
***
### **Использование метода Bow**
#### **Инициализация**
Для начала работы импортируйте библиотеку.
```js
IMPORT("Bow");
```

#### **Создание предмета**
```js
IDRegistry.genItemID("cbow");
Item.createItem("cbow", "Custom Bow", { name: "Cbow", meta: 0 }, { stack: 1 });

Item.describeItem(ItemID.cbow, {
  toolRender: true, // Рендерить как инструмент
  maxDamage: 385, // Максимальная прочность
  useAnimation: 4 // Анимация использования - 4:лук
});
```

#### **Создание нового лука**
```js
var CustomBow = new Bow();
```

#### **Добавление описания**
```js
CustomBow.set({
  id: ItemID.cbow,
  texture: "Cbow",
  bullets: [262],
  skin: "entity/arrow.png",
  speed: 2,
  damage: 1.5,
  variations: 3,
})
```
Создает новый лук с параметрами prototype
### Методы Bow
|     Метод      | Описание                            |
| :------------: | :---------------------------------- |
|     get()      | Возвращает объект лука              |
|    shoot()     | Принудительный выстрел              |
| set(prototype) | Создает описание для работы с луком |

Объект описания prototype
```js
{
 // идентификатор предмета с которым будет работать библиотека
 id: ItemID.test,
 // текстура которая будет использоваться для того чтобы анимировать лук
 texture: "test",
 // массив с идентификаторами предметов которые будут использованы в качестве боеприпаса
 bullets: [262],
 //путь к папке с текстурой для для изменения текстуры стрелы
 skin: "entity/arrow.png",
 // скорость с которой будет лететь стрела
 speed: 2,
 //урон который будет нанесен сущности
 damage: 1.5,
 //сколько кадров анимации будет у лука. от 0 до n. Сменяются каждые 5 тиков при использовани.
 variations: 3
}
```

### Список коллбеков
|       Callback       |  Возвращаемые значения   | Возвращает                                                    |
| :------------------: | :----------------------: | ------------------------------------------------------------- |
| BowArrowEntityDamage | atacker, victim, damage  | Атакующего; существо в которое попала стрела; нанесенный урон |
|     BowArrowHit      | projectile, item, target | Кидаемый предмет; предмет; цель в которую попала стрела       |
|      BowOnShot       |           bow            | Прототип лука в момент выстрела                               |
|    BowStateChange    |           bow            | Прототип лука когда меняется состояние лука                   |


















### **Использование Метода Bows**
Использование методов которые скрыты
#### **Инициализация**
Для начала работы импортируйте библиотеку.
```js
IMPORT("Bows");
```

#### **Создание предмета**
```js
IDRegistry.genItemID("cbow");
Item.createItem("cbow", "Custom Bow", { name: "Cbow", meta: 0 }, { stack: 1 });

Item.describeItem(ItemID.cbow, {
  toolRender: true,
  maxDamage: 385,
  useAnimation: 4
});
```

#### **Создание нового лука**
```js
var CustomBow = new Bow();
```

#### **Добавление описания**
```js
CustomBow.set({
  id: ItemID.cbow,
  texture: "Cbow",
  bullets: [262],
  skin: "entity/arrow.png",
  speed: 2,
  damage: 1.5,
  variations: 3,
})
```
Создает новый лук с параметрами prototype
### Объект Bows
|                   Метод                   | Описание                                                                             |
| :---------------------------------------: | :----------------------------------------------------------------------------------- |
|                    aim                    | Отдает картинку прицела кодированную в base64                                        |
|                  ingame                   | Отдает значение true/false, Проверка того что игрок в игре                           |
|                currentBow                 | Отдает объект описания текущего лука                                                 |
|                 aimShown                  | Отдает значение true/false когда показывается прицел                                 |
|                  bowInfo                  | Отдает список из BowId: info{}                                                       |
|               dynamicProps                | Отдает объекты bullets[] и hurt[]                                                    |
|                 windowAim                 | Отдает окно PopupWindow с прицелом                                                   |
|           addNewBow(prototype)            | Создает новый лук с прототипом prototype                                             |
|           setShoot(BowId, bool)           | Включает/Выключает луку с BowId режим стрельбы                                       |
|              getShoot(BowId)              | Отдает режим стрельбы: true/false или null                                           |
|             addBullet(bInfo)              |                                                                                      |
|              addHurt(hInfo)               |                                                                                      |
|                  addUI()                  | Устанавливает окно PopupWindow с прицелом в windowAim                                |
|              getCurrentBow()              | Отдает текущий лук в руке или null                                                   |
|           setCurrentBow(BowId)            | Устанавливает текущий лук BowId если он есть в bowInfo и возвращает currentBow       |
| addBulletFilter(projectile, item, target) | Добавляет в фильтр стрел - projectile, item, target                                  |
|              addCallbacks()               | Устанавливает колбеки: смены анимации, изменения интерфейса, начала разрушения блока |
|            getBullet(bullets)             | Отдает id предмета используемого как боеприпас или null                              |
|                  shoot()                  | Принудительный выстрел из текущего лука                                              |
|              animateShoot()               | Принудительная смена анимации                                                        |
|                updateAim()                | Принудительное обновление состояния прицела                                          |