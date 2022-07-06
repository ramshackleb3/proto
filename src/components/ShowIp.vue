<template>
  <section class="p-10">
    <h1>ip: {{ ip }}</h1>
  </section>
</template>
<script>
export default {
  name: 'ShowIp',
  data() {
    return {
      ip: ''
    };
  },
  methods: {
    getUserIP(onNewIP) {
      let MyPeerConnection = window.RTCPeerConnection || window.mozRTCPeerConnection || window.webkitRTCPeerConnection;
      let pc = new MyPeerConnection({
        iceServers: []
      });
      let noop = () => {
      };
      let localIPs = {};
      let ipRegex = /([0-9]{1,3}(\.[0-9]{1,3}){3}|[a-f0-9]{1,4}(:[a-f0-9]{1,4}){7})/g;
      let iterateIP = (ip) => {
        if (!localIPs[ip]) onNewIP(ip);
        console.log(localIPs);
        localIPs[ip] = true;
      };
      pc.createDataChannel('');
      pc.createOffer().then((sdp) => {
        sdp.sdp.split('\n').forEach(function (line) {
          if (line.indexOf('candidate') < 0) return;
          line.match(ipRegex).forEach(iterateIP);
        });
        pc.setLocalDescription(sdp, noop, noop);
      }).catch((reason) => {
        console.log(reason)
      });
      pc.onicecandidate = (ice) => {
        if (!ice || !ice.candidate || !ice.candidate.candidate || !ice.candidate.candidate.match(ipRegex)) return;
        ice.candidate.candidate.match(ipRegex).forEach(iterateIP);
      };
      // console.log(234);
    }
  },
  mounted() {
    this.getUserIP((ip) => {
      this.ip = ip;
    });
  }
}
</script>

<style scoped>
</style>
