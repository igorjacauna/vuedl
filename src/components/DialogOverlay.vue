<template>
  <transition name="opacity">
    <div
      class="dialog-overlay-loading"
      :style="{zIndex: zIndex}"
      v-if="visible"
    >
      Loading&#8230;
    </div>
  </transition>
</template>

<script>
export default {
  name: 'VDialogOverlay',
  props: {
    zIndex: {
      type: Number,
      default: () => 1250
    },
    visible: {
      type: Boolean,
      default: () => false
    }
  }
}
</script>

<style>
/* Absolute Center Spinner */
.dialog-overlay-loading {
  position: fixed;
  z-index: 999;
  height: 2em;
  width: 2em;
  overflow: show;
  margin: auto;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  cursor: wait;
}

/* Transparent Overlay */
.dialog-overlay-loading:before {
  content: '';
  display: block;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(rgba(112, 112, 112, 0.4), rgba(50, 50, 50, .8));
}

/* :not(:required) hides these rules from IE9 and below */
.dialog-overlay-loading:not(:required) {
  /* hide "loading..." text */
  font: 0/0 a;
  color: transparent;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}

.dialog-overlay-loading:not(:required):after {
  content: '';
  display: block;
  font-size: 10px;
  width: 1em;
  height: 1em;
  margin-top: -0.5em;
  animation: spinner 1500ms infinite linear;
  border-radius: 0.5em;
  box-shadow: rgba(255,255,255, 0.75) 1.5em 0 0 0, rgba(255,255,255, 0.75) 1.1em 1.1em 0 0, rgba(255,255,255, 0.75) 0 1.5em 0 0, rgba(255,255,255, 0.75) -1.1em 1.1em 0 0, rgba(255,255,255, 0.75) -1.5em 0 0 0, rgba(255,255,255, 0.75) -1.1em -1.1em 0 0, rgba(255,255,255, 0.75) 0 -1.5em 0 0, rgba(255,255,255, 0.75) 1.1em -1.1em 0 0;
}

/* Animation */

@-webkit-keyframes spinner {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
@-moz-keyframes spinner {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
@-o-keyframes spinner {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
@keyframes spinner {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
