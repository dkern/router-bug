<template>
  <ion-page>
    <ion-content>
      <div id="app-loader">
        <div class="loader-icon">
          <img src="assets/icon/icon.png" />
        </div>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';
  import { IonPage, IonContent } from '@ionic/vue';
  import { useIonRouter, createAnimation } from '@ionic/vue';

  export default defineComponent({
    name: 'LoaderPage',
    components: {
      IonPage,
      IonContent,
    },
    setup() {
      const ionRouter = useIonRouter();

      setTimeout(() => {
        const animation = (baseEl: any) => {
          return createAnimation()
            .addElement(baseEl)
            .duration(2500)
            .fromTo('opacity', '1', '0');
        };

        // works
        // ionRouter.push('/folder/Inbox', animation);

        // didn't work
        ionRouter.replace('/folder/Inbox', animation);
      }, 2000);

      return {}
    }
  });
</script>

<style scoped>
  #app-loader {
    background-color: #fff;
    width: 100%;
    height: 100%;
    z-index: 9999;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  #app-loader .loader-icon {
    width: 75%;
    height: auto;
    margin-bottom: 24px;
  }
</style>
