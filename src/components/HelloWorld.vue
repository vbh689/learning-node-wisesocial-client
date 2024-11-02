<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <!-- class binding -->
    <h2 :class="clsColor" v-on:click="changeColor()">{{ demo }}</h2>

    <!-- Increment count -->
    <br>
    <button v-on:click="plus()">Count</button>
    <p>{{ count }}</p>

    <!-- Text box  -->
    <br>
    <input type="text" placeholder="Nhap du lieu vao day" v-model="txt_data" v-on:keyup="updateTxtData()">
    <p style="color: blue;">Content: {{ txt_data }}</p>
    <p style="green">Word count: {{ word_count }}</p>
    <p style="red" v-if="msg_error == true">Ban nhap qua 255 ky tu.</p>
    <p style="green" v-else>Ban co the nhap 255 ky tu.</p>

    <br>
    <h3>List user</h3>
    <table border="1">
      <thead>
        <tr>
          <th>ID</th>
          <th>Email</th>
          <th>Address</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in list_user">
          <td>{{ user.id }}</td>
          <td>{{ user.email }}</td>
          <td>{{ user.address }}</td>
          <td><button v-on:click="removeUser(user.id)">Remove</button></td>
        </tr>
      </tbody>
    </table>

    <!-- To add user -->
    <br>
    <input type="text" name="email" v-model="email" placeholder="Nhap email">
    <input type="text" name="address" v-model="address" placeholder="Nhap dia chi">
    <button v-on:click="store_user()">Add user</button>
  </div>
</template>

<script>
// import Vue from 'vue'
// import axios from 'axios'

// import component1 from 'component1'
// import component2 from 'component2'

// bat dau phan than cua chuong trinh vuejs
export default {
  /***********************************************************************************************************
   ******************************* Pass data to child component **********************************************
   **********************************************************************************************************/
  // prop: [variable1, variable2],
  // components: {component1, component2},
  data() {
    /***********************************************************************************************************
     ******************************* Initialize global variables ***********************************************
     **********************************************************************************************************/
    return {
      msg: 'Hello world!',
      demo: 'This is a demo text (1).',
      clsColor: 'red',

      count: 0,
      txt_data: '',
      word_count: 0,
      msg_error: false,

      list_user: [
        {
          "id": 1,
          "email": "test@test.com",
          "address": "Ha Noi"
        },
        {
          "id": 2,
          "email": "test2@test.com",
          "address": "Ha Tay"
        }
      ],

      email: '',
      address: ''
    }
  },
  created() {
    /***********************************************************************************************************
     *********************** Initialize data when this component is used. **************************************
     **********************************************************************************************************/
    console.log('Init created component and call to function get data from api server.');
  },
  mounted() {
    /***********************************************************************************************************
     ******************** Once created, the interface is displayed and calls mounted. **************************
     **********************************************************************************************************/
  },
  watch: {
    /***********************************************************************************************************
     ********************************* Methods change value for a variable *************************************
     **********************************************************************************************************/
    msg() {
      console.log("When the value of the msg variable changes, this method will be executed.");
    },

    // in watch method, we can use the name of the variable as function
    // it will be called when the value of the variable changes
    word_count() {
      if (this.word_count > 255) {
        this.msg_error = true;
      } else {
        this.msg_error = false;
      }
    },
  },
  computed: {
    appendMsg() {
      return msg + "Process the value and assign the value to the corresponding variable the var has changed.";
    }
  },
  methods: {
    /***********************************************************************************************************
     ******************************* Default functions that handle local data **********************************
     **********************************************************************************************************/

    /**
     * Example default function not using param
     */
    defaultFunction() {
      this.msg = "Replace message here!";
    },
    changeColor() {
      if (this.clsColor == "red") {
        this.clsColor = "green";
      } else {
        this.clsColor = "red";
      }
    },
    plus() {
      this.count++;
    },
    updateTxtData() {
      this.word_count = this.txt_data.length;
    },
    /**
     * Removes a user from the list based on the provided user ID.
     * 
     * This method iterates through the list of users (list_user) and checks 
     * if the ID of any user matches the given ID. If a match is found, 
     * that user is removed from the list using the splice method.
     * 
     * @param {number} id - The ID of the user to be removed.
     */
    removeUser(id) {
      for (let i = 0; i < this.list_user.length; i++) {
        if (id === this.list_user[i].id) {
          this.list_user.splice(i, 1);
          break; // Exit the loop after removing the user
        }
      }
    },
    store_user() {
      // get max current id value
      let max_id = 0;
      // alert(max_id);
      for (let i = 0; i < this.list_user.length; i++) {
        if (this.list_user[i].id > max_id) {
          max_id = this.list_user[i].id;
        }
      };

      let newUser = {
        "id": max_id + 1,
        "email": this.email,
        "address": this.address
      };

      this.list_user.push(newUser);
      this.email = '';
      this.address = '';
    },

    /**
     * Example default function using param 
     *
     * @param int pageNum number of page
     * @return boolean
     */
    defaultFunctionUsingParam(pageNum) {
      console.log(pageNum);
      return false;
    },

    /***********************************************************************************************************
     ******* Async and await functions for manipulating server-side data through internal API protocols ********
     **********************************************************************************************************/

    /**
     * Call API sample
     */
    async callAPI() {
      try {
        const callAPI = await axios.get('/apiendpoint', {
          /************ Attach param for request here ***************/
        });
        console.log(callAPI.data);
      } catch (err) {
        console.log(err);
      }
    },
  },
}
</script>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {

  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}

.red {
  color: red;
}
</style>
