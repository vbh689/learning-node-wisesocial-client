<template>
  <!-- <div class="row">
    <h1>Login and register</h1>
  </div> -->

  <div class="wrapper">
    <div class="sign-in-page">
      <div class="signin-popup">
        <div class="signin-pop">
          <div class="row">
            <div class="col-lg-6">
              <div class="cmp-info">
                <div class="cm-logo">
                  <img src="/src/assets/images/cm-logo.png" alt="" />
                </div>
                <!--cm-logo end-->
                <img src="/src/assets/images/cm-main-img.png" alt="" />
              </div>
              <!--cmp-info end-->
            </div>
            <div class="col-lg-6">
              <div class="login-sec">
                <ul class="sign-control">
                  <li data-tab="tab-1" class="current">
                    <a href="#" title="">Sign In</a>
                  </li>
                  <li data-tab="tab-2">
                    <a href="#" title="">Sign Up</a>
                  </li>
                </ul>
                <div class="sign_in_sec current" id="tab-1">
                  <h3>Sign In</h3>
                  <form>
                    <div class="row">
                      <div class="col-lg-12 no-pdd">
                        <div class="sn-field">
                          <input type="text" name="email" placeholder="Email" />
                          <i class="fa fa-user"></i>
                        </div>
                        <!--sn-field end-->
                      </div>
                      <div class="col-lg-12 no-pdd">
                        <div class="sn-field">
                          <input
                            type="password"
                            name="password"
                            placeholder="Password"
                          />
                          <i class="fa fa-lock"></i>
                        </div>
                      </div>
                      <div class="col-lg-12 no-pdd">
                        <button type="submit" value="submit">Sign In</button>
                      </div>
                    </div>
                  </form>
                  <!--login-resources end-->
                </div>
                <!--sign_in_sec end-->
                <div class="sign_in_sec" id="tab-2">
                  <!--signup-tab end-->
                  <div class="dff-tab current" id="tab-3">
                    <form>
                      <div class="row">
                        <div class="col-lg-12 no-pdd">
                          <div class="sn-field">
                            <input type="text" name="name" placeholder="氏名" />
                            <i class="fa fa-user"></i>
                          </div>
                        </div>
                        <div class="col-lg-12 no-pdd">
                          <div class="sn-field">
                            <input
                              type="text"
                              name="country"
                              placeholder="国"
                            />
                            <i class="fa fa-globe"></i>
                          </div>
                        </div>
                        <div class="col-lg-12 no-pdd">
                          <div class="sn-field">
                            <input
                              type="password"
                              name="password"
                              placeholder="Password"
                            />
                            <i class="fa fa-lock"></i>
                          </div>
                        </div>
                        <div class="col-lg-12 no-pdd">
                          <div class="sn-field">
                            <input
                              type="password"
                              name="repeat-password"
                              placeholder="Repeat Password"
                            />
                            <i class="fa fa-lock"></i>
                          </div>
                        </div>
                        <div class="col-lg-12 no-pdd">
                          <div class="checky-sec st2">
                            <div class="fgt-sec">
                              <input type="checkbox" name="cc" id="c2" />
                              <label for="c2">
                                <span></span>
                              </label>
                              <small> はい、Wise
                                の利用規約を理解し、同意します。</small>
                            </div>
                            <!--fgt-sec end-->
                          </div>
                        </div>
                        <div class="col-lg-12 no-pdd">
                          <button type="submit" value="submit">開始する</button>
                        </div>
                      </div>
                    </form>
                  </div>
                </div>
              </div>
              <!--login-sec end-->
            </div>
          </div>
        </div>
        <!--signin-pop end-->
      </div>
    </div>
    <!--sign-in-page end-->
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
  // props: ["txtMSG"],
  // components: {component1, component2},
  data() {
    /***********************************************************************************************************
     ******************************* Initialize global variables ***********************************************
     **********************************************************************************************************/
    return {
      msg: "Test message 1.",
    };
  },
  /**
   * Define global service socket
   *
   * Listing event from socket.io server
   * "ServerSendCommentToClient" is the name of the channel that sends notifications to all clients installed in the server socket
   */
  sockets: {
    // Send data to server
    ClientSendCommentToServer: function (responseComment) {
      this.comment = responseComment;
    },
    // Listen event from server and render data
    ServerSendCommentToClient: function (responseComment) {
      // Push to the comment list
      if (
        responseComment.type === "comment" &&
        this.transaction.id == responseComment.transaction_id
      ) {
        this.pushCommentToList(responseComment);
        this.$forceUpdate();
      }
    },
  },
  created() {
    /***********************************************************************************************************
     *********************** Initialize data when this component is used. **************************************
     **********************************************************************************************************/
    console.log(
      "Init created component and call to function get data from api server."
    );
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
      console.log(
        "When the value of the msg variable changes, this method will be executed."
      );
    },
  },
  computed: {
    appendMsg() {
      return (
        msg +
        "Process the value and assign the value to the corresponding variable the var has changed."
      );
    },
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
    
    leaveRoom() {
      this.$socket.emit("ClientSendCommentToServer", {
        transaction_id: this.transaction.id,
        // Pass param obj]
      });
    },
    // Join a room
    joinRoom() {
      this.$socket.emit("ClientSendCommentToServer", {
        // Pass param obj
        // transaction_id: this.transaction.id,
        transaction_id: 1,
      });
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
        const callAPI = await axios.get("/apiendpoint", {
          /************ Attach param for request here ***************/
        });
        console.log(callAPI.data);
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>

<style>
/**
* Custom local style css
*/
</style>