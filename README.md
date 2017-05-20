![Video.js logo](http://videojs.com/img/logo.png)

# [Video.js - HTML5 Video Player](http://videojs.com)  [![Build Status](https://travis-ci.org/videojs/video.js.svg?branch=master)](https://travis-ci.org/videojs/video.js)

> Video.js - это веб-видеоплеер, созданный с нуля для мира HTML5. Он поддерживает HTML5 и Flash видео, а также YouTube и Vimeo (через [плагины](https://github.com/videojs/video.js/wiki/Plugins)). Он поддерживает воспроизведение видео на настольных компьютерах и мобильных устройствах. Этот проект был начат в середине 2010 года, и теперь плеер используется на более чем ~~50,000~~ ~~100,000~~ 200,000 сайтов.

## Быстрый старт
Благодаря удивительным людям в [Fastly](http://www.fastly.com/), есть свободная CDN-версия Video.js, которую может использовать каждый. Просто добавьте в
`<head>`:

```html
<link href="http://vjs.zencdn.net/5.0/video-js.min.css" rel="stylesheet">
<script src="http://vjs.zencdn.net/5.0/video.min.js"></script>
```

Когда вы хотите использовать Video.js, вы можете просто использовать элемент `<video>` как обычно, но с дополнительным атрибутом `data-setup`, содержащим любые параметры Video.js. Эти опции могут включать в себя любую опцию Video.js плюс возможность настройки [плагинов](https://github.com/videojs/video.js/wiki/Plugins), просто убедитесь, что они действительны в формате JSON!

```html
<video id="really-cool-video" class="video-js vjs-default-skin" controls
 preload="auto" width="640" height="264" poster="really-cool-video-poster.jpg"
 data-setup='{}'>
  <source src="really-cool-video.mp4" type='video/mp4'>
  <source src="really-cool-video.webm" type='video/webm'>
  <p class="vjs-no-js">
    To view this video please enable JavaScript, and consider upgrading to a web browser
    that <a href="http://videojs.com/html5-video-support/" target="_blank">supports HTML5 video</a>
  </p>
</video>
```

Если вы не хотите использовать автоматическую настройку, вы можете не использовать атрибут data-setup и инициализировать элементы видео вручную.

```javascript
var player = videojs('really-cool-video', { /* Опции */ }, function() {
  console.log('Good to go!');

  this.play(); // если вы по какой-то причине не доверяете автопроигрыванию

  // Как насчет прослушивателя событий?
  this.on('ended', function() {
    console.log('awww...over so soon?');
  });
});
```

Если вы готовы к погружению в [документацию](http://docs.videojs.com) это первое место для получения дополнительной информации.

## Пожертвования
Video.js - это бесплатная библиотека с открытым исходным кодом, и мы ценим любую помощь, которую вы готовы предоставить. Ознакомьтесь с [руководством](CONTRIBUTING.md).

_Для проверки совместимости Video.js использует [BrowserStack](https://browserstack.com)_
## Создание собственного Video.js из исходного кода
Чтобы создать свою собственную версию, прочитайте раздел [вводный код](CONTRIBUTING.md#contributing-code) и ["Создание собственной копии"](CONTRIBUTING.md#building-your-own-copy-of-videojs) в руководстве.
## Лицензия

Лицензия Video.js предоставляется по лицензии Apache, Версия 2.0. [Просмотреть файл лицензии](LICENSE)

Copyright 2014-2015 Brightcove, Inc.
