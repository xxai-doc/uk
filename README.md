<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Рекомендується спочатку встановити nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) , а потім `direnv allow` після входу в каталог ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) буде виконано автоматично після входу в каталог).

Значення таке: переклад з китайської на японську, корейську, англійську, переклад з англійської на всі інші мови. Якщо ви хочете підтримувати лише китайську та англійську, ви можете просто написати `zh: en` .

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

### Інструкція з автоматизації перекладу документів

Перегляньте репозиторій коду [xxai-art/doc](https://github.com/xxai-art/doc)

Рекомендується спочатку встановити nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) , а потім `direnv allow` після входу в каталог ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) буде виконано автоматично після входу в каталог).

Щоб уникнути великої кодової бази, перекладеної на сотні мов, я створив окрему кодову базу для кожної мови та створив організацію для зберігання кодової бази

Якщо встановити змінну середовища `GITHUB_ACCESS_TOKEN` і потім запустити [create.github.coffee,](https://github.com/xxai-art/doc/blob/main/create.github.coffee) сховище коду буде автоматично створено.

Звичайно, ви також можете розмістити його в базі коду.

Посилання на сценарій перекладу [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Код сценарію інтерпретується таким чином:

[bunx](https://bun.sh/docs/cli/bunx) є заміною для npx, який є швидшим. Звичайно, якщо у вас не встановлено bun, ви можете використовувати замість нього `npx` .

`bunx mdt zh` рендерить `.mdt` у каталозі zh як `.md` , перегляньте 2 пов’язані файли нижче

* [coffee_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` є основним кодом для перекладу (якщо у вас встановлено лише `nodejs` , але `bun` і `direnv` не встановлено, ви також можете запустити `npx i18n` для перекладу).

Він аналізуватиме [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , конфігурація `i18n.yml` у цьому документі така:

```
en:
zh: ja ko en
```

Значення таке: переклад з китайської на японську, корейську, англійську, переклад з англійської на всі інші мови. Якщо ви хочете підтримувати лише китайську та англійську, ви можете просто написати `zh: en` .

Останній — [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , який витягує вміст між основним заголовком і першим підзаголовком `README.md` кожної мови для створення запису `README.md` . Код дуже простий, ви можете подивитися на нього самі.

Google API використовується для безкоштовного перекладу. Якщо ви не можете отримати доступ до Google, налаштуйте та встановіть проксі-сервер, наприклад:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Сценарій перекладу згенерує перекладений кеш у каталозі `.i18n` , перевірте його за допомогою `git status` і додайте його до сховища коду, щоб уникнути повторних перекладів.

Будь ласка, запускайте `bunx i18n` кожного разу, коли ви змінюєте переклад, щоб оновити кеш.

Якщо оригінальний текст і переклад змінено одночасно, кеш буде сплутано, тому, якщо ви хочете змінити, ви можете змінити лише один, а потім запустити `bunx i18n` , щоб оновити кеш.
