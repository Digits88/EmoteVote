<template>
  <div id="wrapper">

    <floating-emoji></floating-emoji>
    <floating-emoji>👏</floating-emoji>
    <floating-emoji>👏</floating-emoji>
    <floating-emoji>👏</floating-emoji>
    <floating-emoji>👍</floating-emoji>
    <floating-emoji>👍</floating-emoji>
    <floating-emoji>💖</floating-emoji>
    <floating-emoji>💖</floating-emoji>
    <floating-emoji>💖</floating-emoji>
    <floating-emoji>💖</floating-emoji>

    <div class="server-info">

      <span class="server-info__live" v-if="server && server.url">
        Cast your <strong>Emote Vote</strong> at <strong v-text="server.url"></strong>
      </span>

      <span class="server-info__status" v-else v-text="server.status"></span>

    </div>
  </div>
</template>

<script>
  import SystemInformation from './LandingPage/SystemInformation'
  import FloatingEmoji from './FloatingEmoji';

  export default {
    name: 'landing-page',
    components: {
      SystemInformation,
      FloatingEmoji,
    },

    data: ()=>({
      server: {
        url: 'http://192.168.0.23:1337/'
      }
    }),

    mounted(){
      // INITIALIZE SERVER
    }
  }
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  user-select: none;
  pointer-events: none;
  text-shadow: none;
}

html, body {
  width: 100%;
  overflow: hidden;
  background: transparent;
}

html { height: 100%; }
body { min-height: 100%; }


.server-info {
  display: block;
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  font-family: system, sans-serif;
  text-align: center;
  padding: 0.5em;
  background:rgba(255,255,255,0.6);
  text-shadow: 0 0 5px #FFF;
  border-radius: 10px;
  -webkit-app-region: drag;
  cursor: move;
  pointer-events: auto;
  z-index: 999;
}

.server-info:before {
    content: '';
    display: block;
    position: fixed;
    top: 0; right: 0; bottom: 0; left: 0;
    margin: auto;
    border: dashed 5px transparent;
    pointer-events: none;
}
.server-info:hover::before { border-color: #000; }

</style>
