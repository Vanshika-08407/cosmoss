# 🗺️ OpenStreetMap Guide for Kutumbh

## Why OpenStreetMap?

**OpenStreetMap (OSM) is 100% FREE and requires NO API KEY!**

### Advantages:

- ✅ **Zero Cost**: Completely free forever
- ✅ **No API Key**: No registration or configuration needed
- ✅ **No Billing**: No credit card required
- ✅ **Unlimited Requests**: No rate limits or quotas
- ✅ **Open Source**: Community-driven, transparent data
- ✅ **Privacy-Friendly**: No tracking or data collection
- ✅ **Multiple Styles**: Choose from various map designs
- ✅ **Offline Support**: Can cache tiles for offline use
- ✅ **High Quality**: Excellent worldwide coverage

---

## Already Configured!

**Good news**: OpenStreetMap is already set up in Kutumbh!

No configuration needed. Just run:

```bash
npm install
npm run dev
```

---

## How It Works

### Technology Stack:

- **Leaflet.js**: Open-source JavaScript mapping library
- **React Leaflet**: React components for Leaflet
- **OpenStreetMap Tiles**: Free map tile service

### File Structure:

```
kutumbh-app/
├── src/config/
│   └── openStreetMap.js     ← Map configuration
├── src/pages/
│   └── MapView.jsx          ← Map component
└── package.json             ← Leaflet dependencies
```

---

## Configuration Options

Open `src/config/openStreetMap.js` to customize:

### 1. Change Default Location

```javascript
export const defaultCenter = {
  lat: 28.6139,  // Your latitude
  lng: 77.2090   // Your longitude
};
```

**Popular Locations:**

```javascript
// Mumbai, India
{ lat: 19.0760, lng: 72.8777 }

// Bangalore, India
{ lat: 12.9716, lng: 77.5946 }

// New York, USA
{ lat: 40.7128, lng: -74.0060 }

// London, UK
{ lat: 51.5074, lng: -0.1278 }
```

### 2. Change Map Style

Switch between different map appearances:

```javascript
// In openStreetMap.js, change activeTileProvider:

// Default (Standard OSM)
export const activeTileProvider = TILE_PROVIDERS.default;

// Dark Mode
export const activeTileProvider = TILE_PROVIDERS.dark;

// Light/Minimal
export const activeTileProvider = TILE_PROVIDERS.light;

// Outdoor/Topographic
export const activeTileProvider = TILE_PROVIDERS.outdoor;
```

### 3. Adjust Zoom Levels

```javascript
export const MAP_ZOOM = {
  WORLD: 3,      // Global view
  COUNTRY: 6,    // Country view
  CITY: 12,      // City view (default)
  AREA: 14,      // Neighborhood
  STREET: 16,    // Street level
  BUILDING: 18   // Building level
};
```

### 4. Change Marker Colors

```javascript
export const MARKER_COLORS = {
  NGO: '#004E89',        // Blue
  VOLUNTEER: '#06D6A0',  // Green
  EMERGENCY: '#EF233C',  // Red
  NEED: '#FF6B35',       // Orange
  USER: '#FFB703'        // Your custom color
};
```

---

## Map Features

### ✨ Current Features:

1. **Interactive Map**
    - Pan, zoom, and navigate
    - Click markers for details
    - Responsive on all devices

2. **Custom Markers**
    - Color-coded by type
    - NGOs (Blue)
    - Volunteers (Green)
    - Your location (Yellow)

3. **Popups**
    - Name and details
    - Contact information
    - Distance from you
    - Verification status

4. **Geolocation**
    - Auto-detect your location
    - Show distance to entities
    - Center map on your position

5. **List View**
    - See nearby NGOs/Volunteers
    - Sorted by distance
    - Contact details

---

## Customization Examples

### Add Custom Marker Icon

```javascript
// In MapView.jsx
const customIcon = L.icon({
  iconUrl: '/path/to/your/icon.png',
  iconSize: [32, 32],
  iconAnchor: [16, 32],
  popupAnchor: [0, -32]
});

<Marker position={[lat, lng]} icon={customIcon}>
  <Popup>Your content</Popup>
</Marker>
```

### Add Search/Geocoding

