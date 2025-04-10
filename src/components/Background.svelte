<script lang="ts">
  import { onMount } from "svelte";
  export let rgdba: string;

  let opacity = 1;
  let elementRef: HTMLDivElement;

  function handleScroll() {
    if (!elementRef) return;

    const rect = elementRef.getBoundingClientRect();
    const windowHeight = window.innerHeight;
    const fadeThreshold = windowHeight * 1.4;

    if (rect.top <= fadeThreshold) {
      opacity = Math.max(0, rect.top / fadeThreshold);
    } else {
      opacity = 1;
    }
  }

  onMount(() => {
    handleScroll();
    window.addEventListener("scroll", handleScroll);
    return () => window.removeEventListener("scroll", handleScroll);
  });
</script>

<div
  class="box absolute top-0 w-full h-full"
  bind:this={elementRef}
  style="background-color: rgba({rgdba}, {opacity});"
></div>

<style>
  .box {
    transition: background-color 0.3s ease;
  }
</style>
