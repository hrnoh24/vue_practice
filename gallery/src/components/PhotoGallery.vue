<template>
  <div>
    <h1>미라클 모닝 공모전</h1>
    <ul class="gallery">
      <li v-for="n in 5" :key="n">
        <img
          @click="highlight"
          ref="imgs"
          :id="n==1? 'theater':''"
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
  },
  mounted() {
    this.theatrical = this.$refs.imgs[0].src;
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
.gallery img:hover {
  border: 2px solid orange;
}

#theater {
  width: 100%;
}

#theater:hover {
  border: None;
}

#frame img {
  width: 80%;
}
</style>