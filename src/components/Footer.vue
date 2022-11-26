<template>
  <div class="footer-links">
    <router-link 
      v-for="(link, i) in links" 
      :to="link.url" 
      :key="i"
    >{{ link.title }}</router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      links: [
        {
          title: 'Home',
          url: '/'
        },
        {
          title: 'About',
          url: '/about'
        }
      ]
    }
  }
}
</script>

<style scoped>
.footer-links {
  border-top: 1px solid #888;
  padding: 1.25em;
  display: flex;
  align-self: center;
  justify-content: center;
  gap: 1.25em;
  margin: 1.25em;
}
</style>