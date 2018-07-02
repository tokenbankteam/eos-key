<template>
  <div class="hello">
    <h2>
      <a  class="logo"  href="https://www.mytokenpocket.vip/"><img src="https://dapp.mytokenpocket.vip/TokenPocket-logo-h.png"></a> 
      <span class="title">EOS公钥私钥生成器</span>
    </h2>
    <p>本工具用来随机生成一组EOS公钥私钥，生成过程可断网离线操作。</p>
    <p><strong>请一定注意记录并保管好您的私钥信息</strong></p>
    <button @click="generate">生成EOS公钥和私钥</button>
    <div v-if="privateKey">
      <p>公钥: {{publicKey}}</p>
      <p>私钥: {{privateKey}}</p>
    </div>
    
  </div>
</template>

<script>
import ecc from 'eosjs-ecc';

export default {
  name: 'HelloWorld',
  data () {
    return {
      privateKey: '',
      publicKey: ''
    }
  },
  mounted() {
    
  },
  methods: {
    generate() {
      ecc.randomKey().then(privateKey => {
        this.privateKey = privateKey;
        this.publicKey = ecc.privateToPublic(privateKey);
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

h2 {
  margin-bottom: 80px;
}

.logo {
  display: inline-block;
  vertical-align: middle;
}

.logo img {
  width: 300px;
  float: left;
}

.title {
  display: inline-block;
  vertical-align: middle;
}

strong {
  color: red;
}

button {
  color: #fff;
  background-color: #007bff;
  display: inline-block;
  font-weight: 400;
  text-align: center;
  white-space: nowrap;
  vertical-align: middle;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  border: 1px solid #007bff;
  padding: .375rem .75rem;
  font-size: 1rem;
  line-height: 1.5;
  border-radius: .25rem;
  transition: color .15s 
}

p {
  word-wrap: break-word;
}

a {
  color: #42b983;
}
</style>
