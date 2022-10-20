# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #3 выполнила:
- Набиуллина Розалия Дамировна, ДГТУ, Школа Икс

Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | # | 20 |
| Задание 3 | # | 20 |

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
1. Открыть Unity. Создать пустой объект 3D проект(не обязательно создавать пустой объект) и добавить ML agent  

![image](https://user-images.githubusercontent.com/87576995/194870984-ae32c92b-27e2-46f9-b928-71d5be91bae2.png)
![image](https://user-images.githubusercontent.com/87576995/194871921-963eb8de-035f-411e-8351-7009900a5574.png)


2. Запустить Anaconda Prompt от имени администратора. Устанавливаем ML агента и pytorch в созданный в этом же шаге environment

Получаем это чудо 

(base) C:\Windows\system32>conda create -n MlAgent python=3.6.13

Proceed ([y]/n)? y

(base) C:\Windows\system32>conda activate MlAgent

потом это. очень многострадальное

![image](https://user-images.githubusercontent.com/87576995/195120984-8f1df58e-4198-4ee3-95a9-6c9d6d6b285e.png)

3. Возвращаемся в Unity. Создаем куб, сферу и плоскость. Перемещаем их в пространстве. Раскрашиваем их с помощью создания Материалов. Перемещаем объекты в Иерархии в Целевую область

![image](https://user-images.githubusercontent.com/87576995/197004569-c24df43a-0bcd-44b8-a9a8-06136309ef99.png)


4. Добавляем компоненты к шарику(roller_agent'у): RigidBody, Script(пишем код* прямо там), Decision Requister, Behavioural Parameters

![Uploading image.png…]()


*Код реализации:
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Unity.MLAgents;
using Unity.MLAgents.Sensors;
using Unity.MLAgents.Actuators;

public class roller_agent : Agent

{
    Rigidbody rBody;
    // Start is called before the first frame update
    void Start()
    {
        rBody = GetComponent<Rigidbody>();
    }

    public Transform Target;
    public override void OnEpisodeBegin()
    {
        if (this.transform.localPosition.y < 0)
        {
            this.rBody.angularVelocity = Vector3.zero;
            this.rBody.velocity = Vector3.zero;
            this.transform.localPosition = new Vector3(0, 0.5f, 0);
        }

        Target.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);
    }
    public override void CollectObservations(VectorSensor sensor)
    {
        sensor.AddObservation(Target.localPosition);
        sensor.AddObservation(this.transform.localPosition);
        sensor.AddObservation(rBody.velocity.x);
        sensor.AddObservation(rBody.velocity.z);
    }
    public float forceMultiplier = 10;
    public override void OnActionReceived(ActionBuffers actionBuffers)
    {
        Vector3 controlSignal = Vector3.zero;
        controlSignal.x = actionBuffers.ContinuousActions[0];
        controlSignal.z = actionBuffers.ContinuousActions[1];
        rBody.AddForce(controlSignal * forceMultiplier);

        float distanceToTarget = Vector3.Distance(this.transform.localPosition, Target.localPosition);

        if(distanceToTarget < 1.42f)
        {
            SetReward(1.0f);
            EndEpisode();
        }
        else if (this.transform.localPosition.y < 0)
        {
            EndEpisode();
        }
    }
}

5. Скачиваем файл rollerball_config.yaml в папку с Unity проектом

6. В Anaconda prompt продолжаем. Пишем 
(MlAgent) C:\Users\rosalie>cd C:\Users\rosalie\Lab3
(MlAgent) C:\Users\rosalie\Lab3>mlagents-learn rollerball_config.yaml --run-id=RollerBall --resume
    
7. Мы начали обучение модели. Нужно подождать еще немного времени...
8. Модель обучилась и теперь шар более ловко катится за кубом

## Задание 2
1.


## Задание 3


## Выводы
Я научилась заставлять работать МЛ агента(после стольких усилий только "заставляла" и подходит..), который учит шарик RollerAgent подкатываться к кубу Target 
    
    
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
