/<template>
  <div id="map">

  </div>
</template>

<script>
import { Geolocation } from '@capacitor/geolocation';
//Mapa inicio
var map = L.map('map').setView([0,0], 12);
/* map.zoomControl.setPosition('topright'); */

//Estilo Mapa y Zoom Max
var osm = L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
	attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a>'
});
osm.addTo(map);
// GPS
if(!navigator.geolocation){
    alert("Navegador no soporta geolocalización")   
}else{
    setInterval(() => {
        navigator.geolocation.getCurrentPosition(function(position){
            lat = position.coords.latitude
            long = position.coords.longitude
            coords.push([lat, long])
            console.log(coords)
            marker = L.marker([lat, long])
            var featureGroup = L.featureGroup([marker]).addTo(map)
            map.fitBounds(featureGroup.getBounds())
            marker.bindPopup("<h1>Ubicación actual</h1>"+ "Latitud: "+ lat + " Longitud: " + long).openPopup();
        }, function(error){
            alert("Error")
        },
        {
            enableHighAccuracy: true
        })
    }, 30000);   
};
</script>

<style>

</style>