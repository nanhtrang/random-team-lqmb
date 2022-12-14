<template>
  <div class="home row m-0 p-0">
    <div class="header-container"></div>
    <div class="col-sm-6 m-0 p-0 m-auto p-rel mt-5 content">
      <div class="m-0 py-2 p-0 m-auto bg-secondary">
        <h3 class="text-light m-0 my-2 p-0">Random Team</h3>
      </div>
      <div class="container bg-dark">
        <table class="w-100">
          <tr class="border-bottom">
            <th>Hạt giống 1</th>
            <th>Hạt giống 2</th>
          </tr>
          <tr v-for="item in core" :key="item">
            <td class="border-end">{{ getName(item, true) }}</td>
            <td>{{ getName(item, false) }}</td>
          </tr>
          <tr class="border-top">
            <td colspan="2">
              {{ joinTeam(out) }}
            </td>
          </tr>
        </table>
      </div>
      <div class="mt-4">
        <button class="btn btn-dark" @click="random">Random</button>
      </div>
      <div class="mt-5 w-100">
        <div class="m-0 p-0 mt-5 d-flex justify-content-between">
          <div>
            <h3 v-for="item in team1" :key="item">
              {{item}}
            </h3>
          </div>

          <div>
            <h3 v-for="item in team2" :key="item">
              {{item}}
            </h3>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import json from "../../public/static/config.json";

export default {
  name: "HomeView",
  components: {
    HelloWorld,
  },
  data: function () {
    return {
      core: [],
      out: [],
      team1: [],
      team2: [],
    };
  },
  mounted() {
    this.core = json.core;
    this.out = json.out;
  },
  methods: {
    getName: function (text, action) {
      if (action) {
        return text.split("-")[0].trim();
      }
      return text.split("-")[1].trim();
    },
    joinTeam: function (list) {
      return list.join(", ");
    },
    random: function () {
      let list = [];
      for (const item of this.core) {
        let r = Math.floor(Math.random() * 2);
        list.push(r);
      }
      let shufferCore = this.shuffer(this.core)
      this.team1 = []
      this.team2 = []
      for (let i = 0; i < shufferCore.length; i++) {
        const item = shufferCore[i];
        const r = list[i];
        if (r == 0) {
          this.team1.push(this.getName(item, true))
          this.team2.push(this.getName(item, false))
        } else {
          this.team1.push(this.getName(item, false))
          this.team2.push(this.getName(item, true))
        }
      }
      console.log("team1", this.team1);
      console.log("team2", this.team2);
    },
    shuffer: function (list) {
      let tmp = Object.assign([], list);
      let currentIndex = tmp.length
      let randomIndex

      // While there remain elements to shuffle.
      while (currentIndex != 0) {
        // Pick a remaining element.
        randomIndex = Math.floor(Math.random() * currentIndex);
        currentIndex--;
        // And swap it with the current element.
        [tmp[currentIndex], tmp[randomIndex]] = [
          tmp[randomIndex],
          tmp[currentIndex],
        ];
      }
      return tmp;
    },
  },
};
</script>

<style scoped>
.header-container {
  background-image: url("https://lienquan.garena.vn/asset/images/img-down.png");
  min-height: 480px !important;
  min-width: 100%;
  background-size: contain;
  background-position: center;
  position: absolute;
  background-repeat: no-repeat;
}

.content {
  opacity: 0.9;
}
</style>
