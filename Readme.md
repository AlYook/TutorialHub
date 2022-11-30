# Инструкция для работы с Git и удалёнными репозиториями

## Что такое Git?
Git - это одна из реализаций распределённых систем контроля версий, имеющая как и локальные, так и удалённые репозитории. Является самой популярной реализацией систем контроля версий в мире.

## Подготовка репозитория
Для создание репозитория необходимо выполнить команду *git init*  в папке с репозиторием и у Вас создаться репозиторий (появится скрытая папка .git)

## Создание коммитов

### Git add
Для добавления измений в коммит используется команда *git add*. Чтобы использовать команду *git add* напишите *git add <имя файла>*

### Просмотр состояния репозитория
Для того, чтобы посмотреть состояние репозитория используется команда *git status*. Для этого необходимо в папке с репозиторием написать *git status*, и Вы увидите были ли измения в файлах, или их не было.

### Создание коммитов
Для того, чтобы создать коммит(сохранение) необходимо выполнить команду *git commit*. Выполняется она так: *git commit -m "<сообщение к коммиту>*. Все файлы для коммита должны быть ***ДОБАВЛЕНЫ*** и сообщение к коммиту писать ***ОБЯЗАТЕЛЬНО***.

## Перемещение между сохранениями
Для того, чтобы перемещаться между коммитами, используется команда *git checkout*. Используется она в папке с пепозиторием следующим образом: *git checkout <номер коммита>*

## Журнал изменений
Журнал изменений — это файл, который содержит общий, хронологически упорядоченный список изменений, внесенных в проект. Он часто организован по версии с указанием даты, после чего следует список добавленных, переработанных и удаленных функций.

Команда *git log* показывает список всех выполненных коммитов, отсортированных по дате добавления (сверху самые последние).

## Просмотр индексированных и неиндексированных изменений
Мы можем переключаться между зафиксированными состояниями. Более того, можно посмотреть разницу между текущим и зафиксированным
состоянием файла. Например, мы сделали **commit**. После внесли какие-то изменения, и можем
с помощью команды **_git diff_** (от difference — разница) посмотреть, а чем же отличается файл,
отредактированный сейчас, от файла, сохранённого с помощью **git commit**.

Например, как это наглядно выглядит: ![Пример](GitDiff.png)

## Игнорирование файлов
Git рассматривает каждый файл в вашей рабочей копии как файл одного из трех нижеуказанных типов.

* Отслеживаемый файл — файл, который был предварительно проиндексирован или зафиксирован в коммите.
* Неотслеживаемый файл — файл, который не был проиндексирован или зафиксирован в коммите.
* Игнорируемый файл — файл, явным образом помеченный для Git как файл, который необходимо игнорировать.

Зачастую, у вас имеется группа файлов, которые вы не только не хотите автоматически добавлять в репозиторий, но и видеть в списках неотслеживаемых. К таким файлам обычно относятся автоматически генерируемые файлы (различные логи, результаты сборки программ и т.п.). В таком случае, вы можете создать файл **.gitignore** и указать в нем новые файлы, которые должны быть проигнорированы.

