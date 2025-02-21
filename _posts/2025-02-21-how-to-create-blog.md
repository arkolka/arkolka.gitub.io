---
layout: post
title: "Как создать блог с Jekyll на GitHub Pages"
date: 2025-02-21
categories: Jekyll GitHub AI
comments: true
---

# Как создать блог с Jekyll на GitHub Pages

В мире технологий важно делиться знаниями и опытом. Один из лучших способов сделать это — вести блог. В этой статье мы разберем, как создать свой блог с помощью Jekyll и разместить его на GitHub Pages.

## 🔹 Почему Jekyll?

Jekyll — это статический генератор сайтов, который идеально подходит для блогов и документации. Он поддерживает Markdown, прост в использовании и интегрируется с GitHub Pages без необходимости сложных настроек.

## 🔹 Шаг 1: Установка Jekyll

Перед началом убедитесь, что у вас установлен Ruby. Если нет, скачайте [RubyInstaller](https://rubyinstaller.org/) (для Windows) или установите через пакетный менеджер:

```sh
sudo apt install ruby-full build-essential zlib1g-dev  # Для Linux
brew install ruby                                      # Для macOS
```

Далее установите Jekyll и Bundler:

```sh
gem install jekyll bundler
```

## 🔹 Шаг 2: Создание нового блога

Создайте новую директорию и инициализируйте проект Jekyll:

```sh
jekyll new my-blog
cd my-blog
```

Запустите локальный сервер:

```sh
bundle exec jekyll serve
```

Теперь блог доступен по адресу `http://localhost:4000`.

## 🔹 Шаг 3: Настройка блога

Откройте файл `_config.yml` и измените основные параметры:

```yaml
title: "Мой блог про AI"
description: "Блог о машинном обучении и нейросетях"
author: "Имя Автора"
baseurl: ""
url: "https://username.github.io"
```

## 🔹 Шаг 4: Добавление первой статьи

Все посты находятся в папке `_posts`. Создадим новый файл:

```sh
mkdir _posts
nano _posts/2025-02-21-welcome.md
```

Добавьте в него содержание:

```md
---
layout: post
title: "Привет, мир!"
date: 2025-02-21
categories: AI MachineLearning
---

Этот блог посвящен исследованиям в области искусственного интеллекта. Добро пожаловать!
```

## 🔹 Шаг 5: Размещение на GitHub Pages

1. Создайте репозиторий `username.github.io` на GitHub.
2. Свяжите его с локальным проектом:

```sh
git init
git add .
git commit -m "Первый коммит"
git branch -M main
git remote add origin https://github.com/username/username.github.io.git
git push -u origin main
```

3. Включите GitHub Pages в настройках репозитория (**Settings → Pages**).
4. Через несколько минут блог станет доступен по адресу `https://username.github.io/`.

## 🔹 Заключение

Теперь у вас есть собственный блог на Jekyll! 🚀 Вы можете кастомизировать его, добавлять комментарии через Disqus или подключить Google Analytics.

Если у вас есть вопросы или хотите улучшить свой блог — пишите в комментариях! 😊

