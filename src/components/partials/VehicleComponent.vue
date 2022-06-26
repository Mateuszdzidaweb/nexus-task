<template>
  <div class="">
    <div class="rounded-xl overflow-hidden shadow-lg relative mt-5">
      <img class="w-auto relative" :src="vehicle_media_urls[0]['medium']" alt="" />
      <div class="vehicle-detail-container absolute top-3 left-3 p-1 px-2 md:block">
        <h1 class="normal-case">{{ vehicle.advert_classification }}</h1>
      </div>
      <div
        class="vehicle-more-details-container absolute md:flex flex-row xl:text-sm text-md"
      >
        <div class="vehicle-detail-container px-2 mr-1">
          <h1>{{ mileage + " " + vehicle.odometer_units }}</h1>
        </div>
        <div class="vehicle-detail-container px-2 mr-1">
          <h1>{{ vehicle.fuel_type }}</h1>
        </div>
        <div class="vehicle-detail-container px-2 mr-1">
          <h1 class="normal-case">{{ vehicle.transmission }}</h1>
        </div>
        <div class="vehicle-detail-container px-2 mr-1">
          <h1>{{ vehicle.body_type }}</h1>
        </div>
      </div>

      <div class="px-6 py-4 md:block">
        <div class="flex flex-row justify-between">
          <div class="car-make text-xl mb-2 text-black">
            {{ vehicle.plate + " " + vehicle.make }}
          </div>
          <img
            v-if="vehicle.advertisable_id == 54651"
            class=""
            src="@/assets/icons/star.svg"
            alt=""
          />
          <img v-else class="" src="@/assets/icons/star-black.svg" alt="" />
        </div>
        <div class="vehicle-model-name flex">
          <p class="">{{ vehicle.derivative }}</p>
        </div>
      </div>
      <div class="px-6 md:flex flex-row">
        <h1 class="font-bold text-xl">£550.90</h1>
        <span class="ml-2">/mo(PCP)</span>
      </div>
      <div class="px-6 md:flex flex-row pb-2">
        <h1 class="car-full-price">£{{ vehicle.original_price }}</h1>
        <h1 class="calculate-btn ml-2">Calculate</h1>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["vehicle_media_urls", "vehicle"],
  data() {
    return {
      mileage: Math.floor(this.vehicle.odometer_value / 1000) + "K",
    };
  },
  mounted() {
    console.log(this.vehicle.odometer_value);
  },
};
</script>

<style lang="less">
.vehicle-more-details-container {
  bottom: 165px;
  left: 10px;
}

.vehicle-detail-container {
  background: #3f3a50;
  color: #fff;
  border: 1px solid rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px);
  border-radius: 12px;
}

.vehicle-model-name {
  color: #55595d;
}

.calculate-btn {
  color: #7572ff;
}

.normal-case {
  text-transform: lowercase;
  &::first-letter {
    text-transform: uppercase;
  }
}
</style>
