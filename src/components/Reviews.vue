
<template>
  <section class="reviews">
    <div class="container reviews-container">
      <h1 class="reviews__title title-block">Отзывы о Барселоне</h1>
      <swiper
        :slidesPerView="3"
        :spaceBetween="120"
        :pagination="{
          clickable: true,
        }"
        :modules="modules"
        class="mySwiper"
      >
        <swiper-slide
          v-for="item in accounts"
          :key="item.id"
          @click="updateSelected(item)"
        >
          <div class="reviews-slide">
            <div class="reviews-slide__username">
              <div class="reviews-slide__username-left">
                <img
                  src="../image/avatar.png"
                  alt="Аватар"
                  class="reviews-slide__username-left__img"
                />
              </div>
              <span class="reviews-slide__username-right">{{ item.name }}</span>
            </div>
            <div class="reviews-slide__city">
              <span class="reviews-slide__city-bold">{{ item.country }}</span>
              <span class="reviews-slide__city-about"> — О городе:</span>
            </div>
            <p class="reviews-slide__descr">
              {{ item.countryText }}
            </p>
            <div class="reviews-slide__gallery">
              <div class="reviews-slide__gallery-item">
                <img
                  src="../image/city1.png"
                  alt="Город"
                  class="reviews-slide__gallery-item__img"
                />
              </div>
              <div class="reviews-slide__gallery-item">
                <img
                  src="../image/city2.png"
                  alt="Город"
                  class="reviews-slide__gallery-item__img"
                />
              </div>
              <div class="reviews-slide__gallery-item">
                <img
                  src="../image/city3.png"
                  alt="Город"
                  class="reviews-slide__gallery-item__img"
                />
              </div>
              <div class="reviews-slide__gallery-item">
                <img
                  src="../image/city3.png"
                  alt="Город"
                  class="reviews-slide__gallery-item__img"
                />
                <div class="gallery-overlay">+7</div>
              </div>
            </div>
            <div class="reviews-slide__bottom">
              <div class="reviews-slide__bottom-left">
                <span class="reviews-slide__bottom-left__item"
                  >около {{ item.year }} года назад</span
                >
                <span class="reviews-slide__bottom-left__item"
                  >{{ item.comment }} комментариев</span
                >
              </div>
              <div class="reviews-slide__bottom-right">
                <button class="reviews-slide__bottom-right-button">
                  <svg
                    width="14"
                    height="16"
                    viewBox="0 0 14 16"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <g clip-path="url(#clip0_1_111)">
                      <path
                        fill-rule="evenodd"
                        clip-rule="evenodd"
                        d="M1.00025 10.063L3.75025 8.688L5.06225 4.219C5.06225 4.219 4.84425 2.219 4.71925 1C7.03125 1 7.15625 3.969 7.15625 3.969L7.40625 6.063C7.40625 6.063 9.77025 5.421 10.6253 5.251C11.8753 5.001 12.6883 5.688 12.3753 7C13.0313 7.407 13.0003 8.563 12.4693 9.063C12.9383 9.594 12.8443 10.844 12.1883 11.313C12.3503 12.431 11.9693 12.688 11.6883 12.938C11.4063 13.188 9.93825 14.001 8.28125 14.001C6.62525 14.001 5.18725 13.657 5.18725 13.657L3.03125 15C3.03125 15 2.21925 14.469 1.59425 12.876C0.969252 11.282 1.00025 10.063 1.00025 10.063Z"
                        stroke="#A0A0A0"
                        stroke-linejoin="round"
                      />
                    </g>
                    <defs>
                      <clipPath id="clip0_1_111">
                        <rect width="14" height="16" fill="white" />
                      </clipPath>
                    </defs>
                  </svg>
                  <span class="reviews-slide__bottom-right-button__like">{{
                    item.like
                  }}</span>
                </button>
              </div>
            </div>
          </div>
        </swiper-slide>
        <button class="reviews-button">Все отзывы</button>
      </swiper>
    </div>
  </section>

  <ModalSlide
    :imgGallery="account.imagesCountry"
    v-if="showReviews"
    @close="closeModal"
  />
</template>

<script>
import ModalSlide from "./ModalSlide.vue";
import { Swiper, SwiperSlide } from "swiper/vue";

// Import Swiper styles
import "swiper/css";

import "swiper/css/pagination";

