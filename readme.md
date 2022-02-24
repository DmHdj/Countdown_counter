# Countdown counter
###### ENG

## This counter can be installed on the site. It will work and count down the time until the appointed date - deadline

[counter_screen](img/screen.PNG)

The html structure of the counter is in the file **[index.html](https://github.com/DmHdj/Countdown_counter/blob/main/index.html)**

CSS styles are in the CSS folder and the **[style.css](https://github.com/DmHdj/Countdown_counter/blob/main/css/style.css)** file.<br/>
Styles can be changed if needed.


The script is located in the js folder in the **[script.js](https://github.com/DmHdj/Countdown_counter/blob/main/js/script.js)** file


---
## **[script.js](https://github.com/DmHdj/Countdown_counter/blob/main/js/script.js)**

The end date is placed in the ***deadline*** constant
```
const deadline = '2022-12-31'; 
```
If necessary, the date can be assigned from the input, admin panel or other source.

The getTimeRemaining function considers the difference between the current time and the deadline.
```
function getTimeRemaining (endtime) {
        const t = Date.parse(endtime) - Date.parse(new Date()),
              days = Math.floor(t / (1000 * 60 * 60 * 24)),
              hours = Math.floor((t / (1000 * 60 * 60)) % 24),
              minutes = Math.floor((t / (1000 *60)) % 60),
              seconds = Math.floor((t / 1000) % 60);

        return {
            'total': t,
            'days': days,
            'hours': hours,
            'minutes': minutes,
            'seconds': seconds
        };
    }
```

It takes one argument - the end time and returns an object with days, hours, minutes until the end. <br/>
The 'total' property is needed in order to understand how much is left to the end, so that there are no negative values.

---

The setСlock function sets a timer on the page. It takes two arguments - a selector and an end time.

The ``updateClock`` function updates the timer every second. At the same time, it has three main actions:
1. calculation of the time left for this second, for this you need the `getTimeRemaining` function, which will return an object.<br/>
```
    const t = getTimeRemaining(endtime);
```
2. The calculated values ​​are placed on the page.
<br/>
```
    days.innerHTML = getZero(t.days);
    hours.innerHTML = getZero(t.hours);
    minutes.innerHTML = getZero(t.minutes);
    seconds.innerHTML = getZero(t.seconds);
```
3. Runs `updateClock` every second.
```
timeInterval = setInterval(updateClock, 1000);
```
The condition allows you to exclude negative values
```
if (t.total <= 0) {
    clearInterval(timeInterval);
}
```
---
###### РУС

## Этот счетчик можно установить на сайте. Он будет работать и отсчитывать время до назначенной даты - дедлайна

[counter_screen](img/screen.PNG)

HTML-структура счетчика находится в файле **[index.html](https://github.com/DmHdj/Countdown_counter/blob/main/index.html)**

Стили CSS находятся в папке CSS и в файле **[style.css](https://github.com/DmHdj/Countdown_counter/blob/main/css/style.css)** .<br/>
При необходимости стили можно изменить.


Скрипт находится в папке js в файле **[script.js](https://github.com/DmHdj/Countdown_counter/blob/main/js/script.js)** 


---
## **[script.js](https://github.com/DmHdj/Countdown_counter/blob/main/js/script.js)**

Дата окончания помещается в константу***deadline*** 
```
const deadline = '2022-12-31'; 
```
При необходимости дату можно назначить из input, админки или другого источника.

Функция `getTimeRemaining` учитывает разницу между текущим временем и крайним сроком.
```
function getTimeRemaining (endtime) {
        const t = Date.parse(endtime) - Date.parse(new Date()),
              days = Math.floor(t / (1000 * 60 * 60 * 24)),
              hours = Math.floor((t / (1000 * 60 * 60)) % 24),
              minutes = Math.floor((t / (1000 *60)) % 60),
              seconds = Math.floor((t / 1000) % 60);

        return {
            'total': t,
            'days': days,
            'hours': hours,
            'minutes': minutes,
            'seconds': seconds
        };
    }
```

Он принимает один аргумент - время окончания и возвращает объект с днями, часами, минутами до конца. <br/>
Свойство **total** нужно для того, чтобы понять, сколько осталось до конца, чтобы не осталось отрицательных значений.

---

Функция setСlock устанавливает таймер на странице. Он принимает два аргумента — селектор и время окончания.    

Функция updateClock обновляет таймер каждую секунду. При этом она имеет три основных действия:
1. подсчет времени оставшегося на эту секунду, для этого нужна функция getTimeRemaining, которая будет возвращать объект.<br/>
```
    const t = getTimeRemaining(endtime);
```
2. Рассчитанные значения размещаются на странице.
<br/>
```
    days.innerHTML = getZero(t.days);
    hours.innerHTML = getZero(t.hours);
    minutes.innerHTML = getZero(t.minutes);
    seconds.innerHTML = getZero(t.seconds);
```
3. Запускает `updateClock` каждую секунду.
```
timeInterval = setInterval(updateClock, 1000);
```
Условие позволяет исключить отрицательные значения
```
if (t.total <= 0) {
    clearInterval(timeInterval);
}
```






