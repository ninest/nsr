<template>
  <div class="link">
    <!-- {{ this.siteConfig.footerLinks }} -->
    <ul>
      <li v-for="link in this.siteConfig.footerLinks">
        <a v-if="link.external != false" :href="link.url" target="_blank" rel="noopener">{{ link.title }}</a>
        <nuxt-link v-else :to="link.url">{{ link.title }}</nuxt-link>
      </li>
    </ul>
    <div style="margin-top: 1rem;">
      <adsbygoogle />
    </div>
  </div>
</template>

<style lang="scss" scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  
  display: flex;
  flex-flow: wrap;

  font-weight: 600;
  font-size: 0.9rem;
  color: var(--nav-link);

  li {
    display: inline-block;
    margin-right: 0.9rem;
    
    margin-bottom: 0.5rem;

  }
  
  @include mobile-screen {
    font-size: 1.1rem;

    li {
      margin-right: 1.5rem;
      margin-bottom: 0.75rem;
    }
  }
}
</style>