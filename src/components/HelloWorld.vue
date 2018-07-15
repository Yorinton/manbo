<template>
  <div class="hello">
      <div id="image" :style="styleObject">{{example}}</div>
      <textarea rows="5" cols="50" v-model="example"></textarea><br>
      <button v-on:click="toImage()">画像化</button>
      <div id="container"></div>
  </div>
</template>
<script>

// htmlを画像化してcanvas要素を作成するライブラリ
import html2canvas from 'html2canvas'

export default {
    name: 'HelloWorld',
    data () {
        return {
            example: '',
            styleObject: {
                fontSize: '20px',
                backgroundImage: 'url("http://localhost/static/img/diving.b894e72.jpg")',
                backgroundRepeat: 'no-repeat',
                backgroundPosition: 'top center',
                textAlign: 'center',
                height: '400px',
                lineHeight: '400px',
                width: '50%',
                margin: 'auto',
                marginBottom: '1rem',
                color: 'white'
            }
        }
    },
    methods: {
        toImage: function () {
            // 作成した画像を入れるコンテナ
            let container = document.getElementById('container');

            // 既に要素が入っている場合は削除
            if (container.firstChild) {
                container.removeChild(container.firstChild);
            }

            // 画像作成してコンテナに入れる
            html2canvas(document.getElementById('image')).then(function(canvas) {
                document.getElementById('container').appendChild(canvas);
            });
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
