# il_koordinatlari_json
Türkiye'nin il koordinatları TXT ve JSON formatında

https://www.google.com/maps kullanılarak Türkiye'nin il merkez koordinatları elde edildi. TXT ve JSON formatında dilediğiniz gibi kullanabilirsiniz.

<!DOCTYPE html>
<html>
<body>
	<h1>Leafletjs ile örnek marker uygulaması</h1>
	<p>Leafletjs ile ilgili detaylı bilgilerndirme ve örnekler için <a href="https://leafletjs.com/examples.html" target="_blank" title="Leaflet örnekler">https://leafletjs.com/examples.html</a> sayfasını ziyaret edebilirsiniz.</p>
	
	<div id="leaflet_map" style="width: 100%;height: 500px"></div>

	<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY=" crossorigin=""/>
	<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js" integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo=" crossorigin=""></script>

	<script>
	var iller = [
					{
						"id": "7",
						"il": "Antalya",
						"lan": "36.998017537401594",
						"lon": "30.561566775387313"
					},
					{
						"id": "31",
						"il": "Hatay",
						"lan": "36.20451807529464",
						"lon": "36.16013079163698"
					}
				]
					
		const map = L.map('leaflet_map').setView([39.136818, 35.087120], 6);

		const tiles = L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
			maxZoom: 18,
			attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
		}).addTo(map);
		
		Object.entries(iller).forEach(([key, val]) => {
			L.marker([val.lan,val.lon]).addTo(map).bindPopup(val.il,{autoClose: false, closeOnClick: false});
		})
	</script>

</body>
</html>
