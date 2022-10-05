# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнила:
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
Ознакомиться с программными средствами для организции передачи данных между инструментами google, Python и Unity.

## Ход работы

## Задание 1
0. Включаем Многоточие, а точнее альбом в вк Лучшие песни за 20 лет
1. Открыть через браузер [консоль облака гугл](https://console.cloud.google.com/apis/credentials?project=unitydatascience-364410)

2. Создать новый проект ![image](https://user-images.githubusercontent.com/87576995/194017212-5dba96e5-5f6c-48cb-8cd9-0eda8248cee8.png) 

3. Нажимаем на название нашего проекта, переходим в Marketplace и включаем google drive apl. В APIs & Services включаем google sheets api
![image](https://user-images.githubusercontent.com/87576995/194017920-4cd72ee4-9edd-4a91-adda-735700fd959c.png

4. Creditentials --> создаем service account
![image](https://user-images.githubusercontent.com/87576995/194021102-5a885661-e3e4-460b-9917-67480405e1fb.png)

5. Добавляем API ключ к сервис аккаунту в формате JSON. Сохраняем его в папке с нашим проектом в PyCharm'е
![image](https://user-images.githubusercontent.com/87576995/194023246-9107cb56-52ad-42e1-b7f2-a6d6e40a1730.png)

6. Создаем гугл таблицу и добавляем редактором почту из Деталей сервис аккаунта

7. Скачиваем gspread и numpy в PyCharm'e






*Код реализации:
print('hello world')



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

1.


## Выводы

Сегодня я научилась связывать проект в google sheets с проектом на Unity и VSCode через google cloud и писать(читай копировать, но не понимать) код обозначающий инфляцию. Научилась сначала просматривать все материалы, которые нам скидывают, а потом паниковать, что ничего не находится. Научилась самостоятельности в поиске команд для кода.

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
