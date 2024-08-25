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
Пока мы в своей ветке IDVP-555 делали свою задачу, наши коллеги добавили коммитов в базовую ветку main (обычно надо брать коммиты из developer). Теперь нам надо перенести эти коммиты в свою ветку. Возможны 2 варианты - изменения коллег и наши изменеия - не будут или будут пересекаться.

#### Команды git командной строки
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
# come comment 2
```
то есть мы добавили в файл model4.sql комментарий в последней строке.

сохраняем коммит:
```console
git add model4.sql
git commit -m 'added comment 2 to model4'
```

```console
```

```console
```

```console
```

```console
```


#### Plugin git vscode

В рабочую ветку накатить коммиты из основной, если в рабочей ветке не все закоммичено
Команды git командной строки

Plugin git vscode


Создать merge request
Команды git командной строки

Plugin git vscode


