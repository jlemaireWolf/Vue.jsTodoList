<template>
  <div class="container">
    <div class="row">
      <div class="card">
        <div class="col-sm">
          <div class="hello">
            <h1 align="center">{{ msg }}</h1>
            <form class="col-8 mx-auto">
              <label for="exampleFormControlInput1">Tâche(s) à faire </label>
              <div class="input-group">
                <input
                  class="form-control"
                  id="exampleFormControlInput1"
                  v-model="userInput"
                  type="text"
                  placeholder="renseigner une tache"
                />

                <button
                  align="left"
                  :class="
                    userInput == ''
                      ? 'btn btn-outline-secondary'
                      : 'btn btn-outline-primary'
                  "
                  @click="addTodo($event)"
                >
                  ajouter
                </button>
              </div>
            </form>
            {{ userInput }}
            <div class="row">
              <ul class="col-8 mx-auto">
                <li v-for="(item, index) in items" :key="index">
                  {{ item }}
                  <button
                    class="btn btn-outline-primary"
                    @click="deleteTodo($event)"
                  >
                    x
                  </button>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDoList",
  data() {
    return {
      userInput: "",
      items: [],
    };
  },

  methods: {
    addTodo(event) {
      /**pour eviter le reload de la page car formulaire  */
      event.preventDefault();

      /**champ input vide apre sun ajout */

      /***muter le tableau , faire une copie, pour insereer un nouvelle items methode es6 */
      this.items = [...this.items, this.userInput];
      //this.items.push({itemsuserInput }),

      //this.userInput='',
      console.log(this.items);
      this.userInput = "";
      return this.items.map((item) => {
        return {
          item,
        };
      });
    },

    deleteTodo(event) {
      event.preventDefault();
      var array = this.items;
      var index = array.indexOf(this.item);
      console.log(this.item)
      /***function js pour supp un element */
      array.splice(index, 1);
      /*** mon  items est egale à mon array */

      this.items = array;
    },
  },
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body {
  background-color: red;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
  border-bottom: 1px solid white;
  padding: 0.5em;
}
li {
  display: inline-block;
  margin: 0 10px;
  border-bottom: 1px solid #f1f1f9;
  padding: 0.5em;
  width: 100%;
  line-height: 50px;
  font-weight: 500;
  color: #0d6efd;
  /* font-weight: 700; */
  text-align: left;
}
a {
  color: #42b983;
}

.btn-outline-primary {
  float: right;
}
</style>
