# Ускорение загрузки сайта на мобильных устройствах

Производительность важна для всех сайтов, но когда речь заходит о сайтах для
мобильных устройств, она становится еще важнее. Мобильные устройства имеют
меньшую скорость подключения к сети и менее мощное аппаратное обеспечение,
нежели ваш компьютер или ноутбук. Это приводит к более длительному ожиданию,
прежде чем пользователь сможет просмотреть содержимое сайта и начать с ним
работать. Чтобы понять мою точку зрения на производительность в сети, обратите
внимание на эту статью о том, как производительность может сказаться на
[фактическом результате][0] вашей работы. Ниже я расскажу о нескольких
способах сделать ваш сайт для мобильных устройств быстрее, сократив время его
загрузки. Перед тем, как вы примените любой из этих методов, проверьте текущую
скорость загрузки страницы с помощью [pingdom][1].

*Обратите внимание, что эти решения применимы не только при разработке для
мобильных устройств, и могут быть использованы для полной версии вашего сайта,
равно как и для мобильной.*

## Тяжелые изображения

Изображения — это необходимое зло, но именно они виноваты в длительной
загрузке страниц на большинстве сайтов. Можно улучшить положение вещей с
помощью простых приемов.


### Используйте изображения минимального размера

Если вы используете изображение размером 500х500 пикселей, сжимая его до
50×50, это серьезная проблема. Вашему браузеру все равно приходится загружать
изображение с большим разрешением, даже если его необходимо показывать
уменьшенным в 10 раз. Убедитесь, что вы используете изображения минимально
возможного размера. Если вы переживаете по поводу качества изображений на
Retina-дисплеях, просто сделайте изображение вдвое большим, чем его необходимо
отобразить на экране. Вместо использования изображения размером 500х500
пикселей, используйте изображение размером 100х100 пикселей и уменьшите его до
50х50 с помощью CSS или HTML. Я рекомендую использовать Photoshop и его
функцию [Сохранить для Web][18]. Вот краткое руководство по
[сохранению изображений для использования в веб][2].

### Используйте CSS3 вместо изображений

Чем меньше изображений — тем лучше, так почему бы не использовать CSS3, там,
где это возможно? Благодаря скругленным уголкам, теням, градиентам,
трансформациям и поворотам, а также многим другим свойствам, вы сможете
создавать сложные эффекты с помощью CSS. Несмотря на то, что невозможно
реализовать все с помощью CSS, стоит задуматься о том что бы использовать эту
технологию по максимуму. Обратите внимание на примеры использования СSS3:

* [10 самых крутых эффектов на CSS3][3]
* [One-div.com][4]
* [Модные поля форм на TNW][5]
* [Продвинутые эффекты при наведении][6]

### Плагины для реализации отзывчивых изображений

Одна из самых больших проблем с отзывчивыми сайтами состоит в том, что большие
изображения приходится уменьшать, чтобы они уместились на экранах меньшего
размера. Это не очень удобно для пользователей мобильных устройств, ведь им
приходится загружать огромные изображения, которые затем будут уменьшены раза
в 4. [Responsive Img][7] — это отличный плагин для jQuery, который подменяет
путь к изображению при различных разрешениях экрана. В этом случае
пользователь не будет загружать большие изображения в место маленьких, что
поможет сократить время загрузки страницы. [responsiveBreakpointJQ][8] —
плагин, который полностью работает на стороне клиента.


### Спрайты

Объединение большого количества изображений в один спрайт может сэкономить
несколько HTTP-запросов.

![Спрайт с иконками социальных сетей][Рисунок 1]

Спрайт, показанный выше, в настоящее время используется на моем сайте — 4
картинки наверху несложно заметить. Для загрузки этих значков пришлось бы или
8 HTTP-запросов, или всего один, и лучшим решением было бы использовать один
запрос. Браузеру потребуется значительно больше времени, чтобы выполнить 8
запросов и загрузить 8 изображений, чем выполнить один запрос, даже если
размер загружаемого изображения будет больше. Чтобы узнать о других
преимуществах использования спрайтов, обратите внимание на статью на
[Design Review][9].

Основной недостаток спрайтов в том, что они не могут быть отзывчивыми (или я
не знаю, как их такими сделать). В спрайты обычно имеет смысл объединять
небольшие статичные изображения. Я бы рекомендовал вам [создавать спрайты
вручную][10], а не использовать инструменты, создающие их для вас.

## Посадите ваши файлы на диету

Следующий фактор, который может решительно повлиять на время загрузки — это
количество внешних CSS- и JavaScript-файлов, которые вы загружаете.
Убедитесь, что вы загружаете как можно меньше файлов. Объединяйте файлы, если
это возможно. Существует еще несколько способов уменьшить вес файлов.

### Уменьшите размер CSS и JavaScript