Подробнее о игнорировании файлов можно прочитать здесь [gitignore](https://www.atlassian.com/ru/git/tutorials/saving-changes/gitignore#:~:text=gitignore%20%2C%20%D1%87%D1%82%D0%BE%D0%B1%D1%8B%20%D1%83%D0%BA%D0%B0%D0%B7%D0%B0%D1%82%D1%8C%20%D0%B2%20%D0%BD%D0%B5%D0%BC,%D0%BE%D0%BF%D1%80%D0%B5%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D1%8F%20%D0%BD%D0%B5%D0%BE%D0%B1%D1%85%D0%BE%D0%B4%D0%B8%D0%BC%D0%BE%D1%81%D1%82%D0%B8%20%D0%B8%D0%B3%D0%BD%D0%BE%D1%80%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D1%82%D1%8C%20%D1%8D%D1%82%D0%B8%20%D1%84%D0%B0%D0%B9%D0%BB%D1%8B.)

## Ветки в Git
Ветка (branch) — это история коммитов.
Имя основной ветки Git-проекта по умолчанию — master. Она появляется сразу при инициализации репозитория. Эта ветка ничем не отличается от остальных и также ее можно переименовать, но по договоренности master принято считать главной веткой в проекте.
### Создание ветки
Для того, чтобы создать ветку, используется команда *git branch*. Делается это следующим образом в папке с репозиторием: *git branch <название новой ветки>*

Для преремещения между ветками используется команда *git checout <название ветки>*

### Слияние веток
Для того, чтобы переместить ветку в основную (master) или любую другую ветку, используется команда *git merge <имя перемещаемой ветки>*

Операция может привести к появлению **конфликтов** при попытке слить ветки. Это вызвано тем, что изменения удаляют или переписывают информацию в существующих файлах. При попытке некорректного слияния Git останавливает выполнение команды, чтобы вы могли разрешить конфликт.

Решить конфликт можно двумя способами:
* Вручную разрешить файловый конфликт. Для этого нужно самим изменить файлы, с которыми возникли проблемы. Мы получим файлы такими, какими и представляли их при попытке слияния.
* Выбрать более подходящий файл, а от второго отказаться.

После решения конфликта необходимо закоммитить измененния.

### Переименование веток
Чтобы переименовать ветку применяем:
*git branch -m <новое имя ветки>*

### Удаление веток
С операцией удаления над ветками справляется уже привычная команда git branch с параметром -d: *git branch -d <имя ветки>*

Для корректного удаления нужно помнить несколько правил, чтобы не получить ошибки:

* Нельзя удалить ветку, в которой вы находитесь. Git выкинет ошибку и не произведет удаление. Следовательно, нужно перейти на другую ветку.
* Git не позволит удалить ветку, у которой есть несохраненные изменения. Так мы избегаем ситуации, когда часть написанного кода будет безвозвратно утеряна. Если же мы уверены, что изменения в этой версии не нужны и их можно смело удалять, то вместо флага -d используем -D: *git branch -D <имя ветки>*

## GitHub

**GitHub** — это сервис компании Microsoft, который позволяет интегрироваться с
программой Git и настроить удалённую работу с вашим репозиторием.

## git push
Эта команда позволяет отправить то, что есть на нашем репозитории, на удалённый
репозиторий. Требует авторизации. Если у нас нет прав на внесение изменений в
репозиторий, Git не позволит это делать. На слайде команда указана в усечённом виде,
она так работает, когда всё настроено. Если ещё не до конца всё настроено, Git
подскажет, как сделать это правильно. Там будет параметр set upstream origin и прочие
параметры, которые потребуется указать, Git расскажет об этом.

## git pull
Эта команда позволяет скачать всё актуальное из нашего удалённого репозитория.
Мы указываем программу git и параметр pull. Она позволяет
получить из GitHub актуальное состояние удалённого репозитория и скачать его на
наш репозиторий. Обратите внимание, что pull — составная команда. Помимо
выкачивания из интернета, она ещё и мержит, то есть сливает, изменения с нашими.
Если возникают какие-то конфликты, то окошко будет таким же, как при конфликтах
обычного git merge. То есть коменда состоит из двух частей: первая часть скачивает
изменения с удалённого репозитория, а вторая — сливает эти изменения с текущим
репозиторием.

### Pull request
1. Делаем форк (fork) интересующего нас репозитория.
2. Делаем git clone для нашей версии этого репозитория. Так появляется версия на нашем
аккаунте, и именно эту версию мы клонируем.
3. Создаём ветку с предлагаемыми изменениями.
4. Производим все изменения только в этой ветке.
5. Отправляем эти изменения на свой аккаунт (push).
6. В окне на GitHub появляется возможность отправить pull request.
