<template>
  <ul class="header-nav" @click="navMenuClicked">
    <li v-for="item in items" track-by="$index" :class="{'nav-dropdown-container': item.type === 'dropdown'}">
      <a v-if="item.type === 'dropdown'" v-text="item.label"></a>
      <ul v-if="item.type === 'dropdown'" class="nav-dropdown">
        <li v-for="child in item.children" track-by="$index">
          <a v-if="child.type === 'outgoing'" :href="child.link" target="_blank" v-text="child.label"></a>
          <a v-else v-link="{path: child.path, activeClass: ''}" v-text="child.label"></a>
        </li>
      </ul>
      <a v-if="item.type === 'outgoing'" :href="item.link" target="_blank" v-text="item.label"></a>
      <a v-if="item.type !== 'dropdown' && item.type !== 'outgoing'" v-link="{path: item.path, activeClass: 'current'}" v-text="item.label"></a>
    </li>
  </ul>
</template>

<script>
  export default {
    props: ['items', 'mobileExpanded'],

    methods: {
      navMenuClicked () {
        this.mobileExpanded = false
      }
    }
  }
</script>
