<template>
  <div class="bottom-nav">
    <v-footer fixed height="102">
      <v-btn
        absolute
        dark
        fab
        top
        right
        color="primary"
        @click.stop="syncAddModal(true)"
      >
        <v-icon>add</v-icon>
      </v-btn>

      <v-bottom-nav
        :active.sync="bottomNav"
        :value="true"
        absolute
      >
        <v-btn
          color="primary"
          flat
          value="recent"
          @click="sortList('recent')"
        >
          <span>Recent</span>
          <v-icon>schedule</v-icon>
        </v-btn>

        <v-btn
          color="primary"
          flat
          value="favorites"
          @click="sortList('favorites')"
        >
          <span>Favorites</span>
          <v-icon>favorite</v-icon>
        </v-btn>

        <v-btn
          color="primary"
          flat
          value="nearby"
          @click="sortList('nearby')"
        >
          <span>Nearby</span>
          <v-icon>place</v-icon>
        </v-btn>
      </v-bottom-nav>
    </v-footer>
  </div>
</template>

<script>
export default {
  name: 'BottomNav',
  props: ['current'],
  data () {
    return {
      bottomNav: ''
    }
  },
  created () {
    this.bottomNav = this.$props.current
  },
  methods: {
    sortList (sort) {
      this.$emit('sortList', sort)
    },
    syncAddModal (bool) {
      this.$emit('syncAddModal', bool)
    }
  }
}
</script>

<style scoped>
.theme--light .v-footer {
  background: transparent;
}
</style>
