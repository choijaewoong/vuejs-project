<template>
  <div>
    <div class="header">
      <h1 class="headerText">(주) OpenSG</h1>
      <nav>
        <ul>
          <li>
            <a href="#" @click="changeMenu('home')">Home</a>
          </li>
          <li>
            <a href="#" @click="changeMenu('about')">About</a>
          </li>
          <li>
            <a href="#" @click="changeMenu('contact')">Contact</a>
          </li>
        </ul>
      </nav>
    </div>
    <div class="container">
      <!-- v-bind 디렉티브를 이용해 is 특성 값으로 어떤 컴포넌트를 나타낼 지 결정 -->
      <!-- keep-alive 요소를 이용해 캐싱할 컴포넌트를 지정할 수 있음. 
          include/exclude 특성을 이용하는 경우, 각 컴포넌트의 name 값을 지정해 주어야함.
          -->
      <keep-alive include="about,home">
        <component v-bind:is="currentView"></component>
      </keep-alive>
    </div>
  </div>
</template>

<script>
import Home from './components/Home.vue';
import About from './components/About.vue';
import Contact from './components/Contact.vue';

export default {
  components: { Home, About, Contact },
  data() {
    return { currentView: 'home' }
  },
  methods: {
    changeMenu(view) {
      this.currentView = view;
    }
  }
}
</script>

<style scoped>
.header {
  background-color: #666;
  padding-top: 10px;
}
.headerText {
  padding: 0 20px;
}
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: #800080;
}
li {
  float: left;
}
li a {
  display: block;
  color: yellow;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}
li a:hover {
  background-color: #666;
  color: #000;
}
</style>
