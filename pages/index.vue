<template>
  <div class="home">
    <Banner
      class="home-banner"
      :image="bannerImage"
      title="Welcome to Petflix"
      message=""
    />
    <button class="button">Upload your pet photos!</button>
    <div class="tiles">
      <ContentTile class="tile" v-for="(imageURL, index) in apiResponse" :key="index" :imageURL="imageURL">
      </ContentTile>
    </div>
  </div>
</template>

<script>
import Banner from '@/components/Banner'
import ContentTile from '@/components/ContentTile'
import academyImage from '@/assets/img/academy.png'
import { apiGet } from '@/utils/api'

export default {
  name: 'Home',
  components: {
    Banner,
    ContentTile,
  },
  data() {
    return {
      bannerImage: academyImage,
      tiles: [
        {
          title: 'A tile Bruno',
          text: 'This is a reusable component.',
        },
        {
          title: 'Another tile',
          text:
            'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras fringilla purus eget nibh venenatis.',
        },
        {
          title: 'A third tile',
          text:
            'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc luctus, nibh id faucibus egestas.',
        },
        {
          title: 'A fourth tile',
          text:
            'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc luctus, nibh id faucibus egestas.',
        },
        {
          title: 'A fourth tile',
          text:
            'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc luctus, nibh id faucibus egestas.',
        },
      ],
      apiResponse: [],
    }
  },
  mounted() {
    this.fetchGreeting()
  },
  methods: {
    fetchGreeting() {
      apiGet('https://ck7f3w6408.execute-api.eu-west-1.amazonaws.com/IL/teams/atari/files')
        .then(({ data }) => (this.apiResponse = data["data"]))
        .catch(
          () => (this.apiResponse = 'Failed to retrieve data from server.')
        )
    },
  },
}

</script>

<style scoped lang="css">
.home {
  width: 80%;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
}

.home-banner {
  margin-bottom: 35px;
}

.tiles {
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
}

.tile {
  margin-top: 10px;
}

.picture {
  width: 40px;
  margin-top:90px;
  margin-left: auto; 
  margin-right: auto;
}

.button{
        background-color: lightseagreen;
        margin:20px;
        display:inline-block;
        font-size: 32px;
        max-width: 300px;
        margin: auto;
        border-radius: 5px;
    }
</style>