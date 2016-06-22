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
            <vuedio></vuedio>
        </div>
    </div>
</template>
<script>
import vuedio from './components/video.vue'
export default {
    components: {
        vuedio
    }
}
</script>
