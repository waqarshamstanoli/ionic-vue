<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title @click="openGallery">Photo Gallery</ion-title>

      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large" >Tab 2</ion-title>
        </ion-toolbar>
      </ion-header>

      
    </ion-content>
    <ion-content :fullscreen="true">
  <ion-fab vertical="bottom" horizontal="center" style="margin-bottom: 100px;">
    <ion-fab-button @click="takePhoto()">
      <ion-img src="../../public/unnamed.jpg" alt="Image 1"></ion-img>
    </ion-fab-button>
  </ion-fab>
</ion-content>

  <ion-grid>
    <ion-row>
      <ion-col size="3" :key="photo.filepath" v-for="photo in photos">
        <ion-img :src="photo.webviewPath"></ion-img>
      </ion-col>
    </ion-row>
  </ion-grid>

 
  </ion-page>
</template>

<script setup lang="ts">
import { camera, trash, close } from 'ionicons/icons';
import {
  IonPage,
  IonHeader,
  IonFab,
  IonFabButton,
  IonIcon,
  IonToolbar,
  IonTitle,
  IonContent,
  IonGrid,
  IonRow,
  IonCol,
  IonImg,
} from '@ionic/vue';
import ExploreContainer from '@/components/ExploreContainer.vue';
import { usePhotoGallery, UserPhoto,  } from '@/composables/usePhotoGallery';
const {  photos, takePhoto, loadSaved,cachePhotos,openGallery } = usePhotoGallery();
import { ref, onMounted, watch } from 'vue';


onMounted(() => {
  loadSaved()
}),

watch(photos, cachePhotos,  { deep: true });





</script>
