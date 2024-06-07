<script lang="ts" context="module">
  export const key = Symbol();
  export type CircularLayoutContext = {
    setContent: (content: HTMLElement) => void,
  };
</script>

<script lang="ts">
    import type { UtilityType } from "$lib/utilities/UtilityType";

  import { setContext } from "svelte";

  export let centerPosition: UtilityType.Vector2;
  export let gap: number = 100;
  export let startRad: number = 0;
  export let positionStrategy: UtilityType.PositionStrategy = "absolute";

  let contents: HTMLElement[] = [];

  const setContent = (content: HTMLElement) => {
    contents.push(content);
    setPosition(contents);
  }

  const setPosition = (contents: HTMLElement[]) => {
    const count = Math.max(contents.length, 1);
    const difRad = Math.PI * 2 / count;

    contents.forEach((content, index) => {
      content.style.position = positionStrategy;
      content.style.left = `${Math.cos(startRad + difRad * index) * gap + centerPosition.x}px`;
      content.style.top = `${Math.sin(startRad + difRad * index) * gap + centerPosition.y}px`;
    });
  };

  
  setContext<CircularLayoutContext>(key, {
    setContent
  });
</script>

<slot />
