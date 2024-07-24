
<template>
  <div class="modal">

    <div class="modal-block">
      <swiper
      :pagination="{
        type: 'progressbar',
      }"
      :navigation="true"
      :modules="modules"
      class="modalGallery"
    >
      <swiper-slide v-for="(item, i) in imgGallery" :key="i" class="modal-block__country">
        <img
          :src="item.imageCountry"
          alt="Фото"
          class="modal-block__country-image"
        />
      </swiper-slide>
    </swiper>
    <button @click="close" class="modal-block__close">Закрыть</button>
    </div>
  </div>
</template>

<script>
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from "swiper/vue";

// Import Swiper styles
import "swiper/css";

import "swiper/css/pagination";
import "swiper/css/navigation";

// import required modules
import { Pagination, Navigation } from "swiper/modules";
export default {
  name: "ModalSlider",
  props: {
    imgGallery: {
      type: Array,
      required: true,
    },
  },
  methods: {
    close() {
      this.$emit("close");
    },
  },
  components: {
    Swiper,
    SwiperSlide,
  },
  setup() {
    return {
      modules: [Pagination, Navigation],
    };
  },
};
</script>