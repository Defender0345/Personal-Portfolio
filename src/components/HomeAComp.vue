<script setup></script>

<template>
  <section id="home-a" class="text-center py-2">
    <div class="container">
      <h1>Welcome To my Portfolio</h1>
      <div class="bottom-line"></div>
      <h2 class="section-title">Specializing in</h2>
      <div class="bottom-line"></div>
      <p class="lead">Front-End & Back-End Web development</p>
      <div class="specials">
        <div>
          <i class="fas fa-file-alt fa-2x"></i>
          <h3>Architecture</h3>
          <p>
            Analyzing overall requirements of a software eco-system and research and determine the
            best technology stack applicable.
          </p>
        </div>
        <div>
          <i class="fas fa-desktop fa-2x"></i>
          <h3>UI/UX</h3>
          <p>
            Constructing UI (user interface) and UX (User experience) using industry standards and
            best practices. I tend to prefer material UI. I can utilize designer-provided designs,
            and cut them up into constituent parts (CSS, HTML elements and Images)
          </p>
        </div>
        <div>
          <i class="fas fa-thumbs-up fa-2x"></i>
          <h3>Back-End Systems</h3>
          <p>
            Constructing back-end systems in the form of Web APIs tiered layers such as business
            layers and database access layers and repositories. My backend languages of choice are
            NodeJS and C# but am always keen to broaden into other languages.
          </p>
        </div>
        <div>
          <i class="fas fa-object-ungroup fa-2x"></i>
          <h3>Visual Design</h3>
          <p>
            Using a wide array off graphics tools to construct design elements, graphics and
            mockups.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss">
@import '@/assets/_shared.scss';
#home-a {
  .container {
    h1 {
      font-size: 2.5rem;
      text-transform: uppercase;
      display: block;
      padding-bottom: 0.5rem;
      text-align: center;
      font-weight: 100;
    }
  }
}
</style>