Уменьшение размера файлов становится очень популярным среди разработчиков. Вы
можете заметить нечитаемую мешанину из букв, если посмотрите на исходный код
файла [jQuery][11]. Преимущество этого подхода в том, что вы не только
получите файл меньшего размера, но также в том, что обфусцированный JavaScript
может быть исполнен вашим браузером быстрее, чем этот же скрипт со всеми
пробелами и длинными именами переменных.

* [jscompress][12]
* [Online YUI Compressor][13]
* [CSS Minifier][14]

*Будьте осторожны при уменьшении размеров CSS-файлов, так как ваши медиа-выражения могут сломаться.*

### GZIP-сжатие

GZIP-сжатие — это то же самое, что сжатие ваших файлов в zip-архив на
компьютере. GZIP-сжатие помогает сократить размер HTML, JavaScript и CSS. Браузер
загрузит, разархивирует и проведет анализ файла так же, как любого
другого. Обратите внимание на обсуждение на [Stack Overflow][15] возможности
включения сжатия в .htaccess.

Не все хостинг-провайдеры разрешают использование GZIP на своих серверах.
Несмотря на то, что это удобно, платой за эту возможность является нагрузка на
процессор. Обычно, чем лучше хостинг, тем больше возможностей он вам
предоставляет. Я использую HostGator, и они предоставляют возможность
использовать GZIP только на наиболее дорогих тарифных планах, но благодаря
[Уиллу Рэю (Will Ray)][16], я узнал, что вместо этого можно использовать
[mod_deflate][17], который выполняет аналогичные функции.

## Другие варианты

Вот еще несколько способов снизить нагрузку и уменьшить время загрузки
страницы.

### Встроенные CSS и JavaScript

Все всегда говорят, что вам следует выносить CSS и JavaScript в отдельные
файлы. Но задумывались ли вы когда-нибудь о влиянии этого подхода на скорость
отрисовки страницы вашего сайта? Давайте, я объясню.

Когда ваш браузер анализирует загруженный HTML-документ и встречает в нем блок
встроенных CSS-стилей или JavaScript, ему приходится прекратить анализ
документа, переключиться на другой контекст и анализировать этот блок. Это
приводит к существенному замедлению времени отрисовки страницы на экране, а
также, если CSS описывает стили элемента, расположенного выше в
HTML-документе, браузеру необходимо также перерисовать содержимое экрана
заново. Поэтому окажите услугу вашему браузеру и выделите CSS и JavaScript в
отдельные файлы, если это возможно.

### HTTP-запросы

Каждое изображение, CSS- или JavaScript-файл, который вы подключаете — это еще
один HTTP-запрос к серверу. Слишком большое количество запросов и время,
затрачиваемое на загрузку и анализ каждого из файлов, определенно влияют на
время загрузки и отрисовки страницы. Объединяйте файлы, если это
возможно, и не подключайте CSS и скрипты, которые не понадобятся вам на
конкретной странице.

Еще один короткий совет — распределите ваши HTTP-запросы между различными
ресурсами. Браузер может единовременно загружать от 4 до 6 файлов с каждого
ресурса, поэтому, если вы распределите ваши запросы между 4 различными
ресурсами, браузер сможет загружать одновременно от 16 до 24 файлов.

## Заключение

Я надеюсь, эти советы помогут вам сократить время загрузки и отрисовки страниц
вашего сайта. Я сам постоянно пользуюсь этими советами при разработке.
Убедитесь в снижении времени загрузки вашей страницы с помощью [pingdom][1]
после того, как примените все описанные средства на практике.

[0]: http://blog.kissmetrics.com/loading-time/
[1]: http://tools.pingdom.com/fpt/
[2]: http://sixrevisions.com/web_design/comprehensive-guide-saving-images-for-web/
[3]: http://www.webdesignerdepot.com/2012/03/10-of-the-coolest-css-css3-effects-10-of-the-coolest-css-css3-effects-10-of-the-coolest-css-and-css3-effects/
[4]: http://one-div.com/
[5]: http://thenextweb.com/dd/2013/02/21/fancy-input-adds-css3-text-effects-to-input-fields-a-gimmick-or-a-chance-to-delight/
[6]: http://codecanyon.net/item/advanced-css3-hover-effects-4/4143438
[7]: http://responsiveimg.com/
[8]: https://github.com/Designer023/responsiveBreakpointJQ
[9]: http://designreviver.com/tips/the-advantages-of-using-css-sprites-along-with-a-few-tips/
[10]: http://mysprit.es/tool
[11]: http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js
[12]: http://jscompress.com/
[13]: http://refresh-sf.com/yui/
[14]: http://www.cssminifier.com/
[15]: http://stackoverflow.com/questions/2666120/how-can-i-gzip-my-javascript-and-css-files
[16]: http://www.will-ray.com/
[17]: http://support.hostgator.com/articles/specialized-help/technical/apache-htaccess/mod_deflate
[18]: http://www.deke.com/content/photoshop-top-40-feature-34-save-web-and-devices

[Рисунок 1]: img/social-sprite.png
