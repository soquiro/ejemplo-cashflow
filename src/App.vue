<template>
  <Suspense>
    <template #default> 
        <home/>
    </template>
    <template #fallback>
        <SplashScreen/>
    </template>
  </Suspense>
</template>

<script>
//  <SplashScreen/>
//import Home  from "@/components/Home.vue";
import SplashScreen  from "@/components/SplashScreen.vue";
//import { promiseHooks } from "v8";
import { defineAsyncComponent } from "vue";

export default{
    components:{
     
      SplashScreen,
      Home:defineAsyncComponent(()=>
      new Promise((resolve)=>{
        setTimeout(()=>{
            resolve(import("./components/Home.vue"))
        },2500);
      })),
    },
}
    
   
</script>

<style>
html,
body,
.app {
    min-height: 100vh;
    margin: 0;
    font-family: Arial, Helvetica, sans-serif;  
}
*{
    --brand-green:#04b500;
    --brand-blue:#0689b0;
}
</style>
