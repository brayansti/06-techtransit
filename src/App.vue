<template>
  <div id="app">

    <div class="container">
      <div class="row">
        <div class="col-md-4">
          <article class="itemBox">
            <div class="itemBox__container">
              <div class="itemBox__divider itemBox__divider--top">
                <figure class="itemBox__image">
                  <img src="https://mytablemesa.com/Content/uploads/684a5f05-af87-438e-b32a-82bf7e92e729.png" alt="Image">
                </figure>
                <div class="itemBox__credits">
                  1 credits
                </div>
              </div>
              <div class="itemBox__divider itemBox__divider--bottom">
                <div>
                  <h2 class="itemBox__title">Lorem ipsum dolor</h2>
                  <p class="itemBox__description">
                    Lorem ipsum dolor, sit amet consectetur adipisicing elit.
                  </p>
                </div>
                <div class="d-flex justify-content-between">
                  <div>
                    <h2 class="itemBox__title itemBox__price">$14.15</h2>
                  </div>
                  <div>
                    <input v-model="test" type="number"> {{number}}
                  </div>
                </div>
              </div>
            </div>
          </article>
        </div>
      </div>
    </div>


    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  },
  data: function() {
    return {
      test: 0,
      starStyle: {
        fullStarColor: "#ed8a19",
        emptyStarColor: "#737373",
        starWidth: 20,
        starHeight: 20
      },
        config: {
            rating: 2.5,
            style: {
                fullStarColor: '#ed8a19',
                emptyStarColor: '#737373',
                starWidth: 30,
                starHeight: 30
            }
        }
    }
  },
  computed:{
    number: function(){
      return parseInt(this.test)
    },
  }
}
</script>

<style lang="scss">
@import "./scss/main.scss";
</style>
