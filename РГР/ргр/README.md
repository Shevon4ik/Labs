МІНІСТЕРСТВО ОСВІТИ І НАУКИ УКРАЇНИ

Національний аерокосмічний університет ім. М. Є. Жуковського «Харківський авіаційний інститут»

Факультет «Радіоелектроніки, комп’ютерних систем та інфокомунікацій» Кафедра «Аерокосмічних радіоелектронних систем»  









**Розрахунково – графічна робота**

з дисципліни «Інформаційно-комунікаційні мережі » 

на тему: «Відображення тексту з git репозиторія у Jenkins»



Виконав: студент 4 курсу групи № 536-ст напряму підготовки (спеціальності) 172 «Телекомунікації та радіотехніка»  Шевцов В.В

Прийняв: ас. каф. 501  

Перетятько М. С.  



Національна шкала:  

Кількість балів:  

Оцінка: ECTS  










Харків 2021 

**Ціль роботи:** Відобразити текст з git репозиторія у Jenkins.  

ХІД РОБОТИ 

1) Cтворюємо новий проект у GCP

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.001.png)

1) Створив VPC

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.002.png)

3)Створюємо віртуальну машину з операційною системою лінукс

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.003.png)

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.004.png)



\4) Виконуємо команди з сайта [https://www.jenkins.io/doc/book/installing/linux/#debianubuntu]()

А саме:




Встановлюємо Jenkins

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.005.png)

Оновлюємо репозиторій

sudo apt update

Встановлюємо openjdk

sudo apt install openjdk

Запустив службу Jenkins за допомогою команди:

sudo systemctl start jenkins

Розблукування Jenkins

![Unlock Jenkins page](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.006.jpeg)

Для цього пишемо команду sudo cat /var/lib/jenkins/secrets/initialAdminPassword і в командному вікні буде пароль

І ось ми маємо створений Jenkins

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.007.png)

5)Заходим в ВМ готовую в 3 лабе(Jenkins) и нажимаем ssh

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.008.png)

6)Устанавливаем git на Jenkins

Прописываем sudo apt install git

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.009.png)

7) Заходим в Jenkins и устанавливаем plugin git

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.010.png)

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.011.png)

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.012.png)

7) Далее заходим на главную страницу Jenkins и создаем новый Item

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.013.png)

Пишем название вашего проэкта(любое) и создаем задачу со свободной конфигурацией

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.014.png)

Далее переходим снова в ssh и генерируем ключи 1 для Jenkins 1 для github командой ssh-keygen

Получаем 2 ключа id\_rsa id\_rsa.pub

Чтобы их посмотреть нужно зайти в нужный репозиторий командой

cd .ssh а потом cat id\_rsa и cat id\_rsa.pub

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.015.png)

7) Ключ .pub мы вставляем в github

New ssh key, называем как то ключ и вставляем его

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.016.png)

7) Большой ключ добавляем в Jenkins следующим образом

Заходим в наш созданый item и нажимаем настройки

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.017.png)

Далее выбираем git и нажимаем Add

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.018.png)

После заполняем id и Description как вы хотите одинаково

Username заполняем точно также как логин в jenkins

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.019.png)

Далее в поле key нажимаем add и вставляем ключ id\_rsa

Начиная от -----BEGIN OPENSSH PRIVATE KEY----- и заканчивая -----END OPENSSH PRIVATE KEY----- и сохраняем

Далее заходим на github и копируем любой репозиторий созданый вами ранее

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.020.png)

И вставляем в Jenkins в созданый вами item 

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.021.png)

7) Дублируем ниже и выбираем свой ключ

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.022.png)

Выбираем данный триггер и сохраняем

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.023.png)

7) Далее выбираем ваш Item и собрать сейчас

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.024.png)

7) В левом нижнем углу видем выполнение нашего процеса

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.025.png)

7) Выбираем наш последний успех и выводим консоль( в моем случае №16) 

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.026.png)

![](Aspose.Words.122958ae-dabc-4adf-893e-bbcef754e65c.027.png)

В консоле мы видим что консоль показало выполнение работы, и вывело сообщение krasivaya knopka,что соответствует моему репозиторию в github.




Вывод

В расчетно – графической работе усвоил знания которые использовал в выполнении 3 лабороторной работе, а именно, работа с Jenkins. Так же научился привязывать git к Jenkins. Выполнил установку плагинов для работы Jenkins с git hub. Так же создал 2 вида ключей для связывания gita и Jenkins. Проверил работу jenkins с github, ошибок не получил.




