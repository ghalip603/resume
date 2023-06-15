<template>
  <v-responsive>
    <v-container>
      <div class="ma-2 pa-2 text-sm-h6 text-h5">
        <span class="mdi mdi-xml"></span>
        技术栈&工具
      </div>
      <v-card class="devTools  rounded-lg" elevation="3">
        <div class="devToolsTitle text-sm-h5 text-subtitle-1 ml-sm-12 ml-12 px-2 d-inline-block bg-naiyoubai rounded ">
          Application And Data
        </div>
        <div class="toolsContent ">

            <v-row>
            <v-col v-for="item in devTools" :key="item.id"
                   cols=4
                   sm="4"
                   md="2"
            >
              <div class="d-flex flex-column align-center ma-2 pa-2 IconContainer">
                <div>
                  <v-icon class="text-h3 text-sm-h1 ">
                    <Icon :icon="item.attributes.iconClass" class="devToolsIcon rounded-lg"></Icon>
                  </v-icon>
                </div>
                <div class="text-center text-sm-h6 mt-4 font-weight-medium "> {{ item.attributes.title }}</div>
              </div>
            </v-col>
          </v-row>

        </div>
      </v-card>

      <v-card class="devTools  mt-10 rounded-lg" elevation="3">
        <div class="devToolsTitle text-sm-h5 text-subtitle-1 ml-sm-12 ml-12 px-2 d-inline-block bg-naiyoubai rounded ">
          DevOps
        </div>
        <div class="toolsContent ">

          <v-row>
            <v-col v-for="item in DevOps" :key="item.id"
                   cols=4
                   sm="4"
                   md="2"
            >
              <div class="d-flex flex-column align-center ma-2 pa-2 IconContainer">
                <div>
                  <v-icon class="text-h3 text-sm-h1 ">
                    <Icon :icon="item.attributes.iconClass" class="devToolsIcon rounded-lg"></Icon>
                  </v-icon>
                </div>
                <div class="text-center text-sm-h6 mt-4 font-weight-medium "> {{ item.attributes.title }}</div>
              </div>
            </v-col>
          </v-row>

        </div>
      </v-card>
      <v-card class="devTools  mt-10 rounded-lg" elevation="3">
        <div class="devToolsTitle text-sm-h5 text-subtitle-1 ml-sm-12 ml-12 px-2 d-inline-block bg-naiyoubai rounded ">
          Utilities
        </div>
        <div class="toolsContent ">

          <v-row>
            <v-col v-for="item in Utilities" :key="item.id"
                   cols=4
                   sm="4"
                   md="2"
            >
              <div class="d-flex flex-column align-center ma-2 pa-2 IconContainer">
                <div>
                  <v-icon class="text-h3 text-sm-h1 ">
                    <Icon :icon="item.attributes.iconClass" class="devToolsIcon rounded-lg"></Icon>
                  </v-icon>
                </div>
                <div class="text-center text-sm-h6 mt-4 font-weight-medium "> {{ item.attributes.title }}</div>
              </div>
            </v-col>
          </v-row>

        </div>
      </v-card>


    </v-container>
  </v-responsive>

</template>
<script setup lang="ts">
import {onMounted, ref,} from "vue";
import axios from "axios";
import {Icon} from '@iconify/vue';

const Utilities = ref([])
const devTools = ref([])
const DevOps = ref([])
onMounted(() => {
  axios.get('http://192.168.31.14:1337/api/devtools?pagination[page]=1&pagination[pageSize]=50&populate=*')
    .then(function (response) {
      // handle success

      devTools.value = response.data.data.slice(0, 23);
      DevOps.value = response.data.data.slice(23,32);
      Utilities.value = response.data.data.slice(32, 50);
      console.log(response);
    })
    .catch(function (error) {
      // handle error
      console.log(error);
    })
    .then(function () {
      // always executed

    });
  return {
    devTools,
    DevOps
  }
})
</script>


<style scoped>
.IconContainer :hover{
  background-color: #e0e0e0;
  border-radius: 5px;
  cursor: pointer;
}



</style>
