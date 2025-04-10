<script lang="ts">
  import { X } from "lucide-svelte";
  import { page } from "$app/state";

  export let isOpen: boolean = false;
  export let onClose: () => void;
</script>

<div
  class="w-full max-w-[400px] h-full bg-black fixed top-0 transition-transform z-20 flex flex-col"
  style={`transform: translateX(${isOpen ? "0%" : "-100%"})`}
>
  <div class="w-full flex items-center min-h-[100px]">
    <button on:click={onClose} aria-label="close" class="px-[20px] text-white">
      <X />
    </button>
    <p class="mx-auto text-white font-light text-[16px]">Elzbieta Janowicz</p>
  </div>
  <div class="text-white flex flex-col items-start p-[20px]">
    <a
      class="text-xl py-[30px]"
      class:border-b-2={page.url.pathname === "/"}
      class:border-white={page.url.pathname === "/"}
      href="/"
    >
      About Me
    </a>
    <a
      class="text-xl py-[30px] "
      class:border-b-2={page.url.pathname === "/portfolio"}
      class:border-white={page.url.pathname === "/portfolio"}
      href="/portfolio"
    >
      Portfolio
    </a>
  </div>
  <a
    class="mx-auto bg-white font-light rounded-sm px-[30px] py-[10px] mb-[30px] mt-auto"
    href="mailto:elayanovich@gmail.com">Book Now</a
  >
</div>

<button
  class="w-full h-screen fixed bg-black/60 transition-all z-10"
  style={`visibility: ${isOpen ? "visible" : "hidden"}; opacity: ${isOpen ? "1" : "0"};`}
  aria-label="drawer"
  on:click={onClose}
>
</button>
