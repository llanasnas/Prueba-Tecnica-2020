 <template>
  <v-container fluid>
    <v-row>
      <v-col
        v-for="(photo,index) in visiblePhotos"
        :key="photo.id" 
        xs="12"
        sm="4"
        lg="2"       
        class="image_card_padding clickable"
        @click="onClick(index)"
      >
        <image-card :src="photo.url" :title="photo.title"></image-card>
      </v-col>
    </v-row>
  </v-container>
</template>


 <script>
import axios from "axios";
import ImageCard from "../components/ImageCard";

export default {
  props: {
    source: String
  },
  data: () => ({
    visiblePhotos: null,
    allPhotos: null,
    initialPhotosNumber:40,
    aditionalPhotos:15
  }),
  components: {
    ImageCard
  },
  mounted() {
    axios.get("https://jsonplaceholder.typicode.com/photos").then(response => {
      this.allPhotos = response.data;
      this.initialPhotos();

      // Creamos un evento cuando se esten dibujando las imágenes, que calculará 
      // si estamos al final de la página para cargar más imágenes
      window.onscroll = () => {
        let bottomOfWindow =
          Math.max(
            window.pageYOffset,
            document.documentElement.scrollTop,
            document.body.scrollTop
          ) +
            window.innerHeight ===
          document.documentElement.offsetHeight;

        if (bottomOfWindow) {
          this.getMoreImages();
        }
      };
    });
  },
  methods: {
      //cargamos más 
    getMoreImages() {
      let nextPhotos =this.allPhotos.slice(this.visiblePhotos.length, this.visiblePhotos.length + this.aditionalPhotos);
      this.visiblePhotos = this.visiblePhotos.concat(nextPhotos);
    },
    // Here we select first 30 to show on Page load
    initialPhotos() {
      this.visiblePhotos = this.allPhotos.slice(0, this.initialPhotosNumber);
    },
    onClick(index){
        this.visiblePhotos.splice(index,1)
        this.allPhotos.splice(index,1)
        if(this.visiblePhotos.length < 30)
            this.getMoreImages();      
    }
  }
};
</script>


<style lang="scss">
.image_card_padding {
  padding: 10px;
}
.clickable{
    cursor: pointer; 
}
</style>