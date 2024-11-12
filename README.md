
<h1>Receipt Processor</h1><br>
This is a backend service for processing receipts and calculating points based on various criteria. It provides a simple API with endpoints to process receipts, retrieve points, and check server status. The service is built using Express.js, Dockerized for deployment, and includes Swagger documentation for the API.

<h2>Features</h2>
1. <strong>Receipt Processing:</strong> Submit receipt details and get points based on certain criteria.<br>
2. <strong>Point Retrieval:</strong> Retrieve points for a processed receipt by its ID.<br>
3. <strong>Server Status:</strong> Check if the server is up and running.<br>
4. <strong>Swagger Documentation:</strong> Interactive API documentation.<br>

<h2>Prerequisites</h2><br>
Before running this application, ensure that the following are installed:<br>
<strong>Docker:</strong> The application is Dockerized for easy deployment.<br>
<strong>Node.js:</strong> If you want to run the app locally without Docker.<br>

<h2>Getting Started</h2><br>

<h3>Clone the repository</h3>
<pre><code>git clone https://github.com/arish21/Receipt_Processor.git
cd Receipt_Processor</code></pre>

<h3>Running Locally</h3>
<h4>Install dependencies:</h4>
If you are running the app without Docker, first install the necessary dependencies:
<pre><code>npm install</code></pre>

<h4>Start the server:</h4>
You can run the server locally with:
<pre><code>npm start</code></pre>
The server will start on port 3000 by default.

<h3>Running with Docker</h3>
<h4>Build the Docker image:</h4>
Build the Docker image using the following command:
<pre><code>docker build -t receipt-processor .</code></pre>

<h4>Run the Docker container:</h4>
Once the image is built, run the container:
<pre><code>docker run -p 3000:3000 receipt-processor</code></pre>
The API will now be accessible at <a href="http://localhost:3000" target="_blank">http://localhost:3000</a>.

<h2>Running Tests in Docker</h2>
To run the tests inside the Docker container, you can override the default command as follows:

<strong>Build the Docker image:</strong><br>
<pre><code>docker build -t receipt-processor .</code></pre>

<strong>Run the tests (Override CMD to Run Tests):</strong><br>
<pre><code>docker run receipt-processor npm test</code></pre>

This command will run `npm test` instead of the default `npm start` (which runs the app), allowing you to execute the tests in the container.

<h2>API Endpoints</h2>
This API is documented using <strong>Swagger</strong>. You can view the interactive Swagger API documentation at the following endpoint:
<p><strong>Swagger Documentation:</strong> <a href="http://localhost:3000/api-docs" target="_blank">http://localhost:3000/api-docs</a></p>

<h3>1. POST /receipts/process</h3>
This endpoint processes a receipt, validates the fields, and calculates points based on various criteria.<br>
<h4>Request Body (example):</h4>
<pre><code>{
  "retailer": "SuperMart",
  "purchaseDate": "2024-11-11",
  "purchaseTime": "14:30",
  "items": [
    {
      "shortDescription": "Item A",
      "price": 10.5
    },
    {
      "shortDescription": "Item B",
      "price": 20.0
    }
  ],
  "total": "30.5"
}</code></pre>

<h4>Response (example):</h4>
<pre><code>{
  "id": "777f8695-d842-4eab-844a-fafcfcad3db8"
}</code></pre>

<h3>2. GET /receipts/:id/points</h3>
This endpoint retrieves the points for a processed receipt by its <code>id</code>.<br>
<h4>Response (example):</h4>
<pre><code>{
  "points": 62
}</code></pre>

<h3>3. GET /</h3>
This is a simple endpoint to check the server status. It will return:
<pre><code>Server is up and running!</code></pre>

<h2>Testing</h2>
Tests are written using <strong>Jest</strong>. You can run the tests locally with the following command:
<pre><code>npm test</code></pre>
This will run all the tests and display the results.

<h2>.env Configuration</h2>
<strong>NOTE: For simplicity purposes I have pushed .env to the github. I know it is not a good practice to push a .env to the github.</strong>


<h2>Docker Configuration</h2>
The application is fully Dockerized. To build and run the Docker container, follow these steps:

<h4>Build the Docker image:</h4>
<pre><code>docker build -t receipt-processor .</code></pre>

<h4>Run the Docker container:</h4>
<pre><code>docker run -p 3000:3000 receipt-processor</code></pre>
Once running, you can access the API at <a href="http://localhost:3000" target="_blank">http://localhost:3000</a>.

