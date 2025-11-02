# Performance Garage
**Developer:** Alvaro Magallon-beltran 
**Student ID:** 775288
**Browser Tested:** Chrome

---

## 🏎️ Overview
Performance Garage is a mock web application that allows users to showcase their personal car builds, upload photos, list modifications, and engage with other enthusiasts through likes, comments, and reviews.  
The purpose of this project is to demonstrate core web design principles in HTML, CSS, and JavaScript, while outlining how a Flask backend could support this functionality in a real deployment.

---

## ⚙️ Architecture Overview
The website is built as a static front-end using:
- **HTML5** for page structure  
- **CSS3** for styling and layout (includes a dark/light theme switcher)  
- **JavaScript (ES6)** for interactivity (filters, search, animations, etc.)  

The backend is conceptualized in **Flask (Python)**, which would handle:
- Data storage for builds, users, reviews, and parts
- Routing for creating and fetching data
- Connecting front-end forms to database operations  

---

## 🧭 Proposed Flask Routes and HTTP Methods

| Route | Method | Description |
|-------|---------|-------------|
| `/` | GET | Loads main page displaying most popular builds |
| `/builds` | GET | Fetches all builds in the database |
| `/builds/add` | POST | Adds a new build with car details, images, and mods |
| `/builds/<id>` | GET | Retrieves a specific build by ID |
| `/reviews` | GET | Displays all part reviews |
| `/reviews/add` | POST | Adds a new part review |
| `/compare` | GET | Returns comparison data for selected builds or parts |
| `/users/<username>` | GET | Displays user profile and their builds |
| `/comments/add` | POST | Adds comment to a specific build |
| `/likes/<id>` | POST | Increments like count for a build |
| `/search` | GET | Filters builds by model, type, or category |

---

## 🗃️ Database Schema (Conceptual)

**Tables:**

### `users`
| Column | Type | Description |
|--------|------|-------------|
| `user_id` | INT (PK) | Unique user identifier |
| `username` | TEXT | User display name |
| `bio` | TEXT | Short user description |
| `profile_pic` | TEXT | URL to profile image |

### `builds`
| Column | Type | Description |
|--------|------|-------------|
| `build_id` | INT (PK) | Unique ID for each car build |
| `user_id` | INT (FK) | Owner reference |
| `car_model` | TEXT | Model name (e.g., Corvette Z51) |
| `build_type` | TEXT | Street, Track, or Show |
| `mods` | TEXT | List of installed modifications |
| `hp` | INT | Horsepower |
| `torque` | INT | Torque |
| `likes` | INT | Number of likes |
| `image_url` | TEXT | Main build image link |

### `parts`
| Column | Type | Description |
|--------|------|-------------|
| `part_id` | INT (PK) | Unique ID for each performance part |
| `name` | TEXT | Part name (e.g., VaraRam Intake) |
| `category` | TEXT | Intake, Exhaust, Suspension, etc. |
| `rating` | FLOAT | Average user rating |
| `compatibility_notes` | TEXT | Fitment notes or issues |

### `reviews`
| Column | Type | Description |
|--------|------|-------------|
| `review_id` | INT (PK) | Unique ID for review |
| `user_id` | INT (FK) | Who wrote it |
| `part_id` | INT (FK) | Part being reviewed |
| `rating` | INT | Rating 1–5 |
| `review_text` | TEXT | Review content |

### `comments`
| Column | Type | Description |
|--------|------|-------------|
| `comment_id` | INT (PK) | Unique comment ID |
| `build_id` | INT (FK) | The build being commented on |
| `user_id` | INT (FK) | Comment author |
| `text` | TEXT | Comment body |

---

## 💡 Front-End Interactions (Linked to Features)
- **Add Your Build:** Sends a POST to `/builds/add`  
- **Most Popular Builds:** Pulls from `/builds?sort=likes`  
- **Performance Parts Reviews:** Displays `/reviews` data with user ratings  
- **Modification Checklist:** Saved temporarily using localStorage (mock version)  
- **User Profiles:** Pulled dynamically from `/users/<username>`  
- **Search & Filter:** JS fetch call to `/search` endpoint  
- **Performance Comparison Tool:** Fetches `/compare` results to render charts  
- **Comments & Likes:** POST to `/comments/add` and `/likes/<id>` respectively  
- **Parts Comparison & Reviews:** Both use `/parts` and `/reviews` data  
- **Performance Chart:** Rendered locally using Chart.js or pure JS SVG  
- **Before & After Slider:** Implemented with HTML `<input type="range">` for image control  
- **Build Type Filter:** Uses query params like `/builds?type=Track`  
- **Theme Switcher:** JS toggles CSS classes for light/dark mode  
- **Animation:** Handled by CSS keyframes or small JS triggers  

---

## 🧱 Future Enhancements
- Add user authentication with Flask-Login  
- Allow image uploads using Flask’s `request.files`  
- Use SQLite or MySQL to persist builds and reviews  
- Implement admin panel for moderating reviews  
- Add REST API for external integrations  

---

## 🧩 Testing
The front end is designed to render correctly on:
- Google Chrome  

No backend testing is required, but Flask endpoints were conceptualized for clarity.

---

