#Навигация
`pwd` (от англ. print working directory, «показать рабочую папку») — покажи, в какой я папке;
`ls` (от англ. list directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;
`ls -a` — покажи также скрытые файлы и папки, названия которых начинаются с символа .;
`cd first-project` (от англ. change directory, «сменить директорию») — перейди в папку first-project;
`cd first-project/html` — перейди в папку html, которая находится в папке first-project;
`cd ..` — перейди на уровень выше, в родительскую папку;
`cd ~` — перейди в домашнюю директорию (/Users/Username);
cd / — перейди в корневую директорию.

#Работа с файлами и папками
Создание
touch index.html (англ. touch, «коснуться») — создай файл index.html в текущей папке;
touch index.html style.css script.js — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;
mkdir second-project (от англ. make directory, «создать директорию») — создай папку с именем second-project в текущей папке.
Копирование и перемещение
cp file.txt ~/my-dir (от англ. copy, «копировать») — скопируй файл в другое место;
mv file.txt ~/my-dir (от англ. move, «переместить») — перемести файл или папку в другое место.
Чтение
cat file.txt (от англ. concatenate and print, «объединить и распечатать») — распечатай содержимое текстового файла file.txt.
Удаление
rm about.html (от англ. remove, «удалить») — удали файл about.html;
rmdir images (от англ. remove directory, «удалить директорию») — удали папку images;
rm -r second-project (от англ. remove, «удалить» + recursive, «рекурсивный») — удали папку second-project и всё, что она содержит.
Полезные возможности
Команды необязательно печатать и выполнять по очереди. Можно указать их списком — разделить двумя амперсандами (&&).
У консоли есть собственная память — буфер с несколькими последними командами. По ним можно перемещаться с помощью клавиш со стрелками вверх (↑) и вниз (↓).
Чтобы не вводить название файла или папки полностью, можно набрать первые символы имени и дважды нажать Tab. Если файл или папка есть в текущей директории, командная строка допишет путь сама.
Например, вы находитесь в папке dev. Начните вводить cd first и дважды нажмите Tab. Если папка first-project есть внутри dev, командная строка автоматически подставит её имя. Останется только нажать Enter.

Репозиторий
$ cd ~/dev/first-project # перешли в нужную папку
$ git init # создали репозиторий
"Разгитить" репозиторий:
$ cd <папка с репозиторием> # перешли в папку
$ rm -rf .git # удалили подпапку .git
git status — проверить статус репозитория

$ touch todo.txt
$ touch readme.txt
# создали файлы todo.txt и readme.txt
$ git status # проверили статус
$ git add todo.txt # подготовили к сохранению в репозитории
$ git add readme.txt
$ git status # проверили статус
(Альтернатива
$ git add . # добавить всю текущую папку
$ git status)
$ git commit -m 'Мой первый коммит!'
git log — история коммитов

Github
SSH-ключ
$ cd ~ # перешли в домашнюю директорию
$ ls -la .ssh/ # вывели список созданных ключей
$ ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"
(Альтернатива
$ ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан ваш аккаунт на GitHub")
> Enter a file in which to save the key (C:\Users\<имя_пользователя>\.ssh\):[Press enter] — место хранения ключей
ls -a ~/.ssh — проверка
Привязываем SSH-ключ к GitHub
# скопировать содержимое ключа в буфер обмена:
$ clip < ~/.ssh/id_rsa.pub
# для ed25519:
$ clip < ~/.ssh/id_ed25519.pub
Перейдите на GitHub и выберите пункт Settings (англ. «настройки») в меню аккаунта.
В меню слева нажмите на пункт SSH and GPG keys.
В открывшейся вкладке выберите New SSH key (англ. «новый SSH-ключ»).
В поле Title (англ. «заголовок») напишите название ключа. Например, Personal key (англ. «личный ключ»).
В поле Key type (англ. «тип ключа») должно быть Authentication Key (англ. «ключ аутентификации»).
В поле Key скопируйте ваш ключ из буфера обмена.8. Нажмите на кнопку Add SSH key (англ. «добавить SSH-ключ»).
Проверьте правильность ключа с помощью следующей команды.
$ ssh -T git@github.com

Связываем локальный и удалённый репозитории
Перейдите на страницу удалённого репозитория, выберите тип SSH и скопируйте URL.
$ cd ~/dev/first-project
$ git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git
Проверка:
$ git remote -v
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push)

Отправить изменения на удалённый репозиторий — git push
$ git push -u origin main # Если команда приведёт к ошибке, попробуйте 
                          # заменить main на master.
