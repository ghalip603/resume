<template>
  <v-responsive>
    <v-container>
      <div class="  text-sm-h2 ma-10  NameContainer">
        <div class="text-sm-h2 text-h4 text-start NameTitle pb-8">阿力甫·塔依尔</div>
        <div class="text-sm-h6 text-start  NameSubtitle">初级前端开发工程师</div>
      </div>
    </v-container>
    <v-container>
      <v-row no-gutters>
        <v-col
          v-for="item in GhalipResume"
          :key="item.id"
          cols="6"
          sm="4"
          md="4"
          class="ProfileContent d-flex  justify-center text-sm-h6"
        >
          <div>
            <v-icon class="mx-sm-4 mx-4 my-4 text-teal">mdi-account</v-icon>
          </div>
          <div class="my-2 py-2 ">
            {{ item.attributes.gender }} / {{ item.attributes.age }} /{{ item.attributes.date }}
          </div>
        </v-col>
        <v-col
          v-for="item in GhalipResume"
          :key="item.id"
          cols="6"
          sm="4"
          md="4"
          class="ProfileContent d-flex  justify-center text-sm-h6"
        >
          <div>
            <v-icon class="mx-sm-4 mx-4 my-4 text-teal">mdi mdi-account-school</v-icon>
          </div>
          <div class="my-2 py-2 ">
            {{ item.attributes.major }}
          </div>
        </v-col>
        <v-col
          v-for="item in GhalipResume"
          :key="item.id"
          cols="6"
          sm="4"
          md="4"
          class="ProfileContent d-flex  justify-sm-center  text-sm-h6  "
        >
          <div>
            <v-icon class="mx-sm-4 ml-9  my-4 text-teal">mdi mdi-school</v-icon>
          </div>
          <div class="my-2 py-2  ml-4">
            <a href="https://www.xjufe.edu.cn/" class="link-title">{{ item.attributes.graduated }}</a>
          </div>
        </v-col>
        <v-col
          v-for="item in GhalipResume"
          :key="item.id"
          cols="6"
          sm="4"
          md="4"
          class="ProfileContent d-flex  justify-center text-sm-h6"
        >
          <div>
            <v-icon class="mx-sm-2 ml-5 my-4 text-teal">mdi mdi-map-marker</v-icon>
          </div>
          <div class="my-2 py-2  px-sm-6  px-3">
            {{ item.attributes.location }}
          </div>
        </v-col>
        <v-col
          v-for="item in GhalipResume"
          :key="item.id"
          cols="6"
          sm="4"
          md="4"

          class="ProfileContent d-flex  justify-sm-center text-sm-h6  "
        >
          <div>
            <v-icon class="mx-sm-4 ml-9  my-4 text-teal">mdi mdi-newspaper-variant</v-icon>
          </div>
          <div class="my-2 py-2  ml-4">
            <a href="https://www.tanxianit.com" class="link-title">{{ item.attributes.website }}</a>
          </div>
        </v-col>
        <v-col
          v-for="item in GhalipResume"
          :key="item.id"
          cols="6"
          sm="4"
          md="4"
          class="ProfileContent d-flex  justify-center text-sm-h6"
        >
          <div>
            <v-icon class="mx-sm-4  my-4   text-teal">mdi mdi-wechat</v-icon>
          </div>
          <div class="my-2 py-2 ml-4 ml-sm-12  ">
            {{ item.attributes.wechat }}
          </div>
        </v-col>
          <div class="d-flex flex-column mt-sm-10 text-sm-h6 text-subtitle-1 font-weight-medium text-justify text-kulrang  bg-grey-lighten-4 w-100 rounded"
               v-for="item in GhalipResume" :key="item.id">
            <div class="ma-5"><p><span class="text-sm-h6 text-subtitle-1"><v-icon>mdi mdi-star-shooting-outline</v-icon></span>{{ GhalipResume[0].attributes.description1 }}</p></div>
            <div class="ma-5"><p><span class="text-sm-h6 text-subtitle-1"><v-icon>mdi mdi-star-shooting-outline</v-icon></span>{{ GhalipResume[0].attributes.description2 }}</p></div>
            <div class="ma-5"><p><span class="text-sm-h6 text-subtitle-1"><v-icon>mdi mdi-star-shooting-outline</v-icon></span>{{ GhalipResume[0].attributes.description3 }}</p></div>
            <div class="ma-5"><p><span class="text-sm-h6 text-subtitle-1"><v-icon>mdi mdi-star-shooting-outline</v-icon></span>{{ GhalipResume[0].attributes.description4 }}</p></div>
            <div class="ma-5"><p><span class="text-sm-h6 text-subtitle-1"><v-icon>mdi mdi-star-shooting-outline</v-icon></span>{{ GhalipResume[0].attributes.description5 }}</p></div>
            <div class="ma-5"><p><span class="text-sm-h6 text-subtitle-1"><v-icon>mdi mdi-star-shooting-outline</v-icon></span>{{ GhalipResume[0].attributes.description6 }}</p></div>
            <div class="ma-5"><p><span class="text-sm-h6 text-subtitle-1"><v-icon>mdi mdi-star-shooting-outline</v-icon></span>{{ GhalipResume[0].attributes.description7 }}</p></div>
            <div class="ma-5"><p><span class="text-sm-h6 text-subtitle-1"><v-icon>mdi mdi-star-shooting-outline</v-icon></span>{{ GhalipResume[0].attributes.description8 }}</p></div>
          </div>

      </v-row>



    </v-container>
  </v-responsive>

<tools></tools>

</template>

<style>
.NameTitle {
  text-align: center;
  color: #456990;
}

.NameSubtitle {
  margin: 0 auto;
  width: 100%;
  text-align: center;
  color: #595959;
}

.ProfileContent {
  font-size: 12px;
}

.link-title {
  text-decoration: none;
}

a {
  text-decoration: none;
  color: #456990;
}

.playground{
  height: 2000px;
  width: 100%;

}

</style>
<script setup lang="ts">
import {onMounted, ref,} from "vue";
import axios from "axios";
import {Icon} from '@iconify/vue';
import Tools from "@/components/tools.vue";

const GhalipResume = ref([])
onMounted(() => {
  axios.get('http://192.168.31.14:1337/api/ghalip-resumes?populate=*')
    .then(function (response) {
      // handle success
      GhalipResume.value = response.data.data
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
    GhalipResume
  }
})
</script>
