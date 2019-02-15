<template>
  <div id="app">
    <!-- <div> -->
      <div class="titulo">
        <div>Formulario</div>
      </div>
      <div class="formulario">
        <div>
          <label>Curso :</label><el-input placeholder="Curso" v-model="curso"></el-input>
        </div>
        <div class="ele">
        <label class="facu">Facultad :</label><el-input placeholder="Facultad" v-model="facultad"></el-input>
        </div>
        <div>
        <label >Tema :</label>
          <select class="input-form btn">
            <option>123</option>
            <option>456</option>
            <option>789</option>
          </select>
        </div>
      </div>
      <div class="button">
        <el-button type="primary" plain>Primary</el-button>
      </div>
    <!-- </div> -->
    <!-- <div class="test">
      <div>123</div><div>456</div><div>789</div>
    </div> -->
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      curso: '',
      facultad: ''
    }
  },methods: {
    asd () {
      
    }
  }
}
</script>

<style lang="scss">
* {
  padding: 0px;
  margin: 0px;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

#app{
  width: 700px;
  margin: 0 auto;
}

.titulo {
  font-size: 2em;
  color: gray;
  font-weight: bold;
  margin: 10px 15px;
}
.formulario {
  display: flex;
  position: relative;
  flex-wrap: wrap;
  width: 100%;
  height: auto;
}

.formulario div {
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 5px;
  width: 50%;
}

.input-form{
  border: 1px gray solid;
  border-radius: 4px;
  padding: 5px 6px;
  width: 162px;
  transition:all 0.3s ease;
}

.btn {
  background-color: white;
  height: 40px;
  outline: none
}

.input-form:focus{
  border: .5px lightskyblue solid ;
}

.button {
  display: flex;
  justify-content: center;
  padding: 20px;
}

.test {
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 350px;
  height: auto;
  background-color: lightblue;
}

.test div {
  width: 100px;
  height: 100px;
  background-color: yellow;
}

// .uno {
//   width:483px;
//   height:298px;
//   background:#676470;
//   transition:all 0.3s ease;
// }
</style>
