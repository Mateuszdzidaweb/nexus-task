<template>
  <div>
    <div class="h-auto grid grid-cols-3 gap-1">
      <div class="float-left" v-for="index in 3" :key="index">
        <img style=" ;" class="rounded-xl" :src="vehicle_media_urls[0]['thumb']" alt="" />
      </div>
    </div>
    <div class="vehicle_details_wrapper">
      <div class="w-full flex justify-between pt-5">
        <div class="flex text-xl">
          <h1 class="text-black px-1">{{ vehicle.plate }}</h1>
          <h1 class="text-black px-1">{{ vehicle.make }}</h1>
          <h1 class="text-black px-1">{{ vehicle.model }}</h1>
        </div>
        <div class="flex flex-row text-md gap-2">
          <h1 class="advert_classification normal-case text-black px-1">
            {{ vehicle.advert_classification }}
          </h1>
          <img
            v-if="vehicle.advertisable_id == 54651"
            class="px-2"
            src="@/assets/icons/star.svg"
            alt=""
          />
          <img v-else class="px-2" src="@/assets/icons/star-black.svg" alt="" />
        </div>
      </div>
      <div class="flex w-full text-md text-gray-600 pb-3">
        <h1 v-if="vehicle.attention_grabber" class="px-1">
          {{ vehicle.attention_grabber }}
        </h1>
        <h1 v-else class="px-1">CLA 250E Coupe Shooting Break</h1>
      </div>
      <div class="flex w-full justify-between">
        <div class="flex flex-col py-2">
          <div class="flex flex-row">
            <h1 class="pl-2">{{ mileage }}</h1>
            <h1 class="px-2">{{ vehicle.odometer_units }}</h1>
            <span class="separator"></span>
            <h1 class="px-2">{{ vehicle.technical_data.coinSeries.value }}</h1>
          </div>
          <div class="flex flex-row">
            <h1 class="px-2 normal-case">{{ vehicle.transmission }}</h1>
            <span class="separator"></span>
            <h1 class="px-2">{{ vehicle.body_type }}</h1>
          </div>
        </div>
        <div class="flex flex-col">
          <div class="flex flex-row">
            <div class="flex flex-row pr-5">
              <h1 class="text-black font-bold">£550.90</h1>
              <span>/mo (PCP)</span>
            </div>
          </div>
          <div class="flex">
            <h1 class="text-black">£{{ vehicle.price }}</h1>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
// import json from '@/assets/data.json';
export default {
  props: ["vehicle_media_urls", "vehicle"],

  data() {
    return {
      mileage: Math.floor(this.vehicle.odometer_value / 1000) + "K",
    };
  },
  created() {
  },
};
</script>

<style lang="less">
.vehicle_details_wrapper {
  .normal-case {
    text-transform: lowercase;
    &::first-letter {
      text-transform: uppercase;
    }
  }
  .advert_classification {
    padding: 1px 10px;
    background: #3f3a50;
    border: 1px solid rgba(255, 255, 255, 0.2);
    color: #fff;
    backdrop-filter: blur(10px);
    border-radius: 8px;
  }
  .separator {
    width: 2px;
    height: 20px;
    background: #d1d6e0;
    margin-top: 2px;
  }
}
</style>
