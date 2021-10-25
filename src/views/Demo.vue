<template>
    <section class="content">
      <h1>研修用のページ</h1>


<!--      配列の出力の仕方はrailsと同じ-->
      <ul>
        <li v-for="d in data" :key="d.id">
          <p>{{ d.name }}</p>
          <img :src="d.image">
        </li>
      </ul>

      <button @click="getData" >取得する</button>
    </section>
</template>

<script>
    import { ref, onMounted } from 'vue';
    import axios from 'axios';

    export default {
      name: "Demo",
      setup() {
        const data = ref([]);

        // ここでAPIの読み込み
        const getData = () => {
          axios.get('https://script.google.com/a/macros/s-online.co.jp/s/AKfycbwvrRsYMUM52D3RCpa_OwobeAxDLtigaXcPWOucIn1rrgqTLFWsJrbofXBhGNrmnzicdQ/exec')
          .then((res) => {
            data.value = res.data;
          }).catch((e) => {
            alert(e);
          });
        }

        // 処理の前にMountedするとバグるので注意
        onMounted(getData);

        return{ data }
      }
    }
</script>