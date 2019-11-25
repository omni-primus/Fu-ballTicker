<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>

<style scoped lang="scss">
.home {
  color: #000;
  margin-top: 100px;
}
.mannschaft {
  color: #000;
  height: 100px;
  background-color: #20d164;
  margin-top: 100px;
}
.button {
  --background: #275efe;
  --rectangle: #184fee;
  --success: #{mix(white, #184fee, 20%)};
  --text: #fff;
  --arrow: #fff;
  --checkmark: #fff;
  --shadow: rgba(10, 22, 50, 0.24);
  display: flex;
  overflow: hidden;
  text-decoration: none;
  -webkit-mask-image: -webkit-radial-gradient(white, black);
  background: var(--background);
  border-radius: 8px;
  box-shadow: 0 2px 8px -1px var(--shadow);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  &:active {
  transform: scale(0.95);
  box-shadow: 0 1px 4px -1px var(--shadow);
}
ul {
  margin: 0;
  padding: 16px 40px;
  list-style: none;
  text-align: center;
  position: relative;
  backface-visibility: hidden;
  font-size: 16px;
  font-weight: 500;
  line-height: 28px;
  color: var(--text);
  li {
    &:not(:first-child) {
      top: 16px;
      left: 0;
      right: 0;
      position: absolute;
    }
    &:nth-child(2) {
      top: 76px;
    }
    &:nth-child(3) {
      top: 136px;
    }
  }
}
& > div {
  position: relative;
  width: 60px;
  height: 60px;
  background: var(--rectangle);
  &:before,
  &:after {
    content: '';
    display: block;
    position: absolute;
  }
  &:before {
    border-radius: 1px;
    width: 2px;
    top: 50%;
    left: 50%;
    height: 17px;
    margin: -9px 0 0 -1px;
    background: var(--arrow);
  }
  &:after {
    width: 60px;
    height: 60px;
    transform-origin: 50% 0;
    border-radius: 0 0 80% 80%;
    background: var(--success);
    top: 0;
    left: 0;
    transform: scaleY(0);
  }
  svg {
    display: block;
    position: absolute;
    width: 20px;
    height: 20px;
    left: 50%;
    top: 50%;
    margin: -9px 0 0 -10px;
    fill: none;
    z-index: 1;
    stroke-width: 2px;
    stroke: var(--arrow);
    stroke-linecap: round;
    stroke-linejoin: round;
  }
}
&.loading {
  ul {
    animation: text calc(var(--duration) * 1ms) linear forwards calc(var(--duration) * .065ms);
  }
  & > div {
    &:before {
      animation: line calc(var(--duration) * 1ms) linear forwards calc(var(--duration) * .065ms);
    }
    &:after {
      animation: background calc(var(--duration) * 1ms) linear forwards calc(var(--duration) * .065ms);
    }
    svg {
      animation: svg calc(var(--duration) * 1ms) linear forwards calc(var(--duration) * .065ms);
    }
  }
}
}
</style>
