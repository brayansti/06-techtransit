<template>
  <div id="app">
    <!--  -->
    <div class="container">
      <div class="row">
        <div class="col-md-6">
          <div class="searchBox">
            <input placeholder="Buscar" v-model="newsSearch" @keyup="changeInput" type="text">
          </div>
        </div>
      </div>
      <div class="row">
        <div v-for="(item, $index) in list" :key="$index" class="col-md-4">
          <a target="_blank" :href="item.url" class="itemBox">
            <div class="itemBox__container">
              <div class="itemBox__divider itemBox__divider--top">
                <figure class="itemBox__image">
                  <!-- <img src="https://mytablemesa.com/Content/uploads/684a5f05-af87-438e-b32a-82bf7e92e729.png" alt="Image"> -->
                  <img :src="'https://i.picsum.photos/id/'+item.points+'/400/400.jpg'" :alt="item.title">
                </figure>
                <div class="itemBox__credits">
                  {{item.points}} credits
                </div>
              </div>
              <div class="itemBox__divider itemBox__divider--bottom">
                <div>
                  <h2 class="itemBox__title">
                    {{item.author}}
                  </h2>
                  <p class="itemBox__description">
                    {{item.title}}
                  </p>
                </div>
                <div class="d-flex justify-content-between">
                  <div>
                    <h2 class="itemBox__title itemBox__price">
                      <!-- $14.15 -->
                      ${{item.objectID}}
                    </h2>
                  </div>
                  <div>
                    <vue-stars
                      :name="item.objectID"
                      :max="5"
                      :value="item.points"
                      :readonly="true"
                    />
                  </div>
                </div>
              </div>
            </div>
          </a>
        </div>
      </div>
    </div>
    <div infinite-wrapper>
      <infinite-loading force-use-infinite-wrapper :identifier="infiniteId" @infinite="infiniteHandler"></infinite-loading>
    </div>

    <!--  -->
  </div>
</template>

<script>
import axios from 'axios';
  import { VueStars } from "vue-stars"
import InfiniteLoading from 'vue-infinite-loading';

const api = '//hn.algolia.com/api/v1/search_by_date?tags=story';
// const api = '//test.mytablemesa.com/api/courses?orderBy=popularity+desc&expand=provider&limit=24&profession=&subjectAreaCode=&state=&provider=&name=';

export default {
  name: 'app',
  components: {
    InfiniteLoading,
    VueStars
  },
  data() {
    return {
      page: 1,
      list: [],
      newsSearch: '',
      infiniteId: +new Date(),
    };
  },
  methods: {
    infiniteHandler($state) {
      axios.get(api, {
        params: {
          tags: 'story',
          page: this.page,
          query: this.newsSearch
        },
      }).then(({ data }) => {
        if (data.hits.length) {
          this.page += 1;
          this.list.push(...data.hits);
          $state.loaded();
        } else {
          $state.complete();
        }
      });
    },
    changeInput() {
      let timeout = null;
      clearTimeout(timeout);
      // Delay search
      timeout = setTimeout(() => {
        this.page = 1;
        this.list = [];
        this.infiniteId += 1;
      }, 800);
    },
  },

  // computed:{
  //   number: function(){
  //     return parseInt(this.test)
  //   },
  // }
}
</script>

<style lang="scss">
@import "./scss/main.scss";
</style>
