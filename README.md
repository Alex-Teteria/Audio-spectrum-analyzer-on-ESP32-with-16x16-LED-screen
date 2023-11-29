# Audio-spectrum-analyzer-on-ESP32-with-16x16-LED-screen
Calculation of the audio signal spectrum and its display on the WS2812B RGB LED panel using the ESP32 microcontroller under MicroPython.

## Зміст  

1. [Огляд](./README.md#1-огляд)
2. [Використання API від Twilio](./README.md#2-Використання-API-від-Twilio)
3. [Приклад реалізації](./README.md#3-Приклад-реалізації)
4. [Install](./README.md#4-install)
   
## 1. Огляд

Для розрахунку FFT використано алгоритм Кулі — Тьюкі, зокрема його реалізацію на MicroPython [algorithms](https://github.com/peterhinch/micropython-fourier). Модуль мікрофонного підсилювача має на виході постійну складову VCC / 2, тому сигнал на вхід АЦП подається через конденсатор. Резистори 110к та 20к забезпечують 
та додатково на вхід АЦП додається 0,5В постійної складової  та  надає можливість пересилати повідомлення SMS використовуючи API. Реєстрація на сайті [Twilio](https://www.twilio.com/) та безкоштовне (trial) використання його сервісів передбачає надання одного телефонного номера, через який буде здійснюватись обмін повідомленнями. При цьому trial-режим використання має ряд обмежень, одне з яких - можливість відправляти SMS тільки на один номер +380ХХХХХХХХХ, який зазначається при реєстрації та попередньо перевіряється надсиланням на нього коду. Але ніщо не заважає зареєструвати необхідну кількість телефонів як окремих користувачів, відповідно на кожен з них необхідно мати e-mail, який також перевіряється при реєстрації. Використовуючи мікроконтролер, наприклад ESP8266, можна автоматизувати процес розсилання повідомлень SMS по усім необхідним мобільним телефонам. Як [приклад](./README.md#3-Приклад-реалізації), реалізовано відправлення SMS-повідомлень на окремі телефони при спрацьовуванні датчиків.
