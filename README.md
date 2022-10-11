# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #3 выполнила:
- Набиуллина Розалия Дамировна, ДГТУ, Школа Икс

Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения.
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения.
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения.
- Выводы.



## Цель работы
Познакомиться с программными средствами для создания системы машинного обучения и ее интеграции в Unity.

## Ход работы

## Задание 1
1. Открыть Unity. Создать пустой объект и добавить ML agent  

![image](https://user-images.githubusercontent.com/87576995/194870984-ae32c92b-27e2-46f9-b928-71d5be91bae2.png)
![image](https://user-images.githubusercontent.com/87576995/194871921-963eb8de-035f-411e-8351-7009900a5574.png)


2. Запустить Anaconda Prompt от имени администратора

Получаем это чудо 

(base) C:\Windows\system32>conda create -n MlAgent python=3.6.13

Proceed ([y]/n)? y

(base) C:\Windows\system32>conda activate MlAgent

потом это. очень многострадальное

![image](https://user-images.githubusercontent.com/87576995/195120984-8f1df58e-4198-4ee3-95a9-6c9d6d6b285e.png)


*Код реализации:


## Задание 2
1. Открыть скачанный со всеми расширениями и дополнительными приложениями Unity
2. Создать новый 3D проект
3. В Hierarchy создать пустой объект
4. В окне Project создать папку Скрипты
5. В папке Скрипты создать C# скрипт файл
6. Вставить код**
7. Перенести файл с кодом на пустой объект в окошке Scene
8. Открыть Console
9. Порадоваться, что тебя поприветствовал твой код

**Код реализации:
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class test : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        
    Debug.Log("Hello World");
        
    }
}


![photo_2022-09-26_19-51-39](https://user-images.githubusercontent.com/87576995/192866864-4b9def9b-432b-47b8-8efd-a24aee2f9e94.jpg)
![image](https://user-images.githubusercontent.com/87576995/192869081-76ecf15e-7991-4ea5-bc0f-fdebd8595374.png)



## Задание 3
### Какова роль параметра Lr? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ. В качестве эксперимента можете изменить значение параметра.

1. Произвести подготовку данных для работы с алгоритмом линейной регрессии. 10 видов данных были установлены случайным образом, и данные находились в линейной зависимости. Данные преобразуются в формат массива, чтобы их можно было вычислить напрямую при использовании умножения и сложения.
In [ ]:
#Import the required modules, numpy for calculation, and Matplotlib for drawing
import numpy as np
import matplotlib.pyplot as plt
#This code is for jupyter Notebook only
%matplotlib inline
# define data, and change list to array
x = [3,21,22,34,54,34,55,67,89,99]
x = np.array(x)
y = [2,22,24,65,79,82,55,130,150,199]
y = np.array(y)
#Show the effect of a scatter plot
plt.scatter(x,y)
2. Определить связанные функции. Функция модели: определяет модель линейной регрессии wx+b. Функция потерь: функция потерь среднеквадратичной
ошибки.
Функция оптимизации: метод градиентного спуска для нахождения частных производных w и b.
![image](https://user-images.githubusercontent.com/87576995/192873667-675f703d-3651-4b08-93f8-c5f88d509644.png)

#The basic linear regression model is wx+ b, and since this is a two-dimensional space, the model is ax+ b
def model(a, b, x):
return a*x + b
#The most commonly used loss function of linear regression model is the loss function of mean variance difference
def loss_function(a, b, x, y):
num = len(x)
prediction=model(a,b,x)
return (0.5/num) * (np.square(prediction-y)).sum()
#The optimization function mainly USES partial derivatives to update two parameters a and b
def optimize(a,b,x,y):
num = len(x)
prediction = model(a,b,x)
#Update the values of A and B by finding the partial derivatives of the loss
function on a and b
da = (1.0/num) * ((prediction -y)*x).sum()
db = (1.0/num) * ((prediction -y).sum())
a = a - Lr*da
b = b - Lr*db
return a, b
#iterated function, return a and b
def iterate(a,b,x,y,times):
for i in range(times):
a,b = optimize(a,b,x,y)
return a,b


3. Начать итерацию
Шаг 1. Инициализация и модель итеративной оптимизации
#Initialize parameters and display
a = np.random.rand(1)
print(a)
b = np.random.rand(1)
print(b)
Lr = 0.000001
#For the first iteration, the parameter values, losses, and visualization after the
iteration are displayed
a,b = iterate(a,b,x,y,1)
prediction=model(a,b,x)
loss = loss_function(a, b, x, y)
print(a,b,loss)
plt.scatter(x,y)
plt.plot(x,prediction)

![image](https://user-images.githubusercontent.com/87576995/192875327-0fbe36fc-26d4-4266-b480-b162bbde8ed6.png)

Шаг 2. На второй итерации отображаются значения параметров, значения потерь и эффекты визуализации после итерации
a,b = iterate(a,b,x,y,2)
prediction=model(a,b,x)
loss = loss_function(a, b, x, y)
print(a,b,loss)
plt.scatter(x,y)
plt.plot(x,prediction)

![image](https://user-images.githubusercontent.com/87576995/192876311-902ec7af-ac63-40c9-8e78-07b3792afa3a.png)

Шаг 3. Третья итерация показывает значения параметров, значения потерь и визуализацию после итерации
a,b = iterate(a,b,x,y,3)
prediction=model(a,b,x)
loss = loss_function(a, b, x, y)
print(a,b,loss)
plt.scatter(x,y)
plt.plot(x,prediction)

![image](https://user-images.githubusercontent.com/87576995/192876739-6419df15-801b-4d23-bbb6-48f9242f1e35.png)

Шаг 4. На четвертой итерации отображаются значения параметров, значения потерь и эффекты визуализации
a,b = iterate(a,b,x,y,4)
prediction=model(a,b,x)
loss = loss_function(a, b, x, y)
print(a,b,loss)
plt.scatter(x,y)
plt.plot(x,prediction)

![image](https://user-images.githubusercontent.com/87576995/192877127-f7456a91-2f2d-4730-a66a-9f2fa8dc2cf5.png)

Шаг 5. Пятая итерация показывает значение параметра, значение потерь и эффект визуализации после итерации
a,b = iterate(a,b,x,y,5)
prediction=model(a,b,x)
loss = loss_function(a, b, x, y)
print(a,b,loss)
plt.scatter(x,y)
plt.plot(x,prediction)

![image](https://user-images.githubusercontent.com/87576995/192877504-fd72423a-66e6-4e36-a3cd-5fdf3fd18119.png)

Шаг 6. 10000-я итерация, показывающая значения параметров, потери и визуализацию после итерации
a,b = iterate(a,b,x,y,10000)
prediction=model(a,b,x)
loss = loss_function(a, b, x, y)
print(a,b,loss)
plt.scatter(x,y)
plt.plot(x,prediction)

![image](https://user-images.githubusercontent.com/87576995/192878067-1414b21b-0ce3-4fde-9136-faa304ce8e43.png)


## Выводы

Абзац умных слов о том, что было сделано и что было узнано. А конкретнее, сегодня мы научились пользоваться двумя программами, которые нужны нам. А также ознакомились с основными операторами языка Python на примере реализации линейной регрессии(построили графики).

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**

**LittleNotDigitalNotTeam: Nabiullina
