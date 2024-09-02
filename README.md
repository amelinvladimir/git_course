# Описание процесса работа с git репозиторием. Показан полный цикл работы с задачей.

На примере проекта https://github.com/amelinvladimir/git_course 

## Шаг 1. Скачать проект
Получаем адрес для скачивания:
![image](https://github.com/user-attachments/assets/767a19fe-17d6-4686-98c6-0cf187b8aa90)


### Команды git командной строки
```console
# скачиваем проект
git clone git@github.com:amelinvladimir/git_course.git

# переходим в папку с проектом
cd git_course # переходим в папку с проектом
```

### Скачать еще одну ветку из внешнего репозитория

Чтобы скачать ветку developer из внешнего репозитория и переключиться на нее выполняем команды:
```console
# скачиваем ветку developer
git checkout -b developer origin/developer
branch 'developer' set up to track 'origin/developer'.
Переключились на новую ветку «developer»

# переключаемся на ветку developer
git checkout developer
```

## Шаг 2. Создать ветку и переключиться на нее
### Команды git командной строки
```console
# создаем новую ветку
git branch IDVP-555

# переключаемся в новую ветку
git checkout IDVP-555
```

### Plugin git vscode
![image](https://github.com/user-attachments/assets/1f16de2f-05b1-45b6-90e9-d739113ac34f)
Указываем от какой ветки делаем ответвление
![image](https://github.com/user-attachments/assets/1060cbde-0fe3-4317-b9c6-93f114bb1156)
Указываем название новой ветки
![image](https://github.com/user-attachments/assets/5f83396f-1d05-46fd-a1e9-00b6c3f26144)


## Шаг 3 (опциональный). Если нужно срочно переключиться на другую ветку, а в рабочей есть не закоммиченные изменения
Используется команда [git stash](https://git-scm.com/docs/git-stash)

### Команды git командной строки
Для демонстрации в ветке IDVP-555 один файл был изменен (model1.sql), один файл был удален (model2.sql) и один файл был создан (model3.sql).

Посмотрим текущие локальные не закоммиченные изменения командой git status: 
```console
git status
Текущая ветка: IDVP-555
Изменения, которые не в индексе для коммита:
  (используйте «git add/rm <файл>...», чтобы добавить или удалить файл из индекса)
  (используйте «git restore <файл>...», чтобы отменить изменения в рабочем каталоге)
	изменено:      model1.sql
	удалено:       model2.sql

Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	model3.sql

индекс пуст (используйте «git add» и/или «git commit -a»)
```

Сохраняем локальные изменения без коммита с помощью команды git stash:
```console
git stash push -m 'Начал добавлять расчет 2 показателей'
Рабочий каталог и состояние индекса сохранены On IDVP-555: Начал добавлять расчет 2 показателей
```

Видим, что изменения файла model1.sql отменено и удаленный файл model2.sql восстановлен. Созданный файл model3.sql остался без изменений.
```console
git status
Текущая ветка: IDVP-555
Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	model3.sql

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)
```

Теперь можно переключиться на другую ветку и не беспокоиться о том, что изменения будет утеряны
```console
git checkout main 
```

После того, как будут внесены нужные правки в ветку main и сделаны нужные коммиты, можно переключиться обратно в ветку IDVP-555.
```console
git checkout IDVP-555 
```

Командой git stash list смотрим, какие есть сохраннные состояния. Мы сохранили только одно состояние и его видим в списке:
```console
git stash list
stash@{0}: On IDVP-555: Начал добавлять расчет 2 показателей
```

Восстанавливаем изменения:
```console
git stash pop        
Текущая ветка: IDVP-555
Изменения, которые не в индексе для коммита:
  (используйте «git add/rm <файл>...», чтобы добавить или удалить файл из индекса)
  (используйте «git restore <файл>...», чтобы отменить изменения в рабочем каталоге)
	изменено:      model1.sql
	удалено:       model2.sql

Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	model3.sql

индекс пуст (используйте «git add» и/или «git commit -a»)
Отброшено refs/stash@{0} (1446235384fa6de4881300c9febe549fedb12510)
```

### Plugin git vscode

Для демонстрации в ветке IDVP-555 один файл был изменен (model1.sql), один файл был удален (model2.sql) и один файл был создан (model3.sql).

Сохраняем локальные изменения без коммита.
![image](https://github.com/user-attachments/assets/5aa14626-9676-469f-8215-310753d85318)

Вводим сообщение о скрытии, поясняющее, какие изменения в него входят и жмем enter. Не закоммиченные изменения спрятаны.
![image](https://github.com/user-attachments/assets/e60d4009-497d-45d2-bd83-9e462832070a)

Теперь можно переключиться на другую ветку и не беспокоиться о том, что изменения будет утеряны:
![image](https://github.com/user-attachments/assets/2ad30f26-d216-469e-bb66-c8a9df33eaf8)

После того, как будут внесены нужные правки в ветку main и сделаны нужные коммиты, можно переключиться обратно в ветку IDVP-555.
![image](https://github.com/user-attachments/assets/b1c70673-bd88-4a05-8fbb-1e212953ca77)

Восстанавливаем изменения
![image](https://github.com/user-attachments/assets/c2d64bd5-3e99-4060-a7eb-8fb7bd6d2f1c)

Восстановлено состояние всех файлов, в том числе не закоммиченных. Можно продолжать работу.


## Шаг 4. В рабочую ветку накатить коммиты из основной, если в рабочей ветке все закоммичено
Пока мы в своей ветке IDVP-555 делали свою задачу, наши коллеги добавили коммитов в базовую ветку main (обычно надо брать коммиты из developer). Теперь нам надо перенести эти коммиты в свою ветку. Возможны 2 варианты - изменения коллег и наши изменеия - будут или не будут пересекаться.

### Команды git командной строки
Убеждаемся, что мы в ветке IDVP-555
```console
git branch

* IDVP-555
  main
```

Выполняем команду переноса изменений одной ветки в другую. Если в файлах нет пересекающихся изменений, то мы увидим сообщение об успешном переносе изменений, как в привемере:
```console
git merge main

Обновление 5c407c5..80ab750
Fast-forward
 README.md | 153 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 1 file changed, 153 insertions(+)
 create mode 100644 README.md
```

Теперь сделаем в одном файле пересекающиеся изменения в 2 ветках, а затем перенесем изменения из одной ветки в другую. 

Для этого сначала переходим в ветку main:
```console
git checkout main
```

Меняем содержимое файла model4.sql:
```console
select 4;
```

на:
```console
select 4;
# some comment 1
```
то есть мы добавили в файл model4.sql комментарий в последней строке.

сохраняем коммит:
```console
git add model4.sql
git commit -m 'added comment 1 to model4'
```

Переключаемся на ветку IDVP-555
```console
git checkout IDVP-555
```
Меняем содержимое файла model4.sql с 
```console
select 4;
```

на
```console
select 4;
# some comment 2
```

сохраняем коммит:
```console
git add model4.sql
git commit -m 'added comment 2 to model4'
```

переносим изменения из ветки main в ветку IDVP-555:
```console
git merge main
```

и видим сообщение о появившемся конфликте, который нужно разрешить:
```console
Автослияние model4.sql
КОНФЛИКТ (содержимое): Конфликт слияния в model4.sql
Сбой автоматического слияния; исправьте конфликты, затем зафиксируйте результат.
```

Открываем на редактирование файл model4.sql, чтобы разрешить конфликт:
```console
nano model4.sql
```

Меняем содержимое с:
```console
select 4;
# some comment 1
```

на следующее и сохраняем:
```console
select 4;
# some comment 1
# some comment 2
```

Формируем коммит с файлом с разрешенным конфликтом:
 ```console
 git add model4.sql
 git commit
 ```

Перенос изменений из ветки main в ветку IDVP-555 успешно завершен.

### Plugin git vscode



## Отправить свою рабочую ветку во внешний репозиторий и создать merge request:

### Команды git командной строки
Проверяем, что находимся в ветке IDVP-555
```console
git branch

* IDVP-555
  main
```

Если находимся не в IDVP-555, то переключаемся на нее командой:
```console
git checkout IDVP-555
```

Публикуем рабочую ветку IDVP-555 в gitlab
```console
git push --set-upstream origin IDVP-555

Перечисление объектов: 46, готово.
Подсчет объектов: 100% (46/46), готово.
При сжатии изменений используется до 8 потоков
Сжатие объектов: 100% (38/38), готово.
Запись объектов: 100% (43/43), 5.25 КиБ | 1.05 МиБ/с, готово.
Всего 43 (изменений 15), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: Resolving deltas: 100% (15/15), completed with 1 local object.
remote: 
remote: Create a pull request for 'IDVP-555' on GitHub by visiting:
remote:      https://github.com/amelinvladimir/git_course/pull/new/IDVP-555
remote: 
To github.com:amelinvladimir/git_course.git
 * [new branch]      IDVP-555 -> IDVP-555
branch 'IDVP-555' set up to track 'origin/IDVP-555'.
```

Переходим по указанной в сообщении ссылке (https://github.com/amelinvladimir/git_course/pull/new/IDVP-555), чтобы создать merge request.

### Plugin git vscode
![iScreen Shoter - Code - 240902192701](https://github.com/user-attachments/assets/3eb0d840-35a3-4f31-a29a-1b77734794c2)

![iScreen Shoter - Code - 240902192748](https://github.com/user-attachments/assets/3407f051-7047-4113-93dd-ffbe8d632168)




Создать merge request
Команды git командной строки

Plugin git vscode


