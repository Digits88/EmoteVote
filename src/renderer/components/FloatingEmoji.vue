<template>
<span class="floating-emoji" :style="{ left: randomLeft(), animationDelay: Math.random() * -6 + 's' }">
  <span class="floating-emoji__scale">
    <span class="floating-emoji__wobble">
    <slot>😆</slot>
    </span>
  </span>
</span>

</template>

<script>

  export default {
    name: '',
    data: ()=>({

    }),

    methods: {
      randomLeft(){
        return (window.innerWidth * 0.5)
          + (
            window.innerWidth * 0.25
             * Math.random()
             * (Math.random() < 0.5 ? -1 : 1 )
            ) + 'px';
      }
    }
  }

</script>

<style>

.floating-emoji {
  display: block;
  position: absolute;
  bottom: 0em;
  font-size: 20vw;
  overflow: visibile;
  width: 2em;
  height: 2em;

  animation: float 6s cubic-bezier(.69,.2,.93,.45) infinite;
}

@keyframes float {
  to { transform: translateY(-100vh); }
}


.floating-emoji__scale {
  display: block;
  animation: inherit;
  animation-name: scale;
  animation-timing-function: linear;
}

@keyframes scale {
  0%, 90%, 100% { opacity: 0; transform: scale(0.5); }
  20% { opacity: 1; transform: scale(1); }
}

.floating-emoji__wobble {
  display: block;
  animation: wobble 1.5s ease-in-out infinite;
  animation-delay: inherit;
}

@keyframes wobble {
  0%, 100% { transform: translateX(-10%) translateX(-50%); }
  50% { transform: translateX(10%) translateX(-50%); }
}

</style>