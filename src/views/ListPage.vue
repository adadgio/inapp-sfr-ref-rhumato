<template>
  <div class="ListPage">
    <h1>Menu principal</h1>
    <div class="main-categories">
      <div class="list" v-for="node0 in nodes0" :key="node0.name">
        <router-link :to="'/sublist/' + node0.slug">{{
          node0.name
        }}
          <i class="fas fa-chevron-right"></i>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import DataService from "@/service/DataService";

export default Vue.extend({
  name: "ListPage",
  data() {
    return {
      nodes0: [],
    };
  },
  mounted() {
    DataService.load()
      .then(() => {
        this.nodes0 = DataService.$data.tree;
      })
      .catch((e) => {
        console.log(e);
      });
  },
});
</script>
<style scoped lang="scss">
@import "src/sass/global.scss";;
.ListPage {
    padding: 0 .75rem;

  h1 {
    padding: 0;
    margin-bottom: 0;
    flex-shrink: 0;
    width: 100%;
    max-width: 100%;
    font-size: calc(1.375rem + 1.5vw);
    font-weight: 500;
    line-height: 1.2;
    text-align: left;
    color: #472e5a;
  }
}

.list {
  a {
    all: unset;
    color: #472e5a;
    font-weight: bold;
    background: #ecf1f5;
    border-radius: 5px;
    display: flex;
    margin-top: .5rem;
    padding: 16px;
    cursor: pointer;
    text-align: left;
    justify-content: space-between;
    align-items: center;

    i {
      background: #472e5a;
      color: #ecf1f6;
      padding: .5em .75em;
      border-radius: .5rem;
      font-weight: lighter;
      display: flex;
    }
  }
}
</style>
