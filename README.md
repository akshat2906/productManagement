Product Dashboard Summary :

Login Page :
	Login Functionality :
		The login page provides fields for the user to enter an email and password, with form validation to ensure correct input.
		The Login-UI includes features like hiding/showing the password and real-time validation for email format using regular expressions.
		The user receives immediate feedback if the email format is incorrect or if the password field is empty.
	
	JavaScript/jQuery Interaction :
		jQuery Script manages form interactions, including real-time email validation, toggling password visibility, and handling form submission.
		The 'Continue' button triggers an AJAX POST request to the LoginServlet, sending the entered credentials (username and password).
		
	LoginServlet (Java Servlet)
		This servlet handles POST requests from the login page, comparing the entered credentials with predefined values.
		If the email and password match the stored values, the servlet returns a "Welcome" message, redirecting the user to the main dashboard (product.html).
		If there’s a mismatch, the servlet responds with appropriate messages: "Not a User" for unrecognized emails and "Password Mismatching" for incorrect passwords.
		
Product Page :
	Product View Page :
		The Product View page includes a navigation bar allowing users to switch between viewing products and adding new products.
			A 'Refresh' button updates the product list with the latest data from the backend.
		Products details were displayed in a bootstrap table containing product name, category, price, and stock quantity.
		*Initially populated with sample products, it dynamically updates with real data fetched from the backend.*
	
	AJAX Data Fetching :
		On loading, the page automatically triggers a refresh to fetch product data from the backend.
		The Refresh button initiates an AJAX GET request to the ProductGetApiServer (/get-products), which retrieves the current product list from the database.
	
	Error Handling :
		If there is an error in fetching data, a message is displayed to notify users.
		

ProductGetApiServer (Java HTTP Server for GET requests utilizing REST principles) :
	Server Setup :
		The ProductGetApiServer listens on port 8087 and handles GET requests to the (/get-products) endpoint.
		
	Data Retreival :
		Connects to a PostgreSQL database and executes a SQL query to fetch product data from the ProductData table.
	
	JSON Response :
		Uses Jackson’s ObjectMapper to convert the product list into a JSON format, which is then sent back to the frontend.
		
	Error Handling :
		If a non-GET request is made, it returns a 405 Method Not Allowed status.
		
Add Product Page :
	Navigation and Form Setup :
		The Add Product page includes a form for entering product details: name, category, price, and stock quantity.
		Real-time validation ensures each field is completed correctly, displaying messages if input values are missing or incorrect.
		
	Form Submission and Data Validation
		On submission, an AJAX POST request sends the form data in JSON format to the backend ProductPostApiServer (/post-products) endpoints.
		If data is valid, the form resets, and a success message displays.
		
ProductPostApiServer (Java HTTP Server for POST requests utilizing REST principles) :
	Server Setup :
		The ProductPostApiServer listens on port 8085 and handles POST requests to the (/post-products) endpoint.
	
	Data Handling :
		Receives JSON-formatted product data from the frontend, parses it into a Product object, and inserts the new product into the database.

	Database Insertion :
		Executes an SQL INSERT statement to add product details into the ProductData table.
	
	Response Handling :
		Sends a success message if the product is added successfully; otherwise, an error message is sent.
		
	Error Handling :
		Returns a 405 Method Not Allowed status if a non-POST request is received.
		
Product Class (Java Model) :
	Purpose and Attributes :
		The Product class represents each product with attributes: id, name, category, price, and stock.
	
	Constructor :
		The constructor initializes a Product instance with provided values, making it easy to create and manage product objects throughout the application.
		
		
		

Note:	ProductServlet was used for testing purpose.

Credentials for login:
		user - rehmat@gmail.com
		pass - Rehmat@1001
