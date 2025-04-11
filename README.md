<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Arena of Grace and Testimonies - Transforming Lives Through Faith</title>
    <meta name="description" content="A vibrant Christian community where faith meets miracles and lives are transformed by God's word">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700&family=Playfair+Display:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-color: #3a5a78;
            --primary-light: #5b7b9a;
            --secondary-color: #d4a017;
            --secondary-light: #e6b800;
            --accent-color: #8b5a2b;
            --text-color: #333333;
            --text-light: #666666;
            --bg-color: #f8f9fa;
            --card-bg: #ffffff;
            --nav-bg: #2c3e50;
            --nav-text: #ffffff;
            --footer-bg: #1a252f;
            --footer-text: #dddddd;
            --success-color: #28a745;
            --box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            --box-shadow-hover: 0 8px 25px rgba(0, 0, 0, 0.15);
            --transition: all 0.3s ease-in-out;
            --border-radius: 8px;
        }

        .dark-theme {
            --primary-color: #5b7b9a;
            --primary-light: #7d9bba;
            --secondary-color: #e6b800;
            --secondary-light: #ffcc00;
            --accent-color: #a87b4b;
            --text-color: #f0f0f0;
            --text-light: #bbbbbb;
            --bg-color: #121212;
            --card-bg: #1e1e1e;
            --nav-bg: #121212;
            --nav-text: #ffffff;
            --footer-bg: #000000;
            --footer-text: #cccccc;
            --box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            --box-shadow-hover: 0 8px 25px rgba(0, 0, 0, 0.4);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Montserrat', sans-serif;
            line-height: 1.7;
            color: var(--text-color);
            background-color: var(--bg-color);
            position: relative;
            padding-bottom: 120px;
            min-height: 100vh;
            transition: var(--transition);
        }

        h1, h2, h3, h4 {
            font-family: 'Playfair Display', serif;
            font-weight: 600;
            line-height: 1.3;
            margin-bottom: 1rem;
        }

        a {
            text-decoration: none;
            color: inherit;
            transition: var(--transition);
        }

        ul {
            list-style: none;
        }

        img {
            max-width: 100%;
            height: auto;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 1.5rem;
        }

        .section-padding {
            padding: 5rem 0;
        }

        .section-title {
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
        }

        .section-title h2 {
            font-size: 2.5rem;
            color: var(--primary-color);
            display: inline-block;
        }

        .section-title h2::after {
            content: '';
            display: block;
            width: 80px;
            height: 4px;
            background: var(--secondary-color);
            margin: 1rem auto;
            border-radius: 2px;
        }

        .text-center {
            text-align: center;
        }

        /* Header Styles */
        header {
            background-color: var(--nav-bg);
            color: var(--nav-text);
            padding: 1.5rem 0;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            transition: var(--transition);
        }

        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-family: 'Playfair Display', serif;
            font-size: 2rem;
            font-weight: 700;
            color: var(--nav-text);
        }

        .logo span {
            color: var(--secondary-color);
        }

        /* Navigation */
        .nav-toggle {
            display: none;
            background: none;
            border: none;
            color: var(--nav-text);
            font-size: 1.5rem;
            cursor: pointer;
        }

        nav ul {
            display: flex;
            gap: 1.5rem;
        }

        nav ul li a {
            color: var(--nav-text);
            font-weight: 500;
            padding: 0.5rem 1rem;
            border-radius: var(--border-radius);
            position: relative;
        }

        nav ul li a::before {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: 0;
            left: 0;
            background-color: var(--secondary-color);
            transition: var(--transition);
        }

        nav ul li a:hover::before {
            width: 100%;
        }

        nav ul li a.active {
            color: var(--secondary-color);
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), 
                        url('https://images.unsplash.com/photo-1506126613408-eca07ce68773?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            height: 100vh;
            min-height: 700px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            color: white;
            padding: 0 1.5rem;
            margin-top: 80px;
        }

        .hero-content {
            max-width: 800px;
            animation: fadeInUp 1s ease-out;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1.5rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }

        .hero p {
            font-size: 1.25rem;
            margin-bottom: 2.5rem;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
        }

        /* Button Styles */
        .btn {
            display: inline-block;
            background-color: var(--secondary-color);
            color: #333;
            padding: 0.8rem 2rem;
            border: none;
            border-radius: 50px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 1px;
            cursor: pointer;
            transition: var(--transition);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        .btn:hover {
            background-color: var(--secondary-light);
            transform: translateY(-3px);
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
        }

        .btn-outline {
            background: transparent;
            border: 2px solid var(--secondary-color);
            color: white;
            margin-left: 1rem;
        }

        .btn-outline:hover {
            background: var(--secondary-color);
            color: #333;
        }

        /* Services Section */
        .services {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            margin-bottom: 3rem;
        }

        .service-card {
            background-color: var(--card-bg);
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: var(--box-shadow);
            transition: var(--transition);
            position: relative;
        }

        .service-card:hover {
            transform: translateY(-10px);
            box-shadow: var(--box-shadow-hover);
        }

        .service-card img {
            width: 100%;
            height: 250px;
            object-fit: cover;
            transition: var(--transition);
        }

        .service-card:hover img {
            transform: scale(1.05);
        }

        .service-content {
            padding: 2rem;
        }

        .service-content h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: var(--primary-color);
        }

        .service-content p {
            color: var(--text-light);
            margin-bottom: 1.5rem;
        }

        .service-icon {
            font-size: 2.5rem;
            color: var(--secondary-color);
            margin-bottom: 1rem;
        }

        /* About Section */
        .about {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            align-items: center;
        }

        .about-content h2 {
            font-size: 2.2rem;
            color: var(--primary-color);
            margin-bottom: 1.5rem;
        }

        .about-content p {
            margin-bottom: 1.5rem;
            color: var(--text-light);
        }

        .about-stats {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 1rem;
            margin-top: 2rem;
        }

        .stat-item {
            text-align: center;
            padding: 1.5rem;
            background: rgba(212, 160, 23, 0.1);
            border-radius: var(--border-radius);
        }

        .stat-number {
            font-size: 2rem;
            font-weight: 700;
            color: var(--secondary-color);
            margin-bottom: 0.5rem;
        }

        .stat-label {
            font-size: 0.9rem;
            color: var(--text-light);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* Image Slider */
        .slider-container {
            position: relative;
            width: 100%;
            height: 400px;
            overflow: hidden;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
        }

        .slider {
            display: flex;
            width: 500%;
            height: 100%;
            animation: slide 20s infinite;
        }

        .slider img {
            width: 20%;
            height: 100%;
            object-fit: cover;
        }

        @keyframes slide {
            0% { transform: translateX(0); }
            20% { transform: translateX(0); }
            25% { transform: translateX(-20%); }
            45% { transform: translateX(-20%); }
            50% { transform: translateX(-40%); }
            70% { transform: translateX(-40%); }
            75% { transform: translateX(-60%); }
            95% { transform: translateX(-60%); }
            100% { transform: translateX(-80%); }
        }

        /* Events Section */
        .event-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .event-card {
            background-color: var(--card-bg);
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: var(--box-shadow);
            transition: var(--transition);
            display: grid;
            grid-template-columns: 100px 1fr;
        }

        .event-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--box-shadow-hover);
        }

        .event-date {
            background-color: var(--primary-color);
            color: white;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 1rem;
            text-align: center;
        }

        .event-day {
            font-size: 2rem;
            font-weight: 700;
            line-height: 1;
        }

        .event-month {
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .event-details {
            padding: 1.5rem;
        }

        .event-details h3 {
            font-size: 1.3rem;
            color: var(--primary-color);
            margin-bottom: 0.5rem;
        }

        .event-time {
            display: flex;
            align-items: center;
            color: var(--secondary-color);
            font-weight: 500;
            margin-bottom: 0.5rem;
        }

        .event-time i {
            margin-right: 0.5rem;
        }

        .event-details p {
            color: var(--text-light);
            margin-bottom: 1rem;
        }

        /* Testimonials */
        .testimonials {
            background: linear-gradient(rgba(0, 0, 0, 0.8), rgba(0, 0, 0, 0.8)), 
                        url('https://images.unsplash.com/photo-1530035415911-95194de4ebcc?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            padding: 5rem 0;
            color: white;
            text-align: center;
        }

        .testimonials .section-title h2 {
            color: white;
        }

        .testimonials .section-title h2::after {
            background: var(--secondary-color);
        }

        .testimonial-slider {
            max-width: 800px;
            margin: 0 auto;
            position: relative;
        }

        .testimonial-item {
            padding: 2rem;
            display: none;
            animation: fadeIn 1s ease-in;
        }

        .testimonial-item.active {
            display: block;
        }

        .testimonial-text {
            font-size: 1.2rem;
            font-style: italic;
            margin-bottom: 1.5rem;
            position: relative;
        }

        .testimonial-text::before,
        .testimonial-text::after {
            content: '"';
            font-size: 3rem;
            color: var(--secondary-color);
            opacity: 0.3;
            position: absolute;
        }

        .testimonial-text::before {
            top: -1rem;
            left: -1.5rem;
        }

        .testimonial-text::after {
            bottom: -2rem;
            right: -1.5rem;
        }

        .testimonial-author {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-top: 2rem;
        }

        .author-img {
            width: 70px;
            height: 70px;
            border-radius: 50%;
            overflow: hidden;
            margin-right: 1rem;
            border: 3px solid var(--secondary-color);
        }

        .author-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .author-info h4 {
            font-size: 1.2rem;
            margin-bottom: 0.3rem;
        }

        .author-info p {
            font-size: 0.9rem;
            opacity: 0.8;
        }

        .testimonial-nav {
            margin-top: 2rem;
            display: flex;
            justify-content: center;
            gap: 1rem;
        }

        .testimonial-nav button {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            border: none;
            background: rgba(255, 255, 255, 0.3);
            cursor: pointer;
            transition: var(--transition);
        }

        .testimonial-nav button.active {
            background: var(--secondary-color);
        }

        /* Audio Grid Section */
        .audio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .audio-card {
            background-color: var(--card-bg);
            border-radius: var(--border-radius);
            padding: 1.5rem;
            box-shadow: var(--box-shadow);
            transition: var(--transition);
        }

        .audio-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--box-shadow-hover);
        }

        .audio-title {
            font-size: 1.2rem;
            color: var(--primary-color);
            margin-bottom: 0.5rem;
        }

        .audio-date {
            color: var(--text-light);
            font-size: 0.9rem;
            margin-bottom: 1rem;
        }

        .audio-player {
            width: 100%;
            margin-top: 1rem;
        }

        audio {
            width: 100%;
            border-radius: var(--border-radius);
        }

        /* Sermons Section */
        .sermons {
            display: none;
        }

        .sermons.active {
            display: block;
        }

        /* Audio Testimonies Section */
        .audio-testimonies {
            display: none;
        }

        .audio-testimonies.active {
            display: block;
        }

        /* Contact Section */
        .contact {
            background-color: var(--card-bg);
            border-radius: var(--border-radius);
            padding: 3rem;
            box-shadow: var(--box-shadow);
            margin-bottom: 3rem;
        }

        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .contact-info h3 {
            font-size: 1.5rem;
            color: var(--primary-color);
            margin-bottom: 1.5rem;
        }

        .contact-details {
            margin-bottom: 2rem;
        }

        .contact-item {
            display: flex;
            align-items: flex-start;
            margin-bottom: 1.5rem;
        }

        .contact-icon {
            font-size: 1.2rem;
            color: var(--secondary-color);
            margin-right: 1rem;
            margin-top: 0.3rem;
        }

        .contact-text h4 {
            font-size: 1.1rem;
            margin-bottom: 0.3rem;
        }

        .contact-text p, .contact-text a {
            color: var(--text-light);
        }

        .contact-text a:hover {
            color: var(--secondary-color);
        }

        .contact-form h3 {
            font-size: 1.5rem;
            color: var(--primary-color);
            margin-bottom: 1.5rem;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-control {
            width: 100%;
            padding: 0.8rem 1rem;
            border: 1px solid #ddd;
            border-radius: var(--border-radius);
            font-family: inherit;
            font-size: 1rem;
            transition: var(--transition);
            background-color: var(--bg-color);
            color: var(--text-color);
        }

        .form-control:focus {
            outline: none;
            border-color: var(--secondary-color);
            box-shadow: 0 0 0 3px rgba(212, 160, 23, 0.2);
        }

        textarea.form-control {
            min-height: 150px;
            resize: vertical;
        }

        .submit-btn {
            background-color: var(--secondary-color);
            color: #333;
            border: none;
            padding: 0.8rem 2rem;
            border-radius: 50px;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        .submit-btn:hover {
            background-color: var(--secondary-light);
            transform: translateY(-3px);
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
        }

        /* Prayer Request Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            z-index: 2000;
            overflow-y: auto;
        }

        .modal-content {
            background-color: var(--card-bg);
            margin: 5% auto;
            padding: 2rem;
            border-radius: var(--border-radius);
            width: 90%;
            max-width: 600px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            animation: modalFadeIn 0.3s;
        }

        @keyframes modalFadeIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }

        .modal-header h3 {
            color: var(--primary-color);
            font-size: 1.8rem;
        }

        .close-btn {
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--text-light);
            transition: var(--transition);
        }

        .close-btn:hover {
            color: var(--secondary-color);
            transform: rotate(90deg);
        }

        .file-upload {
            margin-bottom: 1.5rem;
        }

        .file-upload-label {
            display: block;
            margin-bottom: 0.5rem;
            color: var(--text-light);
            font-size: 0.9rem;
        }

        .file-upload-input {
            width: 100%;
        }

        .file-upload-note {
            font-size: 0.8rem;
            color: var(--text-light);
            font-style: italic;
            margin-top: 0.5rem;
        }

        /* Voice Recording */
        .voice-recording {
            margin-bottom: 1.5rem;
        }

        .recording-controls {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-top: 1rem;
        }

        .record-btn, .stop-btn {
            padding: 0.5rem 1rem;
            border: none;
            border-radius: var(--border-radius);
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
        }

        .record-btn {
            background-color: #dc3545;
            color: white;
        }

        .record-btn:hover {
            background-color: #c82333;
        }

        .stop-btn {
            background-color: var(--secondary-color);
            color: #333;
        }

        .stop-btn:hover {
            background-color: var(--secondary-light);
        }

        .recording-status {
            font-size: 0.9rem;
            color: var(--text-light);
            margin-top: 0.5rem;
        }

        .recording-timer {
            font-weight: 600;
            color: var(--primary-color);
        }

        /* Chat Modal */
        .chat-modal {
            display: none;
            position: fixed;
            bottom: 70px;
            right: 20px;
            width: 350px;
            max-width: 90%;
            background-color: var(--card-bg);
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow-hover);
            z-index: 1000;
            overflow: hidden;
        }

        .chat-header {
            background-color: var(--primary-color);
            color: white;
            padding: 1rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .chat-header h3 {
            margin: 0;
            font-size: 1.2rem;
        }

        .chat-close {
            background: none;
            border: none;
            color: white;
            font-size: 1.2rem;
            cursor: pointer;
        }

        .chat-body {
            padding: 1rem;
            height: 300px;
            overflow-y: auto;
        }

        .chat-message {
            margin-bottom: 1rem;
            padding: 0.8rem;
            border-radius: var(--border-radius);
            background-color: rgba(212, 160, 23, 0.1);
        }

        .chat-message.admin {
            background-color: rgba(58, 90, 120, 0.1);
        }

        .chat-input {
            display: flex;
            padding: 1rem;
            border-top: 1px solid #ddd;
        }

        .chat-input input {
            flex: 1;
            padding: 0.8rem;
            border: 1px solid #ddd;
            border-radius: var(--border-radius) 0 0 var(--border-radius);
            outline: none;
        }

        .chat-input button {
            padding: 0.8rem 1.2rem;
            background-color: var(--secondary-color);
            color: #333;
            border: none;
            border-radius: 0 var(--border-radius) var(--border-radius) 0;
            cursor: pointer;
        }

        /* Map */
        .map {
            height: 400px;
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: var(--box-shadow);
            margin-bottom: 3rem;
        }

        .map iframe {
            width: 100%;
            height: 100%;
            border: none;
        }

        /* Footer */
        footer {
            background-color: var(--footer-bg);
            color: var(--footer-text);
            padding: 4rem 0 2rem;
            position: absolute;
            bottom: 0;
            width: 100%;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .footer-column h3 {
            font-size: 1.3rem;
            color: var(--secondary-color);
            margin-bottom: 1.5rem;
            position: relative;
            padding-bottom: 0.5rem;
        }

        .footer-column h3::after {
            content: '';
            position: absolute;
            left: 0;
            bottom: 0;
            width: 50px;
            height: 2px;
            background: var(--secondary-color);
        }

        .footer-column p {
            margin-bottom: 1.5rem;
            color: var(--footer-text);
        }

        .footer-links li {
            margin-bottom: 0.8rem;
        }

        .footer-links a {
            color: var(--footer-text);
            transition: var(--transition);
            display: inline-block;
        }

        .footer-links a:hover {
            color: var(--secondary-color);
            transform: translateX(5px);
        }

        .footer-contact li {
            margin-bottom: 1rem;
            display: flex;
            align-items: flex-start;
        }

        .footer-contact i {
            color: var(--secondary-color);
            margin-right: 0.8rem;
            margin-top: 0.3rem;
        }

        .social-links {
            display: flex;
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .social-links a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.1);
            color: var(--footer-text);
            transition: var(--transition);
        }

        .social-links a:hover {
            background: var(--secondary-color);
            color: #333;
            transform: translateY(-3px);
        }

        .footer-bottom {
            text-align: center;
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        .footer-bottom p {
            color: var(--footer-text);
            font-size: 0.9rem;
        }

        /* Bottom Action Buttons */
        .bottom-actions {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            background-color: var(--nav-bg);
            display: flex;
            justify-content: space-around;
            padding: 10px 0;
            z-index: 999;
            box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.1);
        }

        .action-btn {
            display: flex;
            flex-direction: column;
            align-items: center;
            color: white;
            padding: 10px 15px;
            margin: 0 5px;
            border-radius: var(--border-radius);
            transition: var(--transition);
            font-size: 0.8rem;
        }

        .action-btn i {
            font-size: 1.2rem;
            margin-bottom: 5px;
        }

        .action-btn:hover {
            background-color: rgba(255, 255, 255, 0.1);
            transform: translateY(-3px);
        }

        /* Theme Switcher */
        .theme-switcher {
            position: fixed;
            top: 30px;
            right: 30px;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: var(--card-bg);
            color: var(--text-color);
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 1.2rem;
            box-shadow: var(--box-shadow);
            cursor: pointer;
            z-index: 100;
            transition: var(--transition);
        }

        .theme-switcher:hover {
            transform: scale(1.1);
            box-shadow: var(--box-shadow-hover);
        }

        /* Back to Top Button */
        .back-to-top {
            position: fixed;
            bottom: 70px;
            right: 30px;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: var(--secondary-color);
            color: #333;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 1.2rem;
            box-shadow: var(--box-shadow);
            cursor: pointer;
            z-index: 99;
            opacity: 0;
            visibility: hidden;
            transition: var(--transition);
        }

        .back-to-top.active {
            opacity: 1;
            visibility: visible;
        }

        .back-to-top:hover {
            background-color: var(--secondary-light);
            transform: translateY(-3px);
        }

        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Responsive Design */
        @media (max-width: 992px) {
            .about {
                grid-template-columns: 1fr;
            }
            
            .slider-container {
                order: -1;
                height: 350px;
            }
        }

        @media (max-width: 768px) {
            .header-container {
                flex-direction: column;
                text-align: center;
            }
            
            .logo {
                margin-bottom: 1rem;
            }
            
            .nav-toggle {
                display: block;
                position: absolute;
                top: 30px;
                right: 20px;
            }
            
            nav {
                display: none;
                width: 100%;
                margin-top: 1rem;
            }
            
            nav.active {
                display: block;
            }
            
            nav ul {
                flex-direction: column;
                gap: 0.5rem;
            }
            
            nav ul li a {
                display: block;
                padding: 0.8rem;
            }
            
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .hero p {
                font-size: 1.1rem;
            }
            
            .section-padding {
                padding: 3rem 0;
            }
            
            .section-title h2 {
                font-size: 2rem;
            }

            .bottom-actions {
                justify-content: space-around;
            }

            .action-btn {
                margin: 0;
                padding: 8px 10px;
                font-size: 0.7rem;
            }

            .action-btn i {
                font-size: 1rem;
            }

            .modal-content {
                margin: 10% auto;
                width: 95%;
            }

            .chat-modal {
                width: 300px;
                right: 10px;
            }
        }

        @media (max-width: 576px) {
            .hero h1 {
                font-size: 2rem;
            }
            
            .btn-group {
                display: flex;
                flex-direction: column;
                gap: 1rem;
            }
            
            .btn-outline {
                margin-left: 0;
            }
            
            .services {
                grid-template-columns: 1fr;
            }
            
            .event-list {
                grid-template-columns: 1fr;
            }
            
            .event-card {
                grid-template-columns: 1fr;
            }
            
            .event-date {
                padding: 0.5rem;
                flex-direction: row;
                justify-content: center;
                gap: 1rem;
            }
            
            .event-day, .event-month {
                display: inline-block;
            }

            .bottom-actions {
                padding: 8px 0;
            }

            .action-btn {
                padding: 5px 8px;
            }

            .action-btn i {
                font-size: 0.9rem;
                margin-bottom: 3px;
            }

            .action-btn span {
                font-size: 0.6rem;
            }

            .slider-container {
                height: 250px;
            }

            .chat-modal {
                width: 280px;
                bottom: 60px;
            }
        }
    </style>
</head>
<body>
    <!-- Theme Switcher -->
    <div class="theme-switcher" id="themeSwitcher">
        <i class="fas fa-moon"></i>
    </div>

    <!-- Header -->
    <header>
        <div class="container header-container">
            <a href="#" class="logo">Arena of <span>Grace</span></a>
            
            <button class="nav-toggle" id="navToggle">
                <i class="fas fa-bars"></i>
            </button>
            
            <nav id="mainNav">
                <ul>
                    <li><a href="#home" class="active">Home</a></li>
                    <li><a href="#about">About</a></li>
                    <li><a href="#services">Services</a></li>
                    <li><a href="#events">Events</a></li>
                    <li><a href="#testimonials">Testimonies</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="hero-content">
            <h1>Experience God's Grace & Power</h1>
            <p>Join our vibrant community where lives are transformed through faith, worship, and the power of the Holy Spirit.</p>
            <div class="btn-group">
                <a href="https://example.com/join-us" target="_blank" class="btn">Join Us This Sunday</a>
                <button class="btn btn-outline" id="prayerRequestBtn">Ka kyer3 Nyame</button>
            </div>
        </div>
    </section>

    <!-- Main Content -->
    <main>
        <!-- About Section -->
        <section class="section-padding" id="about">
            <div class="container">
                <div class="section-title">
                    <h2>About Our Church</h2>
                </div>
                
                <div class="about">
                    <div class="about-content">
                        <p>Arena of Grace and Testimonies is a dynamic, Spirit-filled church committed to making disciples of all nations. Founded in 2010 by Pastor John and Sarah Williams, we've grown from a small Bible study group to a thriving congregation impacting our city and beyond.</p>
                        <p>Our vision is to create a community where people encounter God's grace, experience life-changing testimonies, and are equipped to fulfill their divine purpose. We believe in the power of prayer, the authority of Scripture, and the transformative work of the Holy Spirit.</p>
                        <p>Whether you're exploring faith or looking to deepen your relationship with Christ, you'll find a welcoming family here at Arena of Grace.</p>
                        
                        <div class="about-stats">
                            <div class="stat-item">
                                <div class="stat-number">12</div>
                                <div class="stat-label">Years Serving</div>
                            </div>
                            <div class="stat-item">
                                <div class="stat-number">500+</div>
                                <div class="stat-label">Members</div>
                            </div>
                            <div class="stat-item">
                                <div class="stat-number">15</div>
                                <div class="stat-label">Ministries</div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="slider-container">
                        <div class="slider">
                            <img src="https://images.unsplash.com/photo-1542401886-65d6c61db217?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80" alt="Church service">
                            <img src="https://images.unsplash.com/photo-1529107386315-e1a2ed48a620?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80" alt="Youth worship">
                            <img src="https://images.unsplash.com/photo-1434030216411-0b793f4b4173?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80" alt="Bible study">
                            <img src="https://images.unsplash.com/photo-1506126613408-eca07ce68773?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80" alt="Prayer meeting">
                            <img src="https://images.unsplash.com/photo-1530035415911-95194de4ebcc?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80" alt="Church community">
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Services Section -->
        <section class="section-padding" id="services">
            <div class="container">
                <div class="section-title">
                    <h2>Our Services</h2>
                    <p>Join us for powerful worship and life-changing messages</p>
                </div>
                
                <div class="services">
                    <div class="service-card">
                        <img src="https://images.unsplash.com/photo-1434030216411-0b793f4b4173?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80" alt="Sunday Service">
                        <div class="service-content">
                            <div class="service-icon">
                                <i class="fas fa-church"></i>
                            </div>
                            <h3>Sunday Worship</h3>
                            <p>Experience the presence of God through anointed worship and practical Bible teaching that transforms lives.</p>
                            <p><strong>Time:</strong> 9:00 AM & 11:30 AM</p>
                            <p><strong>Location:</strong> Main Sanctuary</p>
                        </div>
                    </div>
                    
                    <div class="service-card">
                        <img src="https://images.unsplash.com/photo-1506126613408-eca07ce68773?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80" alt="Bible Study">
                        <div class="service-content">
                            <div class="service-icon">
                                <i class="fas fa-bible"></i>
                            </div>
                            <h3>Wednesday Bible Study</h3>
                            <p>Deepen your understanding of Scripture and grow in your faith through interactive Bible study and prayer.</p>
                            <p><strong>Time:</strong> 6:30 PM</p>
                            <p><strong>Location:</strong> Fellowship Hall</p>
                        </div>
                    </div>
                    
                    <div class="service-card">
                        <img src="https://images.unsplash.com/photo-1529107386315-e1a2ed48a620?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80" alt="Youth Service">
                        <div class="service-content">
                            <div class="service-icon">
                                <i class="fas fa-fire"></i>
                            </div>
                            <h3>Youth Service</h3>
                            <p>A dynamic gathering for teens and young adults with relevant teaching, worship, and community.</p>
                            <p><strong>Time:</strong> Friday at 7:00 PM</p>
                            <p><strong>Location:</strong> Youth Center</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Sermons Section -->
        <section class="section-padding sermons" id="sermons">
            <div class="container">
                <div class="section-title">
                    <h2>Recent Sermons</h2>
                    <p>Listen to our powerful messages</p>
                </div>
                
                <div class="audio-grid">
                    <div class="audio-card">
                        <h3 class="audio-title">The Power of Faith</h3>
                        <p class="audio-date">June 5, 2023</p>
                        <audio controls class="audio-player">
                            <source src="https://example.com/audio/sermon1.mp3" type="audio/mpeg">
                            Your browser does not support the audio element.
                        </audio>
                    </div>
                    
                    <div class="audio-card">
                        <h3 class="audio-title">Walking in Grace</h3>
                        <p class="audio-date">May 29, 2023</p>
                        <audio controls class="audio-player">
                            <source src="https://example.com/audio/sermon2.mp3" type="audio/mpeg">
                            Your browser does not support the audio element.
                        </audio>
                    </div>
                    
                    <div class="audio-card">
                        <h3 class="audio-title">Overcoming Trials</h3>
                        <p class="audio-date">May 22, 2023</p>
                        <audio controls class="audio-player">
                            <source src="https://example.com/audio/sermon3.mp3" type="audio/mpeg">
                            Your browser does not support the audio element.
                        </audio>
                    </div>
                    
                    <div class="audio-card">
                        <h3 class="audio-title">The Love of God</h3>
                        <p class="audio-date">May 15, 2023</p>
                        <audio controls class="audio-player">
                            <source src="https://example.com/audio/sermon4.mp3" type="audio/mpeg">
                            Your browser does not support the audio element.
                        </audio>
                    </div>
                </div>
            </div>
        </section>

        <!-- Events Section -->
        <section class="section-padding" id="events">
            <div class="container">
                <div class="section-title">
                    <h2>Upcoming Events</h2>
                    <p>Join us for these special gatherings</p>
                </div>
                
                <div class="event-list">
                    <div class="event-card">
                        <div class="event-date">
                            <div class="event-day">15</div>
                            <div class="event-month">June</div>
                        </div>
                        <div class="event-details">
                            <h3>Annual Prayer Conference</h3>
                            <div class="event-time">
                                <i class="far fa-clock"></i> June 15-17, 2023 | 6:00 PM
                            </div>
                            <p>A weekend of powerful prayer sessions, worship, and teaching on the power of prayer to transform lives and communities.</p>
                            <a href="#" class="btn">Register Now</a>
                        </div>
                    </div>
                    
                    <div class="event-card">
                        <div class="event-date">
                            <div class="event-day">08</div>
                            <div class="event-month">July</div>
                        </div>
                        <div class="event-details">
                            <h3>Community Outreach</h3>
                            <div class="event-time">
                                <i class="far fa-clock"></i> July 8, 2023 | 9:00 AM
                            </div>
                            <p>Join us as we serve our community with food, clothing, medical checkups, and most importantly, the love of Christ.</p>
                            <a href="#" class="btn">Volunteer</a>
                        </div>
                    </div>
                    
                    <div class="event-card">
                        <div class="event-date">
                            <div class="event-day">20</div>
                            <div class="event-month">Aug</div>
                        </div>
                        <div class="event-details">
                            <h3>Baptism Service</h3>
                            <div class="event-time">
                                <i class="far fa-clock"></i> August 20, 2023 | 2:00 PM
                            </div>
                            <p>Celebrate new life in Christ as we baptize new believers at the river. Open to all who want to take this step of faith.</p>
                            <a href="#" class="btn">Sign Up</a>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Testimonials Section -->
        <section class="testimonials" id="testimonials">
            <div class="container">
                <div class="section-title">
                    <h2>Transformed Lives</h2>
                    <p>Hear what God is doing in our community</p>
                </div>
                
                <div class="testimonial-slider">
                    <div class="testimonial-item active">
                        <div class="testimonial-text">
                            Arena of Grace has completely transformed my life. When I first walked through those doors, I was broken and lost. Through the love of this community and the power of God's Word, I've found healing, purpose, and a new life in Christ.
                        </div>
                        <div class="testimonial-author">
                            <div class="author-img">
                                <img src="https://randomuser.me/api/portraits/women/32.jpg" alt="Sarah Johnson">
                            </div>
                            <div class="author-info">
                                <h4>Sarah Johnson</h4>
                                <p>Member since 2018</p>
                            </div>
                        </div>
                    </div>
                    
                    <div class="testimonial-item">
                        <div class="testimonial-text">
                            The Wednesday Bible study has deepened my understanding of Scripture in ways I never imagined. I've grown so much spiritually in the past year, and it's all thanks to the faithful teaching and supportive community at Arena of Grace.
                        </div>
                        <div class="testimonial-author">
                            <div class="author-img">
                                <img src="https://randomuser.me/api/portraits/men/45.jpg" alt="Michael Thompson">
                            </div>
                            <div class="author-info">
                                <h4>Michael Thompson</h4>
                                <p>Member since 2020</p>
                            </div>
                        </div>
                    </div>
                    
                    <div class="testimonial-item">
                        <div class="testimonial-text">
                            Our family was going through a very difficult season when we found Arena of Grace. The prayers and support we received carried us through. Now we're serving in the children's ministry to help other families experience God's love.
                        </div>
                        <div class="testimonial-author">
                            <div class="author-img">
                                <img src="https://randomuser.me/api/portraits/women/68.jpg" alt="The Rodriguez Family">
                            </div>
                            <div class="author-info">
                                <h4>The Rodriguez Family</h4>
                                <p>Members since 2019</p>
                            </div>
                        </div>
                    </div>
                    
                    <div class="testimonial-nav">
                        <button class="active"></button>
                        <button></button>
                        <button></button>
                    </div>
                </div>
            </div>
        </section>

        <!-- Audio Testimonies Section -->
        <section class="section-padding audio-testimonies" id="audio-testimonies">
            <div class="container">
                <div class="section-title">
                    <h2>Audio Testimonies</h2>
                    <p>Hear powerful testimonies from our members</p>
                </div>
                
                <div class="audio-grid">
                    <div class="audio-card">
                        <h3 class="audio-title">Healing from Chronic Illness</h3>
                        <p class="audio-date">June 1, 2023</p>
                        <audio controls class="audio-player">
                            <source src="https://example.com/audio/testimony1.mp3" type="audio/mpeg">
                            Your browser does not support the audio element.
                        </audio>
                    </div>
                    
                    <div class="audio-card">
                        <h3 class="audio-title">Deliverance from Addiction</h3>
                        <p class="audio-date">May 25, 2023</p>
                        <audio controls class="audio-player">
                            <source src="https://example.com/audio/testimony2.mp3" type="audio/mpeg">
                            Your browser does not support the audio element.
                        </audio>
                    </div>
                    
                    <div class="audio-card">
                        <h3 class="audio-title">Financial Breakthrough</h3>
                        <p class="audio-date">May 18, 2023</p>
                        <audio controls class="audio-player">
                            <source src="https://example.com/audio/testimony3.mp3" type="audio/mpeg">
                            Your browser does not support the audio element.
                        </audio>
                    </div>
                    
                    <div class="audio-card">
                        <h3 class="audio-title">Restored Marriage</h3>
                        <p class="audio-date">May 11, 2023</p>
                        <audio controls class="audio-player">
                            <source src="https://example.com/audio/testimony4.mp3" type="audio/mpeg">
                            Your browser does not support the audio element.
                        </audio>
                    </div>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section class="section-padding" id="contact">
            <div class="container">
                <div class="section-title">
                    <h2>Contact Us</h2>
                    <p>We'd love to hear from you</p>
                </div>
                
                <div class="contact">
                    <div class="contact-grid">
                        <div class="contact-info">
                            <h3>Get In Touch</h3>
                            <div class="contact-details">
                                <div class="contact-item">
                                    <div class="contact-icon">
                                        <i class="fas fa-map-marker-alt"></i>
                                    </div>
                                    <div class="contact-text">
                                        <h4>Address</h4>
                                        <p>123 Grace Avenue<br>Faith City, FC 12345</p>
                                    </div>
                                </div>
                                
                                <div class="contact-item">
                                    <div class="contact-icon">
                                        <i class="fas fa-phone-alt"></i>
                                    </div>
                                    <div class="contact-text">
                                        <h4>Phone</h4>
                                        <p>(123) 456-7890</p>
                                    </div>
                                </div>
                                
                                <div class="contact-item">
                                    <div class="contact-icon">
                                        <i class="fas fa-envelope"></i>
                                    </div>
                                    <div class="contact-text">
                                        <h4>Email</h4>
                                        <a href="mailto:info@arenaofgrace.org">info@arenaofgrace.org</a>
                                    </div>
                                </div>
                                
                                <div class="contact-item">
                                    <div class="contact-icon">
                                        <i class="fas fa-clock"></i>
                                    </div>
                                    <div class="contact-text">
                                        <h4>Office Hours</h4>
                                        <p>Monday-Friday: 9am-5pm<br>Saturday: 10am-2pm</p>
                                    </div>
                                </div>
                            </div>
                            
                            <div class="social-links">
                                <a href="#"><i class="fab fa-facebook-f"></i></a>
                                <a href="#"><i class="fab fa-twitter"></i></a>
                                <a href="#"><i class="fab fa-instagram"></i></a>
                                <a href="#"><i class="fab fa-youtube"></i></a>
                            </div>
                        </div>
                        
                        <div class="contact-form">
                            <h3>Send Us a Message</h3>
                            <form id="contactForm">
                                <div class="form-group">
                                    <input type="text" class="form-control" placeholder="Your Name" required>
                                </div>
                                <div class="form-group">
                                    <input type="email" class="form-control" placeholder="Your Email" required>
                                </div>
                                <div class="form-group">
                                    <input type="text" class="form-control" placeholder="Subject">
                                </div>
                                <div class="form-group">
                                    <textarea class="form-control" placeholder="Your Message" required></textarea>
                                </div>
                                <button type="submit" class="submit-btn">Send Message</button>
                            </form>
                        </div>
                    </div>
                </div>
                
                <div class="map">
                    <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3022.215209179035!2d-73.9878449242667!3d40.74844097138948!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zNDDCsDQ0JzU0LjQiTiA3M8KwNTknMTAuNyJX!5e0!3m2!1sen!2sus!4v1620000000000!5m2!1sen!2sus" allowfullscreen="" loading="lazy"></iframe>
                </div>
            </div>
        </section>
    </main>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>About Us</h3>
                    <p>Arena of Grace and Testimonies is a vibrant Christian community committed to making disciples, transforming lives, and impacting our world with the love of Christ.</p>
                    <div class="social-links">
                        <a href="#"><i class="fab fa-facebook-f"></i></a>
                        <a href="#"><i class="fab fa-twitter"></i></a>
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fab fa-youtube"></i></a>
                    </div>
                </div>
                
                <div class="footer-column">
                    <h3>Quick Links</h3>
                    <ul class="footer-links">
                        <li><a href="#home">Home</a></li>
                        <li><a href="#about">About Us</a></li>
                        <li><a href="#services">Services</a></li>
                        <li><a href="#events">Events</a></li>
                        <li><a href="#testimonials">Testimonies</a></li>
                        <li><a href="#contact">Contact</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Ministries</h3>
                    <ul class="footer-links">
                        <li><a href="#">Children's Ministry</a></li>
                        <li><a href="#">Youth Ministry</a></li>
                        <li><a href="#">Women's Fellowship</a></li>
                        <li><a href="#">Men's Fellowship</a></li>
                        <li><a href="#">Prayer Ministry</a></li>
                        <li><a href="#">Missions</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Contact Info</h3>
                    <ul class="footer-contact">
                        <li>
                            <i class="fas fa-map-marker-alt"></i>
                            <span>123 Grace Avenue, Faith City, FC 12345</span>
                        </li>
                        <li>
                            <i class="fas fa-phone-alt"></i>
                            <span>(123) 456-7890</span>
                        </li>
                        <li>
                            <i class="fas fa-envelope"></i>
                            <span>info@arenaofgrace.org</span>
                        </li>
                        <li>
                            <i class="fas fa-clock"></i>
                            <span>Sunday Services: 9am & 11:30am</span>
                        </li>
                    </ul>
                </div>
            </div>
            
            <div class="footer-bottom">
                <p>&copy; 2023 Arena of Grace and Testimonies. All Rights Reserved.</p>
            </div>
        </div>
    </footer>

    <!-- Bottom Action Buttons -->
    <div class="bottom-actions">
        <a href="#" class="action-btn" id="sermonsBtn">
            <i class="fas fa-podcast"></i>
            <span>Sermons</span>
        </a>
        <a href="#" class="action-btn" id="testimoniesBtn">
            <i class="fas fa-heart"></i>
            <span>Testimonies</span>
        </a>
        <a href="#" class="action-btn" id="donateBtn">
            <i class="fas fa-hand-holding-heart"></i>
            <span>Donate</span>
        </a>
        <a href="#" class="action-btn" id="chatBtn">
            <i class="fas fa-comments"></i>
            <span>Chat</span>
        </a>
    </div>

    <!-- Prayer Request Modal -->
    <div class="modal" id="prayerRequestModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Ka kyer3 Nyame (Tell God)</h3>
                <span class="close-btn" id="closeModal">&times;</span>
            </div>
            <form action="https://formspree.io/f/YOUR_FORMSPREE_ID" method="POST" enctype="multipart/form-data" id="prayerForm">
                <div class="form-group">
                    <label for="name">Name</label>
                    <input type="text" id="name" name="name" class="form-control" required>
                </div>
                <div class="form-group">
                    <label for="location">Location</label>
                    <select id="location" name="location" class="form-control" required>
                        <option value="">Select Country</option>
                        <option value="Ghana">Ghana</option>
                        <option value="Nigeria">Nigeria</option>
                        <option value="USA">United States</option>
                        <option value="UK">United Kingdom</option>
                        <option value="Canada">Canada</option>
                        <option value="South Africa">South Africa</option>
                        <option value="Other">Other</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="prayer">Prayer Request</label>
                    <textarea id="prayer" name="prayer" class="form-control" required></textarea>
                </div>
                
                <!-- Voice Recording Section -->
                <div class="voice-recording">
                    <label class="file-upload-label">Voice Recording (Optional)</label>
                    <div class="recording-controls">
                        <button type="button" id="recordBtn" class="record-btn">
                            <i class="fas fa-microphone"></i> Record
                        </button>
                        <button type="button" id="stopBtn" class="stop-btn" disabled>
                            <i class="fas fa-stop"></i> Stop
                        </button>
                    </div>
                    <div class="recording-status">
                        Status: <span id="recordingStatus">Ready to record</span>
                        <span id="recordingTimer" class="recording-timer"></span>
                    </div>
                    <audio id="audioPlayback" controls style="display: none; width: 100%; margin-top: 1rem;"></audio>
                    <input type="hidden" id="audioData" name="audio_data">
                </div>
                
                <div class="file-upload">
                    <label class="file-upload-label">Attachment (Optional)</label>
                    <input type="file" id="attachment" name="attachment" class="file-upload-input">
                    <p class="file-upload-note">Add a screenshot of offerings/seeds if any</p>
                </div>
                <button type="submit" class="submit-btn">Submit Prayer Request</button>
            </form>
        </div>
    </div>

    <!-- Chat Modal -->
    <div class="chat-modal" id="chatModal">
        <div class="chat-header">
            <h3>Live Chat</h3>
            <button class="chat-close" id="chatClose">&times;</button>
        </div>
        <div class="chat-body" id="chatBody">
            <div class="chat-message admin">
                <p>Hello! Welcome to Arena of Grace. How can we pray for you today?</p>
            </div>
        </div>
        <div class="chat-input">
            <input type="text" id="chatInput" placeholder="Type your message...">
            <button id="chatSend"><i class="fas fa-paper-plane"></i></button>
        </div>
    </div>

    <!-- Back to Top Button -->
    <div class="back-to-top" id="backToTop">
        <i class="fas fa-arrow-up"></i>
    </div>

    <script>
        // Theme Switcher Functionality
        const themeSwitcher = document.getElementById('themeSwitcher');
        const icon = themeSwitcher.querySelector('i');
        
        // Check for saved theme preference or use preferred color scheme
        const savedTheme = localStorage.getItem('theme') || 
                          (window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light');
        
        if (savedTheme === 'dark') {
            document.body.classList.add('dark-theme');
            icon.classList.remove('fa-moon');
            icon.classList.add('fa-sun');
        }
        
        themeSwitcher.addEventListener('click', () => {
            document.body.classList.toggle('dark-theme');
            
            if (document.body.classList.contains('dark-theme')) {
                icon.classList.remove('fa-moon');
                icon.classList.add('fa-sun');
                localStorage.setItem('theme', 'dark');
            } else {
                icon.classList.remove('fa-sun');
                icon.classList.add('fa-moon');
                localStorage.setItem('theme', 'light');
            }
        });

        // Mobile Navigation Toggle
        const navToggle = document.getElementById('navToggle');
        const mainNav = document.getElementById('mainNav');
        
        navToggle.addEventListener('click', () => {
            mainNav.classList.toggle('active');
        });
        
        // Close mobile menu when clicking on a link
        document.querySelectorAll('#mainNav a').forEach(link => {
            link.addEventListener('click', () => {
                mainNav.classList.remove('active');
            });
        });

        // Smooth scrolling for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                }
            });
        });

        // Sticky header on scroll
        window.addEventListener('scroll', () => {
            const header = document.querySelector('header');
            header.classList.toggle('sticky', window.scrollY > 0);
        });

        // Testimonial slider
        const testimonialItems = document.querySelectorAll('.testimonial-item');
        const testimonialNav = document.querySelectorAll('.testimonial-nav button');
        let currentTestimonial = 0;
        
        function showTestimonial(index) {
            testimonialItems.forEach(item => item.classList.remove('active'));
            testimonialNav.forEach(btn => btn.classList.remove('active'));
            
            testimonialItems[index].classList.add('active');
            testimonialNav[index].classList.add('active');
            currentTestimonial = index;
        }
        
        testimonialNav.forEach((btn, index) => {
            btn.addEventListener('click', () => {
                showTestimonial(index);
            });
        });
        
        // Auto-rotate testimonials
        setInterval(() => {
            let nextTestimonial = currentTestimonial + 1;
            if (nextTestimonial >= testimonialItems.length) {
                nextTestimonial = 0;
            }
            showTestimonial(nextTestimonial);
        }, 5000);

        // Back to top button
        const backToTop = document.getElementById('backToTop');
        
        window.addEventListener('scroll', () => {
            if (window.pageYOffset > 300) {
                backToTop.classList.add('active');
            } else {
                backToTop.classList.remove('active');
            }
        });
        
        backToTop.addEventListener('click', () => {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        });

        // Prayer Request Modal
        const prayerRequestBtn = document.getElementById('prayerRequestBtn');
        const prayerRequestModal = document.getElementById('prayerRequestModal');
        const closeModal = document.getElementById('closeModal');
        
        prayerRequestBtn.addEventListener('click', () => {
            prayerRequestModal.style.display = 'block';
            document.body.style.overflow = 'hidden';
        });
        
        closeModal.addEventListener('click', () => {
            prayerRequestModal.style.display = 'none';
            document.body.style.overflow = 'auto';
        });
        
        window.addEventListener('click', (e) => {
            if (e.target === prayerRequestModal) {
                prayerRequestModal.style.display = 'none';
                document.body.style.overflow = 'auto';
            }
        });

        // Donate button functionality
        const donateBtn = document.getElementById('donateBtn');
        donateBtn.addEventListener('click', (e) => {
            e.preventDefault();
            alert('Thank you for your willingness to give! Our online donation portal will open in a new window.');
            // In a real implementation, you would link to your donation page
            // window.open('https://yourdonationportal.com', '_blank');
        });

        // Form submission
        const contactForm = document.getElementById('contactForm');
        contactForm.addEventListener('submit', (e) => {
            e.preventDefault();
            alert('Thank you for your message! We will get back to you soon.');
            contactForm.reset();
        });

        // Sermons and Testimonies buttons functionality
        const sermonsBtn = document.getElementById('sermonsBtn');
        const testimoniesBtn = document.getElementById('testimoniesBtn');
        const sermonsSection = document.querySelector('.sermons');
        const testimoniesSection = document.querySelector('.audio-testimonies');
        
        sermonsBtn.addEventListener('click', (e) => {
            e.preventDefault();
            // Hide testimonies section if it's visible
            testimoniesSection.classList.remove('active');
            // Toggle sermons section
            sermonsSection.classList.toggle('active');
            
            // Scroll to sermons section
            if (sermonsSection.classList.contains('active')) {
                window.scrollTo({
                    top: sermonsSection.offsetTop - 80,
                    behavior: 'smooth'
                });
            }
        });
        
        testimoniesBtn.addEventListener('click', (e) => {
            e.preventDefault();
            // Hide sermons section if it's visible
            sermonsSection.classList.remove('active');
            // Toggle testimonies section
            testimoniesSection.classList.toggle('active');
            
            // Scroll to testimonies section
            if (testimoniesSection.classList.contains('active')) {
                window.scrollTo({
                    top: testimoniesSection.offsetTop - 80,
                    behavior: 'smooth'
                });
            }
        });

        // Chat functionality
        const chatBtn = document.getElementById('chatBtn');
        const chatModal = document.getElementById('chatModal');
        const chatClose = document.getElementById('chatClose');
        const chatBody = document.getElementById('chatBody');
        const chatInput = document.getElementById('chatInput');
        const chatSend = document.getElementById('chatSend');
        
        chatBtn.addEventListener('click', (e) => {
            e.preventDefault();
            chatModal.style.display = 'block';
        });
        
        chatClose.addEventListener('click', () => {
            chatModal.style.display = 'none';
        });
        
        chatSend.addEventListener('click', sendMessage);
        chatInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                sendMessage();
            }
        });
        
        function sendMessage() {
            const message = chatInput.value.trim();
            if (message) {
                // Add user message
                addMessage(message, 'user');
                chatInput.value = '';
                
                // Simulate admin response after a delay
                setTimeout(() => {
                    const responses = [
                        "We're praying for you. God is faithful!",
                        "Thank you for sharing. The Lord hears your prayers.",
                        "We'll bring this before the Lord in our prayer meeting.",
                        "Is there anything specific you'd like us to pray about?",
                        "May God's peace be with you in this situation."
                    ];
                    const randomResponse = responses[Math.floor(Math.random() * responses.length)];
                    addMessage(randomResponse, 'admin');
                }, 1000);
            }
        }
        
        function addMessage(text, sender) {
            const messageDiv = document.createElement('div');
            messageDiv.className = `chat-message ${sender}`;
            messageDiv.innerHTML = `<p>${text}</p>`;
            chatBody.appendChild(messageDiv);
            chatBody.scrollTop = chatBody.scrollHeight;
        }

        // Voice recording functionality for prayer form
        const recordBtn = document.getElementById('recordBtn');
        const stopBtn = document.getElementById('stopBtn');
        const recordingStatus = document.getElementById('recordingStatus');
        const recordingTimer = document.getElementById('recordingTimer');
        const audioPlayback = document.getElementById('audioPlayback');
        const audioData = document.getElementById('audioData');
        const prayerForm = document.getElementById('prayerForm');
        
        let mediaRecorder;
        let audioChunks = [];
        let startTime;
        let timerInterval;
        
        recordBtn.addEventListener('click', startRecording);
        stopBtn.addEventListener('click', stopRecording);
        
        async function startRecording() {
            try {
                const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
                mediaRecorder = new MediaRecorder(stream);
                
                mediaRecorder.ondataavailable = event => {
                    audioChunks.push(event.data);
                };
                
                mediaRecorder.onstop = () => {
                    const audioBlob = new Blob(audioChunks, { type: 'audio/wav' });
                    const audioUrl = URL.createObjectURL(audioBlob);
                    audioPlayback.src = audioUrl;
                    audioPlayback.style.display = 'block';
                    
                    // Convert blob to base64 for form submission
                    const reader = new FileReader();
                    reader.readAsDataURL(audioBlob);
                    reader.onloadend = () => {
                        audioData.value = reader.result;
                    };
                };
                
                audioChunks = [];
                mediaRecorder.start();
                recordBtn.disabled = true;
                stopBtn.disabled = false;
                recordingStatus.textContent = 'Recording...';
                
                // Start timer
                startTime = Date.now();
                timerInterval = setInterval(updateTimer, 1000);
                
            } catch (error) {
                console.error('Error accessing microphone:', error);
                recordingStatus.textContent = 'Error accessing microphone';
            }
        }
        
        function stopRecording() {
            if (mediaRecorder && mediaRecorder.state !== 'inactive') {
                mediaRecorder.stop();
                mediaRecorder.stream.getTracks().forEach(track => track.stop());
                
                recordBtn.disabled = false;
                stopBtn.disabled = true;
                recordingStatus.textContent = 'Recording complete';
                
                // Stop timer
                clearInterval(timerInterval);
            }
        }
        
        function updateTimer() {
            const elapsedTime = Math.floor((Date.now() - startTime) / 1000);
            const minutes = Math.floor(elapsedTime / 60).toString().padStart(2, '0');
            const seconds = (elapsedTime % 60).toString().padStart(2, '0');
            recordingTimer.textContent = `${minutes}:${seconds}`;
        }
        
        // Form submission handler for prayer form
        prayerForm.addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Here you would typically send the form data to your server
            // For demo purposes, we'll just show an alert
            alert('Your prayer request has been submitted. We will pray for you!');
            prayerForm.reset();
            audioPlayback.style.display = 'none';
            audioPlayback.src = '';
            audioData.value = '';
            recordingTimer.textContent = '';
            prayerRequestModal.style.display = 'none';
            document.body.style.overflow = 'auto';
        });

        // Animation on scroll
        function animateOnScroll() {
            const elements = document.querySelectorAll('.service-card, .slider-container, .event-card');
            
            elements.forEach(element => {
                const elementPosition = element.getBoundingClientRect().top;
                const screenPosition = window.innerHeight / 1.3;
                
                if (elementPosition < screenPosition) {
                    element.style.animation = 'fadeInUp 1s ease-out forwards';
                }
            });
        }
        
        window.addEventListener('scroll', animateOnScroll);
        window.addEventListener('load', animateOnScroll);
    </script>
</body>
</html>
