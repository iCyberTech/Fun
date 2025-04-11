<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Arena of Grace and Testimonies</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Welcome to Arena of Grace and Testimonies</h1>
        <p>Join us in celebrating faith and community!</p>
    </header>
    
    <main>
        <section>
            <h2>About Us</h2>
            <p>At Arena of Grace and Testimonies, we believe in the power of faith and community. Join us for uplifting sermons and heartfelt testimonies.</p>
        </section>
    </main>

    <footer>
        <div class="floating-buttons">
            <a href="#sermons" class="button">Sermons</a>
            <a href="#testimonies" class="button">Testimonies</a>
            <a href="#donate" class="button">Donate</a>
        </div>
        <div class="icons">
            <div class="chatbot-icon">🗨️</div>
            <div class="theme-switcher" onclick="toggleTheme()">🌙</div>
        </div>
    </footer>

    <script">
    function toggleTheme() {
    document.body.classList.toggle('dark-theme');
    document.body.classList.toggle('light-theme');
}

// Set the initial theme
document.body.classList.add('light-theme');

    </script>
</body>
</html>

<style>
  body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    margin: 0;
    padding: 0;
    transition: background-color 0.5s, color 0.5s;
}

header {
    background: #4CAF50;
    color: white;
    padding: 20px;
    text-align: center;
}

main {
    padding: 20px;
}

.floating-buttons {
    position: fixed;
    bottom: 20px;
    right: 20px;
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.button {
    background: #007BFF;
    color: white;
    padding: 10px 15px;
    border-radius: 5px;
    text-decoration: none;
    text-align: center;
}

.icons {
    position: fixed;
    bottom: 20px;
    left: 20px;
    display: flex;
    gap: 15px;
}

.chatbot-icon, .theme-switcher {
    font-size: 30px;
    cursor: pointer;
}

.light-theme {
    background-color: white;
    color: black;
}

.dark-theme {
    background-color: #333;
    color: white;
}

</style>
