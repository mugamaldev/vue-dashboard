🟩 Vue Dashboard (Vue 3 + Router + Axios)

Dashboard connected to Laravel API to manage authentication, products and orders.

🎯 Features

Login / Register (JWT)

Dashboard Statistics

Products Management (CRUD)

Orders List + Order Details

Protected Routes

Token stored in localStorage

🏗 Tech Stack

Vue 3

Vue Router

Axios

Vite

⚙️ Installation
1️⃣ Clone project
git clone https://github.com/mugamaldev/vue-dashboard
cd vue-dashboard

2️⃣ Install dependencies
npm install

3️⃣ Run dev server
npm run dev


Your app will run at:
👉 http://localhost:5173

🔗 API Connection

Configure API endpoint inside:

src/api/axios.js

const api = axios.create({
    baseURL: "http://127.0.0.1:8000/api",
});

📂 Pages
src/pages/
  Login.vue
  Register.vue
  Dashboard.vue
  Products.vue
  Orders.vue

🔐 Route Protection

If no token → redirect to /login

✔ Dashboard Ready.
