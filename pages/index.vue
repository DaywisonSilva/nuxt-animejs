<template>
  <div>
    <div class="flex-container">
      <div class="line-drawing-demo">
        <svg
          class="NuxtLogo"
          width="245"
          height="180"
          viewBox="0 0 452 342"
          xmlns="http://www.w3.org/2000/svg"
        >
          <g
            ref="line"
            fill="none"
            fill-rule="evenodd"
            stroke="greenyellow"
            stroke-width="5"
            class="lines"
          >
            <path
              d="M139 330l-1-2c-2-4-2-8-1-13H29L189 31l67 121 22-16-67-121c-1-2-9-14-22-14-6 0-15 2-22 15L5 303c-1 3-8 16-2 27 4 6 10 12 24 12h136c-14 0-21-6-24-12z"
              fill="#00C58E"
            />
            <path
              d="M447 304L317 70c-2-2-9-15-22-15-6 0-15 3-22 15l-17 28v54l39-67 129 230h-49a23 23 0 0 1-2 14l-1 1c-6 11-21 12-23 12h76c3 0 17-1 24-12 3-5 5-14-2-26z"
              fill="#108775"
            />
            <path
              d="M376 330v-1l1-2c1-4 2-8 1-12l-4-12-102-178-15-27h-1l-15 27-102 178-4 12a24 24 0 0 0 2 15c4 6 10 12 24 12h190c3 0 18-1 25-12zM256 152l93 163H163l93-163z"
              fill="#2F495E"
            />
          </g>
        </svg>
      </div>
      <div class="motion-path-demo">
        <div class="el"></div>
        <svg
          width="256px"
          height="221px"
          viewBox="0 0 245 235"
          version="1.1"
          xmlns="http://www.w3.org/2000/svg"
          xmlns:xlink="http://www.w3.org/1999/xlink"
          preserveAspectRatio="xMidYMid"
        >
          <g
            ref="line"
            fill="none"
            fill-rule="evenodd"
            stroke="greenyellow"
            stroke-width="3"
            class="lines"
          >
            <path
              ref="path"
              d="M204.8,0 L256,0 L128,220.8 L0,0 L50.56,0 L97.92,0 L128,51.2 L157.44,0 L204.8,0 Z"
              fill="#41B883"
            ></path>
            <path
              ref="path"
              d="M0,0 L128,220.8 L256,0 L204.8,0 L128,132.48 L50.56,0 L0,0 Z"
              fill="#41B883"
            ></path>
            <path
              ref="path"
              d="M50.56,0 L128,133.12 L204.8,0 L157.44,0 L128,51.2 L97.92,0 L50.56,0 Z"
              fill="#35495E"
            ></path>
          </g>
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    const anime = this.$anime
    this.$anime({
      targets: '.line-drawing-demo .lines path',
      strokeDashoffset: [anime.setDashoffset, 0],
      easing: 'easeInOutSine',
      duration: 1100,
      // eslint-disable-next-line
      delay: function (el, i) {
        return i * 250
      },
      direction: 'alternate',
      loop: true,
    })

    const path = this.$anime.path('.motion-path-demo path')
    this.$anime({
      targets: '.motion-path-demo .el',
      translateX: path('x'),
      translateY: path('y'),
      rotate: path('angle'),
      easing: 'linear',
      duration: 1800,
      loop: true,
    })
  },
}
</script>

<style>
body {
  background-color: #3d3d3d;
}

.el {
  width: 20px;
  height: 20px;
  background-color: rgb(255, 255, 255);
}

.flex-container {
  width: 100%;
  height: 100vh;
  min-height: 600px;
  align-items: center;
  padding: 20px;
  box-sizing: border-box;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
