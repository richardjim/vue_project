<script>
import Navbar from "@/components/navbar";
import Services from "@/components/services";
import Features from "@/components/features";
import Project from "@/components/projects";
import Blog from "@/components/blog";
import Contact from "@/components/contact";
import Footer from "@/components/footer";


export default {
  name: "Home",
  components: {
    Navbar,
    Services,
    Features,
    Project,
    Blog,
    Contact,
    Footer,
  },
};
</script>

<template>
  <div>
    <Navbar />
    <div v-scroll-spy>
      <!--START HOME-->
      <section
        class="section bg-home home-half"
        id="home"
        :style="{'background-image': 'url(' + require('@/assets/images/bg-home.jpg') + ')', 'background-size': 'cover','background-position': 'center' }"
      >
        <div class="bg-overlay"></div>
        <div class="display-table">
          <div class="display-table-cell">
            <div class="container">
              <div class="row">
                <div class="col-lg-8 offset-lg-2 text-white text-center">
                  <h1 class="home-title">We help startups launch their products</h1>
                  <p
                    class="padding-t-15 home-desc"
                  >We Ensure Quality Services</p>
                  <p class="play-shadow margin-t-30 margin-l-r-auto">
                    <a v-b-modal.modal href="javascript: void(0);" class="play-btn video-play-icon">
                      <i class="mdi mdi-play text-center"></i>
                    </a>
                  </p>
                  <b-modal id="modal" hide-footer size="lg" centered header-close-variant="white">
                    <youtube video-id="" ref="youtube" width="750" height="450"></youtube>
                  </b-modal>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="bg-pattern-effect">
          <img src="@/assets/images/bg-pattern.png" alt />
        </div>
      </section>
      <!--END HOME-->
      <Services />
      <Features />
      <Project />
      <Blog />
      <Contact />
      <Footer />
    </div>
  </div>
</template>

<style scoped>
::v-deep .modal-content {
  background-color: #000000;
  color: white;
  background: none;
  border: none;
}
::v-deep .modal-header {
  border: none;
}
::v-deep .modal-backdrop {
  opacity: 0.5;
}
</style>