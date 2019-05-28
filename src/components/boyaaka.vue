<template>
  <v-container grid-list-md text-xs-center>
    <v-layout row wrap>
      <v-flex
        v-if="images.length"
        :key="image.id"
        v-for="image of images"
        xs4>
        <v-card dark>
        <v-img 
          v-bind:src="image.download_url + '.jpg'"
          aspect-ratio="2.75">
        </v-img>
          <v-card-text class="px-0">{{image.author}}</v-card-text>
           <v-card-actions>
          <v-btn :href="image.url" target="_blank" flat color="orange">Explore</v-btn>
        </v-card-actions>
        </v-card>
      </v-flex>
    </v-layout>
      <div class="text-xs-center">
        <v-pagination
          v-model="page"
          :length="12"
          @input="getData"
          circle>
        </v-pagination>
      </div>
  </v-container>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      images: [],
      page: 1,
      errors: [],
    }
  },

  methods: {
    getData: function () {
      const url = `https://picsum.photos/v2/list?page=${this.page}&limit=9`;
      axios.get(url)
        .then((response) => {
          if(response.status == 200){
            console.log(response.data);
          this.images = response.data;
          }
        })
        .catch((e) => {
          console.log(e);
          this.errors.push(e)
        });
    }
  },

  watch: {
    "page": (page) => {
      // this.getData(page);
    }
  },

  created() {
      this.getData();
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello{
 text-align:center;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
