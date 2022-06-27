<script lang="ts" setup>
  import { ref, reactive, computed, StyleValue } from 'vue'
  const style: StyleValue = reactive({
    fontSize: "16",
    color: "#000",
    backgroundColor:"fff",
    borderRadius:"5",
    opacity:"1",
  })
  const styleObject = computed<StyleValue>(() => {
    return  {
      fontSize : style.fontSize + "px",
      color: style.color,
      backgroundColor: style.backgroundColor,
      borderRadius: style.borderRadius + "%",
      opacity: style.opacity,
    }
  });
  const isDisabled = ref<boolean>(false)
  const text = ref<String>("Button Customizer")
</script>

<template>
  <div id="app">
    <div>
      <input type="button" :style="styleObject" :disabled="isDisabled" :value="text">
    </div>
    <div>
      <label>color</label>
      <input type="color" v-model="style.color" min="10" max="100" step="1">{{style.fontSize}}
    </div>
    <div>
      <label>background-color</label>
      <input type="color" v-model="style.backgroundColor">
    </div>
    <div>
      <label>border-radius</label>
      <input type="range" v-model="style.borderRadius" min="0" max="100" step="1">{{style.borderRadius}}
    </div>
    <div>
      <label>font-size</label>
      <input type="range" v-model="style.fontSize">{{style.fontSize}}
    </div>
    <div>
      <label>opacity</label>
      <input type="range" v-model="style.opacity" min="0" max="1" step="0.1">{{style.opacity}}
    </div>
    <div>
      <label>disabled属性</label>
      <input type="checkbox" v-model="isDisabled">
    </div>
    <div>
      <label>buttonに表示するテキスト</label>
      <input type="text" v-model="text">
    </div>
  </div>
</template>
