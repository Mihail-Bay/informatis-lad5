# Отчет по лабораторной работе 5
---
## Введение
---
### В данной лабораторной работе мы изучили основные команды Git, работу с ветками, разрешение конфликтов, а также использование Git Hooks и Git Flow для автоматизации процессов разработки.
---
## Задание 1 - Автоматизация проверки формата файлов при коммите
Создал bash-скрипт для проверки формата .txt файлов перед коммитом. Скрипт проверяет наличие файлов .txt и наличие текста в конце файла:

```bash
#!/bin/bash

# Флаг для отслеживания статуса проверки
all_files_valid=true

# Проверяем все .txt файлы, которые будут добавлены к коммиту
for file in $(git diff --cached --name-only | grep '\.txt$'); do
    # Проверяем, что файл не пустой
    if [[ ! -s "$file" ]]; then
        echo "Ошибка: Файл '$file' пустой."
        all_files_valid=false
        continue
    fi

done

echo "Все проверки прошли успешно. Можно коммитить."
exit 0
```

Скрипт был помещен в папку .git/hooks/pre-commit. Теперь перед каждым коммитом выполняется проверка.

![image](https://github.com/user-attachments/assets/3341e0b3-6ae7-4dd5-b876-ca3c29b9802c)

---
## Задание 2 - Использование Git Flow в проекте

Убедился, что Git Flow установлен, и инициализировал его:
```bash
git flow init
```

Создал ветку для новой функциональности task-management:
```bash
git flow feature start task-management
```

Внес изменения в файл task_manager.py и закоммитил их:
```
git add task_manager.py
git commit -m "Добавлен функционал управления задачами"
```

Завершил фичу и объединил ее с основной веткой:
```bash
git flow feature finish task-management
```

Создал релиз:
```bash
git flow release start v1.0.0
echo "v1.0.0" > version.txt
git add version.txt
git commit -m "Обновлена версия для релиза v1.0.0"
git flow release finish v1.0.0
```

Создал hotfix:
```bash
git flow hotfix start hotfix-1.0.1
# Исправление ошибки
git add file_with_error.py
git commit -m "Исправлена критическая ошибка"
git flow hotfix finish hotfix-1.0.1
```

### Завершение работы
Отправил изменения на удаленный репозиторий:
```bash
git push origin develop
git push origin main
```
## Заключение

В ходе выполнения лабораторной работы я освоил основные команды Git, научился работать с ветками, разрешать конфликты, а также использовать Git Hooks и Git Flow для улучшения процесса разработки. Все шаги были успешно выполнены, и изменения были отправлены на удаленный репозиторий.
