<template>
  <div id="app">
    <div class="titulo">
      <div>Formulario</div>
    </div>
    <div class="formulario">
      <div>
        <label>Curso :</label>
        <el-autocomplete
          class="inline-input"
          v-model="curso"
          :fetch-suggestions="querySearch"
          placeholder="Please Input"
          @select="handleSelect"
        ></el-autocomplete>
      </div>
      <div class="ele">
        <label class="facu">Facultad :</label>
        <el-input placeholder="Facultad" v-model="facultad"></el-input>
      </div>
      <div>
        <label>Tema :</label>
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
    <!-- <div class="test"> -->
      <!-- <div>A</div><div>B</div><div class="c"><div>C1</div><div>C2</div></div> -->
      <!-- </div><div>D</div><div>E</div><div>F</div> -->
      <!-- <div class="d1">
        <label>123</label>
        <input type="text"/>
      </div>
      <div class="d2">
        <label>456</label>
        <input type="text"/>
      </div>
      <div class="d3">
        <label>789</label>
        <input type="text"/>
      </div> -->
    <!-- </div> -->
  </div>
</template>

<script>
import axios from "axios"

export default {
  name: "app",
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      curso: "",
      facultad: "",
      arrayCursos: [],
      arrayFacultad: []
    }
  },
  methods: {
    async getData() {
      try {
        this.data = await axios.get("http://localhost:1010/data")
        const data = this.data.data
        this.arrayFacultad = data[0].Facultad
        this.arrayCursos = data[1].Cursos
      } catch (error) {
        console.log(error)
      }
    },
    querySearch(queryString, cb) {
      console.log('queryString', queryString)
      const arrayCursos = this.arrayCursos
      const results = queryString ? arrayCursos.filter(this.createFilter(queryString)) : arrayCursos
      const top3 = results.slice(0, 3);
      cb(results);
    },
    createFilter(queryString) {
      return (array) => {
        return (
          array.name.toLowerCase().includes(queryString.toLowerCase())
        )
      }
    },
    toJson(json) {
      const data = JSON.parse(JSON.stringify(json));
      return data
    },
    handleSelect(item) {
      console.log(item)
    }
  },
  mounted() {
    this.getData();
  }
};
</script>

<style lang="scss">
* {
  padding: 0px;
  margin: 0px;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

#app {
  width: 100vw;
  height: 100vh;
  // background-color: gray;
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

.input-form {
  border: 1px gray solid;
  border-radius: 4px;
  padding: 5px 6px;
  width: 162px;
  transition: all 0.3s ease;
}


.el-input__inner {
  width: 450px;
}

.flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.btn {
  background-color: white;
  height: 40px;
  outline: none;
}

.input-form:focus {
  border: 0.5px lightskyblue solid;
}

.button {
  display: flex;
  justify-content: center;
  padding: 20px;
}

.test {
  display: flex;
  // flex-wrap: wrap;
  align-items: flex-end;

  width: 100vw;
  height: 300px;
  // justify-content: space-around;
}

.d2, .d3 {
  display: flex;
  align-self: center;
}


// .test > div {
//   width: 150px;
//   height: 150px;
//   background-color: yellow;
//   border-radius: 50%;
//   text-align: center;
//   line-height: 150px;
// }

// .c {
//   display: flex;
//   justify-content: space-around;
//   align-self: flex-end;
// }

// .c div {
//   display: flex;
//   justify-content: space-around;
//   flex-direction: column
// }
</style>
