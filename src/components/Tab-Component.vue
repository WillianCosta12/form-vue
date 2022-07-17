<template>
    <div class="Tabs">
      <div class="nav">
        <div v-for="(id, index) in ids" :key="id">
          <button @click="contentTab = contents[index]">{{id}}</button>
        </div>
      </div>
      <div class="outlet">
        <p>{{contentTab}}</p>
      </div>
    </div>
</template>

<script>
  export default {
    name: 'Tab-component',

    data(){
      return{
        contentTab: 'Sem Conteúdo',
      }
    },

    props: {
      ids: Array, 
      contents: Array
    } 
}
</script>

<style>


div.nav {
  width: 100%;
  margin: 0 auto 1rem;
  display: flex;
  justify-content:flex-start;

  @media (max-width: 768px) {
    width: 90%;
  }
}

div.nav button {
  height: 50px;
  padding: 1rem;
  margin: 0.5px 10px;
  list-style: none;
  text-align: center;
  cursor: pointer;
  transition: all 0.7s;
  border-top: none;
  border-left: none;
  border-right: none;
  font-size: 20px;
  color: rgb(73, 71, 71);
  background-color: white;
  border-bottom: solid 5px rebeccapurple;
  font-weight: bold;
}


div.nav button:hover {
  background-color: rgba(219, 209, 209, 0.299);
}

div.nav button.active {
  background-color: rgba(219, 209, 209, 0.299);
}

div.outlet {
  width: 100%;
  height: 180px;
  list-style: none;
  cursor: pointer;
  transition: all 0.7s;
  font-size: 25px;
  color: rgb(122, 118, 118);
}


</style>