<script>
  let isExpanded = false;
  let src = "images/icon-arrow-down.svg";

  const clickOutside = (element, callbackFunction) => {
    const onClick = (event) => {
      if (!element.contains(event.target)) {
        callbackFunction();
      }
    };
    document.body.addEventListener("click", onClick);
    return {
      update(newCallbackFunction) {
        callbackFunction = newCallbackFunction;
      },
      destroy() {
        document.body.removeEventListener("click", onClick);
      },
    };
  };

  const toggle = () => {
    isExpanded = !isExpanded;
    isExpanded
      ? (src = "images/icon-arrow-up.svg")
      : (src = "images/icon-arrow-down.svg");
  };

  const hide = () => {
    isExpanded = false;
    src = "images/icon-arrow-down.svg";
  };

  const show = () => {
    isExpanded = true;
    src = "images/icon-arrow-up.svg";
  };

  export let link;
</script>

<li class="nav-item">
  <button
    class="dropdown-item"
    on:click={() => toggle()}
    use:clickOutside={() => hide()}
  >
    {link.name}
    <img {src} alt="arrow" />
  </button>
  {#if isExpanded}
    <ul class="expanded-nav">
      {#each link.links as subLink}
        <li>
          {#if subLink.imgSrc !== undefined && subLink.alt !== undefined}
            <a href={subLink.url}>
              <img src={subLink.imgSrc} alt={subLink.alt} />
              {subLink.text}
            </a>
          {:else}
            <a href={subLink.url}>{subLink.text}</a>
          {/if}
        </li>
      {/each}
    </ul>
  {/if}
</li>

<style>
  ul.expanded-nav {
    display: flex;
    flex-direction: column;
    padding-inline: 48px;
    padding-block: 1.5rem;
    gap: 1rem;
  }
  button.dropdown-item {
    display: flex;
    align-items: center;
    gap: 1rem;
    color: #686868;
  }

  button.dropdown-item:hover {
    color: #151515;
  }

  a {
    display: flex;
    gap: 1rem;
    align-items: center;
  }

  @media screen and (min-width: 1200px) {
    li.nav-item {
      position: relative;
    }

    ul.expanded-nav {
      position: absolute;
      top: calc(100% + 20px);
      right: 0;
      z-index: 10;
      background: #fff;
      border-radius: 10px;
      box-shadow: 0px 10px 40px 0px rgba(0, 0, 0, 0.15);
      text-wrap: nowrap;
      padding-inline: 1rem;
      font-size: 14px;
      line-height: 1rem;
    }

    ul.expanded-nav li a {
      margin-inline-end: 1rem;
    }
  }
</style>
