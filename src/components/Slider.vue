<script>
export default {
  props: {
    initialValue: Boolean
  },
  methods: {
    handleChange(e) {
      this.$emit('change', e.target.checked);
    },
  },
};
</script>

<template>
  <label class="switch">
    <input type="checkbox" @change.stop="handleChange" :checked="initialValue" aria-label="Dark theme switcher"/>
    <div class="slider round" />
  </label>
</template>

<style scoped>
.switch {
  position: relative;
  display: inline-block;
  width: 44px;
  height: 24px;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: var(--color-switcher);
  -webkit-transition: 0.4s linear;
  transition: 0.4s linear;
}

.slider:before {
  position: absolute;
  content: "";
  height: 18px;
  width: 18px;
  left: 23px;
  bottom: 3px;
  background-color: white;
  -webkit-transition: 0.4s linear;
  transition: 0.4s linear;
}

input:checked + .slider {
  background-image: var(--color-switcher__checked);
}

input:focus + .slider {
  box-shadow: 0 0 1px var(--color-switcher);
}

input:checked + .slider:before {
  -webkit-transform: translateX(-20px);
  -ms-transform: translateX(-20px);
  transform: translateX(-20px);
}

.slider.round {
  border-radius: 24px;
}

.slider.round:before {
  border-radius: 50%;
}
</style>
