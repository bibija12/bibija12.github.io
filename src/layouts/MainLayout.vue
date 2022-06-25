<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />
		</q-toolbar>

        <div class="q-px-lg q-pt-xl q-mb-md">
          <div class="text-h3"><span>Todo</span></div><!--todo-->
          <div class="text-subtitle1">{{todaysdate}} </div><!--text-subtitle1-->
        </div><!--q-px-lg-->

        <q-img src = "../assets/mountains.jpg" class="header-image absolute-top">

        </q-img>



    </q-header>



    <!--Q-DRAWER-->

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :width="250"
      :breakpoint="600"
    >
      <q-scroll-area style="height: calc(100% - 142px); margin-top: 142px; border-right: 1px solid #ddd">
        <q-list padding>


          <!--Q-ITEM-->
          <q-item
            to="/"
            clickable
			v-ripple>
            <q-item-section avatar>
              <q-icon name="list" />
            </q-item-section>

            <q-item-section>
             Todo
            </q-item-section>
          </q-item>
          <!--Q-ITEM-->


          <!--Q-ITEM-->
          <q-item
            to="/help"
			exact
            clickable
	     v-ripple>
            <q-item-section avatar>
              <q-icon name="help" />
            </q-item-section>

            <q-item-section>
              Help
            </q-item-section>
          </q-item>
          <!--Q-ITEM-->


        </q-list>
      </q-scroll-area>

      <q-img class="absolute-top" src="../assets/mountains.jpg" style="height: 142px">
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">
            <img src="../assets/IMG_20200825_180511_773.jpg">
          </q-avatar>
          <div class="text-weight-bold">Abia jany</div>
          <div>@ Abia__jany</div>
        </div>
      </q-img>
    </q-drawer>
    <q-page-container>
       <router-view v-slot="{ Component }">
         <keep-alive>
           <component :is="Component" />
         </keep-alive>
        </router-view>
         <!--<keep-alive>
            <router-view/>
            </keep-alive>-->
        </q-page-container>
  </q-layout>
</template>

<script>
import { date } from 'quasar'



export default {
  name:'MainLayout',

  data () {
    return {
      leftDrawerOpen: false
    }
  },

  computed:{
    todaysdate(){
      let timeStamp = Date.now();
      return date.formatDate(timeStamp, 'dddd D MMMM');
    }
  }

}

</script>


<style lang="scss">
.header-image{
  height: 100%;
  z-index:-1;
  opacity:0.2;
  filter:grayscale(100%);
}

</style>
