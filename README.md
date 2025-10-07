
# 🧑‍💻 Freelynk – Freelancing Platform

**Freelynk** is a dynamic web application that connects clients with freelancers. It provides a simple and elegant interface to explore and search for freelancers, view their profiles, and manage projects.
This project uses **HTML**, **CSS**, and **JavaScript** for the frontend and **Node.js + MongoDB** for the backend.

---

## 🚀 Features

* 🌍 **Responsive & Clean UI** – Built with pure HTML and CSS for a clean, modern interface.
* 🔍 **Live Search Bar** – Search freelancers by name dynamically without reloading the page.
* 🧑‍💼 **Freelancer Feed** – Automatically fetches and displays all freelancer data from the backend.
* 💾 **MongoDB Integration** – Stores freelancer information in a MongoDB collection.
* 📄 **Profile Linking** – Each freelancer card redirects to their profile page using their unique ID.
* ⚡ **Fast API** – Node.js + Express backend API for fetching freelancer data.

---

## 🧠 Tech Stack

| Layer        | Technology Used                                        |
| ------------ | ------------------------------------------------------ |
| **Frontend** | HTML5, CSS3, Vanilla JavaScript                        |
| **Backend**  | Node.js, Express.js                                    |
| **Database** | MongoDB                                                |
| **Runtime**  | Node.js                                                |
| **Port**     | `5000` for backend API, `8000` for dashboard (example) |

---

## 📁 Folder Structure

```
Freelynk/
│
├── all_freelancers.html       # Main page displaying all freelancers
├── freelancer_profile.html    # Profile view for individual freelancers
├── about.html                 # About page
├── features.html              # Features page
│
├── server.js                  # Backend API server
├── models/
│   └── Freelancer.js          # Mongoose schema for freelancers
│
├── public/
│   └── images/                # Freelancer images
│
├── package.json               # Node project dependencies
└── README.md                  # Project documentation
```

---

## ⚙️ Installation & Setup

### **1️⃣ Clone the Repository**

```bash
git clone https://github.com/yourusername/freelynk.git
cd freelynk
```

### **2️⃣ Install Dependencies**

```bash
npm install
```

### **3️⃣ Setup MongoDB**

* Make sure MongoDB is running locally or use **MongoDB Atlas**.
* Create a database named `freelynk`.
* Add a `freelancers` collection with documents similar to:

```json
{
  "name": "John Doe",
  "skills": ["Web Development", "UI/UX"],
  "bio": "Creative frontend developer with 3+ years of experience.",
  "rate": 25,
  "image": "https://example.com/john.jpg"
}
```

### **4️⃣ Start the Backend Server**

```bash
node server.js
```

Your backend API will now run at:
👉 `http://localhost:5000/api/freelancers`

### **5️⃣ Run the Frontend**

* Open `all_freelancers.html` in your browser.
* The page will automatically fetch data from your backend.
* Use the search bar to filter freelancers by name.

---

## 🧩 API Endpoint

| Method     | Endpoint               | Description                       |
| ---------- | ---------------------- | --------------------------------- |
| **GET**    | `/api/freelancers`     | Fetch all freelancers             |
| **GET**    | `/api/freelancers/:id` | Fetch a specific freelancer by ID |
| **POST**   | `/api/freelancers`     | Add a new freelancer              |
| **DELETE** | `/api/freelancers/:id` | Delete a freelancer by ID         |

---

## 💡 Example Backend Code (server.js)

```javascript
const express = require('express');
const mongoose = require('mongoose');
const cors = require('cors');

const app = express();
app.use(cors());
app.use(express.json());

// MongoDB Connection
mongoose.connect('mongodb://localhost:27017/freelynk', {
    useNewUrlParser: true,
    useUnifiedTopology: true
}).then(() => console.log('✅ MongoDB Connected'))
  .catch(err => console.log('❌ DB Connection Error:', err));

// Freelancer Schema
const freelancerSchema = new mongoose.Schema({
    name: String,
    skills: [String],
    bio: String,
    rate: Number,
    image: String
});

const Freelancer = mongoose.model('Freelancer', freelancerSchema);

// Routes
app.get('/api/freelancers', async (req, res) => {
    const freelancers = await Freelancer.find();
    res.json(freelancers);
});

app.listen(5000, () => console.log('🚀 Server running on port 5000'));
```

---

## 🎯 Future Enhancements

* ✅ Add rating & reviews for freelancers
* ✅ Include category-based filtering (Design, Development, Writing, etc.)
* ✅ Add real-time chat between client and freelancer
* ✅ Implement authentication and JWT-based login
* ✅ Integrate payment gateway for milestone-based payments

