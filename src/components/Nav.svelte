<script>
  import { createEventDispatcher } from "svelte";
  import Dropdown from "./Dropdown.svelte";
  const dispatch = createEventDispatcher();

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

<nav>
  <img src="images/logo.svg" alt="logo" />
  <ul class="nav-items">
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
    <button>Login</button>
    <button class="register">Register</button>
  </div>
  <button class="menu" on:click={() => dispatch("showOffCanvas")}>
    <img src="images/icon-menu.svg" alt="menu" />
  </button>
</nav>

<style>
  nav {
    padding: 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 80px;
  }

  button {
    color: #686868;
  }

  button:hover {
    color: #151515;
  }

  button.register {
    border: 1px solid #686868;
    color: #686868;
  }

  button.register:hover {
    border: 1.5px solid #151515;
    color: #151515;
  }

  ul.nav-items {
    display: none;
  }

  .account {
    display: none;
  }

  @media screen and (min-width: 1200px) {
    nav {
      justify-content: unset;
    }
    button.menu {
      display: none;
    }

    ul.nav-items {
      display: flex;
      width: 100%;
      gap: 2rem;
      padding-inline: 2rem;
    }

    .account {
      display: flex;
      gap: 2rem;
      justify-content: unset;
      align-items: center;
    }

    .account button {
      font-size: 14px;
    }

    button.register {
      color: #686868;
      font-weight: 500;
      line-height: 1rem;
      border-radius: 14px;
      border: 1.5px solid #686868;
      width: 104px;
      height: 42px;
      font-size: 14px;
    }
  }
</style>
