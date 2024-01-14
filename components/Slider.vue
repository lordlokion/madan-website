<template>
  <div id="default-carousel" class="relative m-auto max-w-7xl w-full lg:w-2/3" data-carousel="slide">
    <div class="flex flex-col lg:flex-row">
      <!-- Slider (2/3 of the screen) -->
      <div class="relative w-full lg:w-2/3 lg:mr-4">
        <div class="relative h-48 lg:h-60 xl:h-80 rounded-lg overflow-hidden">
          <!-- Display the current image -->
          <div
            v-for="(image, index) in images"
            :key="index"
            :class="[
              'absolute inset-0 w-full h-full object-cover transition-opacity',
              { hidden: currentIndex !== index },
            ]"
            data-carousel-item
          >
            <img :src="image.src" :alt="image.alt" class="w-full h-full object-cover rounded-lg" />
          </div>
        </div>
      </div>

      <!-- YouTube video container (1/3 of the screen) -->
      <div class="w-full lg:w-1/3 mt-4 lg:mt-0">
        <!-- You can embed your YouTube video here using an iframe or any other method you prefer -->
        <Youtube />
      </div>
    </div>

    <!-- Slider indicators -->
    <div class="absolute z-30 flex -translate-x-1/2 bottom-3 left-1/2 space-x-3 rtl:space-x-reverse">
      <button
        v-for="(image, index) in images"
        :key="index"
        type="button"
        :class="{
          'w-2 h-2 rounded-full': true,
          'bg-white': currentIndex === index,
          'bg-white/30 dark:bg-gray-800/30': currentIndex !== index,
        }"
        @click="setCurrentIndex(index)"
        aria-current="true"
        :aria-label="`Slide ${index + 1}`"
        data-carousel-slide-to="index"
      ></button>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const images = [
  { src: "/images/S2.png", alt: "Slide 2" },
  { src: "/images/lm.png", alt: "Slide 2" },
  { src: "/images/pc.png", alt: "Slide 2" },
  { src: "/images/dp.png", alt: "Slide 2" },
  // Add more images as needed
];

const currentIndex = ref(0);

const setCurrentIndex = (index) => {
  currentIndex.value = index;
};

const nextSlide = () => {
  currentIndex.value = (currentIndex.value + 1) % images.length;
};

// Auto slide after 10 seconds
let intervalId;

onMounted(() => {
  intervalId = setInterval(() => {
    nextSlide();
  }, 10000); // 10 seconds
});

onUnmounted(() => {
  clearInterval(intervalId);
});

</script>
