## Задание 3

Напишите следующую программу. Сначала пользователю предлагается ввести 2 числа типа с плавающей точкой (используйте тип double). Затем предлагается ввести один из следующих математических символов: +, -, * или /. Программа выполняет выбранную пользователем математическую операцию между двумя числами, а затем выводит результат на экран. Если пользователь ввел некорректный символ, то программа ничего не должна выводить. Например:

Enter a double value: 7
Enter a double value: 5
Enter one of the following: +, -, *, or /: *
7 * 5 = 35

```cpp
#include <iostream>

using namespace std;

double enterNumber(){
   std::cout << "Введите число: ";
   double number;
   std::cin >> number;
   return number;
}

void writeResult(double result){
  std::cout << "Результат вычислений: " << result <<std::endl;
}

double sumNumbers(double num_1, double num_2){
  double result = num_1 + num_2;
  writeResult(result);
  return result;
}

double multiplyNumbers(double num_1, double num_2){
  double result = num_1 * num_2;
  writeResult(result);
  return result;
}

double divNumbers(double num_1, double num_2){
  double result = num_1 / num_2;
  writeResult(result);
  return result;
}

double substractNumbers(double num_1, double num_2){
  double result = num_1 - num_2;
  writeResult(result);
  return result;
}

int main(){
  setlocale(LC_ALL, "Russian");
  double num_1 = enterNumber();
  double num_2 = enterNumber();
  std::cout << "Введите математический символ: ";
  char symbol;
  std::cin >> symbol;
  double result;
  if (symbol == '+')
    result = sumNumbers(num_1, num_2);
  else if (symbol == '-')
    result = substractNumbers(num_1, num_2);
  else if (symbol == '*')
    result = multiplyNumbers(num_1, num_2);
  else if (symbol == '/')
    result = divNumbers(num_1, num_2);
  else   
    std::cout << "Вы ввели неизвестный математический символ";    
  return 0;     
}
```

## Задание 4

Это уже немного сложнее. Напишите небольшую программу-симулятор падения мячика с башни. Сначала пользователю предлагается ввести высоту башни в метрах. Не забывайте о гравитации (9,8м/с2) и о том, что у мячика нет начальной скорости (его держат в руках). Программа должна выводить расстояние от земли, на котором находится мячик после 0, 1, 2, 3, 4 и 5 секунд падения. Минимальная высота составляет 0 метров (ниже мячику падать нельзя).

В вашей программе должен быть заголовочный файл constants.h с пространством имен myConstants. В myConstants определите символьную константу для хранения значения силы тяжести на Земле (9.8). В качестве напоминания смотрите урок №37.

Напишите функцию для вычисления высоты мячика через х секунд падения. Используйте следующую формулу: высота мячика над землей = константа_гравитации * x_секунд2/2.

Пример результата выполнения программы:

Enter the initial height of the tower in meters: 100
At 0 seconds, the ball is at height: 100 meters
At 1 seconds, the ball is at height: 95.1 meters
At 2 seconds, the ball is at height: 80.4 meters
At 3 seconds, the ball is at height: 55.9 meters
At 4 seconds, the ball is at height: 21.6 meters
At 5 seconds, the ball is on the ground.

файл constant.h
``` cpp
#ifndef CONSTANTS_H
#define CONSTANTS_H
 
namespace myConstants
{
    const double gravity(9.8); 
}
#endif

```

файл main.cpp

```cpp

#include <iostream>
#include "constants.h"
 

double getInitialHeight()
{
	std::cout << "Enter the initial height of the tower in meters: ";
	double initialHeight;
	std::cin >> initialHeight;
	return initialHeight;
}
 
double calculateHeight(double initialHeight, int seconds)
{
	double distanceFallen = (myConstants::gravity * seconds * seconds) / 2;
	double currentHeight = initialHeight - distanceFallen;
 
	return currentHeight;
}
 
void printHeight(double height, int seconds)
{
	if (height > 0.0)
		std::cout << "At " << seconds << " seconds, the ball is at height: " << height << " meters\n";
	else
		std::cout << "At " << seconds << " seconds, the ball is on the ground.\n";
}
 
void calculateAndPrintHeight(double initialHeight, int seconds)
{
	double height = calculateHeight(initialHeight, seconds);
	printHeight(height, seconds);
}
 
int main()
{
	const double initialHeight = getInitialHeight();
 
	calculateAndPrintHeight(initialHeight, 0);
	calculateAndPrintHeight(initialHeight, 1);
	calculateAndPrintHeight(initialHeight, 2);
	calculateAndPrintHeight(initialHeight, 3);
	calculateAndPrintHeight(initialHeight, 4);
	calculateAndPrintHeight(initialHeight, 5);
 
	return 0;
}
```
