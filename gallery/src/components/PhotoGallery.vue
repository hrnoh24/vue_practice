<template>
  <div>
    <ul class="gallery">
      <li v-for="n in 5" :key="n">
        <img
          @click="highlight"
          :src="require('@/assets/photos/' + n + '.jpeg')"
        >
      </li>
    </ul>
    <div id="frame">
      <img
        :src="this.theatrical"
      >
    </div>
  </div>
</template>

<script>
export default {
  name: 'PhotoGallery',
  data() {
    return {
      theatrical: ""
    }
  },
  methods: {
    highlight() {
      event.target.id = "theater"
      let eventIterator = event.target.parentNode; // li tag를 가리킴
      while (eventIterator.previousElementSibling !== null) {
        eventIterator.previousElementSibling.getElementsByTagName('img')[0].id = "";
        eventIterator = eventIterator.previousElementSibling;
      }
      eventIterator = event.target.parentNode;
      while (eventIterator.nextElementSibling !== null) {
        eventIterator.nextElementSibling.getElementsByTagName('img')[0].id = "";
        eventIterator = eventIterator.nextElementSibling;
      }
      
      this.theatrical = event.target.src;
    }
  }
}
</script>

<style>
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
.gallery {
  display: flex;
  justify-content: space-around;
}
img {
  width: 80%;
}
#theater {
  width: 100%;
}

#frame img {
  width: 80%;
}
</style>