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
'{% if member.slack_account %}<p class="icon">{% if member.slack_account_url %} <a href="{{ member.slack_account_url }}">{% endif %}<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" height="2em"><path fill="currentColor" d="M446.2 270.4c-6.2-19-26.9-29.1-46-22.9l-45.4 15.1-30.3-90 45.4-15.1c19.1-6.2 29.1-26.8 23-45.9-6.2-19-26.9-29.1-46-22.9l-45.4 15.1-15.7-47c-6.2-19-26.9-29.1-46-22.9-19.1 6.2-29.1 26.8-23 45.9l15.7 47-93.4 31.2-15.7-47c-6.2-19-26.9-29.1-46-22.9-19.1 6.2-29.1 26.8-23 45.9l15.7 47-45.3 15c-19.1 6.2-29.1 26.8-23 45.9 5 14.5 19.1 24 33.6 24.6 6.8 1 12-1.6 57.7-16.8l30.3 90L78 354.8c-19 6.2-29.1 26.9-23 45.9 5 14.5 19.1 24 33.6 24.6 6.8 1 12-1.6 57.7-16.8l15.7 47c5.9 16.9 24.7 29 46 22.9 19.1-6.2 29.1-26.8 23-45.9l-15.7-47 93.6-31.3 15.7 47c5.9 16.9 24.7 29 46 22.9 19.1-6.2 29.1-26.8 23-45.9l-15.7-47 45.4-15.1c19-6 29.1-26.7 22.9-45.7zm-254.1 47.2l-30.3-90.2 93.5-31.3 30.3 90.2-93.5 31.3z" /></svg> <strong>{{ member.slack_account }}</strong> {% if member.slack_account_url %} </a>{% endif %} </p>{% endif %}' +
'{% if member.fediverse_account %}<p class="icon"><a href="{{ member.fediverse_account }}"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" height="2em"><path fill="currentColor" d="M433 179.11c0-97.2-63.71-125.7-63.71-125.7-62.52-28.7-228.56-28.4-290.48 0 0 0-63.72 28.5-63.72 125.7 0 115.7-6.6 259.4 105.63 289.1 40.51 10.7 75.32 13 103.33 11.4 50.81-2.8 79.32-18.1 79.32-18.1l-1.7-36.9s-36.31 11.4-77.12 10.1c-40.41-1.4-83-4.4-89.63-54a102.54 102.54 0 0 1-.9-13.9c85.63 20.9 158.65 9.1 178.75 6.7 56.12-6.7 105-41.3 111.23-72.9 9.8-49.8 9-121.5 9-121.5zm-75.12 125.2h-46.63v-114.2c0-49.7-64-51.6-64 6.9v62.5h-46.33V197c0-58.5-64-56.6-64-6.9v114.2H90.19c0-122.1-5.2-147.9 18.41-175 25.9-28.9 79.82-30.8 103.83 6.1l11.6 19.5 11.6-19.5c24.11-37.1 78.12-34.8 103.83-6.1 23.71 27.3 18.4 53 18.4 175z" /></svg> {{ member.fediverse_account }}</a></p>{% endif %}' +
'{% if member.stack_overflow_account %}<p class="icon"><a href="{{ member.stack_overflow_account }}"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" height="2em"><path fill="currentColor" d="M290.7 311L95 269.7 86.8 309l195.7 41zm51-87L188.2 95.7l-25.5 30.8 153.5 128.3zm-31.2 39.7L129.2 179l-16.7 36.5L293.7 300zM262 32l-32 24 119.3 160.3 32-24zm20.5 328h-200v39.7h200zm39.7 80H42.7V320h-40v160h359.5V320h-40z" /></svg> Stackoverflow</a></p>{% endif %}' +
'{% if member.linkedin_account %}<p class="icon"><a href="https://www.linkedin.com/in/{{ member.linkedin_account }}/"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" height="2em"><path fill="currentColor" d="M416 32H31.9C14.3 32 0 46.5 0 64.3v383.4C0 465.5 14.3 480 31.9 480H416c17.6 0 32-14.5 32-32.3V64.3c0-17.8-14.4-32.3-32-32.3zM135.4 416H69V202.2h66.5V416zm-33.2-243c-21.3 0-38.5-17.3-38.5-38.5S80.9 96 102.2 96c21.2 0 38.5 17.3 38.5 38.5 0 21.3-17.2 38.5-38.5 38.5zm282.1 243h-66.4V312c0-24.8-.5-56.7-34.5-56.7-34.6 0-39.9 27-39.9 54.9V416h-66.4V202.2h63.7v29.2h.9c8.9-16.8 30.6-34.5 62.9-34.5 67.2 0 79.7 44.3 79.7 101.9V416z" /></svg> {{ member.linkedin_account }}</a></p>{% endif %}' +
'{% if member.contact_url %}<p class="icon"><a href="{{ member.contact_url}}"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" height="2em"><path fill="currentColor" d="M436 160c6.6 0 12-5.4 12-12v-40c0-6.6-5.4-12-12-12h-20V48c0-26.5-21.5-48-48-48H48C21.5 0 0 21.5 0 48v416c0 26.5 21.5 48 48 48h320c26.5 0 48-21.5 48-48v-48h20c6.6 0 12-5.4 12-12v-40c0-6.6-5.4-12-12-12h-20v-64h20c6.6 0 12-5.4 12-12v-40c0-6.6-5.4-12-12-12h-20v-64h20zm-68 304H48V48h320v416zM208 256c35.3 0 64-28.7 64-64s-28.7-64-64-64-64 28.7-64 64 28.7 64 64 64zm-89.6 128h179.2c12.4 0 22.4-8.6 22.4-19.2v-19.2c0-31.8-30.1-57.6-67.2-57.6-10.8 0-18.7 8-44.8 8-26.9 0-33.4-8-44.8-8-37.1 0-67.2 25.8-67.2 57.6v19.2c0 10.6 10 19.2 22.4 19.2z" /></svg> Contact</a></p>{% endif %}' +
'{% if member.github_account %}<p class="icon"><a href="https://github.com/{{ member.github_account}}"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" height="2em"><path fill="currentColor" d="M186.1 328.7c0 20.9-10.9 55.1-36.7 55.1s-36.7-34.2-36.7-55.1 10.9-55.1 36.7-55.1 36.7 34.2 36.7 55.1zM480 278.2c0 31.9-3.2 65.7-17.5 95-37.9 76.6-142.1 74.8-216.7 74.8-75.8 0-186.2 2.7-225.6-74.8-14.6-29-20.2-63.1-20.2-95 0-41.9 13.9-81.5 41.5-113.6-5.2-15.8-7.7-32.4-7.7-48.8 0-21.5 4.9-32.3 14.6-51.8 45.3 0 74.3 9 108.8 36 29-6.9 58.8-10 88.7-10 27 0 54.2 2.9 80.4 9.2 34-26.7 63-35.2 107.8-35.2 9.8 19.5 14.6 30.3 14.6 51.8 0 16.4-2.6 32.7-7.7 48.2 27.5 32.4 39 72.3 39 114.2zm-64.3 50.5c0-43.9-26.7-82.6-73.5-82.6-18.9 0-37 3.4-56 6-14.9 2.3-29.8 3.2-45.1 3.2-15.2 0-30.1-.9-45.1-3.2-18.7-2.6-37-6-56-6-46.8 0-73.5 38.7-73.5 82.6 0 87.8 80.4 101.3 150.4 101.3h48.2c70.3 0 150.6-13.4 150.6-101.3zm-82.6-55.1c-25.8 0-36.7 34.2-36.7 55.1s10.9 55.1 36.7 55.1 36.7-34.2 36.7-55.1-10.9-55.1-36.7-55.1z"></path></svg> Github </a></p>{% endif %}' +
'{% if member.gitlab_account %}<p class="icon"><a href="https://gitlab.com/{{ member.gitlab_account}}"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" height="2em"><path fill="currentColor" d="M105.2 24.9c-3.1-8.9-15.7-8.9-18.9 0L29.8 199.7h132c-.1 0-56.6-174.8-56.6-174.8zM.9 287.7c-2.6 8 .3 16.9 7.1 22l247.9 184-226.2-294zm160.8-88l94.3 294 94.3-294zm349.4 88l-28.8-88-226.3 294 247.9-184c6.9-5.1 9.7-14 7.2-22zM425.7 24.9c-3.1-8.9-15.7-8.9-18.9 0l-56.6 174.8h132z"></path></svg> Gitlab </a></p>{% endif %}' + 
'{% if member.twitter_account %}<p class="icon"><a href="https://twitter.com/{{ member.twitter_account}}"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" height="2em"><path fill="currentColor" d="M459.37 151.716c.325 4.548.325 9.097.325 13.645 0 138.72-105.583 298.558-298.558 298.558-59.452 0-114.68-17.219-161.137-47.106 8.447.974 16.568 1.299 25.34 1.299 49.055 0 94.213-16.568 130.274-44.832-46.132-.975-84.792-31.188-98.112-72.772 6.498.974 12.995 1.624 19.818 1.624 9.421 0 18.843-1.3 27.614-3.573-48.081-9.747-84.143-51.98-84.143-102.985v-1.299c13.969 7.797 30.214 12.67 47.431 13.319-28.264-18.843-46.781-51.005-46.781-87.391 0-19.492 5.197-37.36 14.294-52.954 51.655 63.675 129.3 105.258 216.365 109.807-1.624-7.797-2.599-15.918-2.599-24.04 0-57.828 46.782-104.934 104.934-104.934 30.213 0 57.502 12.67 76.67 33.137 23.715-4.548 46.456-13.32 66.599-25.34-7.798 24.366-24.366 44.833-46.132 57.827 21.117-2.273 41.584-8.122 60.426-16.243-14.292 20.791-32.161 39.308-52.628 54.253z"></path></svg> Twitter </a></p>{% endif %}'
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
