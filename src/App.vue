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
                  <h2>Lorem ipsum dolor</h2>
                  <p>
                    Lorem ipsum dolor, sit amet consectetur adipisicing elit.
                  </p>
                </div>
                <div class="">
                  <star-rating v-bind="{rating: number, starStyle:starStyle}"></star-rating>
                </div>
                <div class="">
                  <star-rating v-bind="{rating: 2.1, starStyle:starStyle}"></star-rating>
                </div>
                <div class="">
                  <star-rating v-bind="{rating: 1.1, starStyle:starStyle}"></star-rating>
                </div>
                <div class="">
                  <star-rating :config="config"></star-rating>
                </div>
                <input v-model="test" type="number">
                {{number}}
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
import StarRating from 'vue-dynamic-star-rating'

export default {
  name: 'app',
  components: {
    HelloWorld,
    StarRating
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
// #app {
//   font-family: 'Avenir', Helvetica, Arial, sans-serif;
//   -webkit-font-smoothing: antialiased;
//   -moz-osx-font-smoothing: grayscale;
//   text-align: center;
//   color: #2c3e50;
//   margin-top: 60px;
// }

.itemBox{
  &__container{
    border: 1px solid gray;
  }
  &__divider{
    padding: 0 20px;
    &--top{
      height: 50px;
      display: flex;
      position: relative;
      align-items: center;
      justify-content: flex-end;
      background-color: lightgray;
    }
    &--bottom{
      padding-top: 20px;
      padding-bottom: 20px;
    }
  }
  &__image{
    top: 10px;
    left: 20px;
    position: absolute;
    width: 60px;
    img{
      width: 100%;
      display: block;
    }
  }
  &__credits{
    padding: 10px;
    background: $white;
    border-radius: 10px;
    letter-spacing: .6px;
    @include fontSize(12);
  }

}
</style>
