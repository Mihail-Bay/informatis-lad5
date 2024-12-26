# Отчет по лабораторной работе 5

## Введение

### В данной лабораторной работе мы изучили основные команды Git, работу с ветками, разрешение конфликтов, а также использование Git Hooks и Git Flow для автоматизации процессов разработки.

Шаги выполнения лабораторной работы:
1. Создание репозитория на GitHub
Создал новый репозиторий с именем git-practice в своей учетной записи на GitHub.
Скопировал URL репозитория.
2. Клонирование репозитория
В терминале выполнил следующие команды для клонирования репозитория:

git clone <URL-репозитория>
cd git-practice
3. Добавление файла
Создал файл example.txt с текстом, описывающим структуру книги, и добавил его в репозиторий:

git add example.txt
git commit -m "File added example.txt"
git push origin main
4. Создание ветки
Создал новую ветку feature-branch и переключился на нее:

git branch feature-branch
git checkout feature-branch
Отредактировал файл example.txt, добавив дополнительный текст, и закоммитил изменения:

git add example.txt
git commit -m "Добавлен текст в example.txt"
git push origin feature-branch
5. Слияние изменений
Переключился обратно на основную ветку и выполнил слияние:

git checkout main
git merge feature-branch
git push origin main
6. Работа с ветками
Создал новый текстовый файл с базовой структурой книги и создал ветку feature-login:

git checkout -b feature-login
Отредактировал файл, добавив новую главу, и закоммитил изменения:

git add example.txt
git commit -m "Добавлена глава 3: Вход в систему"
git push origin feature-login
7. Работа с удаленным репозиторием
Переключился на основную ветку и внес изменения в файл:

git checkout main
# Изменил содержимое файла
git add example.txt
git commit -m "Изменено название книги и введение"
git push origin main
8. Моделирование конфликта
Вернулся в ветку feature-login и внес изменения в ту же часть файла, что и в основной ветке:

git checkout feature-login
# Изменил главу 2
git add example.txt
git commit -m "Добавлен раздел о магии конфликтов"
git push origin feature-login
9. Разрешение конфликта
Переключился на основную ветку и попытался слить изменения:

git checkout main
git pull origin main
При этом возник конфликт, который был разрешен вручную. Я оставил нужные изменения и закоммитил их:

git add example.txt
git commit -m "Resolved conflict in chapter 2"
git push origin main
Задание 1 - Автоматизация проверки формата файлов при коммите
Создал bash-скрипт для проверки формата .txt файлов перед коммитом. Скрипт проверяет наличие файлов .txt и наличие текста в конце файла:

#!/bin/bash
for file in *.txt; do
  if [[ ! -s "$file" ]]; then
    echo "Ошибка: файл $file пустой!"
    exit 1
  fi
done
Скрипт был помещен в папку .git/hooks/pre-commit. Теперь перед каждым коммитом выполняется проверка.

Задание 2 - Использование Git Flow в проекте
Убедился, что Git Flow установлен, и инициализировал его:

git flow init
Создал ветку для новой функциональности task-management:

git flow feature start task-management
Внес изменения в файл task_manager.py и закоммитил их:

git add task_manager.py
git commit -m "Добавлен функционал управления задачами"
Завершил фичу и объединил ее с основной веткой:

git flow feature finish task-management
Создал релиз:

git flow release start v1.0.0
echo "v1.0.0" > version.txt
git add version.txt
git commit -m "Обновлена версия для релиза v1.0.0"
git flow release finish v1.0.0
Создал hotfix:

git flow hotfix start hotfix-1.0.1
# Исправление ошибки
git add file_with_error.py
git commit -m "Исправлена критическая ошибка"
git flow hotfix finish hotfix-1.0.1
Завершение работы
Отправил изменения на удаленный репозиторий:

git push origin develop
git push origin main
Заключение
В ходе выполнения лабораторной работы я освоил основные команды Git, научился работать с ветками, разрешать конфликты, а также использовать Git Hooks и Git Flow для улучшения процесса разработки. Все шаги были успешно выполнены, и изменения были отправлены на удаленный репозиторий.
