<template>
    <div class="home">
        <h1>Welcome to the Home Page</h1>
        <p>This is the content of the home page.</p>
        <button   type="button"
          class="btn btn-lg btn-alt-secondary"
          @click="logout">

            Logout
        </button>
    </div>
</template>
<script setup>
import { useTemplateStore } from "@/stores/template";
import { useRouter } from "vue-router";


// Main store
const store = useTemplateStore();
const router = useRouter();

// Set default elements for this layout
store.setLayout({
  header: false,
  sidebar: false,
  sideOverlay: false,
  footer: false,
}); 

// Set various template options for this layout variation
store.mainContent({ mode: "full" });

const logout= ()=> {
  
  router.push({ name: "auth-signin" });
  localStorage.removeItem('token');
 }
</script>

<style scoped>
.home {
    text-align: center;
    margin-top: 50px;
}
</style>
