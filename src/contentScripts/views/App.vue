<script setup lang="ts">
import { useDraggable, useToggle } from "@vueuse/core";
import "uno.css";

const el = ref<HTMLElement | null>(null);

// `style` will be a helper computed for `left: ?px; top: ?px;`
const { x, y, style } = useDraggable(el, {
  initialValue: { x: 40, y: 40 },
});

const [show, toggle] = useToggle(false);
</script>

<template>
  <Slider v-if="show" />
  <button
    ref="el"
    :style="style"
    class="flex w-15 h-15 rounded-full shadow cursor-pointer border-none fixed z-9999"
    bg="teal-600 hover:teal-700"
    @click="toggle()"
  >
    <pixelarticons-power class="block m-auto text-white text-xl" />
  </button>
</template>
