# Инструкции

Сюда размещаем различные инструкции по сборке и развертыванию приложения. А так же различные гайды.

## Использование языков

Язык комментариев, инструкций, задач, коммитов - русский.
Название веток - английский.

## Code style

https://github.com/yandex/codestyle/blob/master/javascript.ru.md

## Стараемся комментировать свой код

## Работа с git

Каждую задачу делаем на свое ветке. Ветка именуется: `(номер задачи)_краткое-описание`, например `2_add-new-message-api`

Каждый коммит начинается с #номер задачи, например #4 - коммит по 4 задаче. Когда заканчиваем задачу, последний коммит должен быть close #4

## Настройка и запуск
В системе должны быть установлены
- mongodb - должна быть запущена
- npm

Сборка
- npm i

Запуск
- дев сборка ``npm run dev``
- прод сборка ``npm run prod``

Деплой на прод сервер:
- подключить репозиторий git remote add live ssh://root@IP/root/shri/production.git
- деплой git push live master
- сервер поднимится не сразу. Он сначала должен собраться

Развертка прод сервера
- сервер не ниже 1Gb ram
- Distributions: ubuntu 14.04
- Applications: node v4.1.0 on 14.04
- ставим галочку 'User Data' и туда вставляем содержимое файла cloud-init
- добавляем ssh ключи
- запускаем создание droplet
- после создания нужно поменять адрес webhook в проекте https://github.com/ya-shred/production/settings/hooks/6036173
- поменять адреса callback при гит авторизации https://github.com/organizations/ya-shred/settings/applications/250785

Для деплоя на heroku
- git remote add heroku https://git.heroku.com/shri-production.git
- git push heroku master

Для запуска тестов
- npm test
- для дебага тестов. Нужно поменять в karma.conf.js параметр singleRun на false