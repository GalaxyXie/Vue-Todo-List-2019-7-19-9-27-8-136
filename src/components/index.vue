<template>
  <div class="index">
    <div class="container">
      <div>
        <h2>Jquery To Do List</h2>
        <p>
          <em>Simple Todo List with adding and filter by diff status.</em>
        </p>
      </div>
      <div>
        <input class="input-text" type="text" v-model="checkString" />
        <div id="button" @click="add">Add</div>
      </div>
      <br />
      <Content :items="items" />
      <div>
        <ul id="filters">
          <li>
            <a  data-filter="all"  @click="showAll">ALL</a>
          </li>
          <li>
            <a data-filter="active"  @click="showChecked">Active</a>
          </li>
          <li>
            <a data-filter="complete" @click="showNotChecked">Complete</a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Content from "./content";
export default {
  name: "index",
  components: {
      Content,
  },
  data() {
    return {
      checkString: "",
      items: [],
      itemsCopy:[],
    };
  },
  methods: {
    add() {
      
      this.items.push({stringcontent:this.checkString,isChecked:false});
      this.itemsCopy=this.items.slice();
      this.checkString= "";
    },
    showAll() {
      this.items=this.itemsCopy;
    },
    showChecked(){
      this.items=null;
      this.items=this.itemsCopy.filter(item=>item.isChecked==false);
      this.checkString= "";
    },
    showNotChecked(){
      this.items=null;
      this.items=this.itemsCopy.filter(item=>item.isChecked==true);
      this.checkString= "";
    },
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url("../css/todo.css");

</style>
