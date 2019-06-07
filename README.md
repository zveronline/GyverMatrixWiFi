![PROJECT_PHOTO](https://github.com/vvip-68/GyverMatrixWiFi/blob/master/proj_img.jpg)

# Адресная матрица на NodeMCU с управлением по WiFi
* [Описание проекта](#chapter-0)
* [Папки проекта](#chapter-1)
* [Схемы подключения](#chapter-2)
* [Материалы и компоненты](#chapter-3)
* [Как скачать и прошить](#chapter-4)
* [FAQ](#chapter-5)
* [Полезная информация](#chapter-6)

<a id="chapter-0"></a>
## Описание проекта
Этот проект основан на проекте AlexGyver ["Матрица на адресных светодиодах с управлением по Bluetooth"](https://github.com/AlexGyver/GyverMatrixBT)
#### Изменения по справнению с исходным пректом:
 - Поддержка только контроллера с большим объемом памятии наличием WiFi на борту - NodeMCU
 - Другие типы контроллеров (Arduino Mega + WiFi, Wemod D1) - не тестировались.
 - Удалена поддержка управления с кнопок
 - Оставлена одна кнопка управления для переключения режимов, отключения работающего будильника
 - Удалена поддержка управления по Bluetooth
 - Удалена поддержка платы часов реального времени
 - Управление матрицей - через WiFi (локальная сеть)
 - Синхронизация времени с NTP сервером через интернет
 - Адаптированная программа управления матрицей на Andrioid
 - Изменены настройки режимов воспроизведения эффектов
 - Настройки режимов можно изменять из программы со смартфона
   - Яркость матрицы - единая для всех режимов
   - Скорость эффектов - индивидуально для каждого режима
   - Наличие наложения часов на эффекты - индивидуально для каждого режима
   - Включение/исключение режима из списка любимых режимов
 - Настройки сохраняются в энергонезависимой памяти EEPROM
 - К режиму часов добавлен календарь - кратковременное отображение текущей даты поверх эффекта
 - Настройка сервера синхронизации времени
 - Будильник "рассвет", настройки через программу на смартфоне 
 - Поддержка звука будильника  / звука рассвета звуковой платой MP3 DFPlayer
 - Настройки сетевого подключения (SSID и пароль) задаются в программе и сохраняются в EEPROM
 - Если не удается подключиться к сети (неверный пароль или имя сети) - создается точка подключения
   с именем MatrixAP, пароль 12341234, IP 192.168.4.1. Подключившись к точке доступа из приложения
   можно настроить параметры сети. Если после задания параметиров сети WiFi соединение установлено - 
   в приложении на смартфоне виден IP адрес подключения к сети WiFi.  
 - Быстрое включение режимов лампы белого или заданного цвета из приложения (вся панель светится), 
   выключение панели, комбинация лампы с отображением часов, ночные часы (пониженная яркость).
 - Автоматическая установка яркости матрицы в зависимости от уровня внешней освещенности.
 - Два программируемых по времени режима, позволяющие, например, настроить автоматическое выключение экрана матрицы в ночное время и автоматическое же включение матрицы утром.

## От исходного проекта сохранены следующие возможности:
#### Режимы:
 - Рисование
 - Загрузка картинок
 - Бегущая строка  
#### Эффекты:
 - "Дыхание" яркости
 - Смена цвета
 - Снегопад
 - Блуждающий кубик
 - Радуга
 - Огонь
 - The Matrix
 - Летающие частицы
 - Звездопад
 - Шумовые эффекты с разными цветовыми палитрами
 - Анимация
 - Часы  
#### Игры:
 - Змейка
 - Tетриc
 - Лабиринт  
 - Арканоид
 - Runner
 - Flappy bird
#### Возможности:
- Автоподключение к матрице при запуске
- Настройки яркости и скорости отображения
- Использование акселерометра в играх

### Кнопка управления режимами, последовательность переключения:
#### Будильник сработал, идет рассвет или мелодия пробуждения
- Любое нажатие кнопки отключает будильник
#### Долгое удержание кнопки (более 3 секунд)
- Если матрица включена, она будет выключена (черный экран)
- Если матрица выключена (черный экран) - включается режим часов
#### Однократное нажатие кнопки
- Если матрица включена в режиме часов, происходит переключение часов по циклу:
  - Часы на черном фоне
  - Часы на фоне огня (камин)
  - Ночные часы
- Если матрица включена в режим лампы (белый экран) - вкл / выкл отображения часов.
- Если работают демо-режимы -  переход к следующему режиму
#### Двухкратное нажатие кнопки
- Из любого режима включается режим часов на черном фоне
- Из режима часов переключается в режим лампы
#### Трехкратное нажатие кнопки
- Включается демо-режим
#### Четырехкратное нажатие кнопки
- На экране матрицы в режиме бегущей строки отображается IP адрес матрицы, если подключение к локальной WiFi сети установлено

<a id="chapter-1"></a>
## Папки
**ВНИМАНИЕ! Если это твой первый опыт работы с Arduino, читай [инструкцию](#chapter-4)**
- **libraries** - библиотеки проекта.
- **firmware** - прошивки для NodeMCU
- **schemes** - схемы подключения компонентов
- **sounds** - звуковые файлы будильника для размещения на SD-карте
- **Android** - файлы с приложениями, примерами для Android и Thunkable

<a id="chapter-2"></a>
## Схемы
![SCHEME](https://github.com/vvip-68/GyverMatrixWiFi/blob/master/schemes/scheme.jpg)

<a id="chapter-3"></a>
## Материалы и компоненты
### Ссылки оставлены на магазины
Полный список компонентов есть в статье https://alexgyver.ru/matrix_guide/
- NodeMCU http://ali.onl/1dVU http://ali.onl/1dVV
- Матрицы разные http://ali.ski/pw2ic
- Лента http://ali.ski/YdfMN
- Модульная гирлянда http://ali.ski/0h35RR
- Резисторы http://ali.ski/UEez2
- БП 5 Вольт http://ali.ski/3cNyj  http://ali.ski/qSKFK
- MP3 DFPlayer http://ali.onl/1gY1 http://ali.onl/1gY3
- Динамики http://ali.onl/1h3u http://ali.onl/1h3v

## Вам скорее всего пригодится
* [Всё для пайки (паяльники и примочки)](http://alexgyver.ru/all-for-soldering/)
* [Недорогие инструменты](http://alexgyver.ru/my_instruments/)
* [Все существующие модули и сенсоры Arduino](http://alexgyver.ru/arduino_shop/)
* [Электронные компоненты](http://alexgyver.ru/electronics/)
* [Аккумуляторы и зарядные модули](http://alexgyver.ru/18650/)

<a id="chapter-4"></a>
## Как скачать и прошить
* [Первые шаги с Arduino](http://alexgyver.ru/arduino-first/) - ультра подробная статья по началу работы с Ардуино, ознакомиться первым делом!
* Скачать архив с проектом
> На главной странице проекта (где ты читаешь этот текст) вверху справа зелёная кнопка **Clone or download**, вот её жми, там будет **Download ZIP**
* Установить библиотеки в  
`C:\Program Files (x86)\Arduino\libraries\` (Windows x64)  
`C:\Program Files\Arduino\libraries\` (Windows x86)
* **Подключить внешнее питание 5 Вольт**
* Подключить Ардуино к компьютеру
* Запустить файл прошивки (который имеет расширение .ino)
* Настроить IDE (COM порт, модель Arduino, как в статье выше)
* Настроить что нужно по проекту
* Нажать загрузить
* Скачать и установить на смартфон GyverMatrix
* Пользоваться  

<a id="chapter-5"></a>
## FAQ
### Основные вопросы
В: Как скачать с этого грёбаного сайта?  
О: На главной странице проекта (где ты читаешь этот текст) вверху справа зелёная кнопка **Clone or download**, вот её жми, там будет **Download ZIP**

В: Скачался какой то файл .zip, куда его теперь?  
О: Это архив. Можно открыть стандартными средствами Windows, но думаю у всех на компьютере установлен WinRAR, архив нужно правой кнопкой и извлечь.

В: Я совсем новичок! Что мне делать с Ардуиной, где взять все программы?  
О: Читай и смотри видос http://alexgyver.ru/arduino-first/

В: Вылетает ошибка загрузки / компиляции!   
О: Читай тут: https://alexgyver.ru/arduino-first/#step-5

### Вопросы по этому проекту

В: Эй чувак! У тебя проект не компилится. Ты файл DFRobotDFPlayerMini.h в проект забыл включить. Выложи!   
О: Это стандартная библиотека для MP3 DFPlayer. Идите в менеджер библиотек и установите ее. Или скачайте с [сайта производителя](https://github.com/DFRobot/DFRobotDFPlayerMini)

В: Собрал, использую NodeMCU. Ничего не работает! Мигает один или несколько светодиодов в начале матрицы. И всё.   
О: NodeMCU v3 чрезвычайно требователен к источнику питания. Ему на вход VIN нужно подавать напряжение в диапазоне 4.7-5 вольт. И не более. Описанные эффекты возникают даже при питании в 5.25 (а тем более - 5.45) вольт. Для проверки - не подключайте +5 вольт от блока питания к NodeMCU совсем, питание подавайте на матрицу непосредственно. Землю NodeMCU и ленты соедините. Подключите сигнальный пин NodeMCU ко входу DIN ленты. Подключите NodeMCU к компьютеру через USB (питание будет поступать отсюда). Должно заработать. Далее регулируйте выходное напряжение своего блока питания.

В: Не компилируется. Выбрана плата "голая ESP8266-12E". Сообщение об ошибке: "D4 was not declared in this scope."   
О: Очевидно производители библиотеки для "голой ESP8266-12E" не определили данную константу. Используйте всесто константы D4 числовое определение пина для вашей платы или выполните компиляцию проекта для плат NodeMCU или WeMos D1 R2.

В: Не компилируется. В сообщении об ошибке содержатся сведения о дублирующихся библиотеках.    
О: В вашей среде установлено две версии одной и той же библиотеки. Обычно это библиотека FastLED - одна версия находится в папке установки среды Ардуино (например в "C:\Program Files (x86)\Arduino\libraries\"), другая - в папке документов пользователя (например "C:\Users\vvip-68\Documents\Arduino\libraries\"). Удалите одну из версий библиотек и попробуйте скомпилировать снова.

В: Не компилируется. В сообщении об ошибке что-то про несоответствие типов.   
О: Обычно такая ситуация возникает в двух случаях:
- выбрана неверная плата. Используйте NodeMCU 1.0 (ESP-12E Module) или Wemos D1 R1. Под эти платы проект собирается, под другие, возможно, нужна модификация кода.
- установлена устаревшая версия библиотек поддержки плат - например для ESP8266 версия библиотеки 2.4.2. Данный проект использует библиотеки для плат ESP8266 версии 2.5. Обновите библиотеки поддержки плат.

<a id="chapter-6"></a>
## Полезная информация
* [Cайт Alex Gyver](http://alexgyver.ru/)
* [Канал Alex Gyver на YouTube](https://www.youtube.com/channel/UCgtAOyEQdAyjvm9ATCi_Aig?sub_confirmation=1)
* [YouTube канал про Arduino](https://www.youtube.com/channel/UC4axiS76D784-ofoTdo5zOA?sub_confirmation=1)
* [Видеоуроки по пайке](https://www.youtube.com/playlist?list=PLOT_HeyBraBuMIwfSYu7kCKXxQGsUKcqR)
* [Видеоуроки по Arduino](http://alexgyver.ru/arduino_lessons/)
