<template>
    <div class="login-content">
        <div class="login-itemlist">
            <h3>Item List</h3>
            <table>
                <tr>
                    <th>Item</th>
                    <th>Price</th>
                    <th></th>
                </tr>
                    <itemList itemName="Intel i3 12th gen" :itemPrice="8500" :isDisabled="itsDisabled" />
                    <itemList itemName="Intel i5 12th gen" :itemPrice="10500" :isDisabled="itsDisabled" />
                    <itemList itemName="Intel i7 12th gen" :itemPrice="12500" :isDisabled="itsDisabled" />
                    <itemList itemName="Intel i9 12th gen" :itemPrice="14500" :isDisabled="itsDisabled" />
            </table>
        </div>
    
        <div class="login-form">
            <h3>Login</h3>
            <h5>Enter Password <br> {{ errmsg }}</h5>
            <input type="password" v-model="password">
            <button @click="login()">Login</button>
        </div>
    </div>
</template>

<script>
import itemList from '@/components/itemList.vue'

export default {
    name: 'loginPage',
    components: {
        itemList,
    },
    
    data() {
        return {
            password: '',
            errmsg: '',
            itsDisabled: true
        }
    },

    methods: {
        login() {
            if (this.password != 'abcdef') {
                this.errmsg = 'wrong password';
            } else {
                localStorage.setItem('authToken', 'true'); // Set the 'logged' item in localStorage to 'true'
                this.$router.push('/shop')
            }
        }
    }
};

</script>

<style>

.login-content {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
    }

.login-form {
    display: grid;
    grid-template-rows: repeat(3, 0.1fr);
    padding-inline: 30%;
    gap: 10px;
}

.login-itemlist {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  border: 1px solid black;
  text-align: center;
  padding: 5px;
}
</style>