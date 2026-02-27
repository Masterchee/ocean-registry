# 🔱 Underwater Research Registry

An interactive, geospatial web application designed for marine researchers and enthusiasts to catalog sea creatures, map their discovery locations, and maintain a centralized specimen database.

### 🌐 Quick Links

* **Live Discovery Map:** [masterchee.github.io/ocean-registry/](https://masterchee.github.io/ocean-registry/)
* **Official Repository:** [github.com/Masterchee/ocean-registry](https://github.com/Masterchee/ocean-registry)

---

## 🚀 Features

* **Discovery Map:** A high-performance interactive map powered by Leaflet.js, featuring dark-ocean tiles and automated specimen plotting.
* **Deep Dive Navigation:** Clicking a species name triggers a cinematic "fly-to" animation, centering the map on the specimen's coordinates and launching the high-fidelity photo gallery.
* **Secure Admin Panel:** Built-in authentication via Supabase Auth, allowing authorized researchers to add, edit, or delete registry entries.
* **Dynamic Data Sync:** Support for bulk-uploading species data via standardized CSV files with automatic coordinate validation.
* **Intelligent Visuals:** A multi-stage image engine that prioritizes registry-defined photos but utilizes a smart fallback search for specimen visual representation.
* **Dark Mode:** A togglable interface tailored for low-light research environments.

## 🛠️ Tech Stack

* **Frontend:** Vanilla HTML5, CSS3 (Modern Flexbox/Grid), JavaScript (ES6+).
* **Mapping:** [Leaflet.js](https://leafletjs.com/) with CartoDB Dark Matter tiles.
* **Backend & Auth:** [Supabase](https://supabase.com/) (PostgreSQL & GoTrue).
* **Visuals:** Wikimedia Commons API & LoremFlickr Fallback.

---

## 📊 Data Architecture

### 1. Database Schema (Supabase)

To ensure geospatial accuracy and proper "Deep Dive" functionality, your Supabase table should be named `Sea Creatures` and follow this schema:

| Column | Type | Description |
| --- | --- | --- |
| `id` | `int8` | Primary Key (Identity) |
| `sea_creature` | `text` | Common name (Unique constraint) |
| `scientific_name` | `text` | Latin name (Unique constraint) |
| `status` | `text` | Conservation status |
| `source` | `text` | Data origin / Citation |
| `latitude` | `float8` | Decimal latitude (Essential for Map placement) |
| `longitude` | `float8` | Decimal longitude (Essential for Map placement) |
| `image_url` | `text` | Direct link to specimen photo |

### 2. CSV Import Specification

For bulk synchronization, your CSV must adhere to the following 7-column structure:

`Sea Creature, Scientific Name, Status, Source, Latitude, Longitude, Image URL`

> **Note:** Latitude and Longitude must be pure decimal numbers (e.g., `-75.21`). Including degree symbols or directional letters (N/S/E/W) will trigger the "Top-Left Null Island" safety guard.

---

## 🏗️ Setup & Installation

1. **Clone the Repository:**
```bash
git clone https://github.com/Masterchee/ocean-registry.git

```


2. **Initialize Supabase:**
* Create a new project in the Supabase Dashboard.
* Run the schema setup (listed above) in the SQL Editor.
* Enable **Email/Password** authentication in the Auth settings.


3. **Link Credentials:**
Update the `_URL` and `_KEY` constants in your `<script>` tag:
```javascript
const _URL = https://dfuqjromqjmpeeymiejx.supabase.co
const _KEY = sb_publishable_Tow5s3qQR_3ZOXZpDrjl4Q_a5xFXCRX

```


4. **Launch:**
Open `index.html` in any modern web browser or use a Live Server extension.

---

## 📜 License

This project is licensed under the MIT License - see the LICENSE file for details.

---
