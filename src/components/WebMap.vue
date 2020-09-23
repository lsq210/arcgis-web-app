<template>
  <div></div>
</template>

<script>
import { loadModules } from "esri-loader";

export default {
  name: "web-map",
  mounted() {
    // lazy load the required ArcGIS API for JavaScript modules and CSS
    loadModules([
      "esri/Map",
      "esri/views/MapView",
      "esri/layers/FeatureLayer",
      "esri/widgets/CoordinateConversion",
      // "esri/widgets/Directions",
      // "esri/widgets/Bookmarks",
      // "esri/widgets/Expand"
      ], { css: true }).then(([
        ArcGISMap,
        MapView,
        FeatureLayer,
        CoordinateConversion,
        // Directions,
        // Bookmarks,
        // Expand
        ]) => {
        var map = new ArcGISMap({
          basemap: "topo-vector",
        });
        // var layer0 = new FeatureLayer({
        //   url:
        //     "https://services6.arcgis.com/iIGNxHY29Qqg0LRI/arcgis/rest/services/20140501_0h/FeatureServer",
        // });
        var layer0 = new FeatureLayer({
          url:
          "https://services6.arcgis.com/iIGNxHY29Qqg0LRI/arcgis/rest/services/10min/FeatureServer"
        });
        map.add(layer0, 0);
        this.view = new MapView({
          container: this.$el,
          map: map,
          center: [114.28518, 30.55068],
          zoom: 13,
        });
        var ccWidget = new CoordinateConversion({
          view: this.view
        });
        // var directionsWidget = new Directions({
        //   view: this.view,
        //   // Point the URL to a valid route service that uses an
        //   // ArcGIS Online hosted service proxy instead of the default service
        //   routeServiceUrl:
        //     "https://utility.arcgis.com/usrsvcs/appservices/uz57EVPszZxo5yzm/rest/services/World/Route/NAServer/Route_World"
        // });
        // const bookmarks = new Bookmarks({
        //   view: this.view,
        //   // allows bookmarks to be added, edited, or deleted
        //   editingEnabled: true
        // });

        // const bkExpand = new Expand({
        //   view: this.view,
        //   content: bookmarks,
        //   expanded: true
        // });
        this.view.ui.add(ccWidget, "bottom-left");
        // this.view.ui.add(directionsWidget, {
        //   position: "top-right"
        // });
        // this.view.ui.add(bkExpand, "top-right");
      }
    );
    
  },
  beforeUnmount() {
    if (this.view) {
      // destroy the map view
      this.view.container = null;
    }
  },
};
</script>

<style scoped>
div {
  padding: 0;
  margin-top: 0;
  width: 100%;
  height: 100%;
}
</style>