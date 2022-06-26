<template>
  <div class="home">
    <HeaderComponent></HeaderComponent>
    <div class="flex flex-row">
      <MenuComponent></MenuComponent>
      <div
        class="margin-auto 2xl:container h-auto py-2 px-2 md:px-5 lg:px-5 xl:px-5 grid grid-cols-1 md:grid-cols-2 lg:grid-cols-2 xl:grid-cols-3 gap-2 md:gap-3"
      >
        <VehicleComponentMobile
          class="block md:hidden"
          v-for="vehicle of vehicles"
          :key="vehicle"
          :vehicle_media_urls="vehicle.media_urls"
          :vehicle="vehicle"
        >
        </VehicleComponentMobile>

        <VehicleComponent
          class="hidden md:block lg:block xl:block 2xl:block"
          v-for="vehicle of vehicles"
          :key="vehicle"
          :vehicle_media_urls="vehicle.media_urls"
          :vehicle="vehicle"
        >
        </VehicleComponent>
      </div>
    </div>
    <FooterComponent></FooterComponent>
  </div>
</template>

<script>
import json from "@/assets/data.json";
import HeaderComponent from "@/components/partials/HeaderComponent.vue";
import FooterComponent from "@/components/partials/FooterComponent.vue";
import MenuComponent from "@/components/partials/MenuComponent.vue";
import VehicleComponentMobile from "@/components/partials/VehicleComponentMobile.vue";
import VehicleComponent from "@/components/partials/VehicleComponent.vue";

export default {
    name: 'HomeView',
  components: {
    HeaderComponent,
    FooterComponent,
    MenuComponent,
    VehicleComponentMobile,
    VehicleComponent,
  },
  data() {
    return {
      vehicles: json.data,
      vehicle_media_urls: "",
      vehicle: "",
    };
  },
  created() {
  },
};
</script>

<style lang="less">
.margin-auto {
  margin-left: auto;
  margin-right: auto;
}
</style>
