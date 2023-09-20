<script>
  import Dropdown from "./Dropdown.svelte";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let isVisible = false;

  const links = [
    {
      name: "Features",
      links: [
        {
          text: "Todo List",
          url: "/",
          imgSrc: "images/icon-todo.svg",
          alt: "todo",
        },
        {
          text: "Calendar",
          url: "/",
          imgSrc: "images/icon-calendar.svg",
          alt: "calendar",
        },
        {
          text: "Reminders",
          url: "/",
          imgSrc: "images/icon-reminders.svg",
          alt: "reminders",
        },
        {
          text: "Planning",
          url: "/",
          imgSrc: "images/icon-planning.svg",
          alt: "planning",
        },
      ],
    },
    {
      name: "Company",
      links: [
        { text: "History", url: "/" },
        { text: "Our Team", url: "/" },
        { text: "Blog", url: "/" },
      ],
    },
  ];
</script>

<div class="offcanvas {isVisible ? 'show' : ''}">
  <div class="overlay" />
  <div class="offcanvas-content">
    <span class="offcanvas-header">
      <button on:click={() => dispatch("closeOffCanvas", isVisible)}>
        <img src="images/icon-close-menu.svg" alt="close" />
      </button>
    </span>
    <ul class="offcanvas-nav">
      {#each links as link, i (i)}
        <Dropdown {link} />
      {/each}
      <li>
        <a href="/">Careers</a>
      </li>
      <li>
        <a href="/">About</a>
      </li>
    </ul>
    <div class="account">
      <a href="/">Login</a>
      <button class="register">Register</button>
    </div>
  </div>
</div>

<style>
  .offcanvas {
    visibility: hidden;
    opacity: 0;
    display: flex;
    position: fixed;
    height: 100vh;
    z-index: 100;
    width: 100%;
    top: 0;
    right: 0;
    transition: visibility 0s linear 300ms, opacity 300ms;
  }

  .offcanvas.show {
    opacity: 1;
    visibility: visible;
    transition: visibility 0s linear 0s, opacity 300ms;
  }

  .offcanvas-content {
    background: #fff;
    width: 70%;
  }
  .offcanvas-header {
    display: flex;
    justify-content: end;
    width: 100%;
    padding: 24px;
  }

  .overlay {
    opacity: 0.75;
    background: #151515;
    width: 30%;
  }

  ul.offcanvas-nav {
    display: flex;
    flex-direction: column;
    padding-inline: 24px;
    gap: 2rem;
  }

  .account {
    margin-block-start: 2rem;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    justify-content: center;
    align-items: center;
  }

  .account a {
    font-size: 14px;
  }

  button.register {
    color: #686868;
    font-weight: 500;
    line-height: 1rem;
    border-radius: 14px;
    border: 1.5px solid #686868;
    width: 195px;
    height: 42px;
    font-size: 14px;
  }

  button.register:hover {
    border: 1.5px solid #151515;
    color: #151515;
  }
</style>
