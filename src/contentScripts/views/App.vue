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
  <div
    :style="style"
    class="fixed right-0 bottom-0 m-5 z-100 flex items-end font-sans select-none leading-1em"
  >
    <div
      class="bg-white text-gray-800 rounded-lg shadow w-max h-min"
      p="x-4 y-2"
      m="y-auto r-2"
      transition="opacity duration-300"
      :class="show ? 'opacity-100' : 'opacity-0'"
    >
      <h1 class="text-lg">111Vitesse WebExt {{ x }}-{{ y }}-{{ style }}</h1>
      <SharedSubtitle />
    </div>

    <button
      ref="el"
      :style="style"
      class="flex w-15 h-15 rounded-full shadow cursor-pointer border-none fixed z-9999"
      bg="teal-600 hover:teal-700"
      @click="toggle()"
    >
      <pixelarticons-power class="block m-auto text-white text-xl" />
    </button>
  </div>
</template>