Install Nominatim (OSM's geocoding service):

```bash
npm install leaflet-geosearch
```

```javascript
import { GeoSearchControl, OpenStreetMapProvider } from 'leaflet-geosearch';

const searchControl = new GeoSearchControl({
  provider: new OpenStreetMapProvider(),
  style: 'bar',
});
```

### Add Routing

Install routing plugin:

```bash
npm install leaflet-routing-machine
```

```javascript
import L from 'leaflet';
import 'leaflet-routing-machine';

L.Routing.control({
  waypoints: [
    L.latLng(start.lat, start.lng),
    L.latLng(end.lat, end.lng)
  ]
}).addTo(map);
```

---

## Fair Use Policy

OpenStreetMap is free but has a **fair use policy**:

### ✅ Good Practices:

1. **Cache tiles** locally when possible
2. **Provide attribution** (already included)
3. **Reasonable request volume**
4. **Don't hammer servers** with rapid requests

### ⚠️ Heavy Usage:

If your app grows to >**500K tile requests/month**, consider:

1. **Self-hosting tiles**
    - Download OSM data
    - Set up your own tile server
    - Full control and privacy

2. **Commercial Providers**
    - Mapbox (free tier: 50K requests/month)
    - Maptiler (free tier: 100K requests/month)
    - Thunderforest (free tier: 150K requests/month)

3. **Support OSM**
    - Donate to OpenStreetMap Foundation
    - Contribute map data
    - Help with maintenance

---

## Troubleshooting

### ❌ Map not loading

**Solutions:**

1. Check internet connection
2. Clear browser cache
3. Check console for errors
4. Verify Leaflet CSS is imported

### ❌ Markers not showing

**Solutions:**

1. Check marker data has `location` field
2. Verify lat/lng values are valid
3. Check marker icon configuration
4. Look for console errors

### ❌ "Cannot read property 'lat' of null"

**Solutions:**

1. Add null checks for location data
2. Verify database has location fields
3. Check user permission for geolocation

### ❌ Map tiles not loading

**Solutions:**

1. Check if tile server is accessible
2. Try different tile provider
3. Check network tab in DevTools
4. Verify attribution is present

---

## Alternative Tile Providers

You can use other free tile providers:

### 1. Stamen Terrain

```javascript
{
  url: 'https://stamen-tiles-{s}.a.ssl.fastly.net/terrain/{z}/{x}/{y}.png',
  attribution: 'Map tiles by Stamen Design, CC BY 3.0 — Map data © OpenStreetMap'
}
```

### 2. Stamen Watercolor

```javascript
{
  url: 'https://stamen-tiles-{s}.a.ssl.fastly.net/watercolor/{z}/{x}/{y}.jpg',
  attribution: 'Map tiles by Stamen Design, CC BY 3.0 — Map data © OpenStreetMap'
}
```

### 3. Esri World Imagery

```javascript
{
  url: 'https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}',
  attribution: 'Tiles © Esri'
}
```

---

## Comparing with Google Maps

| Feature | OpenStreetMap | Google Maps |
|---------|---------------|-------------|
| **Cost** | ✅ Free forever | ⚠️ $200 free/month |
| **API Key** | ✅ Not required | ❌ Required |
| **Billing** | ✅ Never needed | ⚠️ Credit card required |
| **Rate Limits** | ✅ Fair use only | ⚠️ Strict quotas |
| **Privacy** | ✅ No tracking | ⚠️ Google tracking |
| **Customization** | ✅ Highly flexible | ⚠️ Limited |
| **Quality** | ✅ Excellent | ✅ Excellent |
| **Coverage** | ✅ Global | ✅ Global |
| **Offline Use** | ✅ Possible | ❌ Difficult |
| **Open Source** | ✅ Yes | ❌ No |

---

## Advanced Features

### Clustering Markers

For many markers, use clustering:

```bash
npm install react-leaflet-cluster
```

```javascript
import MarkerClusterGroup from 'react-leaflet-cluster';

<MarkerClusterGroup>
  {markers.map(marker => (
    <Marker key={marker.id} position={marker.position}>
      <Popup>{marker.info}</Popup>
    </Marker>
  ))}
</MarkerClusterGroup>
```

### Heatmaps

Show density of activities:

```bash
npm install leaflet.heat
```

```javascript
import 'leaflet.heat';

L.heatLayer(points, {radius: 25}).addTo(map);
```

### Drawing Tools

Let users draw on map:

```bash
npm install leaflet-draw
```

---

## Resources

### Documentation:

- [Leaflet.js Docs](https://leafletjs.com/)
- [React Leaflet Docs](https://react-leaflet.js.org/)
- [OpenStreetMap Wiki](https://wiki.openstreetmap.org/)

### Tutorials:

- [Leaflet Quick Start](https://leafletjs.com/examples/quick-start/)
- [React Leaflet Tutorial](https://react-leaflet.js.org/docs/start-introduction/)

### Community:

- [OSM Community](https://community.openstreetmap.org/)
- [Leaflet GitHub](https://github.com/Leaflet/Leaflet)
- [React Leaflet GitHub](https://github.com/PaulLeCam/react-leaflet)

### Tile Servers:

- [OSM Tile Servers](https://wiki.openstreetmap.org/wiki/Tile_servers)
- [Leaflet Providers](https://leaflet-extras.github.io/leaflet-providers/preview/)

---

## Supporting OpenStreetMap

If you find OSM valuable, consider:

1. **Donate**
    - [OpenStreetMap Foundation](https://donate.openstreetmap.org/)

2. **Contribute Data**
    - Add missing places
    - Update incorrect information
    - Map your local area

3. **Spread the Word**
    - Tell others about OSM
    - Write blog posts
    - Share on social media

---

**OpenStreetMap is ready to use in Kutumbh! 🗺️**

No setup required. Just install dependencies and start developing!

```bash
npm install
npm run dev
```
