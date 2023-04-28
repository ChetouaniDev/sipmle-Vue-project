<template>
  <Add />
  <ul>
    <li v-if="showdata" v-for="book in favbooks" :class="{fav: book.isfav}" @click="toglefav(book)">
      <h3>{{ book.title }}</h3>
      <p>{{ book.author }}</p>
    </li>
  </ul>
  <button @click="toggle">
    <span v-if="!showdata">Show data</span>
    <span v-if="showdata">Hide data</span>
  </button>
</template>

<script>
import Add from "./components/Add.vue";
export default {
  components: { Add },
  data() {
    return {
      showdata: true,
      books: [
        { title: "name of the wind", author: "adnane chetouani",isfav:true },
        { title: "name of the wind", author: "yahya chetouani",isfav:false},
        { title: "name of the wind", author: "mehdi mamas" ,isfav:true},
      ],
    };
  },
  methods: {
    toggle() {
      this.showdata = !this.showdata;
    },
    toglefav(book){
      book.isfav =!book.isfav

    }
  },
  computed: {
    favbooks(){
      return this.books.filter((e)=>e.isfav)
    }
  }
};
</script>
<style>
body {
  background: rgb(196, 192, 192);
  max-width: 960px;
  margin: 20px auto;
}
p,
h3,
ul {
  margin: 0;
  padding: 0;
}

li {
  list-style-type: none;
  background: #fff;
  margin: 20px auto;
  padding: 30px 20px;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
li.fav{
  background-color: rosybrown;
  color: #fff;
}
</style>
