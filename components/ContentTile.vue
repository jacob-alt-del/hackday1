<template>
  <div class="tile-wrapper clickable">
    <div class="tile-content">
      <div>
        <img class="tile-image" :src="imageURL"/>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ContentTile',
  props: {
    imageURL: {
      type: String,
      default: "Default Image URL"
    }
  },
}
</script>

<style scoped lang="css">
.tile-wrapper {
  width: 220px;
  height: 240px;
  border: 1.5px solid dimgrey;
  border-radius: 25px;
  transition: 0.3s;
}

.tile-wrapper:hover {
  background-color: whitesmoke;
  border-color: $bjss-house-colour;
}

.tile-content {
  display: flex;
  flex-direction: column;
  padding: 20px;
}

.tile-title {
  padding-bottom: 20px;
  font-size: 20px;
  font-weight: bold;
}

.tile-image {
  width: 90%;
  height: 90%;
  margin: auto;
}
</style>
