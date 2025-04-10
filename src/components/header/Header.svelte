<script lang="ts">
  import { AlignJustify } from "lucide-svelte";
  import Drawer from "./Drawer.svelte";
  import { page } from "$app/state";
  import { onMount } from "svelte";

  let scrolledDown = false;

  onMount(() => {
    const handleScroll = () => {
      scrolledDown = window.scrollY > 0;
    };

    handleScroll();

    window.addEventListener("scroll", handleScroll);

    return () => {
      window.removeEventListener("scroll", handleScroll);
    };
  });

  let isOpen: boolean = false;
</script>

<header
  class="fixed w-full min-h-[100px] px-[20px] flex items-center z-10"
  class:bg-black={scrolledDown}
>
  <div class="flex items-center justify-between w-full">
    <button on:click={() => (isOpen = true)} class="text-white md:hidden">
      <AlignJustify />
    </button>
    <nav class="text-white mx-[20px] max-md:hidden" style="flex: 1 1 0;">
      <ul class="mr-[12px] flex items-center gap-2">
        <li>
          <a
            class="text-base p-[20px] border-transparent hover:border-b-2 hover:border-white"
            class:border-b-2={page.url.pathname === "/"}
            class:border-white={page.url.pathname === "/"}
            href="/"
          >
            About Me
          </a>
        </li>
        <li>
          <a
            class="text-base p-[20px] border-transparent hover:border-b-2 hover:border-white"
            class:border-b-2={page.url.pathname === "/portfolio"}
            class:border-white={page.url.pathname === "/portfolio"}
            href="/portfolio"
          >
            Portfolio
          </a>
        </li>
      </ul>
    </nav>
    <h2 class="mx-auto text-white font-light text-[16px]">Elzbieta Janowicz</h2>
    <div class="flex justify-end mx-[20px] max-md:hidden" style="flex: 1 1 0;">
      <a
        class="bg-white font-light rounded-sm px-[30px] py-[8px] hover:bg-white/90"
        href="mailto:elayanovich@gmail.com"
      >
        Book Now
      </a>
    </div>
  </div>
</header>
<Drawer {isOpen} onClose={() => (isOpen = false)} />
