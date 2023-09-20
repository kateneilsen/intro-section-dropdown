<script>
  import Nav from "./components/Nav.svelte";
  import Home from "./components/Home.svelte";
  import OffCanvas from "./components/OffCanvas.svelte";

  let isVisible = false;
  const showOffCanvas = () => {
    isVisible = true;
  };
</script>

<Nav on:showOffCanvas={() => (isVisible = true)} />
<OffCanvas {isVisible} on:closeOffCanvas={() => (isVisible = false)} />
<Home />
