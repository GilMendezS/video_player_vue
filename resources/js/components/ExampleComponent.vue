<template>
    <div class="video-player">
        <video-player  class="video-player-box"
            ref="videoPlayer"
            :options="playerOptions"
            :playsinline="true"
            customEventName="customstatechangedeventname"

            @play="onPlayerPlay($event)"
            @pause="onPlayerPause($event)"
            @ended="onPlayerEnded($event)"
            @waiting="onPlayerWaiting($event)"
            @playing="onPlayerPlaying($event)"
            @loadeddata="onPlayerLoadeddata($event)"
            @timeupdate="onPlayerTimeupdate($event)"
            @canplay="onPlayerCanplay($event)"
            @canplaythrough="onPlayerCanplaythrough($event)"

            @statechanged="playerStateChanged($event)"
            @ready="playerReadied">
        </video-player>
    </div>
    
</template>
<style scoped>

</style>

<script>
    import 'video.js/dist/video-js.css'
    import { videoPlayer } from 'vue-video-player'

    export default {
        components: {
            videoPlayer
        },
        data() {
            return {
                playerOptions: {
                    // videojs options
                    muted: false,
                    language: 'en',
                    playbackRates: [0.7, 1.0, 1.5, 2.0],
                    sources: [{
                        type: "video/mp4",
                        src: "/videos/example.mp4"
                    }],
                    poster: "/images/author.jpg",
                    height: 500,
                    width: 300
                }
            }
        },
        mounted() {
            console.log('this is current player instance object', this.player)
        },
        computed: {
            player() {
                return this.$refs.videoPlayer.player
            }
        },
        methods: {
            // listen event
            onPlayerPlay(player) {
                // console.log('player play!', player)
            },
            onPlayerPause(player) {
                // console.log('player pause!', player)
            },
            // ...player event

            // or listen state event
            playerStateChanged(playerCurrentState) {
                // console.log('player current update state', playerCurrentState)
            },

            // player is ready
            playerReadied(player) {
                console.log('the player is readied', player)
                // you can use it to do something...
                // player.[methods]
            },
            onPlayerWaiting(player){

            },
            onPlayerPlaying(player){

            },
            onPlayerLoadeddata(player){

            },
            onPlayerTimeupdate(player){

            },
            onPlayerCanplay(player){

            },
            onPlayerCanplaythrough(player){

            }


        }
    }
</script>
