Системные требования

python 3.9.19

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
