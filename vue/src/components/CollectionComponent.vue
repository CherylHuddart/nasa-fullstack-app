<template>
    <div class="collection-view">
      <h1 class="collection-title">{{ collectionTitle }}</h1>
  
      <div class="media-grid">
        <div v-for="item in collectionItems" :key="item.data[0].nasa_id" class="media-item">
          <div v-if="item.data[0].media_type === 'image'" class="media-thumbnail">
            <img :src="item.links[0].href" :alt="item.data[0].title" />
          </div>
          <div v-else-if="item.data[0].media_type === 'video'" class="media-thumbnail">
            <video :src="item.links[0].href" controls>
              Your browser does not support the video tag.
            </video>
          </div>
          <div class="media-details">
            <h3 class="media-title">{{ item.data[0].title }}</h3>
            <p class="media-date">{{ item.data[0].date_created }}</p>
            <p class="media-description">{{ item.data[0].description }}</p>
          </div>
        </div>
      </div>
    </div>
  </template>

<script>
import service from '../services/NasaService'

export default {
    data() {
        return {
            collectionItems: [],
            collectionTitle: ''
        }
    },
    props: {
        collectionQuery: String
    },
    created() {
        service.getCollectionItems(this.collectionQuery)
        .then((response) => {
            console.log(response);
            this.collectionItems = response.data.collection.items;
            if (this.collectionItems.length > 0){
                this.collectionTitle = this.collectionItems[0].data[0].title;
            }
        })
    }
}
</script>

<style scoped>
.collection-view {
  padding: 20px;
}

.collection-title {
  text-align: center;
  margin-bottom: 20px;
}

.media-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}

.media-item {
  border: 1px solid #ddd;
  padding: 10px;
  border-radius: 5px;
}

.media-thumbnail {
  width: 100%;
  margin-bottom: 10px;
}

.media-thumbnail img,
.media-thumbnail video {
  width: 100%;
  height: auto;
  display: block;
}

.media-details {
  text-align: left;
}

.media-title {
  font-size: 1.1em;
  margin-bottom: 5px;
}

.media-date {
  font-size: 0.9em;
  color: #777;
  margin-bottom: 5px;
}

.media-description {
  font-size: 0.95em;
}
</style>