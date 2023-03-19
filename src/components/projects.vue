<template>
  <section class="section pt-5" id="project">
    <div class="container">
      <div class="row">
        <div class="col-lg-8 offset-lg-2">
          <h1 class="section-title text-center">Projects</h1>
          <div class="section-title-border margin-t-20"></div>
          <p class="section-subtitle font-secondary text-muted text-center padding-t-30">Call to action pricing table is
            really crucial to your for your business website. Make your bids stand-out with amazing options.</p>
        </div>
      </div>



      <div id="app" v-cloak>
        <div class="d-flex justify-content-around" v-for="(record, index) of displayedRecords" :key="index">
          <div class="col-lg-8 ">
            <div class="text-center pricing-box hover-effect">
              <h4 class="text-uppercase">{{ record.language }}</h4>
              <h5>{{ record.name }}</h5>
              <h6 class="text-uppercase text-muted">{{ record.full_name }}</h6>
              <div class="pricing-border"></div>
              <a href="javascript: void(0);" class="btn btn-custom waves-effect waves-light margin-t-30">View</a>
            </div>
          </div>
        </div>
        <pagination class="d-flex justify-content-around overflow-auto" :records="records.length" v-model="page"
          :per-page="perPage">
        </pagination>
      </div>
    </div>
  </section>
</template>
<script>

import axios from 'axios'
import Vue from 'vue'
import VueAxios from 'vue-axios'
Vue.use(VueAxios, axios)
Vue.component('pagination', Pagination);
import Pagination from 'vue-pagination-2';

export default {
  name: 'Projects',
  components: {
    Pagination
  },
  data() {
    return {
      repos: [],
      page: 1,
      perPage: 5,
      records: [this.repo]
    }
  },
  mounted() {
    Vue.axios.get('https://api.github.com/users/richardjim/repos')
      .then(response => {
        this.records = response.data
        console.log(this.records)
      })
  },

  computed: {
    displayedRecords() {
      const startIndex = this.perPage * (this.page - 1);
      const endIndex = startIndex + this.perPage;
      return this.records.slice(startIndex, endIndex);
    }
  },
  created() {
    // here we simulate an api call that returns the complete list
    for (let i = 1; i <= 500; i++) {
      this.records.push(`Item ${i}`);
    }
  }

}
</script>
<style>
#app {
  text-align: center;
}

[v-cloak] {
  display: none;
}
</style>