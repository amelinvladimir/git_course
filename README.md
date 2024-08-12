# Описание процесса работа с git репозиторием. Показан полный цикл работы с задачей.

На примере проекта https://github.com/amelinvladimir/git_course 

## Скачать проект
Получаем адрес для скачивания:
![image](https://github.com/user-attachments/assets/767a19fe-17d6-4686-98c6-0cf187b8aa90)


### Команды git командной строки
```console
#скачиваем проект
git clone git@github.com:amelinvladimir/git_course.git

# переходим в папку с проектом
cd git_course # переходим в папку с проектом
```

## Создать ветку и переключиться на нее
### Команды git командной строки
```console
#  создаем новую ветку
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



Если нужно срочно переключиться на другую ветку, а в рабочей есть не закоммиченные изменения
Команды git командной строки

Plugin git vscode


В рабочую ветку накатить коммиты из основной, если в рабочей ветке все закоммичено
Команды git командной строки

Plugin git vscode


В рабочую ветку накатить коммиты из основной, если в рабочей ветке не все закоммичено
Команды git командной строки

Plugin git vscode


Создать merge request
Команды git командной строки

Plugin git vscode


