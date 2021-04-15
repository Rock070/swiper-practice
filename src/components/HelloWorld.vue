<template lang="pug">
Swiper(
    :slides-per-view="1"
    :space-between="50"
    navigation
    :pagination="{ clickable: true }"
    :scrollbar="{ draggable: true }"
    @swiper="onSwiper"
    @slideChange="onSlideChange"
  )
  swiper-slide(v-if="routerState == 'first'") slide 1
  swiper-slide(v-if="routerState == 'second'") slide 2
  swiper-slide(v-if="routerState == 'third'") slide 3

progress(id="file" max="100" value="50" @click="historyGo({foo: 'first'})") 
br
progress(id="file" max="100" value="60" @click="historyGo({foo: 'second'})")
br
progress(id="file" max="100" value="70" @click="historyGo({foo: 'third'})") 
//- img(src="https://www.itread01.com/uploads/images/20170305/1488674316-5250.jpg")

</template>



<script>

import { Swiper, SwiperSlide } from 'swiper/vue';
import SwiperCore, { Navigation, Pagination, Scrollbar, A11y } from 'swiper';


import 'swiper/swiper-bundle.css';

// Import Swiper styles
import 'swiper/swiper.scss';
import 'swiper/components/navigation/navigation.scss';
import 'swiper/components/pagination/pagination.scss';
import 'swiper/components/scrollbar/scrollbar.scss';
import { ref } from 'vue'

// install Swiper modules
SwiperCore.use([Navigation, Pagination, Scrollbar, A11y]);

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: {
    Swiper,
    SwiperSlide,
  },
  setup() {

    function onSwiper() {
      // console.log()
    }
    function onSlideChange() {
      console.log('slide change')
      // console.log(window.history.back())
    }
    console.log(window)
    console.log(window.performance.timing.requestStart)

    let routerState = ref(null)

    function historyGo (stateObj) {
      let { foo }= stateObj
      console.log(foo)
      history.pushState(stateObj, "", `#${foo}`)
      console.log(`history: `, history)
      console.log(`state:`, history.state)
      routerState.value = history.state.foo
      console.log(routerState.value)
      // let url = window.URL(URL.pathname)
      console.log('url', location.hash)
    }

   
    
    return {
      routerState,
      onSwiper,
      onSlideChange,
      historyGo,
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.swiper-container {
  width: 600px;
  height: 300px;
}

.swiper-slide {
    width: 100%;
    text-align: center;
    font-size: 18px;
    background: #fff;

    /* Center slide text vertically */
    display: -webkit-box;
    display: -ms-flexbox;
    display: -webkit-flex;
    display: flex;
    -webkit-box-pack: center;
    -ms-flex-pack: center;
    -webkit-justify-content: center;
    justify-content: center;
    -webkit-box-align: center;
    -ms-flex-align: center;
    -webkit-align-items: center;
    align-items: center;
  }
</style>
