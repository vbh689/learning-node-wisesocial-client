<script setup lang="ts">
import FriendRequestComponent from '@/components/FriendRequestComponent.vue';
import HeaderComponent from '@/components/HeaderComponent.vue';
import MostFollowComponent from '@/components/MostFollowComponent.vue';
import MyFavoriteComponent from '@/components/MyFavoriteComponent.vue';
import SuggestionComponent from '@/components/SuggestionComponent.vue';
import TimelimeComponent from '@/components/TimelimeComponent.vue';
import UserProfileComponent from '@/components/UserProfileComponent.vue';
</script>

<template>
  <div class="wrapper">
    <!-- Begin header -->
     <HeaderComponent/>
    <!-- Header end -->

    <main>
      <div class="main-section">
        <div class="container">
          <div class="main-section-data">
            <div class="row">
              <div class="col-lg-3 col-md-4 pd-left-none no-pd">
                <div class="main-left-sidebar no-margin">

                  <!-- User data -->
                   <UserProfileComponent/>
                  <!-- user-data end -->
                  
                  <!-- Suggestion -->
                   <SuggestionComponent/>
                  <!-- suggestions end -->

                  <div class="tags-sec full-width">
                    <div class="cp-sec">
                      <img src="../assets/images/logo2.png" alt="" />
                      <p>&copy; Copyright 2024.</p>
                    </div>
                  </div>
                  <!--tags-sec end-->
                </div>
                <!--main-left-sidebar end-->
              </div>
              <div class="col-lg-6 col-md-8 no-pd">

                <!-- Main-ws -->
                 <TimelimeComponent/>
                <!--main-ws-sec end-->

              </div>
              <div class="col-lg-3 pd-right-none no-pd">
                <div class="right-sidebar">
                  
                  <!-- Most follow widget -->
                   <MostFollowComponent/>
                  <!--widget-about end-->

                  <!-- Favorite post -->
                  <MyFavoriteComponent/>
                  <!-- End Favorite post -->

                  <!-- Request friend People-->
                   <FriendRequestComponent/>
                  <!-- Friend request End -->
                </div>
                <!--right-sidebar end-->
              </div>
            </div>
          </div>
          <!-- main-section-data end-->
        </div>
      </div>
    </main>
    <!--chatbox-list end-->
  </div>
</template>
