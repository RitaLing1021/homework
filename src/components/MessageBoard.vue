<template>
<div id="app">
  <div class="text-end">
    <button class="btn btn-primary" type="button" v-on:click="addItem">新增</button>
  </div>
  <table class="table">
    <thead>
      <tr>
        <th>標題</th>
        <th>內容</th>
        <th>編輯</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in products" :key="item.id">
        <td>{{ item.name }}</td>
        <td>{{ item.note }}</td>
        <td>
          <button type="button" class="btn btn-outline-primary"
          v-on:click="editItem(item)">修改</button>
        </td>
      </tr>
    </tbody>
  </table>
  <form v-if="isNew || temp.id">
    <div class="mb-3">
      <label for="productName" class="form-label">標題
      <input type="text" id="productName"
        class="form-control"
        v-model="temp.name"
      ></label>
    </div>
    <div class="mb-3">
      <label for="productNote" class="form-label">內容
      <input type="text" id="productNote"
        class="form-control"
        v-model="temp.note"
      ></label>
    </div>
    <button type="button"
    class="btn btn-secondary"
    v-on:click="confirmEdit">更新</button>
  </form>
</div>
</template>

<script>
  const products = [{
  id: '1',
  name: '我想下班',
  note: '今天禮拜五',
},
{
  id: '2',
  name: '下班還要加班',
  note: '小孩都不睡覺',
}];

export default {
  data() {
    return {
      products: [],
      temp: {},
      isNew: 'false',
    };
  },
  methods: {
    addItem() {
      this.isNew = true;
      this.temp = {};
    },
    editItem(item) {
      this.temp = { ...item };
    },
    confirmEdit() {
      if (!this.temp.id) {
        this.temp.id = new Date().getTime();
        this.products.push(this.temp);
      } else {
        this.products.forEach((item, i) => {
          if (item.id === this.temp.id) {
            this.products[i] = this.temp;
          }
        });
      }
      this.isNew = false;
      this.temp = {};
    },
  },
  created() {
    this.products = products;
  },
};
</script>
