<!DOCTYPE html>
<html>
<head>
    <title>TravelBloom</title>
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background: url('https://forums.frontier.co.uk/attachments/9867b4e5-c0fc-4fd1-8df0-f21c47339837-jpeg.145574/') no-repeat center center fixed;
            background-size: cover;
            color: white;
        }
        nav {
            background-color: rgba(0, 0, 0, 0.8);
            overflow: hidden;
            padding: 10px 20px;
        }
        nav a {
            color: white;
            text-decoration: none;
            padding: 14px 20px;
            display: inline-block;
            cursor: pointer;
        }
        nav input[type="text"] {
            padding: 6px;
            margin-left: 20px;
        }
        nav button {
            padding: 6px 10px;
            margin-left: 5px;
        }
        .section { display: none; padding: 50px; }
        .active { display: block; }
        .member {
            background: rgba(0,0,0,0.6);
            padding: 20px;
            margin-bottom: 10px;
            width: fit-content;
        }
        #results img {
            width: 200px;
            height: auto;
            margin: 10px;
        }
    </style>
</head>
<body>

    <nav>
        <img src="https://cdn.worldvectorlogo.com/logos/jurassic-park-2.svg" alt="Jurassic Park Logo" style="height:40px; vertical-align: middle; margin-right: 20px;">
        
        <a onclick="showSection('home')">Home</a>
        <a onclick="showSection('about')">About Us</a>
        <a onclick="showSection('contact')">Contact Us</a>
        <input type="text" id="searchInput" placeholder="Enter a destination or keyword">
        <button onclick="searchRecommendations()">Search</button>
        <button onclick="clearResults()">Clear</button>
    </nav>
    
    
    <!-- Home Section -->
    <div id="home" class="section active">
        <h1>Welcome to Jurrasic Rides</h1>
        <p>Explore amazing destinations and plan your next adventure with dinosaurs.</p>
        <button>BOOK NOW</button>
        <div id="results"></div>
    </div>

    <!-- About Us Section -->
    <div id="about" class="section">
        <h1>ABOUT US</h1>
        <p>We are a team of passionate individuals dedicated to providing excellent travel recommendations to our users. Our mission is to help you explore amazing destinations and plan memorable adventures worldwide.</p>
        <h2>Our Team</h2>
        <div class="member"><strong>John Doe</strong> - CEO</div>
        <div class="member"><strong>Celina Thomas</strong> - Team Lead</div>
        <div class="member"><strong>Mike Tyen</strong> - Delivery Head</div>
    </div>

    <!-- Contact Us Section -->
    <div id="contact" class="section">
        <h1>Contact Us</h1>
        <form>
            <input type="text" placeholder="Your Name">
            <input type="email" placeholder="Your Email">
            <textarea placeholder="Your Message"></textarea>
            <button type="submit">Submit</button>
        </form>
    </div>

    <script src="travel.js"></script>
</body>
</html>
