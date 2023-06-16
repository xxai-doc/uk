<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

Частина коду веб-сайту є відкритим кодом, ласкаво просимо допомогти оптимізувати переклад.

## інтерфейсний код

* [інтерфейсний код](https://github.com/xxai-art/web)
* [Мовні пакети для сайту в цілому](https://github.com/xxai-art/web/tree/main/i18n)
* [Мовні пакети для модулів входу](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Багатомовна документація веб-сайту](https://github.com/xxai-doc)

Мова зовнішнього програмування — [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , яка додає деякі функції на основі синтаксису coffeescript, див [. ./coffee_plus.md](./coffee_plus.md) .

## Інтернаціоналізація веб-сайтів і документів

Спирайтеся на наступні 3 проекти

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Суфікс — `.mdt` , ви можете використовувати синтаксис, подібний до `<+ ./coffee_plus/import.js>` , щоб посилатися на зовнішні файли та генерувати розмітку за допомогою суфікса `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Переклад Markdown не перекладатиме коди та посилання та кешуватиме перекладені речення. Якщо переклад змінено, але вихідний текст не змінено, його повторне виконання не перезапише зміну перекладу.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Мовні файли для перекладу веб-сайтів, згенерованих `yaml` .
