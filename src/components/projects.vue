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


      <div class="d-flex justify-content-around"  v-for="repo in repos" v-bind:key="repo.id">
        <div class="col-lg-8 ">
          <div class="text-center pricing-box hover-effect">
            <h4 class="text-uppercase">{{ repo.language }}</h4>
            <h5>{{ repo.name }}</h5>
            <h6 class="text-uppercase text-muted">{{ repo.full_name }}</h6>
            <div class="pricing-border"></div>
            <pagination :repos="reposLength" v-model="page" :per-page="perPage" @paginate="getPage">
            </pagination>
            <a href="javascript: void(0);" class="btn btn-custom waves-effect waves-light margin-t-30">View</a>
          </div>
          
        </div>

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
      reposLength: 0,
      perPage: 10,
      page: 1
    }
  },
  mounted() {
    Vue.axios.get('https://api.github.com/users/richardjim/repos')
      .then(response => {
        this.repos = response.data
        console.log(this.repos)
      })
  },
  methods: {
    getPage: function (page) {
      // we simulate an api call that fetch the records from a backend
      this.records = [];
      const startIndex = this.perPage * (page - 1) + 1;
      const endIndex = startIndex + this.perPage - 1;
      for (let i = startIndex; i <= endIndex; i++) {
        this.records.push(`Item ${i}`);
      }
    },
    getRecordsLength() {
      // here we simulate an api call that returns the records length
      this.recordsLength = 50;
    }
  },
  created() {
    this.getRecordsLength();
    this.getPage(this.page);
  }
}
</script>