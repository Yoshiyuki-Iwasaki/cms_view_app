<template>
 <main class="content">
   <section class="ListSec">
      <div class="ListSec__title">
        <h1>microCMS 勉強</h1>
      </div>
      <ul class="ListSec__list">
        <li v-for="item in items" :key="item" class="ListSec__list__item">
          <figure class="ListSec__list__item__image">
            <img :src="item.image.url" alt="">
          </figure>
          <div class="ListSec__list__item__text">
            <p class="ListSec__list__item__text__textarea">{{ item.textarea }}</p>
            <p class="ListSec__list__item__text__textedit">{{ item.textedit }}</p>
          </div>
        </li>
      </ul>
    </section>
    <div class="footer">
      <p>Copyright &copy; picture All Rights Reserved.</p>
    </div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
 data () {
   return {
     items: ''
   }
 },
 head: {
   script: [
   ],
 },
 async asyncData () {
   const { data } = await axios.get('https://iwasaki_sample.microcms.io/api/v1/sample/', {
     headers: { 'X-API-kEY': 'cb86f6af-4329-4353-82b9-51fbdf636c66' }
   })
   return {
     items: data.contents
   }
 }
}
</script>


<style>
ul,figure {
  margin: 0;
  padding: 0;
}
img {
  width: 100%;
}
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.ListSec {
  margin: 50px auto 0;
  width: 500px;
}

.ListSec__list__item {
  display: flex;
  align-items: center;
  list-style: none;
}
.ListSec__list__item__image {
  margin: 0 auto;
  width: 150px;
}

.ListSec__list__item__text {
  margin-left: 10px;
}
</style>
