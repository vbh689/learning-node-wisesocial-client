<template>
  <div class="suggestions full-width">
    <div class="sd-title">
      <h3>提案</h3>
    </div>
    <!--sd-title end-->
    <div class="suggestions-list">
      <div class="suggestion-usd">
        <img src="../assets/images/resources/s1.png" alt="" />
        <div class="sgt-text">
          <h4>香野綾花</h4>
          <span>Graphic Designer</span>
        </div>
        <span><i class="fa fa-plus"></i></span>
      </div>
      <div class="suggestion-usd">
        <img src="../assets/images/resources/s2.png" alt="" />
        <div class="sgt-text">
          <h4>安座間麗美</h4>
          <span>PHP Developer</span>
        </div>
        <span><i class="fa fa-plus"></i></span>
      </div>
      <div class="suggestion-usd">
        <img src="../assets/images/resources/s3.png" alt="" />
        <div class="sgt-text">
          <h4>寺田航平</h4>
          <span>Wordpress Developer</span>
        </div>
        <span><i class="fa fa-plus"></i></span>
      </div>
      <div class="suggestion-usd">
        <img src="../assets/images/resources/s4.png" alt="" />
        <div class="sgt-text">
          <h4>長谷部千佳</h4>
          <span>C & C++ Developer</span>
        </div>
        <span><i class="fa fa-plus"></i></span>
      </div>
      <div class="suggestion-usd">
        <img src="../assets/images/resources/s5.png" alt="" />
        <div class="sgt-text">
          <h4>上田梓</h4>
          <span>Graphic Designer</span>
        </div>
        <span><i class="fa fa-plus"></i></span>
      </div>
      <div class="suggestion-usd">
        <img src="../assets/images/resources/s6.png" alt="" />
        <div class="sgt-text">
          <h4>システム太郎</h4>
          <span>PHP Developer</span>
        </div>
        <span><i class="fa fa-plus"></i></span>
      </div>
    </div>
    <!--suggestions-list end-->
  </div>
</template>

<script>
// import Vue from 'vue'
import axios from 'axios'

// import component1 from 'component1'
// import component2 from 'component2'

// bat dau phan than cua chuong trinh vuejs
export default {
  /***********************************************************************************************************
   ******************************* Pass data to child component **********************************************
   **********************************************************************************************************/
  // props: [variable1, variable2],
  // components: {component1, component2},
  data() {
    /***********************************************************************************************************
     ******************************* Initialize global variables ***********************************************
     **********************************************************************************************************/
    return {
      msg: 'Hello world!',
      users: [],
      token: sessionStorage.getItem("token"),
      suggestFriend: []
    }
  },
  created() {
    /***********************************************************************************************************
     *********************** Initialize data when this component is used. **************************************
     **********************************************************************************************************/
    console.log('Init created component and call to function get data from api server.');
    this.listSuggestFriend();
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
    }
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
    async listSuggestFriend() {
      try {
        const callAPI = await axios.get('http://localhost/wisesocial_api/public/api/list-suggest-friend', {
          headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer ' + this.token,
          }
        });
        if (callAPI.data.code == 200) {
          this.suggestFriend = callAPI.data.data;
        } else {
          alert("Call API failed, please check again!");
        }
        console.log(callAPI.data);
      } catch (err) {
        console.log(err);
      }
    },

    async deleteUser(id) {
      try {
        const callAPI = await axios.delete('http://localhost/DemoAPI/public/api/delete-user/' + id, {
          headers: {
            'Content-Type': 'application/json',
            'Authorization': 'Bearer 12|KpRlUny9IfRhG9h8wp3Emi7Mwv1eR1d5dt06Wavkb1be01bc'
          }
        }); 
        this.callAPI();
      } catch (err) {
        console.log(err);
      }

    }
  },
}
</script>

<style>
/**
* Custom local style css
*/
</style>