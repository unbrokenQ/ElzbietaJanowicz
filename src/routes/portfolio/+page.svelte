<script lang="ts">
  import { onMount } from "svelte";
  import Background from "../../components/Background.svelte";
  import { register } from "swiper/element/bundle";
  import { ChevronLeft, ChevronRight } from "lucide-svelte";

  let swiperEl: HTMLElement | undefined;
  let swiperSecond: HTMLElement | undefined;

  function updatePaginationStyles() {
    if (!swiperEl) return;
    const bullets = swiperEl.querySelectorAll(".swiper-pagination-bullet");
    bullets.forEach((bullet) => {
      bullet.setAttribute(
        "style",
        "background: #cccccc !important; opacity: 0.7 !important;"
      );
      if (bullet.classList.contains("swiper-pagination-bullet-active")) {
        bullet.setAttribute(
          "style",
          "background: #ff0000 !important; opacity: 1 !important;"
        );
      }
    });
  }

  onMount(() => {
    register();

    if (swiperEl) {
      const swiperParams = {
        slidesPerView: 1,
        spaceBetween: 20,

        loop: true,
        autoplay: {
          delay: 2000,
          disableOnInteraction: false,
        },
      };

      Object.assign(swiperEl, swiperParams);
      (swiperEl as any).initialize();
      swiperEl.addEventListener("slidechange", updatePaginationStyles);
    }
    if (swiperSecond) {
      const swiperParams = {
        slidesPerView: 1,
        spaceBetween: 20,

        loop: true,
        autoplay: {
          delay: 2000,
          disableOnInteraction: false,
        },
      };

      Object.assign(swiperSecond, swiperParams);
      (swiperSecond as any).initialize();
      swiperSecond.addEventListener("slidechange", updatePaginationStyles);
    }
  });

  function nextSlide(swiperEl: HTMLElement | undefined) {
    if (swiperEl) {
      (swiperEl as any).swiper.slideNext();
    }
  }
  function prevSlide(swiperEl: HTMLElement | undefined) {
    if (swiperEl) {
      (swiperEl as any).swiper.slidePrev();
    }
  }

  const firstBooks = [
    "/assets/first_books/1.png",
    "/assets/first_books/2.png",
    "/assets/first_books/3.png",
    "/assets/first_books/4.png",
    "/assets/first_books/5.png",
    "/assets/first_books/6.png",
    "/assets/first_books/7.png",
    "/assets/first_books/8.png",
    "/assets/first_books/9.png",
    "/assets/first_books/10.png",
  ];
  const secondBooks = [
    "/assets/second_books/1.png",
    "/assets/second_books/2.png",
    "/assets/second_books/3.png",
    "/assets/second_books/4.png",
    "/assets/second_books/5.png",
    "/assets/second_books/6.png",
    "/assets/second_books/7.png",
    "/assets/second_books/8.png",
    "/assets/second_books/9.png",
    "/assets/second_books/10.png",
    "/assets/second_books/11.png",
    "/assets/second_books/12.png",
  ];
</script>

<div class="w-full h-full">
  <section class="bg-[#4f0d20] w-full">
    <div class="w-full px-[10px] pt-[140px]">
      <h1 class="text-[40px] font-family-bebas text-white py-[20px]">
        PORTFOLIO
      </h1>
    </div>
    <div class="w-full pt-[20px] md:flex">
      <img
        class="w-full object-cover"
        src="/assets/as_good_dead.png"
        alt="as_good_dead"
        draggable="false"
      />
      <img
        class="w-full object-cover"
        src="/assets/good_girl.png"
        alt="good_girl"
        draggable="false"
      />
    </div>
  </section>
  <section>
    <div
      class="w-full grid grid-cols-1 gap-6 px-[20px] py-[60px] md:grid-cols-2"
    >
      <img
        src="/assets/moon_and_pixora.png"
        alt="moon_and_pixora"
        draggable="false"
      />
      <img src="/assets/aero_woomen.png" alt="aero_woomen" draggable="false" />
      <img src="/assets/abctracts.png" alt="abctracts" draggable="false" />
      <img src="/assets/loopies.png" alt="loopies" draggable="false" />
    </div>
  </section>
  <section class="relative">
    <div class="w-full grid grid-cols-1 py-[60px] md:grid-cols-2">
      <img src="/assets/woomen_face.png" alt="woomen_face" draggable="false" />
      <img src="/assets/woomen_body.png" alt="woomen_body" draggable="false" />
      <img
        src="/assets/woomen_face_plus.png"
        alt="woomen_face_plus"
        draggable="false"
      />
      <img
        src="/assets/woomen_light.png"
        alt="woomen_light"
        draggable="false"
      />
    </div>
    <Background rgdba="79, 13, 32" />
  </section>
  <div class="w-full h-full flex items-center bg-[#4f0d20] max-h-[640px]">
    <button
      class="hidden p-4 bg-gray-400/40 text-white rounded-full m-5 md:block"
      on:click={() => prevSlide(swiperEl)}><ChevronLeft size={30} /></button
    >
    <swiper-container
      class="w-full max-w-full py-[60px]"
      init="false"
      bind:this={swiperEl}
    >
      {#each firstBooks as book}
        <swiper-slide>
          <img class=" h-full" src={book} alt="book" draggable="false" />
        </swiper-slide>
      {/each}
    </swiper-container>
    <button
      class="hidden p-4 bg-gray-400/40 text-white rounded-full m-5 md:block"
      on:click={() => nextSlide(swiperEl)}><ChevronRight size={30} /></button
    >
  </div>
  <div class="w-full h-full flex items-center bg-white max-h-[640px]">
    <button
      class="hidden p-4 bg-gray-400/90 text-white rounded-full m-5 md:block"
      on:click={() => prevSlide(swiperSecond)}><ChevronLeft size={30} /></button
    >
    <swiper-container
      class="w-full max-w-full py-[60px]"
      init="false"
      bind:this={swiperSecond}
    >
      {#each secondBooks as book}
        <swiper-slide>
          <img class=" h-full" src={book} alt="book" draggable="false" />
        </swiper-slide>
      {/each}
    </swiper-container>
    <button
      class="hidden p-4 bg-gray-400/90 text-white rounded-full m-5 md:block"
      on:click={() => nextSlide(swiperSecond)}
      ><ChevronRight size={30} /></button
    >
  </div>
</div>

<style>
  @import "swiper/css";
  @import "swiper/css/navigation";
  @import "swiper/css/pagination";

  :global(swiper-container) {
    width: 100% !important;
    height: 100%;
    overflow: hidden;
    display: block;
  }

  :global(swiper-slide) {
    width: 100% !important;
    height: 100% !important;
    padding-top: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 24px;
    box-sizing: border-box;
  }
</style>
