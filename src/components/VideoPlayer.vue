<template>
  <div class="liveView">
    <video-player
      class="vjs-custom-skin"
      ref="videoPlayer"
      :options="playerOptions"
      @ready="onPlayerReadied"
      @timeupdate="onTimeupdate"
      :playsinline="playsinline"
    >
    </video-player>
  </div>
</template>



<script>
import { videoPlayer } from "vue-video-player";
import "video.js/dist/video-js.css";
import "vue-video-player/src/custom-theme.css";
import "videojs-contrib-hls";

export default {
  name: "live",
  components: {
    videoPlayer,
  },
  data() {
    return {
      initialized: false,
      currentTech: "",
      streams: {
        rtmp: "",
        hls: "",
      },
      playerOptions: {
        overNative: true,
        autoplay: false,
        controls: true,
        techOrder: ["html5"],
        sourceOrder: true,
        // flash: {
        //   hls: { withCredentials: false },
        // },
        html5: { hls: { withCredentials: false } },
        sources: [
          {
            // withCredentials: false,
            type: "application/x-mpegURL",
            // src: "http://127.0.0.1:8889/static/ts2/index.m3u8",
            // src: "http://127.0.0.1:8889/static/ts-1m/index.m3u8",
            // src: "http://127.0.0.1:8889/static/ts-h264-2/index.m3u8",
            // src: "http://127.0.0.1:8889/static/ts-h264-2/index-p1.m3u8",
            src: "./static/video/video1/index.m3u8",
          },
          // {
          //   // withCredentials: false,
          //   type: "video/mp4",
          //   // src: "http://127.0.0.1:8889/static/out-h264-2.mp4",
          //   src: "http://127.0.0.1:8889/static/out-h264.mp4",
          // },
        ],
      },
    };
  },
  computed: {
    player() {
      return this.$refs.videoPlayer.player;
    },
    currentStream() {
      return this.currentTech === "Flash" ? "RTMP" : "HLS";
    },
    playsinline() {
      let ua = navigator.userAgent.toLocaleLowerCase();
      // x5内核
      if (ua.match(/tencenttraveler/) != null || ua.match(/qqbrowse/) != null) {
        return false;
      } else {
        // ios端
        return true;
      }
    },
  },
  methods: {
    onPlayerReadied() {
      if (!this.initialized) {
        this.initialized = true;
        this.currentTech = this.player.techName_;
      }
    },
    // record current time
    onTimeupdate(e) {
      console.log("currentTime", e.cache_.currentTime);
    },
  },
};
</script>

<style scoped>
.liveView {
  position: relative;
}

</style>
