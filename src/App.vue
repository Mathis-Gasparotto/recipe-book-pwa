<template>
  <div class="dark">
    <div v-if="route.name || route.name !== 'NotFound'">
      <NavBar />
      <div class="p-4 sm:ml-64 text-black dark:text-white">
        <router-view></router-view>
      </div>
    </div>
    <router-view v-else></router-view>
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue'
import { useRoute } from 'vue-router'
import { initShoppingList } from './services/shoppingListService'
import { initUser } from './services/userService'
import { initRecipes } from './services/recipesService'
import { initIngredients } from './services/ingredientsService'
import { getMessaging, getToken } from "firebase/messaging";

export default {
  setup() {
    const route = useRoute()
    return {
      route
    }
  },
  components: {
    NavBar
  },
  created() {
    initShoppingList()
    initUser()
    initRecipes()
    initIngredients()
    // window.Tesseract = Tesseract.create({
    //   workerPath: '/assets/lib/tesseract.js-worker_5.0.4.js',
    //   langPath: '/assets/lib/lang/tesseract.js-fra.traineddata.gz',
    //   corePath: '/assets/lib/tesseract-core.js',
    // })
    
    
  }
}
</script>