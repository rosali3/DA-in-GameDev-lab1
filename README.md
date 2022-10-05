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

7. Скачиваем gspread и numpy в PyCharm'e и начинаем писать код*(в коде вставляем ссылку из гугл таблиц и этим связываем эти два элемента)
![image](https://user-images.githubusercontent.com/87576995/194025966-37d443a5-a427-4e73-a582-8d5541c9d247.png)
![image](https://user-images.githubusercontent.com/87576995/194026029-591b1be5-2657-485c-97c1-690a25a95e19.png)

8. Создаем API ключ в гугл клауде. Сужая его до API ключа к гугл таблицам. Дать редакторские права в гугл таблицах этому ключу

9. Создаем новый проект в Unity
![image](https://user-images.githubusercontent.com/87576995/194028559-40154893-a19a-47e7-9329-591d3ce6bd1f.png)

9.1 Скачиваем jsonPackage и soundPackage из предоставленного яндекс диска и вставляем их в Assets
9.2 Создаем пустоту и добавляем к ней AudioSource
9.3 Создаем C# код** в папке с JSON script
9.4 Связываем наш код в VSCode через Unity c Google Sheets
![image](https://user-images.githubusercontent.com/87576995/194029669-62b38ddc-ff8c-4da9-a79b-bfed241a6f3a.png)
9.5 Добавляем к коду связку со звуком
![image](https://user-images.githubusercontent.com/87576995/194030293-3cd11895-d5a5-4281-a43f-d76c6dc4fb01.png)
9.6 Добавляем к свойствам нашей пустоты в Unity звук из папочки
![image](https://user-images.githubusercontent.com/87576995/194030783-994ed01e-7f41-429a-aa40-d83075915227.png)

10. Слушаем как нами восхищаются и доверяют, а главное называют "Мой Лорд"






*Код реализации:
import gspread
import numpy as np
gc = gspread.service_account(filename='unitydatascience-364410-a6cc42f0950f.json')
sh = gc.open("UnitySheets")
price = np.random.randint(2000, 10000, 11)
mon = list(range(1,11))
i = 0
while i <= len(mon):
    i += 1
    if i == 0:
        continue
    else:
        tempInf = ((price[i-1]-price[i-2])/price[i-2])*100
        tempInf = str(tempInf)
        tempInf = tempInf.replace('.',',')
        sh.sheet1.update(('A' + str(i)), str(i))
        sh.sheet1.update(('B' + str(i)), str(price[i-1]))
        sh.sheet1.update(('C' + str(i)), str(tempInf))
        print(tempInf)

**Код реализации:

using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Networking;
using SimpleJSON;

public class NewBehaviourScript : MonoBehaviour
{
    public AudioClip goodSpeak;
    public AudioClip normalSpeak;
    public AudioClip badSpeak;
    private AudioSource selectAudio;
    private Dictionary<string,float> dataSet = new Dictionary<string, float>();
    private bool statusStart = false;
    private int i = 1;

    // Start is called before the first frame update
    void Start()
    {
        StartCoroutine(GoogleSheets());
    }

    // Update is called once per frame
    void Update()
    {
        if (dataSet["Mon_" + i.ToString()] <= 10 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlaySelectAudioGood());
            Debug.Log(dataSet["Mon_" + i.ToString()]);
        }

        if (dataSet["Mon_" + i.ToString()] > 10 & dataSet["Mon_" + i.ToString()] < 100 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlaySelectAudioNormal());
            Debug.Log(dataSet["Mon_" + i.ToString()]);
        }

        if (dataSet["Mon_" + i.ToString()] >= 100 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlaySelectAudioBad());
            Debug.Log(dataSet["Mon_" + i.ToString()]);
        }
    }

    IEnumerator GoogleSheets()
    {
        UnityWebRequest curentResp = UnityWebRequest.Get("https://sheets.googleapis.com/v4/spreadsheets/1Sz9BsfX-8dUDcynBBLGFBrbVgDm_uDcsKRwHNK5sst0/values/Лист1?key=AIzaSyDvgaykBBgwOgeFnunpDX0SdtaceZ5NLLU");
        yield return curentResp.SendWebRequest();
        string rawResp = curentResp.downloadHandler.text;
        var rawJson = JSON.Parse(rawResp);
        foreach (var itemRawJson in rawJson["values"])
        {
            var parseJson = JSON.Parse(itemRawJson.ToString());
            var selectRow = parseJson[0].AsStringList;
            dataSet.Add(("Mon_" + selectRow[0]), float.Parse(selectRow[2]));
        }
    }

    IEnumerator PlaySelectAudioGood()
    {
        statusStart = true;
        selectAudio = GetComponent<AudioSource>();
        selectAudio.clip = goodSpeak;
        selectAudio.Play();
        yield return new WaitForSeconds(3);
        statusStart = false;
        i++;
    }
    IEnumerator PlaySelectAudioNormal()
    {
        statusStart = true;
        selectAudio = GetComponent<AudioSource>();
        selectAudio.clip = normalSpeak;
        selectAudio.Play();
        yield return new WaitForSeconds(3);
        statusStart = false;
        i++;
    }
    IEnumerator PlaySelectAudioBad()
    {
        statusStart = true;
        selectAudio = GetComponent<AudioSource>();
        selectAudio.clip = badSpeak;
        selectAudio.Play();
        yield return new WaitForSeconds(4);
        statusStart = false;
        i++;
    }
}




## Задание 2
1. Смешать код с третьего задания первой лабораторной работы и первого задания второй 

![image](https://user-images.githubusercontent.com/87576995/194128840-696f536b-404f-4704-86d4-b830261fa96a.png)


***Код реализации:
{import gspread
import numpy as np
x = [3,21,22,34,54,34,55,67,89,99]
x = np.array(x)
y = [2,22,24,65,79,82,55,130,150,199]
y = np.array(y)
def model(a, b, x):
    return a*x + b
#The most commonly used loss function of linear regression model is the loss function of mean variance difference
def loss_function(a, b, x, y):
    num = len(x)
    prediction=model(a,b,x)
    return (0.5/num) * (np.square(prediction-y)).sum()

def optimize(a,b,x,y):
    num = len(x)
    prediction = model(a,b,x)
    da = (1.0/num) * ((prediction -y)*x).sum()
    db = (1.0/num) * ((prediction -y).sum())
    a = a - Lr*da
    b = b - Lr*db
    return a, b

def iterate(a,b,x,y,times):
    for i in range(times):
        a,b = optimize(a,b,x,y)
    return a,b

gc = gspread.service_account(filename='unitydatascience-364410-a6cc42f0950f.json')
sh = gc.open("UnitySheets")
mon = list(range(1,11))

a = np.random.rand(1)
print(a)
b = np.random.rand(1)
print(b)
Lr = 0.000001


i = 0
while i <= len(mon):
    i += 1
    if i == 0:
        continue
    else:
        a, b = iterate(a, b, x, y, 100)
        loss = loss_function(a, b, x, y)
        tempInf = str(loss)
        tempInf = tempInf.replace('.',',')
        sh.sheet1.update(('A' + str(i)), str(i))
        sh.sheet1.update(('B' + str(i)), str(tempInf))
        print(tempInf)
}




## Задание 3

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
