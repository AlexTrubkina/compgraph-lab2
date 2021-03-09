## Напишите функцию doubleNumber(), которая принимает целое число в качестве параметра, удваивает его, а затем возвращает результат обратно в caller.

``` cpp
int doubleNumber(int num){
  return 2 * a;
}

```

## Напишите полноценную программу, которая принимает целое число от пользователя (используйте std::cin), удваивает его с помощью функции doubleNumber() из предыдущего задания, а затем выводит результат на экран.

``` cpp

int doubleNumber(int num){
  return 2 * num;
}

int main(){
  int number;
  std::cin >> number; 
  std:cout >> doubleNumber(number) << std::endl;
  return 0;
}

```
