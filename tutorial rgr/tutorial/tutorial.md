Tutorial po rgr ITS

1) Заходим в ВМ готовую в 3 лабе(Jenkins) и нажимаем ssh

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.001.png)

1) Устанавливаем git на Jenkins

Прописываем sudo apt install git

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.002.png)

1) Заходим в Jenkins и устанавливаем plugin git

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.003.png)

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.004.png)

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.005.png)

1) Далее заходим на главную страницу Jenkins и создаем новый Item

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.006.png)

Пишем название вашего проэкта(любое) и создаем задачу со свободной конфигурацией

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.007.png)

Далее переходим снова в ssh и генерируем ключи 1 для Jenkins 1 для github командой ssh-keygen

Получаем 2 ключа id\_rsa id\_rsa.pub

Чтобы их посмотреть нужно зайти в нужный репозиторий командой

cd .ssh а потом cat id\_rsa и cat id\_rsa.pub

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.008.png)

1) Ключ .pub мы вставляем в github

New ssh key, называем как то ключ и вставляем его

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.009.png)

1) Большой ключ добавляем в Jenkins следующим образом

Заходим в наш созданый item и нажимаем настройки

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.010.png)

Далее выбираем git и нажимаем Add

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.011.png)

После заполняем id и Description как вы хотите одинаково

Username заполняем точно также как логин в jenkins

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.012.png)

Далее в поле key нажимаем add и вставляем ключ id\_rsa

Начиная от -----BEGIN OPENSSH PRIVATE KEY----- и заканчивая -----END OPENSSH PRIVATE KEY----- и сохраняем

Далее заходим на github и копируем любой репозиторий созданый вами ранее

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.013.png)

И вставляем в Jenkins в созданый вами item 

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.014.png)

1) Дублируем ниже и выбираем свой ключ

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.015.png)

Выбираем данный триггер и сохраняем

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.016.png)

1) Далее выбираем ваш Item и собрать сейчас

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.017.png)

1) В левом нижнем углу видем выполнение нашего процеса

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.018.png)

1) Выбираем наш последний успех и выводим консоль( в моем случае №16) 

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.019.png)

![](Aspose.Words.e901261c-5e31-4bec-b670-5d816fe17e3c.020.png)

В консоле мы видим что консоль показало выполнение работы, и вывело сообщение krasivaya knopka,что соответствует моему репозиторию в github.

