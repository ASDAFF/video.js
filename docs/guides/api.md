API
===

API Video.js позволяет вам взаимодействовать с видео через JavaScript, независимо от того, проигрывает ли браузер видео через HTML5 видео, Flash или любые другие поддерживаемые технологии воспроизведения.

Referencing the Player
----------------------
Чтобы использовать функции API, вам нужен доступ к объекту проигрывателя. К счастью, его легко получить. Вам просто нужно убедиться, что ваш видеотег имеет ID. Пример кода для вставки имеющий ID "example\_video_1". Если у вас есть несколько видео на одной странице, убедитесь, что у каждого тега есть уникальный идентификатор (ID).

```js
var myPlayer = videojs('example_video_1');
```

(Если проигрыватель еще не был инициализирован с помощью атрибута настройки данных или другого метода, это также приведет к инициализации проигрывателя.)

Wait Until the Player is Ready
------------------------------
Время, необходимое Video.js для настройки видео и API, будет зависеть от используемой технологии воспроизведения (HTML5 часто будет намного быстрее загружать, чем Flash).The time it takes Video.js to set up the video and API will vary depending on the playback technology being used (HTML5 will often be much faster to load than Flash). For that reason we want to use the player's 'ready' function to trigger any code that requires the player's API.

```javascript
videojs("example_video_1").ready(function(){
  var myPlayer = this;

  // EXAMPLE: Start playing the video.
  myPlayer.play();

});
```

API Methods
-----------
Now that you have access to a ready player, you can control the video, get values, or respond to video events. The Video.js API function names follow the [HTML5 media API](http://www.whatwg.org/specs/web-apps/current-work/multipage/the-video-element.html). The main difference is that getter/setter functions are used for video properties.

```js

// setting a property on a bare HTML5 video element
myVideoElement.currentTime = "120";

// setting a property on a Video.js player
myPlayer.currentTime(120);

```

The full list of player API methods and events can be found in the [player API docs](http://docs.videojs.com/docs/api/index.html).
