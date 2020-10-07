---
layout: default
---

<script language="javascript">
    var member_markers = [];

    var member_probe_icon = L.icon({
        iconSize:      [25, 41],
        iconAnchor:    [12, 41],
        popupAnchor:   [1, -34],
        tooltipAnchor: [16, -28],
        shadowSize:    [41, 41],
        iconUrl:       'marker-active.png',
        shadowUrl:     'marker-shadow.png',
    });

    {% for member in site.members %}
    member_markers.push(L.marker([{{ member.lat }}, {{ member.lng }}], { icon: member_probe_icon }).bindPopup('<h1>{% if member.photo %}<img src="{{ member.photo }}" alt="photo" class="photo" width="64" height="64" />{% endif %}{{ member.title }}</h1>{{ member.content | markdownify | normalize_whitespace }}' +
'{% if member.slack_account %}<p class="icon"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" height="2em"><path fill="currentColor" d="M446.2 270.4c-6.2-19-26.9-29.1-46-22.9l-45.4 15.1-30.3-90 45.4-15.1c19.1-6.2 29.1-26.8 23-45.9-6.2-19-26.9-29.1-46-22.9l-45.4 15.1-15.7-47c-6.2-19-26.9-29.1-46-22.9-19.1 6.2-29.1 26.8-23 45.9l15.7 47-93.4 31.2-15.7-47c-6.2-19-26.9-29.1-46-22.9-19.1 6.2-29.1 26.8-23 45.9l15.7 47-45.3 15c-19.1 6.2-29.1 26.8-23 45.9 5 14.5 19.1 24 33.6 24.6 6.8 1 12-1.6 57.7-16.8l30.3 90L78 354.8c-19 6.2-29.1 26.9-23 45.9 5 14.5 19.1 24 33.6 24.6 6.8 1 12-1.6 57.7-16.8l15.7 47c5.9 16.9 24.7 29 46 22.9 19.1-6.2 29.1-26.8 23-45.9l-15.7-47 93.6-31.3 15.7 47c5.9 16.9 24.7 29 46 22.9 19.1-6.2 29.1-26.8 23-45.9l-15.7-47 45.4-15.1c19-6 29.1-26.7 22.9-45.7zm-254.1 47.2l-30.3-90.2 93.5-31.3 30.3 90.2-93.5 31.3z" /></svg> <strong>{{ member.slack_account }}</strong></p>{% endif %}' +
'{% if member.fediverse_account %}<p class="icon"><a href="{{ member.fediverse_account }}"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" height="2em"><path fill="currentColor" d="M433 179.11c0-97.2-63.71-125.7-63.71-125.7-62.52-28.7-228.56-28.4-290.48 0 0 0-63.72 28.5-63.72 125.7 0 115.7-6.6 259.4 105.63 289.1 40.51 10.7 75.32 13 103.33 11.4 50.81-2.8 79.32-18.1 79.32-18.1l-1.7-36.9s-36.31 11.4-77.12 10.1c-40.41-1.4-83-4.4-89.63-54a102.54 102.54 0 0 1-.9-13.9c85.63 20.9 158.65 9.1 178.75 6.7 56.12-6.7 105-41.3 111.23-72.9 9.8-49.8 9-121.5 9-121.5zm-75.12 125.2h-46.63v-114.2c0-49.7-64-51.6-64 6.9v62.5h-46.33V197c0-58.5-64-56.6-64-6.9v114.2H90.19c0-122.1-5.2-147.9 18.41-175 25.9-28.9 79.82-30.8 103.83 6.1l11.6 19.5 11.6-19.5c24.11-37.1 78.12-34.8 103.83-6.1 23.71 27.3 18.4 53 18.4 175z" /></svg> {{ member.fediverse_account }}</a></p>{% endif %}' +
'{% if member.contact_url %}<p class="icon"><a href="{{ member.contact_url}}"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" height="2em"><path fill="currentColor" d="M436 160c6.6 0 12-5.4 12-12v-40c0-6.6-5.4-12-12-12h-20V48c0-26.5-21.5-48-48-48H48C21.5 0 0 21.5 0 48v416c0 26.5 21.5 48 48 48h320c26.5 0 48-21.5 48-48v-48h20c6.6 0 12-5.4 12-12v-40c0-6.6-5.4-12-12-12h-20v-64h20c6.6 0 12-5.4 12-12v-40c0-6.6-5.4-12-12-12h-20v-64h20zm-68 304H48V48h320v416zM208 256c35.3 0 64-28.7 64-64s-28.7-64-64-64-64 28.7-64 64 28.7 64 64 64zm-89.6 128h179.2c12.4 0 22.4-8.6 22.4-19.2v-19.2c0-31.8-30.1-57.6-67.2-57.6-10.8 0-18.7 8-44.8 8-26.9 0-33.4-8-44.8-8-37.1 0-67.2 25.8-67.2 57.6v19.2c0 10.6 10 19.2 22.4 19.2z" /></svg> contact</a></p>{% endif %}'
));
    {% endfor %}

    var common_attribution_pre = 'Données cartographiques : <a href="https://www.openstreetmap.fr/">OpenStreetMap France</a> | Tuiles : ';
    var common_attribution_post = ' | Icônes : <a href="https://fontawesome.com/">Font Awesome</a> | <a href="{{ "/about" | relative_url }}">À propos de ce site</a>';

    var neighbourhood_map_layer = L.tileLayer('https://tile.thunderforest.com/neighbourhood/{z}/{x}/{y}.png?apikey=f001bec5e17447b0b597e5a8e766bbf2', {attribution: common_attribution_pre + '<a href="https://www.thunderforest.com/maps/neighbourhood/">Neighbourhood</a>' + common_attribution_post});

    var markers_layer = L.markerClusterGroup();

    var active_probes_layer   = L.featureGroup.subGroup(markers_layer, member_markers);

    markers_layer.addLayer(active_probes_layer);

    var map = L.map('map', {layers: [neighbourhood_map_layer, markers_layer, active_probes_layer]});

    L.control.scale({maxWidth: 300}).addTo(map);

    map.fitBounds(L.latLngBounds(member_markers.map(e => e.getLatLng())));
</script>
