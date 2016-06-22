<style>
.__cov-video-container {
    position: relative;
    width: 100%;
    background-color: #000;
}

.__cov-video {
    width: 100%;
    height: 100%;
    vertical-align: bottom;
}

.__cov-contrl-content {
    position: absolute;
    display: flex;
    left: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.41);
    height: 2rem;
    width: 100%;
    z-index: 2147483647;
}
.__cov-contrl-play-btn {
    position: relative;
    height: 100%;
    background: none;
    border: none;
    width: 4rem;
    outline: none;
    vertical-align: top;
}
.__cov-contrl-play-btn:hover {
    background-color: rgba(255, 255, 255, 0.27);
}
.__cov-contrl-play-btn-icon {
    position: absolute;
    height: 1rem;
    width: 1rem;
    top: 50%;
    left: 50%;
    margin-top: -.5rem;
    margin-left: -.5rem;
}
.__cov-contrl-vol-btn-icon {
    position: absolute;
    height: 1.1rem;
    width: 1.1rem;
    top: 50%;
    left: 50%;
    margin-top: -.55rem;
    margin-left: -.55rem;
}
.__cov-contrl-vol-slider {
    position: relative;
    display: inline-block;
    height: 100%;
    width: 0;
    overflow: hidden;
    transition: all .2s ease-in;
}
.__cov-contrl-vol-rail {
    position: absolute;
    top: 50%;
    width: 6rem;
    height: .1rem;
    margin-top: -.05rem;
    background: #fff;
}
.__cov-contrl-vol-inner {
    position: absolute;
    display: inline-block;
    left: 0;
    top: 50%;
    background: #fff;
    width: .5rem;
    height: .5rem;
    border-radius: 50%;
    margin-top: -.25rem;
    z-index: 2;
    cursor: pointer;
}
.__cov-contrl-vol-box {
    display: flex;
    padding-right: 1rem;
}
.__cov-contrl-vol-box:hover .__cov-contrl-vol-slider {
    width: 6rem;
}
.__cov-contrl-video-slider {
    position: relative;
    display: inline-block;
    height: 100%;
    width: 100%;
    overflow: hidden;
    transition: all .2s ease-in;
}
.__cov-contrl-video-rail {
    position: absolute;
    top: 50%;
    width: 100%;
    height: .1rem;
    margin-top: -.05rem;
    background: #fff;
}
.__cov-contrl-video-inner {
    position: absolute;
    display: inline-block;
    left: 0;
    top: 50%;
    background: #fff;
    width: .5rem;
    height: .5rem;
    border-radius: 50%;
    margin-top: -.25rem;
    z-index: 2;
    cursor: pointer;
    transition: all 16ms;
}
.__cov-contrl-video-time {
    padding: 0 1rem;
}
.__cov-contrl-video-time-text {
    color: #fff;
    line-height: 2rem;
    font-size: .8rem;
}
::-webkit-media-controls {
  display:none !important;
}
video::-webkit-media-controls {
  display:none !important;
}
video::-webkit-media-controls-enclosure {
  display:none !important;
}
</style>
<template>
    <div id="app">
        <div class="container">
            <div class="__cov-video-container">
                <video class="__cov-video" poster="http://covteam.u.qiniudn.com/poster.png">
                    <source id="covVideoSrc_mp4" src="http://covteam.u.qiniudn.com/oceans.mp4" type='video/mp4; codecs="avc1.42E01E, mp4a.40.2"'>
                    </source>
                </video>
                <div class="__cov-contrl-content">
                    <button class="__cov-contrl-play-btn" @click="play">
                        <svg class="__cov-contrl-play-btn-icon" v-show="!state.playing" viewBox="0 0 47 57" version="1.1" xmlns="http://www.w3.org/2000/svg">
                            <!-- Generator: Sketch 3.8.3 (29802) - http://www.bohemiancoding.com/sketch -->
                            <title>Triangle 1</title>
                            <desc>Created with Sketch.</desc>
                            <defs></defs>
                            <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
                                <polygon id="Triangle-1" stroke="#FFFFFF" fill="#FFFFFF" points="1 56 1 1 47 28.5"></polygon>
                            </g>
                        </svg>
                        <svg class="__cov-contrl-play-btn-icon" v-show="state.playing" viewBox="0 0 15 22" version="1.1" xmlns="http://www.w3.org/2000/svg">
                            <!-- Generator: Sketch 3.8.3 (29802) - http://www.bohemiancoding.com/sketch -->
                            <title>Combined Shape</title>
                            <desc>Created with Sketch.</desc>
                            <defs>
                                <path d="M0,0.979149244 L5,0.979149244 L5,22 L0,22 L0,0.979149244 Z M10,0.979149244 L15,0.979149244 L15,22 L10,22 L10,0.979149244 Z" id="path-1"></path>
                                <mask id="mask-2" maskContentUnits="userSpaceOnUse" maskUnits="objectBoundingBox" x="0" y="0" width="15" height="21.0208508" fill="white">
                                    <use xlink:href="#path-1"></use>
                                </mask>
                            </defs>
                            <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
                                <use id="Combined-Shape" stroke="#FFFFFF" mask="url(#mask-2)" stroke-width="2" fill="#FFFFFF" xlink:href="#path-1"></use>
                            </g>
                        </svg>
                    </button>
                    <div class="__cov-contrl-video-slider" @mousedown="videoMove">
                        <div class="__cov-contrl-video-inner" :style="{ 'transform': `translate3d(${video.pos.current}px, 0, 0)`}"></div>
                        <div class="__cov-contrl-video-rail"></div>
                    </div>
                    <div class="__cov-contrl-video-time">
                        <span class="__cov-contrl-video-time-text">{{video.displayTime}}</span>
                    </div>
                    <div class="__cov-contrl-vol-box">
                        <button class="__cov-contrl-play-btn">
                            <svg class="__cov-contrl-vol-btn-icon" viewBox="0 0 20 38" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                                <!-- Generator: Sketch 3.8.3 (29802) - http://www.bohemiancoding.com/sketch -->
                                <title>Combined Shape</title>
                                <desc>Created with Sketch.</desc>
                                <defs>
                                    <path d="M8.61522369,12 L20,0.615223689 L20,37.3847763 L8.61522369,26 L1.99201702,26 C0.891856397,26 0,25.1029399 0,23.9941413 L0,14.0058587 C0,12.8980535 0.900176167,12 1.99201702,12 L8.61522369,12 Z" id="vol-1"></path>
                                    <mask id="mask-2" maskContentUnits="userSpaceOnUse" maskUnits="objectBoundingBox" x="0" y="0" width="20" height="36.7695526" fill="white">
                                        <use xlink:href="#vol-1"></use>
                                    </mask>
                                </defs>
                                <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
                                    <use id="Combined-Shape" stroke="#FFf" mask="url(#mask-2)" stroke-width="2" fill="#fff" xlink:href="#vol-1"></use>
                                </g>
                            </svg>
                        </button>
                        <div class="__cov-contrl-vol-slider" @mousedown="volMove">
                            <div class="__cov-contrl-vol-inner" :style="{ 'transform': `translate3d(${volume.pos.current}px, 0, 0)`}"></div>
                            <div class="__cov-contrl-vol-rail"></div>
                        </div>
                    </div>
                    <button class="__cov-contrl-play-btn" @click="fullScreen">
                        <svg class="__cov-contrl-vol-btn-icon" viewBox="0 0 33 33" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                            <!-- Generator: Sketch 3.8.3 (29802) - http://www.bohemiancoding.com/sketch -->
                            <defs></defs>
                            <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
                                <path d="M31.1682064,22 L31.1682064,31.0073537 L22,31.0073537 M22,1 L31.0073537,1 L31.0073537,10.1682064 M1,10.0073537 L1,1 L10.1682064,1 M10.0073537,31.1682064 L1,31.1682064 L1,22" id="Combined-Shape" stroke="#FFFFFF" stroke-width="2"></path>
                            </g>
                        </svg>
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
const getMousePosition = function (e) {
    return e.pageX
}
const pad = (val) => {
    val = Math.floor(val)
    if (val < 10) {
        return '0' + val
    }
    return val + ''
}
const timeParse = (sec) => {
    let min = 0
    min = Math.floor(sec / 60)
    sec = sec - min * 60
    return pad(min) + ':' + pad(sec)
}
export default {
    data () {
        return {
            $video: null,
            video: {
                $videoSlider: null,
                len: 0,
                current: 0,
                moving: false,
                displayTime: '00:00',
                pos: {
                    start: 0,
                    width: 0,
                    innerWidth: 0,
                    current: 0
                }
            },
            volume: {
                $volBox: null,
                percent: 60,
                moving: false,
                pos: {
                    start: 0,
                    width: 0,
                    innerWidth: 0,
                    current: 0
                }
            },
            state: {
                vol: 0.5,
                currentTime: 0,
                fullScreen: false,
                playing: false
            }
        }
    },
    ready () {
        this.$video = this.$el.getElementsByTagName('video')[0]
        this.initVideo()
        document.body.addEventListener('mousemove', this.mouseMoveAction, false)
        document.body.addEventListener('mouseup', this.mouseUpAction, false)
    },
    beforeDestroy () {
        document.body.removeEventListener('mousemove', this.mouseMoveAction)
        document.body.removeEventListener('mouseup', this.mouseUpAction)
    },
    methods: {
        init () {
            const $volBox = this.$el.getElementsByClassName('__cov-contrl-vol-slider')[0]
            const $volInner = $volBox.getElementsByClassName('__cov-contrl-vol-inner')[0]
            this.volume.$volBox = $volBox
            this.volume.pos.innerWidth = $volInner.getBoundingClientRect().width
            this.volume.pos.start = $volBox.getBoundingClientRect().left
            this.volume.pos.width = $volBox.getBoundingClientRect().width - this.volume.pos.innerWidth
        },
        initVideo () {
            const $videoSlider = this.$el.getElementsByClassName('__cov-contrl-video-slider')[0]
            const $videoInner = $videoSlider.getElementsByClassName('__cov-contrl-video-inner')[0]
            this.$videoSlider = $videoSlider
            this.video.pos.start = $videoSlider.getBoundingClientRect().left
            this.video.pos.innerWidth = $videoInner.getBoundingClientRect().width
            this.video.pos.width = $videoSlider.getBoundingClientRect().width - this.video.pos.innerWidth
            this.getTime()
        },
        getTime () {
            this.video.len = this.$video.duration
        },
        setVideoByTime (percent) {
            this.$video.currentTime = Math.floor(percent * this.video.len)
        },
        play () {
            this.state.playing = !this.state.playing
            if (this.$video) {
                if (this.state.playing) {
                    this.$video.play()
                    this.$video.addEventListener('waiting', (e) => {
                        console.log(e)
                    })
                    this.$video.addEventListener('timeupdate', this.timeline)
                } else {
                    this.$video.pause()
                }
            }
        },
        timeline () {
            // console.log(this.$video.readyState)
            const percent = this.$video.currentTime / this.$video.duration
            this.video.pos.current = (this.video.pos.width * percent).toFixed(3)
            this.video.displayTime = timeParse(this.$video.duration - this.$video.currentTime)
        },
        volMove (e) {
            this.init()
            this.volume.moving = true
        },
        videoMove (e) {
            this.initVideo()
            this.video.moving = true
        },
        setVol (val) {
            if (this.$video) {
                this.$video.volume = val
            }
        },
        fullScreen () {
            if (!this.state.fullScreen) {
                this.state.fullScreen = true
                this.$video.webkitRequestFullScreen()
            } else {
                this.state.fullScreen = false
                document.webkitCancelFullScreen()
            }
        },
        mouseMoveAction (e) {
            if (this.volume.moving) {
                const x = getMousePosition(e) - this.volume.pos.start
                if (x > 0 && x < this.volume.pos.width) {
                    this.volume.pos.current = x
                    this.setVol(x / this.volume.pos.width)
                }
            }
            if (this.video.moving) {
                const x = getMousePosition(e) - this.video.pos.start
                if (x > 0 && x < this.video.pos.width) {
                    this.video.pos.current = x
                    this.setVideoByTime(x / this.video.pos.width)
                }
            }
        },
        mouseUpAction (e) {
            this.volume.moving = false
            this.video.moving = false
        }
    }
}
</script>
