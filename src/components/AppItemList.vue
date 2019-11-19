<template>
  <div>
    <h5>{{ title }} <span class="badge badge-info">{{ items.length }} </span></h5>
    <div class="card">
      <div class="card-body">
        <ul class="list-group">
          <li class="list-group-item" v-for="item in items" v-bind:key="item">
            <div class="row align-items-center">
              <div class="col-md-8">
                {{ item }}
              </div>
              <div class="col-md-4 text-right">
                <button class="btn btn-danger btn-sm" v-on:click="deleteItem(item)"><span class="fas fa-trash"></span></button>
              </div>
            </div>
          </li>

        </ul>
        <br/>
        <div class="input-group">
          <input type="text" class="form-control" v-model="item" v-on:keyup.enter="addItem(item)" placeholder="Digite o item...">
          <div class="input-group-append">
            <button class="btn btn-info" v-on:click="addItem(item)"><i class="fas fa-plus"></i></button>
          </div>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppItemList",
  props: ["title", "items"],
  data() {
    return {
      item: ""
    };
  },
  methods: {
    addItem(item) {
      this.$emit("addItem", item);
      this.item = "";
    },
    deleteItem(item) {
      this.$emit("deleteItem", item);
    }
  }
};
</script>

<style scoped>

</style>
