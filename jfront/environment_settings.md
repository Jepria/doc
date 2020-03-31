# Настройка окружения для JavaScript разработчиков

Для работы с JavaScript разработчикам необходимо установить [Node.js](https://nodejs.org).
Также рекомендую установить [yarn](https://yarnpkg.com/).

## Настройка для работы из внутренней сети

Для корректной работы из внутренней сети необходимо в файле C:\Users\{userName}\.npmrc прописать следующие настройки для работы через [cntlm](https://github.com/Jepria/doc/blob/master/cntlm-settings-for-npm-yarn-maven.md):

```
   proxy=http://localhost:53128/
   https-proxy=http://localhost:53128/
   registry=https://registry.npmjs.org
```

## Инструменты разработчика

Самый популярный редактор кода на JavaScript - [VS Code](https://code.visualstudio.com/).
Или можно использовать [intellij idea ultimate](https://www.jetbrains.com/ru-ru/idea/download).

Для удобной работы с VS Code стоит поставить плагины:

- [Auto Import](https://marketplace.visualstudio.com/items?itemName=steoates.autoimport)
- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense)
- [Auto Close Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-close-tag)
- [Auto Rename Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag)

Для отладки React приложений есть плагин для Chrome [React Developer Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi).

## Начало работы с React

Начало знакомства с React можно начать с [create-react-app](https://ru.reactjs.org/docs/create-a-new-react-app.html).

Или сразу:

```
npx create-react-app my-app
cd my-app
npm start
```

## Для тех кто не знаком с JavaScript

Хороший онлайн учебник https://learn.javascript.ru/

## Ещё полезное:

- [Style Guide от Airbnb](https://github.com/airbnb/javascript)
- [How to learn React.js](https://www.robinwieruch.de/learn-react-j) - также у [автора](https://www.robinwieruch.de/) много других статей.
- [Хороший ресурс по HTML и CSS](http://htmlbook.ru/)
- [Путь к изучению React](https://leanpub.com/the-road-to-learn-react-russian)
