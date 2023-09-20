<script></script>

<main>
  <picture>
    <source media="(min-width:1200px)" srcset="images/image-hero-desktop.png" />
    <img class="hero" src="images/image-hero-mobile.png" alt="remote work" />
  </picture>

  <div class="hero-content">
    <h1>Make remote work</h1>
    <p>
      Get your team in sync, no matter your location. Streamline processes,
      create team rituals, and watch productivity soar.
    </p>
    <button>Learn More</button>
    <div class="clients">
      <img class="client-data" src="images/client-databiz.svg" alt="databiz" />
      <img
        class="client-audio"
        src="images/client-audiophile.svg"
        alt="audiophile"
      />
      <img class="client-meet" src="images/client-meet.svg" alt="meet" />
      <img class="client-maker" src="images/client-maker.svg" alt="maker" />
    </div>
  </div>
</main>

<style>
  main {
    display: flex;
    flex-direction: column;
    gap: 3rem;
    height: calc(100vh - 80px);
    align-items: center;
  }

  img.hero {
    max-width: 100%;
    height: fit-content;
  }

  .hero-content {
    padding-inline: 1rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1rem;
    width: 100%;
  }

  h1 {
    font-size: 2rem;
    font-weight: 700;
    text-align: center;
  }

  p {
    color: #686868;
    text-align: center;
    line-height: 26px;
  }

  .clients {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-block-start: 2rem;
    width: 100%;
  }

  img.client-data {
    height: 14px;
  }
  img.client-audio {
    height: 26px;
  }
  img.client-meet {
    height: 14px;
  }
  img.client-maker {
    height: 17px;
  }

  button {
    background: #151515;
    border-radius: 15px;
    color: #fafafa;
    width: 136px;
    height: 48px;
    font-weight: 600;
    transition: all 500ms ease-in;
  }

  button:hover {
    background: #fafafa;
    color: #151515;
    border: 1.5px solid #151515;
  }

  @media screen and (min-width: 1200px) {
    picture {
      display: flex;
      justify-content: center;
    }
    main {
      padding-inline: 2rem;
      display: grid;
      grid-template-areas: "hero-content hero";
      grid-template-columns: 1fr 1fr;
      height: fit-content;
    }

    img.hero {
      grid-area: hero;
      height: 640px;
    }

    .hero-content {
      grid-area: hero-content;
      align-items: flex-start;
      justify-content: space-between;
      gap: 3rem;
      /* height: 100%; */
    }

    h1 {
      width: 530px;
      font-size: 80px;
      line-height: 80px;
      letter-spacing: -1.111px;
      text-align: start;
      letter-spacing: -1.111px;
    }

    p {
      width: 445px;
      font-size: 18px;
      line-height: 28px;
      text-align: start;
    }

    button {
      width: 163px;
      height: 56px;
      font-size: 18px;
      line-height: 28px;
    }

    .clients {
      display: flex;
      gap: 2.5rem;
      width: unset;
    }
    img.client-data {
      height: 20px;
    }
    img.client-audio {
      height: 34px;
    }
    img.client-meet {
      height: 20px;
    }
    img.client-maker {
      height: 24px;
    }
  }
</style>
