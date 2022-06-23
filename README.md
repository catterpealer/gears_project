[Отчет шестеренки.pdf](https://github.com/kostnine/gears_project/files/8967882/default.pdf)
# gears_project
Ремонт механизма шестеренок


Задачи:
Базовая часть:
1. Установить недостающую шестеренку на имеющуюся ось.
Бонусная часть:
2. Найти и заменить сломанную шестеренку.
3. Определить количество зубцов у каждой шестеренки(в том числе, у
сломанных, если они присутствуют).
Этапы для выполнения базовой части задания:
1. Бинаризация изображения (отсечение значений пикселей по порогу).
2. Выделение связных компонент на изображении.
3. Классификация связных компонент на шестеренки и ось.
4. Положение центра шестеренки, радиус меньшей окружности, радиус большей
окружности.
5. Выбор шестеренки, которую необходимо установить на ось, учитывая ее
размер.
1 этап: Бинаризация изображения.
Процесс бинаризации – это перевод цветного изображения в двухцветное чернобелое. Главным параметром такого преобразования является порог h – значение, с
которым сравнивается яркость каждого пикселя. Данный порог может быть
вычислен по формуле: 0.3 * r + 0.59 * g + 0.11 * b.

2 этап: Выделение связных компонент на изображении.
Определение связной области: множество пикселей, у каждого пикселя у которого
есть хотя бы один сосед, принадлежащий данному множеству. Выделение связных
компонент выполняет с помощью рекурсивного алгоритма, данный алгоритм
реализован в моей программе с помощью двух функций:
void fill (const Matrix<uint> &bin, Matrix<uint> &lbl, int i, int j, uint counter);
int labeling (const Matrix<uint> &bin, Matrix<uint> &lbl, int i, int j, uint counter);
По результатам выделения связных компонент, у меня получается размеченное
изображение шестеренок в 7 цветах от красного до белого соответственно.
  
Вычисление внешнего и внутреннего радиусов:
Радиус большей окружности, образующей шестеренку – это расстояние от центра
самой удаленной точки шестеренки, а радиус меньшей окружности – это
расстояние от центра шестеренки до ближайшей точки, не принадлежащей
шестеренке.
  
3 этап: Выбор подходящей шестеренки и установка её на ось. На выбор дается 3
шестеренки разных размеров и только одна является правильной для данного
механизма шестеренок.
  
4 этап: Запуск программы.
Для того, чтобы запустить программу у нас есть makefile, при помощи которого
создается папка build. Для запуска нашей программы необходимо при запуске
указать изображение без одной шестеренки, новое изображение со вставленное
шестеренкой, изображение одной из трех шестеренок и имя текстового файла, в
который будет записываться информация о параметрах шестеренок.
Например: ./main 0001.bmp 1.bmp 0001_1.bmp info.txt
Текстовый файл с результатами выглядит следующим образом:
Gears count: 1
Gear #0
X = 147
Y = 147
R = 146
r = 113  

РЕЗУЛЬТАТЫ:
1. Вставка шестеренки на ось
  
![Безымянный](https://user-images.githubusercontent.com/92250704/175317897-1740f056-940c-4694-b87d-debaf5a1d1d1.png)


  
![image](https://user-images.githubusercontent.com/92250704/175317745-b9cef0b3-240b-4dfe-ab25-55f4a8055189.png)
  

  
  
  
  
  
