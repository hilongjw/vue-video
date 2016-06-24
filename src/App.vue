<style>
html,
body {
    margin: 0;
    padding: 0;
    text-align: center;
}

.container {
    display: inline-block;
    width: 60rem;
    background: #ccc;
}
</style>
<template>
    <div id="app">
        <div class="container">
            <vuedio :sources="video.sources"></vuedio>
        </div>
    </div>
</template>
<script>
import vuedio from './components/video.vue'
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
        vuedio
    }
}
</script>
