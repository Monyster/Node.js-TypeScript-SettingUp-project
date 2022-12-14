# Node.js-TypeScript-SettingUp-project

1. Инициализация проекта npm
   npm init (флаг "-y" - разрешить значения по умолчанию)

2. Установка пакетов

   - Установка пакетов для разработки на тайпскрипт

   npm install -D typescript

   - Установите окружающие типы Node.js для TypeScript

   npm install -D @types/node

   https://typescript-eslint.io/docs/
   (флаг "-D" - установить как зависимость для разработки)

3. Конфигурация ТайпСкрипта

rootDir: Здесь TypeScript ищет наш код. Мы настроили его для просмотра в src/папке. Вот где мы напишем наш TypeScript.
outDir: Куда TypeScript помещает наш скомпилированный код. Мы хотим, чтобы он попал в build/папку.
esModuleInterop: Если бы вы были в сфере JavaScript в последние пару лет, вы могли бы заметить, что системы модулей немного вышли из-под контроля (AMD, SystemJS, ES-модули и т. Д.). Для темы, требующей гораздо более длительного обсуждения, если мы используем в commonjsкачестве нашей модульной системы (для приложений Node вы должны использовать), тогда нам нужно установить для нее значение true.
resolveJsonModule: Если мы используем JSON в этом проекте, эта опция позволяет TypeScript использовать его.
lib: Эта опция добавляет в наш проект внешние типы, позволяя нам полагаться на функции из разных версий Ecmascript, библиотеки тестирования и даже API DOM браузера. Мы хотели бы использовать некоторые es6языковые функции. Все это компилируется в es5.
module: commonjsэто стандартная модульная система Node в 2019 году. Давайте воспользуемся этим.
allowJs: Если вы конвертируете старый проект JavaScript в TypeScript, эта опция позволит вам включать .jsфайлы среди .tsних.
noImplicitAny: В файлах TypeScript не разрешайте неявно указывать тип. Каждый тип должен иметь определенный тип или быть объявлен явно any. Никаких неявных anys.

npx tsc --init --rootDir src --outDir build --esModuleInterop --resolveJsonModule --lib es6 --module commonjs --allowJs true --noImplicitAny true

4. Работа с файлами и компиляция

   Создадим "src" папку и файл TypeScript ".ts"
   Скомпилируем все в папке при помощи комманды

   npx tsc

5. Дополнение для удобства

ts-node - для запуска кода TypeScript напрямую,
nodemon - для отслеживания изменений в нашем коде и автоматического перезапуска при изменении файла.

npm install -D ts-node nodemon

Для конфигурации nodemon необходимо создать файл nodemon.json

---

{
"watch": ["src"],
"ext": ".ts,.js",
"ignore": [],
"exec": "ts-node ./src/index.ts"
}

---

Для запуска nodemon можно добавить сценарий

---

"start:dev": "nodemon",

---
