<script lang="ts">
  import type { UtilityType } from "$lib/utilities/UtilityType";
  import { tick } from "svelte";

  export let position: UtilityType.Vector2 = {x: 0, y: 0};
  export let showContextMenu: boolean = false;

  const onPageClick = () => {
    showContextMenu = false;
  };

  const onContextMenu = async (ev: MouseEvent) => {
    showContextMenu = false;
    position = {
      x: ev.x,
      y: ev.y,
    };
    await tick();
    showContextMenu = true;
  };
</script>

<svelte:window on:contextmenu|preventDefault={onContextMenu} on:click={onPageClick} />

{#if showContextMenu}
  <slot position={position} />
{/if}
