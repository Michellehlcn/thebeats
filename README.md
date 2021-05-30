


<script src="https://api.mapbox.com/mapbox-gl-js/v2.1.1/mapbox-gl.js"></script>
<link href="https://api.mapbox.com/mapbox-gl-js/v2.1.1/mapbox-gl.css" rel="stylesheet">

<style>

.map_box_container{
position:relative;
background-color: #ddd;

  top:0px; left:0px; bottom:0px; right:0px; width:100%; height:100%; border:none; margin:0; padding:0; overflow:hidden; z-index:999999;
}

body {
        color: #404040;
        font: 400 15px/22px 'Source Sans Pro', 'Helvetica Neue', Sans-serif;
        margin: 0;
        padding: 0;
        -webkit-font-smoothing: antialiased;
      }

      * {
        -webkit-box-sizing: border-box;
        -moz-box-sizing: border-box;
        box-sizing: border-box;
      }

      .sidebar {
        position: absolute;
        width: 33.3333%;
        height: 100%;
        top: 0;
        left: 0;
        overflow: hidden;
        border-right: hidden;
      }

      .map {
        position: absolute;
        left: 33.3333%;
        width: 66.6666%;
        top: 0;
        bottom: 0;
      }

      h1 {
        font-size: 22px;
        margin: 0;
color:#404040;
        line-height: 20px;
        padding: 20px 2px;
      }

      a {
        color: #404040;
        text-decoration: none;
      }

      a:hover {
        color: #101010;
      }

      .heading {
       
        border-bottom: 1px solid #eee;
        min-height: 60px;
        line-height: 60px;
        padding: 0 10px;
        background-color: #d74216;
        color: #ddd;
      }

      .listings {
        height: 100%;
        overflow: auto;
        padding-bottom: 60px;
      }

      .listings .item {
        display: block;
        border-bottom: 1px solid #eee;
        padding: 10px;
        text-decoration: none;
font-size: 13px;
      }

      .listings .item:last-child {
        border-bottom: none;
      }
      .listings .item .title {
        display: block;
        color:  #d74216;
        font-weight: 700;
font-size: 15px;
      }

      .listings .item .title small {
        font-weight: 400;
      }
      .listings .item.active .title,
      .listings .item .title:hover {
        color: #404040;
      }
      .listings .item.active {
        background-color: #fafafa;
        opacity: 1;
      }
      ::-webkit-scrollbar {
        width: 3px;
        height: 3px;
        border-left: 0;
        background: rgba(0, 0, 0, 0.1);
      }
      ::-webkit-scrollbar-track {
        background: none;
      }
      ::-webkit-scrollbar-thumb {
        background: #00853e;
        border-radius: 0;
      }

      .marker {
        border: none;
        
      height:50px;
      
        width: 50px;
        background-image: url(https://i.ibb.co/wKSQwwJ/rsz-screen-shot-2021-05-20-at-125511-pm.png);
        
      }
      .clearfix {
        display: block;
      }
      .clearfix: after {
        content: '.';
        display: block;
        height: 0;
        clear: both;
        visibility: hidden;
      }

         .mapboxgl-popup {
        padding-bottom: 50px;
      }

      .mapboxgl-popup-close-button {
        display: none;
      }
      .mapboxgl-popup-content {
        font: 400 15px/22px 'Source Sans Pro', 'Helvetica Neue', Sans-serif;
        padding: 0;
        width: 200px
      }
      .mapboxgl-popup-content-wrapper {
        padding: 0%;
      }
      .mapboxgl-popup-content h3 {
       background: #ddd;
        color: #d74216;
        margin: 0; 
       padding: 10px;
    
        border-radius: 8px;
        font-weight: 700;
        margin-top: -15px;
      }

      .mapboxgl-popup-content h4 {
        margin: 0;
        display: block;
        padding: 10px 10px 10px 10px;
        font-weight: 400;
        
      }
      .mapboxgl-popup-content div {
        padding: 10px;
      }
      .mapboxgl-container .leaflet-marker-icon {
        cursor: pointer;
      }
      .mapboxgl-popup-anchor-top > .mapboxgl-popup-content {
        margin-top: 15px;
      }
      .mapboxgl-popup-anchor-top > .mapboxgl-popup-tip {
        border-bottom-color: #ddd;
      }
    </style>
 <section class="map_box_container">

<div class="sidebar">
      <div class="heading">
        <h1>Park Locations</h1>
      </div>
      <div id="listings" class="listings"></div>
    </div>
    <div id="map" class="map"></div>
</section>

<script>
 if (!('remove' in Element.prototype)) {
  Element.prototype.remove = function() {
    if (this.parentNode) {
      this.parentNode.removeChild(this);
    }
  };
}

mapboxgl.accessToken = 'pk.eyJ1IjoibWljaGVsbGVobGNuIiwiYSI6ImNrb2tuczRsNjA1c3AycHJ6M25oZ3dwOTkifQ.PwztYmGkX406GWClPKsOyg';

var map = new mapboxgl.Map({
  container: 'map',
  style: 'mapbox://styles/mapbox/streets-v11',
  center: [146.231820338829,-26.404762976254],
  zoom: 13,

});

var places = {
  'type': 'FeatureCollection',
  'features': [{
      'type': 'Feature',
      'geometry': {
        'type': 'Point',
        'coordinates': [146.231820338829,-26.404762976254]
      },
      'properties': {
        'image':'<a href="https://ibb.co/TMb4Mvx"><img src="https://i.ibb.co/5hnrhMg/Majella-Steedman.jpg" alt="Majella-Steedman" border="0" width="180px" height="320px" border-radius="8px"></a>',
        
        'park': 'Majella Steedman',
        'description': 'The Park is located at 8 Adrian Street, Charleville, QLD 4470. Type: Kangaroos, Wallabies, Possums. Budget is up to $100 per month.</p>Sourced from <a href="http://www.theBeats.org" target="_blank" title="Opens in a new window"><u>TheBeats<u></a>'
        
      }
    },

    {
      'type': 'Feature',
      'geometry': {
        'type': 'Point',
        'coordinates': [147.190777654084,-33.0684040149608]
      },
      'properties': { 
      'image':'<a href="https://ibb.co/p3xJMzZ"><img src="https://i.ibb.co/JzK5G72/John-Tafe.jpg" alt="John-Tafe" width="180px" height="320px" border-radius="8px"></a>',
        'park': 'John Tafe',
        'description': 'The Park is located at 23 Airport Road, Condobolin, NSW 2877. Type: Birds. Budget is up 100-200 per month.</p>Sourced from <a href="http://www.theBeats.org" target="_blank" title="Opens in a new window"><u>TheBeats<u></a>'       
      }
    },    
    {
      'type': 'Feature',
      'geometry': {
        'type': 'Point',
        'coordinates': [144.102222265137,-37.623351118331]
      },
      'properties': {
      'image':'<a href="https://ibb.co/D1csNYM"><img src="https://i.ibb.co/rQ8Tg3p/Joan-Marsh.jpg" alt="Joan-Marsh" border="0" width="180px" height="320px" border-radius="8px"></a>',
        'park': 'Joan Marsh',
        'description': 'The Park is located at 20 Steetley Lane,Mount Egerton, VIC 3352. Type: Ferns. Budget is up to $100 per month.</p>Sourced from <a href="http://www.theBeats.org" target="_blank" title="Opens in a new window"><u>TheBeats<u></a>'
        
      }
    }
  ]
};
places.features.forEach(function(place, i) {
  place.properties.id = i;
});

map.on('load', function(e) {
  map.addSource('places', {
    'type': 'geojson',
    'data': places
  });

  buildLocationList(places);
  addMarkers();
});

function addMarkers() {
places.features.forEach(function (marker) {
    var el = document.createElement('div');
    el.id = 'marker-' + marker.properties.id;
    el.className = 'marker';

    new mapboxgl.Marker(el, {
        offset: [0, -23]
      })
      .setLngLat(marker.geometry.coordinates)
      .addTo(map);
      
 el.addEventListener('click', function(e){
      flyToPlace(marker);
      createPopUp(marker);
      var activeItem = document.getElementsByClassName('active');
      e.stopPropagation();
      if (activeItem[0]) {
        activeItem[0].classList.remove('active');
      }
      var listing = document.getElementById(
        'listing-' + marker.properties.id
      );
      listing.classList.add('active');
    });
  });
}
function buildLocationList(data) {
  data.features.forEach(function(place, i) {
      var prop = place.properties;
      var listings = document.getElementById('listings');
var listing = listings.appendChild(document.createElement('div'));
      listing.id = 'listing-' + prop.id;
      listing.className = 'item';
      var link = listing.appendChild(document.createElement('a'));
      link.href = '#';
      link.className = 'title';
      link.id = 'link-' + prop.id;
      link.innerHTML = prop.park;
      var details = listing.appendChild(document.createElement('div'));
      details.innerHTML = prop.description
      if (prop.phone) {
details.innerHTML += ' &middot; ' + prop.phoneFormatted;

    }
    link.addEventListener('click', function(e) {
      for (var i = 0; i < data.features.length; i++) {
        if (this.id === 'link-' + data.features[i].properties.id) {
          var clickedListing = data.features[i];
          flyToPlace(clickedListing);
          createPopUp(clickedListing);
        }
      }
      var activeItem = document.getElementsByClassName('active');
      if (activeItem[0]) {
        activeItem[0].classList.remove('active');
      }
      this.parentNode.classList.add('active');
    });
  });
}
function flyToPlace(currentFeature) {
  map.flyTo({
    center: currentFeature.geometry.coordinates,
    zoom: 15
  });
}
function createPopUp(currentFeature) {
  var popUps = document.getElementsByClassName('mapboxgl-popup');
  if (popUps[0]) popUps[0].remove();
  var popup = new mapboxgl.Popup({
      closeOnClick: true
    })
    .setLngLat(currentFeature.geometry.coordinates)
    .setHTML(
      '<h3> <center>' + currentFeature.properties.image + '</center></h3>'
     
 
    )
    .addTo(map);
}



</script>
