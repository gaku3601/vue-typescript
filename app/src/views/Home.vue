<template>
  <div class="home">
    {{incrementCounter}}
    <button @click="increment">add</button>
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src
import { counterModule } from '@/store/modules/counter';

@Component({
  components: {
    HelloWorld,
  },
})
export default class Home extends Vue {
  get incrementCounter() {
    return counterModule.incrementCounter; // インテリセンスが効く
  }
  increment() {
    counterModule.SET_INCREMENT_COUNTER(counterModule.incrementCounter + 1); // 型チェックが効く
  }
}
</script>
