<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Inbox</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Inbox</ion-title>
        </ion-toolbar>
      </ion-header>
      
      <ion-list>
        <ion-button @click="scrollBottom">Scroll down</ion-button>
        <MessageListItem v-for="message in messages" :key="message.id" :message="message" />
        <ion-button @click="scrollTop">Scroll top</ion-button>
      </ion-list>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonList, IonPage, IonTitle, IonToolbar, IonButton, } from '@ionic/vue';
import MessageListItem from '@/components/MessageListItem.vue';
import { defineComponent } from 'vue';
import { getMessages } from '@/data/messages';

export default defineComponent({
  name: 'HomePage',
  data() {
    return {
      messages: getMessages()
    }
  },
  methods: {
    scrollBottom: () => {
      setTimeout(() => {
        const element = document.querySelector('ion-content');
        if(!element) {
          alert('Did not found any scrollable element');
          return;
        }
        element.scrollToBottom(0);
      }, 200);
    },
    scrollTop: () => {
      setTimeout(() => {
        const element = document.querySelector('ion-content');
        if(!element) {
          alert('Did not found any scrollable element');
          return;
        }
        element.scrollToTop(0);
      }, 200);
    },
  },
  components: {
    IonContent,
    IonHeader,
    IonList,
    IonPage,
    IonTitle,
    IonToolbar,
    MessageListItem,
    IonButton,
  },
});
</script>
