# Requests module 
- before diving into the requests module, let us now first understand what are APIs and HTTP requests, let us understand how each request work diffrently in the background.

### What are APIs?
- API (Application Programming Interface)
- An API is a bridge that allows two applications or systems to communicate with each other.
- It defines a set of rules that software applications follow to interact, request and excange data.

### Real-Life Example of an API
🚕 API & HTTP Requests as a Food Delivery Service, Imagine you are ordering food from Zomato or Swiggy 🍔🍕

1️⃣ GET Request – Checking Menu

> You: "Hey, can I see the menu?"<br>
> Restaurant (Server): "Sure! Here’s the list of available items."<br>
> 👉 requests.get("https://foodapp.com/menu"). <br>
> 📜 Response: List of food items in JSON.

2️⃣ POST Request – Placing an Order
> You: "I’d like to order a large pizza and a Coke."<br>
> Restaurant: "Okay, your order is confirmed!"<br>
> 👉 requests.post("https://foodapp.com/order", data={"item": "Pizza", "drink": "Coke"})<br>
> 📜 Response: "Your order ID is 123. It will arrive in 30 minutes."

3️⃣ PUT Request – Changing Your Order
> You: "Oops! I want Pepsi instead of Coke."<br>
> Restaurant: "Got it! Order updated."<br>
> 👉 requests.put("https://foodapp.com/order/123", data={"drink": "Pepsi"})<br>
> 📜 Response: "Your drink has been updated to Pepsi."

4️⃣ DELETE Request – Cancelling Your Order
> You: "Oh no, I changed my mind! Cancel my order."<br>
> Restaurant: "Okay, your order has been canceled."<br>
> 👉 requests.delete("https://foodapp.com/order/123")<br>
> 📜 Response: "Your order has been deleted."

5️⃣ 404 Not Found – Restaurant is Closed
> You: "Can I order food?"<br>
> Restaurant: "Sorry, we are closed!"<br>
> 👉 requests.get("https://foodapp.com/midnight-menu")<br>
> 📜 Response: 404 Not Found

6️⃣ 401 Unauthorized – Wrong Password
> You: "Let me log in and get a discount."<br>
> Server: "Wrong password, access denied!"<br>
> 👉 requests.get("https://foodapp.com/discount", headers={"Authorization": "WrongToken"})<br>
> 📜 Response: 401 Unauthorized

7️⃣ 500 Internal Server Error – Kitchen is on Fire! 🔥
> You: "Hey, where’s my order?"<br>
> Restaurant: "Our kitchen just caught fire! We can’t serve your order!"<br>
> 👉 requests.get("https://foodapp.com/order-status/123")<br>
> 📜 Response: 500 Internal Server Error

- Yeah, this is a fun way to know api keys. However you might be confused why in some places put used and in other places post used and at some other place delete used. To know more about it, keep on reading below..... hold your enthusiasm.....

# How APIs work with HTTP Methods
ApIs work over the HTTP, the same protocol used in webbrowsers.The most common methods used in APIs are:

|HTTP| Method	|Purpose	Example|
|:----:|:-----:|:-----------:|
|GET|	Fetch data from the server|	View a user profile|
|POST	|Send data to the server to create a resource	|Register a new user|
|PUT|	Update a resource on the server|	Update user details|
|DELETE	|Remove a resource from the server	|Delete a user account|
|PATCH|	Partially update a resource|	Change only the email of a user|


# How HTTP Requests work in the background?
When you call requests.get("https://example.com/data"), here's what happens behind the scenes:
1. Client Request (Your browser or python code)
- the client (your computer) sends a request to the API.
- this request contains:
    - URL
    - HTTP Method(get)
    - Headers(Authentication,etc)
    - Parameters(if any eg: ?id=123)
2. DNS Resolution & Connection Establishment
- Your system finds the IP address of example.com using DNS.
- A TCP connection is established between your system and the API server.
3.  Server Processing
  - The server receives your request and processes it.
  - it checks
      - Authentication
      - Databases queries(Does the requested data exist?)
      - Business Logic (What needs to be returned?)
  - it prepares response.
4. Server Response
  - The server sends back a response with:
       - status code
       - headers
       - body
5. Client Receives Response
  - The response reaches your system
  - If it's JSON, you use .json to parse it.
  - Your program displays or processes the data.


# Now let us come to main moto of our rl. Requests Module
The requests module is used to send HTTP requests(get,post,put,delete etc) adn handle web interactions easily. It is one of the most popular libraries for working with APIs in python.

### Installation
First, install the requests module if you haven't already:
```
pip install requests
```

### Basic Example: GET Request
```
import requests
response = requests.get("https://api.github.com")
print(response.status_code)  # 200 (OK)
print(response.text)  # Prints the response content
```

### Handling JSON Data (APIs)
Many APIs return responses in JSON format. Use .json() to parse the response:
```
Edit
response = requests.get("https://jsonplaceholder.typicode.com/users")
data = response.json()
print(data[0]["name"])  # Prints the first user's name
```

### Sending Parameters with GET
```
params = {"q": "Python", "sort": "stars"}
response = requests.get("https://api.github.com/search/repositories", params=params)
print(response.url)  # Shows the full URL with parameters
```

Sending Data with POST
```
data = {"username": "Chithra", "password": "mypassword"}
response = requests.post("https://httpbin.org/post", data=data)
print(response.json())  # Prints the server response
```

Headers in requests
```
headers = {"User-Agent": "MyApp/1.0"}
response = requests.get("https://api.github.com", headers=headers)
print(response.headers)  # Shows the response headers
```

Downloading a File
```
url = "https://example.com/sample.pdf"
response = requests.get(url)

with open("sample.pdf", "wb") as file:
    file.write(response.content)

print("Download complete!")
```
### Error Handling
Use try-except blocks to handle errors:
```
try:
    response = requests.get("https://wrongurl.com", timeout=5)
    response.raise_for_status()  # Raises an error for bad responses (4xx, 5xx)
except requests.exceptions.RequestException as e:
    print("Error:", e)
```


