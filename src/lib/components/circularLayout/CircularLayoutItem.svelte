<script lang="ts">
  import { getContext } from "svelte";
  import { key, type CircularLayoutContext } from "./CircularLayout.svelte";

  let content: HTMLDivElement;

  $: {
    if(content) {
      const { setContent } = getContext<CircularLayoutContext>(key);
      setContent(content);
    }
  }
</script>

<div bind:this={content}>
  <slot />
</div>
