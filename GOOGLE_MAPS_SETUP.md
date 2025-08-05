# Configuración de Google Maps API

## Pasos para configurar Google Maps en el sitio web

### 1. Obtener una API Key de Google Maps

1. Ve a la [Google Cloud Console](https://console.cloud.google.com/)
2. Crea un nuevo proyecto o selecciona uno existente
3. Habilita la **Maps JavaScript API**
4. Ve a "Credenciales" y crea una nueva API Key
5. Restringe la API Key a tu dominio por seguridad

### 2. Configurar la API Key en el código

En el archivo `src/components/Contacto.astro`, busca esta línea:

```javascript
script.src = `https://maps.googleapis.com/maps/api/js?key=YOUR_GOOGLE_MAPS_API_KEY&callback=initMap`;
```

Reemplaza `YOUR_GOOGLE_MAPS_API_KEY` con tu API Key real:

```javascript
script.src = `https://maps.googleapis.com/maps/api/js?key=TU_API_KEY_AQUI&callback=initMap`;
```

### 3. Configurar las coordenadas de tu ubicación

En el mismo archivo, busca esta línea:

```javascript
const location = { lat: 40.7128, lng: -74.0060 }; // New York coordinates as example
```

Reemplaza las coordenadas con las de tu ubicación real:

```javascript
const location = { lat: TU_LATITUD, lng: TU_LONGITUD };
```

### 4. Personalizar el marcador del mapa

Puedes personalizar el marcador modificando el SVG en la función `initMap()`:

```javascript
icon: {
  url: "data:image/svg+xml;charset=UTF-8," + encodeURIComponent(`
    <svg width="40" height="40" viewBox="0 0 40 40" xmlns="http://www.w3.org/2000/svg">
      <circle cx="20" cy="20" r="18" fill="#3b82f6" stroke="white" stroke-width="2"/>
      <path d="M20 8l-8 12h6v8l8-12h-6v-8z" fill="white"/>
    </svg>
  `),
  scaledSize: new google.maps.Size(40, 40)
}
```

### 5. Personalizar la ventana de información

Modifica el contenido de la ventana de información:

```javascript
const infoWindow = new google.maps.InfoWindow({
  content: `
    <div style="padding: 10px; max-width: 200px;">
      <h3 style="margin: 0 0 5px 0; color: #1e3a8a;">Waywen Climatización</h3>
      <p style="margin: 0; color: #64748b;">Aire Acondicionado</p>
      <p style="margin: 5px 0 0 0; color: #64748b;">TU_DIRECCION_AQUI</p>
    </div>
  `
});
```

## Notas importantes

- **Seguridad**: Siempre restringe tu API Key a tu dominio específico
- **Costo**: Google Maps tiene un límite gratuito generoso, pero revisa los precios
- **Alternativas**: Si no quieres usar Google Maps, puedes usar OpenStreetMap con Leaflet
- **Fallback**: El mapa muestra un placeholder si no se puede cargar la API

## Alternativa: Usar OpenStreetMap (Gratuito)

Si prefieres no usar Google Maps, puedes reemplazar el código con OpenStreetMap:

```html
<!-- Agregar en el head -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
```

Y modificar el JavaScript para usar Leaflet en lugar de Google Maps.

## Soporte

Para más información sobre Google Maps API, visita:
- [Google Maps JavaScript API Documentation](https://developers.google.com/maps/documentation/javascript)
- [Google Cloud Console](https://console.cloud.google.com/) 