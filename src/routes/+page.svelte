<script>
    import CircularLayout from "$lib/components/circularLayout/CircularLayout.svelte";
    import CircularLayoutItem from "$lib/components/circularLayout/CircularLayoutItem.svelte";
import ContextMenu from "$lib/components/contextMenu/ContextMenu.svelte";

</script>
<svelte:head>
	<title>Home</title>
	<meta name="description" content="ui demo by SvelteKit + tailwind" />
</svelte:head>

<section>
	<p>Hello World!</p>
</section>

<ContextMenu let:position>
  <CircularLayout centerPosition={position}>
    <CircularLayoutItem>Hello</CircularLayoutItem>
    <CircularLayoutItem>World</CircularLayoutItem>
    <CircularLayoutItem>Hello</CircularLayoutItem>
    <CircularLayoutItem>World</CircularLayoutItem>
  </CircularLayout>
</ContextMenu>
