<template>
  <div class="content">
    <div class="item-list">
      <h3>Item List</h3>
      <table>
        <tr>
          <th>Item</th>
          <th>Price</th>
          <th></th>
        </tr>
          <itemList itemName="Intel i3 12th gen" :itemPrice="8500" @addCart="addToArray" />
          <itemList itemName="Intel i5 12th gen" :itemPrice="10500" @addCart="addToArray" />
          <itemList itemName="Intel i7 12th gen" :itemPrice="12500" @addCart="addToArray" />
          <itemList itemName="Intel i9 12th gen" :itemPrice="14500" @addCart="addToArray" />
      </table>
    </div>
    <div class="cart-list">
      <h3>Shopping Cart</h3>
      <cartList :cartList="cartList" @removeCart="removeToArray" />
    </div>
  </div>
</template>

<script>
import itemList from '@/components/itemList.vue'
import cartList from '@/components/cartList.vue'

export default {
  name: 'ShopApp',
  components: {
    itemList,
    cartList
  },

  data() {
    return {
      cartList: []
    }
  },

  methods: {
    addToArray(item) {
      this.cartList.push(item);
      console.log('Cart List:', this.cartList); // Log the cartList array
    },

    removeToArray(index) {
      this.cartList.splice(index, 1);
    },
  }
}
</script>

<style>
    .content {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 20px;
    }

    .item-list {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    .cart-list {
      display: flex;
      flex-direction: column;
      align-items: center;
    }
</style>