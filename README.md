<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Himachal Pradesh Travel Guide</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        body {
            background-color: #f5f5f5;
        }

        .header {
            background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.7)), url('https://placehold.co/1200x400');
            background-size: cover;
            color: white;
            padding: 100px 20px;
            text-align: center;
            position: relative;
        }

        .weather {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(255, 255, 255, 0.8);
            padding: 10px 20px;
            border-radius: 10px;
            text-align: center;
        }

        .weather h3 {
            margin-bottom: 5px;
            font-size: 16px;
            color: #333;
        }

        .nav {
            background: #333;
            padding: 15px;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .nav a {
            color: white;
            text-decoration: none;
            margin: 0 15px;
            font-size: 16px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }

        .card {
            background: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            transition: transform 0.3s, box-shadow 0.3s;
            cursor: pointer;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
        }

        .card h3 {
            color: #333;
            margin-bottom: 15px;
        }

        .card i {
            font-size: 24px;
            color: #4CAF50;
            margin-bottom: 15px;
        }

        .search-bar {
            padding: 20px;
            text-align: center;
        }

        .search-bar input {
            padding: 10px;
            width: 300px;
            border-radius: 5px;
            border: 1px solid #ddd;
        }

        .events-section {
            background: #fff;
            padding: 20px;
            margin-top: 30px;
            border-radius: 10px;
        }

        .events-section h2 {
            cursor: pointer;
        }

        .events-list {
            display: none;
            margin-top: 10px;
        }

        .footer {
            background: #333;
            color: white;
            text-align: center;
            padding: 20px;
            margin-top: 50px;
        }
    </style>
</head>
<body>
    <div class="header">
        <h1>Welcome to Himachal Pradesh</h1>
        <p>Discover the Land of Gods</p>
        <div class="weather" id="weather">
            <h3>Loading Weather...</h3>
        </div>
    </div>

    <div class="nav">
        <a href="#transport">Transport</a>
        <a href="#stays">Stays</a>
        <a href="#food">Food</a>
        <a href="#activities">Activities</a>
        <a href="#events">Events</a>
        <a href="#work">Work & Volunteer</a>
    </div>

    <div class="search-bar">
        <input type="text" placeholder="Search for places, activities, or events...">
    </div>

    <div class="container">
        <div class="grid">
            <div class="card">
                <i class="fas fa-bus"></i>
                <h3>Transport</h3>
                <p>Find information about buses, cabs, and local transport options.</p>
            </div>
            <div class="card">
                <i class="fas fa-hotel"></i>
                <h3>Stays</h3>
                <p>Discover hotels, hostels, and homestays for every budget.</p>
            </div>
            <div class="card">
                <i class="fas fa-utensils"></i>
                <h3>Cafes & Restaurants</h3>
                <p>Explore local cuisine and popular dining spots.</p>
            </div>
            <div class="card">
                <i class="fas fa-hiking"></i>
                <h3>Treks & Adventures</h3>
                <p>Find popular treks and hidden trails.</p>
            </div>
            <div class="card">
                <i class="fas fa-store"></i>
                <h3>Local Shopping</h3>
                <p>Explore markets and special shops.</p>
            </div>
            <div class="card">
                <i class="fas fa-laptop"></i>
                <h3>Work & Volunteer</h3>
                <p>Find gig work and volunteering opportunities.</p>
            </div>
        </div>

        <div class="events-section">
            <h2 id="toggle-events">Today's Special Events <i class="fas fa-chevron-down"></i></h2>
            <div class="events-list" id="events-list">
                <p>Local Music Festival at Mall Road</p>
                <p>Handicraft Exhibition at Ridge</p>
            </div>
        </div>
    </div>

    <div class="footer">
        <p>© 2025 Himachal Pradesh Travel Guide</p>
    </div>

    <script>
        // Fetch real-time weather data
        const weatherElement = document.getElementById('weather');
        const apiKey = 'YOUR_OPENWEATHERMAP_API_KEY'; // Replace with your OpenWeatherMap API key
        const city = 'Shimla'; // Default city for weather

        async function fetchWeather() {
            try {
                const response = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=${apiKey}`);
                const data = await response.json();
                const { temp } = data.main;
                const { description } = data.weather[0];
                weatherElement.innerHTML = `
                    <h3>${city}</h3>
                    <p>${temp}°C, ${description}</p>
                `;
            } catch (error) {
                weatherElement.innerHTML = '<h3>Unable to fetch weather</h3>';
            }
        }

        fetchWeather();

        // Toggle events section
        const toggleEvents = document.getElementById('toggle-events');
        const eventsList = document.getElementById('events-list');

        toggleEvents.addEventListener('click', () => {
            const isVisible = eventsList.style.display === 'block';
            eventsList.style.display = isVisible ? 'none' : 'block';
        });
    </script>
</body>
</html>
