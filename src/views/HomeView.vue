<template>
<navbarComponent />
<firtsSection />
<secondSection />
<thirdSection />
<fourthComponent />
<contactusComponent />
<footerComponent />
</template>
<script>
import navbarComponent from '../components/navbarComponent.vue';
import firtsSection from '../components/firstsectionComponent.vue';
import secondSection from "../components/secondsectionComponent.vue";
import thirdSection from "../components/thirdsectionComponent.vue";
import fourthComponent from "../components/fourthsectionComponent.vue";
import contactusComponent from "../components/contcactusComponent.vue";
import footerComponent from "../components/footerComponent.vue"
  export default{
    name: 'HomeView',
    components:{
      navbarComponent,
      firtsSection,
      secondSection,
      thirdSection,
      fourthComponent,
      contactusComponent,
      footerComponent
    }
  }
</script>