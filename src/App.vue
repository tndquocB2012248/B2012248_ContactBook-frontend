<script>
  import AppHeader from "@/components/AppHeader.vue";
  
  export default {
    components: {
      AppHeader,
    },
  };
  </script>
  
  <template>
    <div id="app">
      <AppHeader />
      
      <div class="container ">
        <router-view />
      </div>
    </div>
  </template>
  
  <style>
    .page {
      max-width: 400px;
      margin: auto;
      font-size: 1.2rem;
    }
  </style>