// import required modules
import { Pagination } from "swiper/modules";
export default {
  name: "ReviewsBlock",
  components: {
    Swiper,
    SwiperSlide,
    ModalSlide,
  },
  data() {
    return {
      showReviews: false,
      account: {},
      accounts: [
        {
          id: 1,
          name: "Наталия Полянская",
          country: "Барселона",
          countryText:
            "Барселона – моя третья большая любовь, после Вены и Крита. Это город, в который я каждый раз возвращаюсь с огромным удовольствием, всем рекомендую хоть раз там побывать и осмотреть ...",
          year: "1",
          comment: "9",
          like: "9",
          imagesCountry: [
            {
              imageCountry:
                "https://media.gettyimages.com/id/1301579230/photo/spanish-cities-the-sacred-barcelona-family.jpg?s=2048x2048&w=gi&k=20&c=TIoJzh3sxx-O6kQ009Jhc6xXeUanXYFUfcpd9mclVeI=",
            },
            {
              imageCountry:
                "https://media.gettyimages.com/id/1133826808/photo/pla%C3%A7a-despanya-long-exposure-at-sunset-in-barcelona.webp?s=2048x2048&w=gi&k=20&c=OP-yNNXa8dIe7ypHpuvPKfavQomjF_BRKGNlzCYCQlw=",
            },
            {
              imageCountry:
                "https://media.gettyimages.com/id/1455056257/photo/tibidabo-mountain-and-sagrat-cor-church-at-sunset-barcelona-spain.jpg?s=2048x2048&w=gi&k=20&c=b2GZJmwgg6wVmqodS0D3zivxFvPRpYrm_tVKAbUGDH0=",
            },
          ],
        },
        {
          id: 2,
          name: "Elena Bulgakova",
          country: "Барселона",
          countryText:
            "Плюсы города: весь город одни плюсы! Минусы города: не видела. В наш марафон по Европе не вписалось 2 испанских города от усталости - решили остаток путешествия провести в Барселоне ...",
          year: "1",
          comment: "5",
          like: "1",
          imagesCountry: [
            {
              imageCountry:
                "https://media.gettyimages.com/id/1354946258/photo/barcelona-skyline-at-sunrise-catalonia-spain.jpg?s=2048x2048&w=gi&k=20&c=RRJR_K0nCRxg6f_KW3rXrhq_-d6oXEZ_ES5tBFFIhqw=",
            },
            {
              imageCountry:
                "https://media.gettyimages.com/id/1194266968/photo/smiling-vacationers-holding-hands-and-walking-in-barcelona.jpg?s=2048x2048&w=gi&k=20&c=f3euRzusD9JGmyX4H1-3Xd3Ws30wykcaciRfO0dQUlQ=",
            },
            {
              imageCountry:
                "https://media.gettyimages.com/id/1143273440/photo/aerial-view-of-barcelona-skyline-with-sagrat-cor-temple-catalonia-spain.jpg?s=2048x2048&w=gi&k=20&c=_9qvCXN0Uv75LcX1mLJ72MnscOStcpysAFaz5W87EYI=",
            },
          ],
        },
        {
          id: 3,
          name: "Виктория Газова",
          country: "Англия",
          countryText:
            "Англия – моя третья большая любовь, после Вены и Крита. Это город, в который я каждый раз возвращаюсь с огромным удовольствием, всем рекомендую хоть раз там побывать и осмотреть ...",
          year: "1",
          comment: "6",
          like: "9",
          imagesCountry: [
            {
              imageCountry:
                "https://media.gettyimages.com/id/1161610632/photo/high-angle-view-over-barcelona-spain-at-sunset.jpg?s=2048x2048&w=gi&k=20&c=soh_ZbGWmEfhnydJ3D3LEBFOOWASHn_Uq5B-4tdFoCs=",
            },
            {
              imageCountry:
                "https://media.gettyimages.com/id/111728536/photo/barcelona-sagrada-familia.jpg?s=2048x2048&w=gi&k=20&c=ytgHSkT6eECc79rsZ4KuXCj18jhIQa7hWFB2WFXDl14=",
            },
            {
              imageCountry:
                "https://media.gettyimages.com/id/1255871728/photo/barceloneta-beach.jpg?s=2048x2048&w=gi&k=20&c=OrGtC_h-CY5srxvpcmLSzZK-OU_DUjAeHvIYs0X_7Xo=",
            },
          ],
        },
        {
          id: 4,
          name: "Анна Лухо",
          country: "Англия",
          countryText:
            "Англия – моя третья большая любовь, после Вены и Крита. Это город, в который я каждый раз возвращаюсь с огромным удовольствием, всем рекомендую хоть раз там побывать и осмотреть ...",
          year: "1",
          comment: "6",
          like: "9",
          imagesCountry: [
            {
              imageCountry:
                "https://media.gettyimages.com/id/1161610632/photo/high-angle-view-over-barcelona-spain-at-sunset.jpg?s=2048x2048&w=gi&k=20&c=soh_ZbGWmEfhnydJ3D3LEBFOOWASHn_Uq5B-4tdFoCs=",
            },
            {
              imageCountry:
                "https://media.gettyimages.com/id/111728536/photo/barcelona-sagrada-familia.jpg?s=2048x2048&w=gi&k=20&c=ytgHSkT6eECc79rsZ4KuXCj18jhIQa7hWFB2WFXDl14=",
            },
            {
              imageCountry:
                "https://media.gettyimages.com/id/1255871728/photo/barceloneta-beach.jpg?s=2048x2048&w=gi&k=20&c=OrGtC_h-CY5srxvpcmLSzZK-OU_DUjAeHvIYs0X_7Xo=",
            },
          ],
        },
        {
          id: 5,
          name: "Ульяна Максимовна",
          country: "Англия",
          countryText:
            "Англия – моя третья большая любовь, после Вены и Крита. Это город, в который я каждый раз возвращаюсь с огромным удовольствием, всем рекомендую хоть раз там побывать и осмотреть ...",
          year: "1",
          comment: "6",
          like: "9",
          imagesCountry: [
            {
              imageCountry:
                "https://media.gettyimages.com/id/1161610632/photo/high-angle-view-over-barcelona-spain-at-sunset.jpg?s=2048x2048&w=gi&k=20&c=soh_ZbGWmEfhnydJ3D3LEBFOOWASHn_Uq5B-4tdFoCs=",
            },
            {
              imageCountry:
                "https://media.gettyimages.com/id/111728536/photo/barcelona-sagrada-familia.jpg?s=2048x2048&w=gi&k=20&c=ytgHSkT6eECc79rsZ4KuXCj18jhIQa7hWFB2WFXDl14=",
            },
            {
              imageCountry:
                "https://media.gettyimages.com/id/1255871728/photo/barceloneta-beach.jpg?s=2048x2048&w=gi&k=20&c=OrGtC_h-CY5srxvpcmLSzZK-OU_DUjAeHvIYs0X_7Xo=",
            },
          ],
        },
        {
          id: 6,
          name: "Таисия Елисеевна",
          country: "Англия",
          countryText:
            "Англия – моя третья большая любовь, после Вены и Крита. Это город, в который я каждый раз возвращаюсь с огромным удовольствием, всем рекомендую хоть раз там побывать и осмотреть ...",
          year: "1",
          comment: "6",
          like: "9",
          imagesCountry: [
            {
              imageCountry:
                "https://media.gettyimages.com/id/1161610632/photo/high-angle-view-over-barcelona-spain-at-sunset.jpg?s=2048x2048&w=gi&k=20&c=soh_ZbGWmEfhnydJ3D3LEBFOOWASHn_Uq5B-4tdFoCs=",
            },
            {
              imageCountry:
                "https://media.gettyimages.com/id/111728536/photo/barcelona-sagrada-familia.jpg?s=2048x2048&w=gi&k=20&c=ytgHSkT6eECc79rsZ4KuXCj18jhIQa7hWFB2WFXDl14=",
            },
            {
              imageCountry:
                "https://media.gettyimages.com/id/1255871728/photo/barceloneta-beach.jpg?s=2048x2048&w=gi&k=20&c=OrGtC_h-CY5srxvpcmLSzZK-OU_DUjAeHvIYs0X_7Xo=",
            },
          ],
        },
      ],
    };
  },
  methods: {
    updateSelected(selectedItem) {
      this.account = selectedItem;
      this.showReviews = !this.showReviews;
    },
    closeModal() {
      this.showReviews = !this.showReviews;
    },
  },
  watch: {
    showReviews: function () {
      if (this.showReviews) {
        document.documentElement.style.overflow = "hidden";
        return;
      }
      document.documentElement.style.overflow = "auto";
    },
  },
  setup() {
    return {
      modules: [Pagination],
    };
  },
};
</script>