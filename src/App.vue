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
