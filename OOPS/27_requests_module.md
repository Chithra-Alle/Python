# Requests module 
- before diving into the requests module, let us now first understand what are APIs and HTTP requests, let us understand how each request work diffrently in the background.

### What are APIs?
- API (Application Programming Interface)
- An API is a bridge that allows two applications or systems to communicate with each other.
- It defines a set of rules that software applications follow to interact, request and excange data.

### Real-Life Example of an API
🚕 API & HTTP Requests as a Food Delivery Service
- Imagine you are ordering food from Zomato or Swiggy 🍔🍕

1️⃣ GET Request – Checking Menu

> You: "Hey, can I see the menu?"
> Restaurant (Server): "Sure! Here’s the list of available items."
> 👉 requests.get("https://foodapp.com/menu"). <br>
> 📜 Response: List of food items in JSON.
