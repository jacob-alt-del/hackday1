<template>
  <div class="home">
    <Banner
      class="home-banner"
      :image="bannerImage"
      title="Dogs!"
      message="This is a simple Vue app demonstrating components, routing and API calls."
    />
    <div class="tiles">
      <ContentTile
        v-for="tile in tiles"
        :key="tile.title + '-tile'"
        :title="tile.title"
        :text="tile.text"
        class="tile"
      />
    </div>
    <br />
    <div v-if="apiResponse">Server response: {{ apiResponse }}</div>
    <img src="https://gradhack-2020.s3-eu-west-1.amazonaws.com/atari/05eda999-0ef0-451e-aca3-1a1950af4e63.png"></img>
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
      apiResponse: '',
    }
  },
  mounted() {
    this.fetchGreeting()
  },
  methods: {
    fetchGreeting() {
      apiGet('https://ck7f3w6408.execute-api.eu-west-1.amazonaws.com/IL/teams/atari/files')
        .then(({ data }) => (this.apiResponse = JSON.parse(JSON.stringify(data))))
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
</style>