<script setup lang="ts">
import {computed, ref, onMounted, inject} from "vue";

const props = defineProps({
      show: {
        type: Boolean,
        default: false
      },
      animation: {
        type: String,
        default: 'fade',
      },
      time: {
        type: Number,
        default: 500,
      },
      background: {
        type: String,
        default: 'radial-gradient(circle, rgba(198,90,254,1) 0%, rgba(184,251,196,1) 100%)',
      },
      spinner: {
        type: String,
      },
      text: {
        type: String,
        default: '',
      },
    }
)
const time = ref<string>('');
const background = ref<string>('');
let spinnerDefault = ref<string>(`
    <svg width="38" height="38" viewBox="0 0 38 38" xmlns="http://www.w3.org/2000/svg">
    <defs>
        <linearGradient x1="8.042%" y1="0%" x2="65.682%" y2="23.865%" id="a">
            <stop stop-color="#fff" stop-opacity="0" offset="0%"/>
            <stop stop-color="#fff" stop-opacity=".631" offset="63.146%"/>
            <stop stop-color="#fff" offset="100%"/>
        </linearGradient>
    </defs>
    <g fill="none" fill-rule="evenodd">
        <g transform="translate(1 1)">
            <path d="M36 18c0-9.94-8.06-18-18-18" id="Oval-2" stroke="url(#a)" stroke-width="2">
                <animateTransform
                    attributeName="transform"
                    type="rotate"
                    from="0 18 18"
                    to="360 18 18"
                    dur="0.9s"
                    repeatCount="indefinite" />
            </path>
            <circle fill="#fff" cx="36" cy="18" r="1">
                <animateTransform
                    attributeName="transform"
                    type="rotate"
                    from="0 18 18"
                    to="360 18 18"
                    dur="0.9s"
                    repeatCount="indefinite" />
            </circle>
        </g>
    </g>
</svg>
`);

const getSpinnerPath = computed(() => {
  return props.spinner ? new URL('/src'+props.spinner, import.meta.url).href : spinnerDefault.value;
})

onMounted(() => {
  time.value = ' ' + (props.time / 1000) + 's ease';
  background.value = ''+props.background+'';
})





</script>

<template>
  <Transition :name="animation">
    <div
        class="slay-container"
        v-if="show"
    >
      <div class="slay-container__content">
        <img
            v-if="props.spinner"
            :src="getSpinnerPath"
            class="slay-container__spinner"
            alt="Spinner"
        >
        <div
            v-else
            v-html="getSpinnerPath"
            class="slay-container__spinner"
        ></div>
        <p class="slay-container__text">{{text}}</p>
      </div>
    </div>
  </Transition>
</template>

<style scoped>
/*body {*/
/*  overflow: hidden;*/
/*}*/
.slay-container {
  position: fixed;
  z-index: 999;
  left: 0;
  top: 0;
  right: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: v-bind('background');
}
.slay-container__content {
  max-width: 800px;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.slay-container__spinner {
  margin: 15px auto;
}
.slay-container__text {
  margin: 0;
  font-size: 16px;
  text-align: center;
  color: white;
}

/*FADE ANIMATION*/
.fade-enter-active,
.fade-leave-active {
  transition: opacity v-bind('time');
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
/*FADE ANIMATION*/


/*DROP-TOP ANIMATION*/
.drop-top-enter-active,
.drop-top-leave-active {
  transition: transform v-bind('time');
}
.drop-top-enter-from,
.drop-top-leave-to {
  transform: translateY(-100%);
}
/*DROP-TOP ANIMATION*/

/*DROP-LEFT ANIMATION*/
.drop-left-enter-active,
.drop-left-leave-active {
  transition: transform v-bind('time');
}
.drop-left-enter-from,
.drop-left-leave-to {
  transform: translateX(-100%);
}
/*DROP-LEFT ANIMATION*/


/*DROP-RIGHT ANIMATION*/
.drop-right-enter-active,
.rop-right-leave-active {
  transition: transform v-bind('time');
}
.rop-right-enter-from,
.rop-right-leave-to {
  transform: translateX(-100%);
}
/*DROP-RIGHT ANIMATION*/


/*DROP-BOTTOM ANIMATION*/
.drop-bottom-enter-active,
.drop-bottom-leave-active {
  transition: transform v-bind('time');
}
.drop-bottom-enter-from,
.drop-bottom-leave-to {
  transform: translateY(100%);
}
/*DROP-BOTTOM ANIMATION*/

</style>
