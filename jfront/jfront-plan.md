<p align="center">
  <a href="https://github.com/Jepria/jfront/blob/master/README.md">
    <img src="images/jfront-logo.png" alt="drawing" width="100"/>
  </a>
</p>

# План работ по *JFront*

---

## Карта боевых действий

![План-схема разработки](images/jfront-plan.svg)

Отражает актуальное состояние проекта.

---

Принципы ведения работ на проекте:
1. Не одно решение, а постоянно обновляемая иерархия решений, гармонично обеспечивающая поддержку необходимых классов
продуктов;
2. Не одна библиотека, а иерархия библиотек, зависимости между которыми, в частности, обусловлены иерархией решений
3. Разработка библиотек не должна опережать разработку приложений:
   - Библиотеки должны огранически вырастать, как средство повторного использования кода существующих приложений;
   - По мере роста библиотек *JFront* должны соответственно изменяться jfront-стартеры;
4. Разработка эталонных приложений и генераторов прототипов выполняется после стабилизации (окончания бурного роста)
библиотек
5. Проект поддерживает следующие классы frontend-решений:
- внутренние web-приложения компании
- динамические web-сайты
- статические web-сайты
- мобильные приложения с нативным интерфейсом

Разработка web-сайтов и web-приложений ориентируется на одновременную поддержку desktop-браузеров и браузеров мобильных
устройств и основывается на принципах *отзывчивой вёрстки*.

---

### Разработка совмещается с обучением

Боевая разработка предваряется изучением и освоением необходимых инструментов.  
Главным средством освоения инструментов служит практика разработки соответствующих *стартеров*.  
В дальнейшем качественные стартеры предполагается использовать в качестве основы для разработки боевых проектов. 

---

### Общий план действий

Предполагается следующий порядок разработки:

1. Разработка стартеров
2. Разработка первых приложений
3. Разработка библиотек и фреймворков
   - *jfront-component*
   - *jfront-core*
   - *jfront-oauth*
   - *jfront-rest*
   - ...
4. Разработка эталонных приложений и генераторов с использованием и на основе разработанных библиотек и фреймворков
5. Массовая разработка боевых приложений с использованием эталонных приложений, разработанных библиотек, фреймворков и
генераторов

---
### О стартерах

***Стартер*** *это работоспособная программа (приложение, библиотека, ...) имеющая ***определённый набор свойств***, которая служит основой для разработки множества других программ, нуждающихся в этих свойствах*. 

Присутствие бизнес-логики в стартерах минимально, оно ограничивается задачей демонстрации применения тех или иных свойств
и программных решений. Примерами таких стартеров служат разнообразные мини-todo-приложения.

#### Контейнеры для бизнес-логики
В этом смысле стартеры можно рассматривать как *абстрактные программы*, являющиеся своего рода контейнерами для
бизнес-логики, которые превращаются в настоящие программы по мере их наполнения функциональностью целевой предметной
области.

#### *JFront*-стартеры

Должны поддерживать все необходимые классы frontend-решений (см. выше, как минимум, по одному стартеру на класс).

В идеале каждый из продуктов и все вместе в качестве вех своего роста (с некоторой точки зрения - в качестве побочного
результата его разработки) оставляют за собой иерархию стартеров, каждый из которых служит потенциальной основой для
создания множества программ, отвечающих соответствующему набору требований.

Стартеры создаются в иерархии и по правилам проекта [*SoftSpiders*](https://github.com/softspiders/softspiders).
