<template>
  <div id="app">
    <h1>My Wishlist📌</h1>
    <p>Don't forget to save your money</p>
    
    <!-- Form untuk menambah item baru -->
    <div class="input-section">
      <input type="text" v-model="newItem" placeholder="Enter item...">
      <button @click="addItem">Add</button>
    </div>
    
    <!-- Daftar item wishlist -->
    <div v-if="wishlist.length > 0" class="wishlist">
      <div v-for="(item, index) in wishlist" :key="index" class="wishlist-item">
        <p>{{ item }}</p>
        <button @click="removeItem(index)">Remove</button>
      </div>
    </div>
    <div v-else>
      <p>Your wishlist is empty.</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: '',
      wishlist: []
    };
  },
  methods: {
    addItem() {
      if (this.newItem.trim() !== '') {
        this.wishlist.push(this.newItem.trim());
        this.newItem = '';
      }
    },
    removeItem(index) {
      this.wishlist.splice(index, 1);
    }
  }
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
}

.input-section {
  margin-bottom: 20px;
}

input {
  padding: 10px;
  border: 1px solid #eb9c9c;
  border-radius: 5px;
}

button {
  padding: 10px 20px;
  background-color: #e4b9b8;
  color: rgb(230, 124, 124);
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #a75546;
}

.wishlist {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.wishlist-item {
  background-color: #030101;
  padding: 10px;
  margin: 5px;
  border-radius: 5px;
}

.wishlist-item p {
  margin: 0;
}

.wishlist-item button {
  margin-top: 5px;
}
</style>
