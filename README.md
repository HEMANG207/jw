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
function searchRecommendations() {
    const keyword = document.getElementById("searchInput").value.toLowerCase();
    const resultsDiv = document.getElementById("results");
    resultsDiv.innerHTML = "Loading...";

    fetch('travel_recommendation_api.json')
    .then(response => response.json())
    .then(data => {
        const results = data.places.filter(place =>
            place.category.toLowerCase().includes(keyword) ||
            place.name.toLowerCase().includes(keyword)
        );

        if (results.length > 0) {
            resultsDiv.innerHTML = "";
            results.forEach(place => {
                resultsDiv.innerHTML += `
                    <div style="background:white; border-radius:8px; overflow:hidden; box-shadow:0 2px 8px rgba(0,0,0,0.2); margin-bottom:20px; max-width:400px;">
                        <img src="${place.imageUrl}" alt="${place.name}" style="width:100%; height:200px; object-fit:cover;">
                        <div style="padding:15px;">
                            <h3 style="margin:0 0 10px;">${place.name}</h3>
                            <p style="font-size:14px; color:#555;">${place.description}</p>
                            <button style="margin-top:10px; background-color:teal; color:white; border:none; padding:8px 12px; cursor:pointer; border-radius:4px;">Visit</button>
                        </div>
                    </div>
                `;
            });
        } else {
            resultsDiv.innerHTML = "No results found.";
        }
    })
    .catch(error => {
        resultsDiv.innerHTML = "Error loading recommendations.";
        console.error(error);
    });
}
{
    "places": [
        {
            "name": "Isla Nublar",
            "category": "island",
            "description": "The island that is home to Jurassic Park and Jurassic World, featuring lush jungles and dinosaurs.",
            "imageUrl": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQY_qdnGfdP7VgFvQYVo_RZ_lsw1TFpfnsdjw&s"
        },
        {
            "name": "Isla Sorna",
            "category": "island",
            "description": "Also known as Site B, Isla Sorna is where dinosaurs were engineered and held before being moved to Isla Nublar.",
            "imageUrl": "https://cdnb.artstation.com/p/assets/images/images/055/154/177/large/rezwanur-rafi-final-copy.jpg?1666244410" 
        },
        {
            "name": "Sorna Thulbert",
            "category": "island",
            "description": "Sorna Thulbert is another part of the Isla Sorna ecosystem, rich in biodiversity and dinosaur habitats.",
            "imageUrl": "https://deadline.com/wp-content/uploads/2025/07/MCDJUWO_UV128.jpg?w=681&h=383&crop=1"
        }
    ]
}
-



