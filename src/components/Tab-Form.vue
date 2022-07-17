<template>
     <div class="main-index">
      <div class="form-div">
        <p>Tabs</p>
        <div class="nav">
          <nav id="tab-form">
            <div class="form-input">
              <label htmlFor="numTabs" class="numTabs">Num.Tabs</label>
              <input placeholder="1" type="text" id="numTabs" class="inputNum" @change="editNum"/>
              <div class="error" v-if="num == 0"> Deve haver ao menos uma aba</div>
              <hr />

            </div>
              <form class="data-input">
                  <div class="form-input" v-for="(id, index) in array" :key="id">
                    <div class="form-container">
                      <label class="titulo">Título</label>
                      <input type="text" id="titulo" class="inputTitulo" v-model="titulos[index]" />
                      <div className="error" v-if="!titulos[index] && erro == true"> É necessário informar o título da aba</div>
                    </div>
                    <div class="form-container">
                      <label class="label-conteudo" >Conteúdo </label>
                      <textarea id="conteudo" class="textAConteudo" v-model="conteudos[index]" ></textarea>
                      <div className="error" v-if="!conteudos[index] && erro == true"> É necessário informar o conteúdo da aba</div>
                    </div>
                  </div>
                  <div class="form-btn">
                    <input type="button" class="submit-btn" @click="cadastro" value="Salvar" />
                  </div>
              </form>
          </nav>
        </div>
      </div>
      <div class="conteudo">
        <p>Conteúdo</p>
        <TabComponent :ids="titulosF" :contents="contentsF"/>
      </div>
    </div>
</template>

<script>
import TabComponent from './Tab-Component.vue';

  export default {
    name: "Tab-form",
    components: { TabComponent },

    data(){

        return{
            num: 1,
            array: Array,
            titulos: [],
            conteudos: [],
            titulosF: [],
            contentsF: [],
            erro: false,
            count: 0,
        }
    },

    methods : {

        editNum(event) {
            this.num = event.target.value;
            let rows = [];
            let aux = parseInt(this.num)
            for (let i = 0; i < aux; i++) {
            rows.push(i);
            }
            this.array = rows;
        },

        cadastro(){

          this.count = 0;
          
          for (let i = 0; i < this.num; i++) {
            if (!this.titulos[i]) {
              this.erro = true;
              this.count = this.count + 1;
            }
            if (!this.conteudos[i]) {
              this.erro = true;
              this.count = this.count + 1;
            }
          }

          if(this.count == 0){
            this.titulosF = this.titulos
            this.contentsF = this.conteudos
          }

        },
    }
  }

</script>

<style>

div.main-index{
  width: 100%;
  display: flex;
  flex-flow: row;
  align-items: center;
  justify-content: space-between;
}

div.form-div{
  align-items: flex-start;
  width: 100%;
  margin: 5px;
  margin-left: 20px;
  margin-bottom: 20px;
  margin-top: 20px;
  padding: 10px;
  box-shadow: 0 0 1em gray;
}

div.conteudo{
  width: 100%;
  margin: 50px;
  padding: 10px;
  box-shadow: 0 0 1em gray;
}

div.form-div p{
  font-family:Arial, Helvetica, sans-serif ;
  font-size: 25px;
  font-weight: bold;
}


div.conteudo p{
  font-family:Arial, Helvetica, sans-serif ;
  font-size: 25px;
  font-weight: bold;
}

.submit-btn{
  background-color: rebeccapurple;
  width: 100px;
  color: #e8f0f2;
  font-weight: bold;
  border-radius: 10%;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: .5s;
  align-items: flex-end;
  margin-bottom: 10px;
}

.submit-btn:hover{
  background-color: transparent;
  color: #222;
}

div.form-btn {
  text-align: right;
}

#tab-form{
  width: 100%;
  margin: 0 auto;
}

.form-input{
  text-align: right;
  align-items:flex-start;
  margin-bottom: 10px;
}

input{
  padding: 5px 10px;
  width: 500px;
  border-color: rgb(184, 181, 181);
  border-radius: 5px;
}

textarea{
  padding: 5px 10px;
  width: 500px;
  border-color: rgb(184, 181, 181);
  border-radius: 5px;
}

label{
  margin-top: 0;
  font-weight: bold;
  margin-bottom: 5px;
  color: #222;
  padding: 5px 10px;
}

.label-conteudo{

  vertical-align:top
}

hr{
  text-align: right;
  width: 94%;
  margin-right: 0;
}

.error{
  color: red;
}

.form-container{
  margin-bottom: 7px;
}

</style>