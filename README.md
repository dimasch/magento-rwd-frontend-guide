# Руководство по разработке RWD темы для Magento 1.9.x

## Articles
* [Responsive Web Design Developer's Guide](http://devdocs.magento.com/guides/m1x/ce19-ee114/RWD_dev-guide.html) - Magento Community Edition (CE) 1.9 and Magento Enterprise Edition (EE) 1.14 Responsive Web Design Developer's Guide
* [Getting Ready For HTTP/2](https://www.smashingmagazine.com/2016/02/getting-ready-for-http2/) - Getting Ready For HTTP/2: A Guide For Web Designers And Developers
* [Css-tricks - Susy](https://css-tricks.com/build-web-layouts-easily-susy/) - Build Web Layouts Easily with Susy.


## Sass/Compass
* [Sass - variables, mixins](http://www.youtube.com/watch?v=iWOGk_b2yac) — основы CSS препроцессора (variables, mixins)
* [Compass](http://www.youtube.com/watch?v=jWKcPW5rXmo) - Compass (Sass Framework) config.rb & watch
* [Compass - sprites](http://www.youtube.com/watch?v=arQhD9Jc81M) - работаем со спрайтами (sprites).


## Добавление JS логики
* `skin/frontend/kmplzt/theme/js` - проектные JavaScript классы 
* `skin/frontend/kmplzt/theme/vendor` - в vendor храним только то, что устанавливается и обновляем из пакетного менеджера Bower (`bower install owl.carousel —save-dev`)
Для того чтобы при установке модули сохранялись в папку vendor настроим `.bowerrc`
* Добавляем jQuery в раздел ignoredDependencies `.bowerrc` (пример в этом репозитории)
* vendor храним в нашем git.
* Никаких jQuery onReady - используем Magento Way. Кнопочку добавили - сразу под ней кусочек JS кода `<script pagespeed_no_defer=""></script>` Создание экземпляров или настроки плагинов добавляем в шаблонах в теге непосредственно в шаблонах после соответствующей html разметки.
* `pagespeed_no_defer=""` - означает что при включенном pagespeed не откладывать выполнение скрипта, делается иногда для тоо чтобы некоторые UI-элементы написанные на JS отрисовывались быстрее.
* Используем неймспейс jQuery 


## Работа с Sass/Compass
* Спрайты делаем модульными, например создаем папку images/social или images/account. И добавляем не все изображения через all ключевое слово, а добавляем через include точечно каждое изображение на месте использования. Таким образом будут генериться только действительно используемые css-правила для микинов.
* Используем брейкпоинты [breakpoint-sass.com](http://breakpoint-sass.com/) для описания адаптивных блоков.
`.johnny-utah {
  @include breakpoint($high-tide) {
    content: 'Whoa.';
  }
}`
