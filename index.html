<!DOCTYPE html>
<html lang="sv">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <title>GPS Prototyp</title>

    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
     integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY="
     crossorigin=""/>

    <style>
        /* Gör så att kartan fyller hela skärmen */
        body, html { 
            height: 100%; 
            margin: 0; 
            padding: 0; 
        }
        #map { 
            height: 100%; 
            width: 100%; 
        }

        /* --- CSS FÖR DEN PULSERANDE GULA PUNKTEN --- */
        
        /* Själva kärnan av punkten */
        .yellow-dot-marker {
            background-color: #ffeb3b; /* Stark gul färg */
            border-radius: 50%;
            border: 2px solid #fff; /* Vit kant för kontrast mot kartan */
            box-shadow: 0 0 5px rgba(0,0,0,0.3);
            position: relative;
        }

        /* Ringen som pulserar utåt */
        .yellow-dot-marker::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 100%; /* Startar samma storlek som punkten */
            height: 100%;
            border-radius: 50%;
            /* En halvgenomskinlig gul ring */
            border: 3px solid rgba(255, 235, 59, 0.7); 
            /* Starta animationen */
            animation: pulse-ring 2s cubic-bezier(0.455, 0.03, 0.515, 0.955) infinite;
            opacity: 0; /* Börja osynlig */
        }

        /* Definiera animationen */
        @keyframes pulse-ring {
            0% {
                width: 100%;
                height: 100%;
                opacity: 0.8;
            }
            100% {
                width: 300%; /* Väx till 3 gånger storleken */
                height: 300%;
                opacity: 0; /* Tona ut helt */
            }
        }

        /* Statusruta för debugging (valfritt) */
        #status-box {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(255,255,255,0.9);
            padding: 10px 15px;
            border-radius: 20px;
            z-index: 1000; /* Lägg ovanpå kartan */
            font-family: sans-serif;
            font-size: 14px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
        }

    </style>
</head>
<body>

    <div id="map"></div>
    
    <div id="status-box">Väntar på GPS-signal...</div>


    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"
     integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo="
     crossorigin=""></script>

    <script>
        // --- 1. Initiera Kartan ---
        // Starta med en utzoomad vy över Sverige tills vi har en position
        const map = L.map('map').setView([62.0, 15.0], 5);

        // Lägg till kartlager från OpenStreetMap (gratis)
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
            maxZoom: 19
        }).addTo(map);

        // Variabel för att hålla koll på markören
        let userMarker = null;
        const statusBox = document.getElementById('status-box');
        let firstFix = true;

        // --- 2. Skapa den anpassade pulserande ikonen ---
        // Vi använder L.divIcon för att kunna använda vår egen CSS
        const pulsingIcon = L.divIcon({
            className: 'yellow-dot-marker', // Vår CSS-klass
            iconSize: [20, 20], // Storleken på själva den fasta punkten (px)
            iconAnchor: [10, 10] // Punkten som pekar på den exakta koordinaten (mitten)
        });


        // --- 3. Geolocation Logik (Hög Precision) ---
        const geoOptions = {
            enableHighAccuracy: true, // KRITISKT för Android GPS
            timeout: 15000,           // Vänta lite längre på första fixen
            maximumAge: 0             // Ingen cachad data
        };

        function success(pos) {
            const lat = pos.coords.latitude;
            const lng = pos.coords.longitude;
            const accuracy = pos.coords.accuracy; // Noggrannhet i meter

            // Uppdatera statusrutan
            statusBox.innerHTML = `Noggrannhet: +/- ${Math.round(accuracy)}m`;

            // Om markören inte finns än, skapa den
            if (!userMarker) {
                userMarker = L.marker([lat, lng], {icon: pulsingIcon}).addTo(map);
            } else {
                // Om den finns, flytta den smidigt till nya positionen
                userMarker.setLatLng([lat, lng]);
            }

            // Om det är första gången vi får en position, zooma in till användaren
            if (firstFix) {
                // Zooma in nära (nivå 17) så man ser rörelsen
                map.setView([lat, lng], 17, { animate: true });
                firstFix = false;
            }
        }

        function error(err) {
            let msg = "Kunde inte hitta position.";
            if (err.code === 1) msg = "Åtkomst nekad. Du måste tillåta platsdata.";
            if (err.code === 2) msg = "Position ej tillgänglig (slå på GPS).";
            if (err.code === 3) msg = "Timeout - fick ingen signal.";
            
            console.warn(`ERROR(${err.code}): ${err.message}`);
            statusBox.innerHTML = `<span style="color:red;">Fel: ${msg}</span>`;
        }

        // Starta övervakningen av positionen
        if ('geolocation' in navigator) {
            // Använd watchPosition för kontinuerliga uppdateringar när man rör sig
            navigator.geolocation.watchPosition(success, error, geoOptions);
        } else {
            statusBox.innerHTML = "Geolocation stöds inte av din webbläsare.";
        }

    </script>
</body>
</html>
