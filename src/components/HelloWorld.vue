<template>
  <v-responsive>
    <v-container>
      <div class="  text-sm-h2 ma-10  NameContainer">
        <div class="text-sm-h2 text-h4 text-center NameTitle pb-8">阿力甫·塔依尔</div>
        <div class="text-sm-h6 text-sm-center  NameSubtitle">前端开发工程师</div>
      </div>
    </v-container>
    <v-container>
      <v-row>
        <v-col
          v-for="item in resumeabouts"
          :key="item.id"
          cols="6"
          sm="4"
        >
          <v-sheet class="ma-2 pa-2 d-flex  pl-sm-10  text-sm-h6  AboutTitle">
            <slot>
              <v-icon>
                <Icon :icon="item.attributes.iconClass" class="text-sm-h5"/>
              </v-icon>
            </slot>
            <div class="pl-sm-5 pl-2 "> {{ item.attributes.title }}
            </div>
          </v-sheet>
        </v-col>
      </v-row>
    </v-container>
  </v-responsive>


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

.AboutTitle {
  font-size: 12px;

}


</style>
<script setup lang="ts">
import {onMounted, ref,} from "vue";
import axios from "axios";
import {Icon} from '@iconify/vue';

const resumeabouts = ref()
onMounted(() => {
  axios.get('http://localhost:1337/api/resumeabouts?populate=*')
    .then(function (response) {
      // handle success
      resumeabouts.value = response.data.data
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
