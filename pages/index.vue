<template>
  <v-layout column justify-center align-center>    
    <div class="headline">Indonesia COVID-19 Realtime Data</div>
    <div class="">Data fetched from official kawalcovid.id API</div>
    <v-row>
      <v-col cols="12" md="6">
        <v-card>
          <v-card-title class="headline">
            Confirmed
          </v-card-title>
          <v-card-text class="m-2 amount-text red">
            {{apiData.confirmed}}
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="12" md="6">
        <v-card>
          <v-card-title class="headline">
            Recovered
          </v-card-title>
          <v-card-text class="m-2 amount-text green">
            {{apiData.recovered}}
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="12" md="6">
        <v-card>
          <v-card-title class="headline">
            Deceased
          </v-card-title>
          <v-card-text class="m-2 amount-text black">
            {{apiData.deceased}}
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="12" md="6">
        <v-card>
          <v-card-title class="headline">
            On treatment
          </v-card-title>
          <v-card-text class="m-2 amount-text blue">
            {{apiData.activeCare}}
          </v-card-text>
        </v-card>
        
      </v-col>
    </v-row>
  </v-layout>
</template>

<script>
import Logo from "~/components/Logo.vue";
import VuetifyLogo from "~/components/VuetifyLogo.vue";

export default {
  async asyncData({ req, $axios, redirect }) {
    const data = await $axios.$get(
      `https://api.kawalcovid19.id/case/summary`
    );

    return {apiData: data}
  },
  components: {
    Logo,
  }
};
</script>
<style lang="scss" scoped>
.amount-text{
  font-family: 'Anton', sans-serif;
  font-size: 48px;
}
</style>