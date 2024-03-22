Системные требования

1. python 3.9.19
2. у меня все работает на ubuntu 22.04

Установка

`git clone https://github.com/denis-kosolapov/integris_test.git`

`cd integris_test`

`pip install -r requirements.txt`

Запуск из корневой папки integris_test

`python app.py`


Основной код находится в пакете DataProcessing. Время работы программы при тестировании 1500 миллисекунд.
Настроить автоматического переход на страницу изображений можно в файле 
templates/index.html в строке 34 

`}, 1500); // Переход через ... `

Самая сложная часть работы находится в файле DataProcessing/DataProcessor.py . Идея состоит в том чтобы разбить данные на части
с помощью Pandas. Затем обработать части асинхронно и собрать результат обратно в один файл или вывод функции. 
Комментарии оставил в коде.

При щапуске программа сама создает 3 папки:

`data`

`images`

`uploaded_files`

После запуска нужно загрузить файл `20240213_1000.csv` на главной странице. После загрузки файла программа автоматически переходит на новую
вкладку с отображаемыми картами и графиком. При скачивании репозитория файл находится в корневом каталоге, поэтому его нужно загрузить в приложении.

Суть работы программы.
1. Разбить на части файл и все части обработать асинхронно
2. обработка каждой части в своем потоке
3. объединение результатов работы в один файл или вывод класса

Таким образом, обработка данных файла происходит намного быстрее, так как каждая часть обрабатывается в своем потоке.
Количество частей можно настраивать, в программе CSV файл на 97000+ строк делится на части по 1000 строк. 
Затем каждая часть обрабатывается в своем потоке. В итоге, скорость срабатывания приложения с момента загрузки файла
до вывода обработанных данных на страницу составляет менее 1.5 секунд. 