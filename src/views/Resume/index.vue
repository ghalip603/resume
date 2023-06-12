<template>
  <!--头部-->
      <header>
        <!--头部导航条-->
        <v-app-bar app
                   color="naiyoubai"
                   dark
                   flat
                   height="80">
          <v-app-bar-title class="text-sm-h4 text-h4 font-weight-black">Resume</v-app-bar-title>
          <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        </v-app-bar>
      </header>
    <!--侧边导航栏 -->
  <v-navigation-drawer width="300" elevation="2"
    v-model="drawer"
  >
        <v-list class="pa-2 text-sm-h6 ">
          <v-list-subheader class="text-sm-h4 pa-10">REPORTS</v-list-subheader>
          <!--导航栏项目循环-->
          <v-list-item
            v-for="(item, i) in items"
            :key="i"
            :value="item"
            color="primary"
            rounded="lg"
            class="ma-3 py-4 "
          >
            <template v-slot:prepend>
              <v-icon>
                <Icon :icon="item.attributes.iconClass"/>
              </v-icon>
            </template>

            <v-list-item-title class="font-weight-medium"
            >
              {{ item.attributes.title }} &nbsp; / &nbsp; {{ item.attributes.titleEn }}
            </v-list-item-title>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>

  <!--内容部分-->
  <v-main app  class="mainning">
    <!--路由组件-->
    <HelloWorld></HelloWorld>
</v-main>

</template>

<script lang="ts" setup>
import HelloWorld from '@/components/HelloWorld.vue'
import { onMounted, ref,} from "vue";
import axios from "axios";
import {Icon} from '@iconify/vue';

const drawer = ref(null)
const items = ref()

onMounted(() => {
  axios.get('http://localhost:1337/api/items?populate=*')
    .then(function (response) {
      // handle success
      items.value = response.data.data
      console.log(response);
    })
    .catch(function (error) {
      // handle error
      console.log(error);
    })
    .then(function () {
      // always executed

    });
})


</script>


<style>


</style>
