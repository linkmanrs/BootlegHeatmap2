<template>
  <div class="basic-example">
    <l-map :zoom="zoom" :center="center">
      <l-tile-layer :url="url"></l-tile-layer>
      <Vue2LeafletHeatmap
        v-show="haveReports"
        :lat-lng="reportPoints"
        :radius="60"
        :min-opacity="0.75"
        :max-zoom="10"
        :blur="60"
      ></Vue2LeafletHeatmap>
    </l-map>
  </div>
</template>

<script>
import { LMap, LTileLayer } from "vue2-leaflet";
import Vue2LeafletHeatmap from "vue2-leaflet-heatmap";

export default {
  components: {
    LMap,
    LTileLayer,
    Vue2LeafletHeatmap
  },
  data() {
    return {
      url: "https://{s}.tile.osm.org/{z}/{x}/{y}.png",
      zoom: 16,
      center: [40.73061, -73.935242],
      reports: [
        {
          id: 1,
          event_name: "דקירה במקדונלס",
          event_description: null,
          event_id: 2,
          event_type: "דקירה",
          event_time: "2021-06-06T00:00:00.000Z",
          report_time: "2021-06-06T00:00:00.000Z",
          user_name: "גלי גרשטיין",
          lat: 54,
          lon: 23,
          region: null,
          criminal: "משה הדוקר",
          report_id: 1,
          weapon_type: "מברג",
          casualties: "משה כהן, מנחם לוי"
        },
        {
          id: 9,
          event_name: "tytytyty",
          event_description: null,
          event_id: 1,
          event_type: "ירי",
          event_time: "2021-06-23T21:00:00.000Z",
          report_time: "2021-06-29T21:00:00.000Z",
          user_name: "גלי גרשטיין",
          lat: 40.7319983769566,
          lon: -73.9363789546116,
          region: "ברוקלין",
          criminal: "gdfgd",
          report_id: 9,
          weapon_type: "dsfd",
          casualties: "ירי"
        },
        {
          id: 10,
          event_name: "tytytyty",
          event_description: null,
          event_id: 2,
          event_type: "דקירה",
          event_time: "2021-06-27T21:00:00.000Z",
          report_time: "2021-06-28T21:00:00.000Z",
          user_name: "גלי גרשטיין",
          lat: 40.7306818075672,
          lon: -73.9345979677001,
          region: "מנהטן",
          criminal: "ניר",
          report_id: 10,
          weapon_type: "dsfd",
          casualties: "ירי"
        },
        {
          id: 11,
          event_name: "אירוע חטיפה",
          event_description: null,
          event_id: 3,
          event_type: "חטיפה",
          event_time: "2021-06-28T21:00:00.000Z",
          report_time: "2021-06-20T21:00:00.000Z",
          user_name: "גלי גרשטיין",
          lat: 40.7345976559954,
          lon: -73.9292979240418,
          region: "מנהטן",
          criminal: "גכגכגכ",
          report_id: 11,
          kidnapped: "dfdfd",
          last_place_known: "ניו יורק"
        },
        {
          id: 13,
          event_name: "tytytyty",
          event_description: null,
          event_id: 2,
          event_type: "דקירה",
          event_time: "2021-06-20T21:00:00.000Z",
          report_time: "2021-06-17T21:00:00.000Z",
          user_name: "גלי גרשטיין",
          lat: 40.784391851743,
          lon: -74.3080901927126,
          region: "מנהטן",
          criminal: "ניר",
          report_id: 13,
          weapon_type: "dsfd",
          casualties: "ירי"
        },
        {
          id: 14,
          event_name: "tytytyty",
          event_description: null,
          event_id: 3,
          event_type: "חטיפה",
          event_time: "2021-06-20T21:00:00.000Z",
          report_time: "2021-06-15T21:00:00.000Z",
          user_name: "גלי גרשטיין",
          lat: 40.6647953368207,
          lon: -74.2263793715174,
          region: "סטייטן איילנד",
          criminal: "שדג",
          report_id: 14,
          kidnapped: "שדג",
          last_place_known: "ניו יורק"
        }
      ],
      haveReports: false,
      reportServerUrl:
        "http://siton-backend-securityapp3.apps.openforce.openforce.biz/reports"
    };
  },
  computed: {
    reportPoints: function() {
      const points = [];

      this.reports.forEach(report => {
        points.push([report.lat, report.lon, 0.5]);
      });

      return points;
    }
  },
  methods: {
    getReports: function() {}
  }
};
</script>

<style>
.basic-example {
  height: 85vh;
  direction: rtl;
}
</style>
