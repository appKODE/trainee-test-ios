# Привет!

Во-первых, поздравляем! Ты выбрал для начала своей карьеры, пожалуй, самый эффективный и увлекательный старт - стажировку в нашей компании.

Во-вторых, приготовься к тому, что будет непросто - мы разработчики, а не университетские преподаватели. Времени на раскачку не будет, а обучение на стажировке максимально приближено к реальной работе :)

В-третьих, надо сделать тестовое задание, чтобы попасть на стажировку. Нам это нужно для того, чтобы понять, что ты уже немного умеешь программировать и сможешь справиться с тем материалом, который мы будем давать в процессе стажировки.

## Что нужно сделать?

В качестве тестового задания мы предлагаем тебе реализовать небольшое приложение, в котором есть всего по чуть-чуть: верстки, работы с api, преобразование данных и т.д.

## Какие требования к процессу и результату?

1. Первое, что нужно сделать - это прочитать и разобраться во всех требованиях, дизайне и api, указанных в этом документе;
2. Затем - разбить проект на отдельные задачи, т.е. продекомпозировать;
3. После этого дать временную оценку в часах каждой задаче. Если ожидаемое тобой время выполнения отдельной задачи превышает 2 часа - значит, нужно эту задачу разбить на подзадачи и оценить каждую из них. В итоге у тебя должен получиться план работ и ожидаемое время выполнения всего тестового задания;
4. После планирования можно переходить к программированию. Создай новый репозиторий в GitHub, сделай его приватным (после старта стажировки можно будет его сделать публичным) и добавь в collaborators пользователя kode-ios;
5. В первом commit в репозиторий в файле [readme.md](http://readme.md) зафиксируй свой план задач с ожидаемой временной оценкой из пункта 3;
6. Двигаясь по собственному плану, реализуй тестовое задание;
7. По завершении работ добавь в [readme.md](http://readme.md) реальное время выполнение задач и напиши в телеграм о готовности HR-специалисту, чтобы задание начали проверять.

### На что мы будем смотреть? На все сразу:

- на полноту реализованного функционала и соответствие дизайну;
- количество ошибок;
- стиль и оформление кода;
- работу с git - оформление commits, pull requests;
- декомпозицию и оценку - то есть на твоё умение разбивать задачи и планировать собственное время;
- на что-то ещё :)

### Сколько есть времени?

Столько, сколько потребуется. Но, разумеется, у реализации тестового, как и у любой рабочей задачи, есть дедлайн - 15 ноября 2021 23:59:59 UTC +2. Но постарайся закончить выполнение тестового как можно быстрее, чтобы мы смогли вдумчиво его проверить!

Достаточно вводных, переходим к требованиям!

# Требования

## Стэк
- Swift 5
- UIKit
- iOS 13+
- Зависимости через SPM или Cocoapods

## Дизайн

Хороший дизайн для клиентского разработчика - отличный способ быстро понять, что предстоит сделать. Он у нас именно такой:

[https://www.figma.com/file/GRRKONipVClULsfdCAuVs1/KODE-Trainee-Dev-Осень'21?node-id=0%3A1](https://www.figma.com/file/GRRKONipVClULsfdCAuVs1/KODE-Trainee-Dev-%D0%9E%D1%81%D0%B5%D0%BD%D1%8C'21?node-id=0%3A1)

## API

Спецификация метода API (он у нас один) - [https://kode-education.stoplight.io/docs/trainee-test/b3A6MjUxNDM5Mjg-get-users](https://kode-education.stoplight.io/docs/trainee-test/b3A6MjUxNDM5Mjg-get-users)

Запрос для получения успешного ответа:

```bash
curl --request GET \
  --url https://stoplight.io/mocks/kode-education/trainee-test/25143926/users \
  --header 'Content-Type: application/json' \
  --header 'Prefer: code=200, example=success'
```

Запрос для тестирования на разных данных (генерируется автоматически при каждом запросе):

```bash
curl --request GET \
  --url https://stoplight.io/mocks/kode-education/trainee-test/25143926/users \
  --header 'Content-Type: application/json' \
  --header 'Prefer: code=200, dynamic=true'
```

Запрос, который вернет ошибку с http кодом 500:

```bash
curl --request GET \
  --url https://stoplight.io/mocks/kode-education/trainee-test/25143926/users \
  --header 'Content-Type: application/json' \
  --header 'Prefer: code=500, example=error-500'
```

## Функциональные требования

### **Запуск**

Когда пользователь открывает приложение, необходимо загрузить актуальный список работников компании.

При входе в приложение необходимо отобразить экран 2.0.0. Изначально он должен быть в состоянии загрузки, экран 1.0.0. Если при загрузке произошла ошибка, отсутствует интернет-соединение или API вернул ошибку, необходимо отобразить экран "Критическая ошибка". В случае успеха необходимо отобразить список людей.

### **Навигация**

Компонент навигации находится в верхней части экрана и содержит поле поиска, кнопку сортировки и панель вкладок. В списке на главном экране должны быть работники департамента, соответствующего выбранной вкладке, либо вообще все сотрудники, если выбрана вкладка "Все".

Соответствия названия вкладок с полем "department" из запроса api:

android - Android

ios - iOS

design - Дизайн

management - Менеджмент

qa - QA

back_office - Бэк-офис

frontend - Frontend

hr - HR

pr - PR

backend - Backend

support - Техподдержка

analytics - Аналитика

При нажатии на кнопку "Фильтр" открывается Bottom Sheet с вариантами сортировки списка работников. Есть два варианта сортировки: "По алфавиту" (по умолчанию) и "По дню рождения". При переключении варианта сортировки Bottom Sheet должен закрываться, а список на главной странице должен быть обновлен.

Когда пользователь вводит текст в поле поиска, необходимо фильтровать список и отображать только работников, соответствующих параметрам поиска. Поиск может осуществляться по имени, фамилии или никнейму, состоящему из двух символов.

В случае отсутствия результатов поиска необходимо отобразить информацию о том, что ничего не было найдено. Экран "2.0.0Г Люди (Ошибка поиска)".

### Список работников

В режиме сортировки "По алфавиту" для каждого работника отображается его фотография, имя, никнейм и департамент.

В режиме сортировки "По дню рождения" список отображается от ближайшей даты для рождения вниз. Если день рождения следующего работника будет только в следующем году, то необходимо отобразить блок с годом, экран 2.0.1А.

При тапе на сотрудника нужно открыть экран информации о нём (экран "детали").

Пользователь должен иметь возможность перезагрузить список людей жестом pull-to-refresh. Если в процессе обновления произошла ошибка, необходимо ее игнорировать. Если данные загрузились успешно, необходимо обновить список на главном экране. При этом параметры поиска и сортировки должны учитываться и не должны быть сброшены.

### Экран "детали"

В шапке должны отображаться аватарка пользователя, имя, никнейм и название департамента.

Ниже находятся дата рождения и номер телефона. При нажатии на номер телефона необходимо показать action sheet с подтверждением звонка. При нажатии на кнопку с номером телефона в action sheet должен начаться звонок, а сам action sheet должен закрыться.

## Дополнительные задания

Дополнительные задания не обязательны для выполнения. Если вы не успеваете - лучше сделать хорошо основную часть. Но если время осталось...

### Отображение ошибки обновления

Если при загрузке списка людей произошла ошибка, необходимо показать уведомление с текстом ошибки - экран "2.0.0.А – Люди (Ошибка)". Существует несколько видов ошибок:

- Отсутствует интернет соединение. В этом случае в уведомлении должен отображаться текст "Не могу обновить данные. Проверь соединение с интернетом."
- Ошибка API. В этом случае в уведомлении должен быть отображен текст "Не могу обновить данные. Что-то пошло не так".

Уведомление закрывает собой Status bar. Оно должно скрываться спустя 3 секунды, также его можно убрать тапом.

### Анимированный индикатор pull-to-refresh

Индикатор должен заполняться по часовой стрелке в зависимости от того, как далеко его вытянул пользователь, а при старте обновления вращаться по кругу (см. [пример анимации](https://material.angular.io/components/progress-spinner/overview)). Экран "Refresh" под звездочкой.

# На этом всё, желаем удачи!
