Несколько классов для несложной графики
----------------------------------------------------------
Классы:  
 * Pixel - пиксель с координатами и RGB цветом
 * BMP_Image - класс для работы с 24-битными бмп изображениями
 * Canvas - основной класс с графическими методами
----------------------------------------------------------
Canvas - два конструктора:
  - canvas(int x, int y)  - создает пустой чёрный холст х на у.
  - canvas(string filename) - загружает в холст бмп картинку filename с последующей возможностью изменения.
----------------------------------------------------------
Методы Canvas-a:
  - canvas.save(string filename) - сохраняет холст в файл filename (расширение *.bmp)
  - canvas.put_pixel(int x, int y, int R, int G, int B) - закрасить пиксель по координатам (х, у) цветом RGB
  - canvas.get_pixel(int x, int y) - возвращает обьект класса Pixel - содержит координаты и цвет
  - canvas.fill_canvas(int R, int G, int B) - закрашивает весь холст цветом RGB
  - canvas.fill_area(int x, int y, int R, int G, int B, int R_stop = -1, int G_stop = -1, int B_stop = -1) - закрашивает область,
  содержащую точку (х, у) цветом RGB - стандартная заливка. Если переданы аргументы R_stop, ..., B_stop - закрашиваемая область 
  ограничена не изначальным цветом пикселя (х,у), а цветом R_stop, ..., B_stop
  - canvas.draw_segment(int x1, int y1, int x2, int y2, int R, int G, int B) - рисует отрезок из (x1, y1) в (x2, y2) цвета RGB 
  - canvas.draw_segment(int x1, int y1, int x2, int y2, int w, int R, int G, int B) - рисует отрезок толщины w из (x1, y1) в (x2, y2)
  - canvas.draw_rectangle(int x1, int y1, int x2, int y2, int w = 1, int R_f = -1, int G_f = -1, int B_f = -1) - рисует прямоугольник со сторонами
  параллельными сторонам изображения, с главной диагональю (x1, y1) --> (x2, y2), ширина сторон w, R_f, G_f, B_f - цвет заливки. (по умолчанию заливки нет)
  - canvas.draw_triangle(int x1, int y1, int x2, int y2, int x3, int y3, int R, int G, int B, int R_f=-1, int G_f = -1, int B_f=-1) - рисует треугольник
  по указанным вершинам, цвет сторон RGB, заливка цветом R_f, G_f, B_f (по умолчанию нет)
  - canvas.draw_circle(int x, int y, int Rad, int R, int G, int B, int R_f = -1, int G_f = -1, int B_f = -1) - рисует окружность
  с центром (х, у) и радиусом Rad, цвет RGB, цвет заливки R_f, G_f, B_f (по умолчанию нет)
  - canvas.draw_circle(int x, int y, int Rad, int R, int G, int B, int w, int R_f = -1, int G_f = -1, int B_f = -1) - то же самое
  с возможностью указать толщину окружности
  - canvas.plot(double* var_values, double* func_values, int sample_count) - рисует график по var_values - переменной и func_values - соответствующим
  значениям функции. sample_count - число точек. (Перед построением графика меняет масштаб на 800х800 и очищает холст).
  - canvas.scatterplot(double* var_values, double* func_values, int sample_count) - то же самое, но точечный график.
  - canvas.copy_fragment(int x1, int y1, int x2, int y2) - вырезает прямоугольный фрагмент от (x1, y1) до (x2, y2) и возвращает его в качестве
  объекта Canvas.
  - canvas.insert_fragment(int x, int y, Canvas fragment) - вставляет в текущий холст фрагмент fragment, (x,y) - кординаты левой верхней вершины вставляемого
  прямоугольного фрагмента.
  - canvas.insert_fragment(int x, int y, string filename) - делает то же самое, но загружает фрагмент из файла filename (тоже бмп картинка).
  - canvas.to_black_n_white() - переводит холст в чёрно-белый формат (средн. арифм. RGB цвета).
  - canvas.cut(int x_margin, int y_margin) - обрезает текущий холст - слева и справа поля шириной x_margin, снизу и сверху - поля шириной y_margin.
  - canvas.help() - выводит документацию в консоль.
  
  P.S. Методы построения графиков будут улучшены и расширены в функционале
----------------------------------------------------------
Исключения:
 - inner_error - внутренняя ошибка
 - draw_error - ошибка при рисовании
 - plot_error - ошибка при построении графика