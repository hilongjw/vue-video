# vue-video

> A HTML5 video player component for Vue.js

## Demo

live demo is here: [https://hilongjw.github.io/vue-video/ocean.html](https://hilongjw.github.io/vue-video/ocean.html )
![](https://raw.githubusercontent.com/hilongjw/vue-video/master/preview.png)
![](https://raw.githubusercontent.com/hilongjw/vue-video/master/preview2.png)


## Installation
```bash

npm i vue-video --save

```


## Usage

```
// script
import myVideo from 'vue-video'
export default {
    data () {
        return {
            video: {
                sources: [{
                    src: 'http://covteam.u.qiniudn.com/oceans.mp4',
                    type: 'video/mp4'
                }],
                options: {
                    autoplay: true,
                    volume: 0.6,
                    poster: 'http://covteam.u.qiniudn.com/poster.png'
                }
            }
        }
    },
    components: {
        myVideo
    }
}
```

```html
<template>
    <div id="app">
        <div class="container">
            <my-video :sources="video.sources" :options="video.options"></my-video>
        </div>
    </div>
</template>
```

## API

> sources

```
sources: [{
    // video uri
    src: 'http://covteam.u.qiniudn.com/oceans.mp4',
    // video meta type
    type: 'video/mp4'
}]

```

> options

```
options: {
    // autoplay
    autoplay: true,
    // default volume
    volume: 0.6,
    // poster (cover image)
    poster: 'http://covteam.u.qiniudn.com/poster.png'
}
```

