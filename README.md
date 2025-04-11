<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SwiftCard</title>
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
  <script src="https://kit.fontawesome.com/334e9957b6.js" crossorigin="anonymous"></script>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300&display=swap" rel="stylesheet">
  <script src="https://unpkg.com/sweetalert/dist/sweetalert.min.js"></script>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    /* Advanced Christian-themed Loader with Blurred Background */
    .loader {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      z-index: 1000;
      animation: fadeOut 0.9s 9s forwards;
      background-color: rgba(0,0,0,0.5);
      backdrop-filter: blur(10px);
      -webkit-backdrop-filter: blur(10px);
    }

    .loader-content {
      position: relative;
      width: 200px;
      height: 200px;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .halo {
      position: absolute;
      width: 180px;
      height: 180px;
      border-radius: 50%;
      border: 3px solid transparent;
      border-top: 3px solid rgba(255,215,0,0.8);
      border-bottom: 3px solid rgba(255,215,0,0.8);
      animation: spinHalo 3s linear infinite;
      filter: drop-shadow(0 0 10px gold);
    }

    .halo:nth-child(2) {
      width: 150px;
      height: 150px;
      border-top: 3px solid rgba(255,69,0,0.8);
      border-bottom: 3px solid rgba(255,69,0,0.8);
      animation-direction: reverse;
      filter: drop-shadow(0 0 10px orange);
    }

    .halo:nth-child(3) {
      width: 120px;
      height: 120px;
      border-top: 3px solid rgba(75,0,130,0.8);
      border-bottom: 3px solid rgba(75,0,130,0.8);
      filter: drop-shadow(0 0 10px indigo);
    }

    .cross-loader {
      position: relative;
      width: 80px;
      height: 80px;
      animation: pulseCross 4s ease-in-out infinite;
    }

    .cross-loader:before, .cross-loader:after {
      content: '';
      position: absolute;
      background: white;
      box-shadow: 0 0 15px rgba(255,255,255,0.8);
      border-radius: 5px;
    }

    .cross-loader:before {
      width: 15px;
      height: 80px;
      left: 32.5px;
      top: 0;
      background: linear-gradient(to bottom, gold, orange);
    }

    .cross-loader:after {
      width: 80px;
      height: 15px;
      left: 0;
      top: 32.5px;
      background: linear-gradient(to right, gold, orange);
    }

    .loader-text {
      font-size: 1.5rem;
      font-weight: bold;
      color: white;
      margin-top: 30px;
      text-align: center;
      text-shadow: 0 0 10px rgba(255,255,255,0.8);
      animation: textGlow 4s infinite alternate;
    }

    .bible-verse {
      font-size: 1rem;
      color: white;
      margin-top: 20px;
      font-style: italic;
      max-width: 80%;
      text-align: center;
      opacity: 0;
      animation: fadeIn 2s 4s forwards;
      text-shadow: 0 0 5px rgba(255,255,255,0.5);
    }

    .progress-bar {
      width: 200px;
      height: 5px;
      background: rgba(255,255,255,0.2);
      border-radius: 5px;
      margin-top: 20px;
      overflow: hidden;
    }

    .progress {
      height: 100%;
      width: 0;
      background: linear-gradient(to right, gold, orange);
      border-radius: 5px;
      animation: loadProgress 5s linear forwards;
    }

    @keyframes spinHalo {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    @keyframes pulseCross {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.1); }
    }

    @keyframes textGlow {
      from { text-shadow: 0 0 5px rgba(255,255,255,0.5); }
      to { text-shadow: 0 0 15px rgba(255,255,255,0.9), 0 0 20px gold; }
    }

    @keyframes fadeIn {
      to { opacity: 1; }
    }

    @keyframes fadeOut {
      to {
        opacity: 0;
        visibility: hidden;
      }
    }

    @keyframes loadProgress {
      0% { width: 0; }
      100% { width: 100%; }
    }

    /* Animated Text at the Upper-Left Side of the Homepage */
    .top-loader-text {
      position: fixed;
      top: 20px;
      left: 20px;
      font-size: 0.5rem;
      font-weight: bold;
      color: #fff;
      text-transform: uppercase;
      z-index: 1001;
      opacity: 0;
      animation: slideIn 0.5s 5.5s forwards, animateText 2s infinite 6s;
      background-color: #0077b5;
      padding: 10px 20px;
      border-radius: 0 20px 20px 0;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
    }

    @keyframes slideIn {
      from {
        opacity: 0;
        transform: translateX(-50px);
      }
      to {
        opacity: 1;
        transform: translateX(0);
      }
    }

    /* Auto-changing Transformation Text */
    .transforming-text {
      font-size: 1.5rem;
      margin: 10px 0;
      color: #333;
      text-shadow: 7px 7px 10px -2px rgba(0,0,0,0.5);
      transition: all 0.5s ease;
      height: 2.5rem;
      overflow: hidden;
      position: relative;
      width: 100%;
      text-align: center;
    }

    .transforming-text span {
      position: absolute;
      width: 100%;
      text-align: center;
      left: 0;
      opacity: 0;
      animation: textChange 12s infinite;
      font-size: 1.5rem;
      line-height: 1.2;
      padding: 0 10px;
      box-sizing: border-box;
    }

    .transforming-text span:nth-child(1) {
      animation-delay: 0s;
    }
    .transforming-text span:nth-child(2) {
      animation-delay: 3s;
    }
    .transforming-text span:nth-child(3) {
      animation-delay: 6s;
    }
    .transforming-text span:nth-child(4) {
      animation-delay: 9s;
    }

    @keyframes textChange {
      0% { opacity: 0; transform: translateY(20px); }
      10% { opacity: 1; transform: translateY(0); }
      20% { opacity: 1; transform: translateY(0); }
      30% { opacity: 0; transform: translateY(-20px); }
      100% { opacity: 0; transform: translateY(-20px); }
    }

    /* Image Slider Styles */
    .image-slider {
      width: 100%;
      margin: 20px 0;
      position: relative;
      overflow: hidden;
      border-radius: 20px;
      box-shadow: 7px 7px 17px -2px rgba(0,0,0,0.5), -7px -7px 17px -2px rgba(255,255,255,0.7);
    }

    .slider-container {
      display: flex;
      transition: transform 0.5s ease-in-out;
      height: 300px;
    }

    .slide {
      min-width: 100%;
      height: 100%;
    }

    .slide img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .slider-nav {
      position: absolute;
      bottom: 10px;
      left: 0;
      right: 0;
      display: flex;
      justify-content: center;
      gap: 10px;
    }

    .slider-dot {
      width: 12px;
      height: 12px;
      border-radius: 50%;
      background-color: rgba(255,255,255,0.5);
      cursor: pointer;
      transition: background-color 0.3s ease;
    }

    .slider-dot.active {
      background-color: #0077b5;
    }

    .slider-arrow {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      width: 40px;
      height: 40px;
      background-color: rgba(0,0,0,0.5);
      color: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      z-index: 10;
      transition: background-color 0.3s ease;
    }

    .slider-arrow:hover {
      background-color: rgba(0,0,0,0.7);
    }

    .slider-arrow.prev {
      left: 10px;
    }

    .slider-arrow.next {
      right: 10px;
    }

    /* Dark Mode Styles for Slider */
    body.dark-mode .image-slider {
      box-shadow: 7px 7px 17px -2px rgba(0,0,0,0.7), -7px -7px 17px -2px rgba(50,50,70,0.3);
    }

    body.dark-mode .slider-dot {
      background-color: rgba(255,255,255,0.3);
    }

    body.dark-mode .slider-dot.active {
      background-color: #00b5ad;
    }

    body.dark-mode .slider-arrow {
      background-color: rgba(50,50,70,0.5);
    }

    body.dark-mode .slider-arrow:hover {
      background-color: rgba(50,50,70,0.7);
    }

    /* General Styles */
    body {
      font-family: 'Montserrat', sans-serif;
      background-color: #d1d9eb;
      color: #333;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      position: relative;
      transition: all 0.5s ease;
      padding-bottom: 80px; /* Add padding for floating buttons */
    }

    /* Dark Mode Styles */
    body.dark-mode {
      background-color: #1a1a2e;
      color: #f0f0f0;
    }

    body.dark-mode .container {
      background-color: #16213e;
      box-shadow: 7px 7px 17px -2px rgba(0,0,0,0.7), -7px -7px 17px -2px rgba(50,50,70,0.3);
      color: #f0f0f0;
    }

    body.dark-mode .profile-img-container {
      background-color: #16213e;
      box-shadow: 7px 7px 17px -1px rgba(0,0,0,0.7), -7px -7px 17px -1px rgba(50,50,70,0.3);
    }

    body.dark-mode .name {
      color: #f0f0f0;
      text-shadow: 7px 7px 10px -2px rgba(0,0,0,0.7);
    }

    body.dark-mode .bio {
      color: #b8b8b8;
      text-shadow: inset 7px 7px 10px -2px rgba(0,0,0,0.7), inset -7px -7px 10px -2px rgba(50,50,70,0.3);
    }

    body.dark-mode .info p {
      color: #b8b8b8;
    }

    body.dark-mode .icons a {
      background-color: #16213e;
      box-shadow: 7px 7px 17px -2px rgba(0,0,0,0.7), -7px -7px 17px -2px rgba(50,50,70,0.3);
      color: #f0f0f0;
    }

    body.dark-mode button,
    body.dark-mode .submit-btn,
    body.dark-mode .nav a {
      background-color: #16213e;
      box-shadow: 7px 7px 17px -2px rgba(0,0,0,0.7), -7px -7px 17px -2px rgba(50,50,70,0.3);
      color: #f0f0f0;
    }

    body.dark-mode .sermons,
    body.dark-mode .testimonies,
    body.dark-mode .message-form,
    body.dark-mode .prayer-form {
      background-color: #16213e;
      box-shadow: inset 7px 7px 17px -2px rgba(0,0,0,0.5), inset -7px -7px 17px -2px rgba(50,50,70,0.2);
    }

    body.dark-mode .form-group input,
    body.dark-mode .form-group textarea,
    body.dark-mode .form-group select {
      background-color: #16213e;
      box-shadow: inset 7px 7px 17px -2px rgba(0,0,0,0.5), inset -7px -7px 17px -2px rgba(50,50,70,0.2);
      color: #f0f0f0;
    }

    body.dark-mode .sermon-item,
    body.dark-mode .testimony-item {
      box-shadow: 7px 7px 17px -2px rgba(0,0,0,0.5), -7px -7px 17px -2px rgba(50,50,70,0.2);
    }

    /* Container */
    .container {
      max-width: 800px;
      width: 90%;
      margin: 20px;
      padding: 20px;
      background-color: #d1d9eb;
      box-shadow: 7px 7px 17px -2px rgba(0,0,0,0.5), -7px -7px 17px -2px rgba(255,255,255,0.7);
      border-radius: 50px;
      text-align: center;
      position: relative;
      transition: all 0.5s ease;
    }

    /* Enhanced Profile Section */
    .profile-img-container {
      background: linear-gradient(45deg, #d1d9eb, #c1c9db, #d1d9eb);
      box-shadow: 
        7px 7px 17px -1px rgba(0,0,0,0.5), 
        -7px -7px 17px -1px rgba(255,255,255,0.7),
        inset 3px 3px 10px rgba(0,0,0,0.1),
        inset -3px -3px 10px rgba(255,255,255,0.5);
      display: flex;
      overflow: hidden;
      height: 180px;
      width: 180px;
      margin: 0 auto 20px;
      border-radius: 40% 60% 65% 35% / 35% 55% 45% 65%;
      animation: bari 12s linear infinite, float 6s ease-in-out infinite;
      justify-content: center;
      align-items: center;
      padding: 8px;
      transition: all 0.5s ease;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }

    .profile-img {
      width: 100%;
      height: 100%;
      border-radius: 50%;
      object-fit: cover;
      transition: all 0.5s ease;
      cursor: pointer;
      position: relative;
      z-index: 2;
      border: 3px solid rgba(255,255,255,0.3);
      box-shadow: 0 0 20px rgba(0,0,0,0.1);
    }

    @keyframes bari {
      0% {border-radius: 40% 60% 65% 35% / 35% 55% 45% 65%; transform: rotate(0deg);}
      25% {border-radius: 65% 35% 40% 60% / 55% 40% 60% 45%;}
      50% {border-radius: 35% 65% 50% 50% / 65% 55% 45% 35%;}
      75% {border-radius: 55% 45% 45% 55% / 60% 45% 55% 40%;}
      100% {border-radius: 40% 60% 65% 35% / 35% 55% 45% 65%; transform: rotate(360deg);}
    }

    .profile-img-container::before {
      content: '';
      position: absolute;
      top: -5px;
      left: -5px;
      right: -5px;
      bottom: -5px;
      background: linear-gradient(45deg, #0077b5, #00b5ad, #0077b5);
      z-index: 1;
      border-radius: 50%;
      opacity: 0;
      transition: opacity 0.5s ease;
      animation: rotateBorder 8s linear infinite;
    }

    @keyframes rotateBorder {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    .profile-img-container:hover::before {
      opacity: 0.7;
    }

    .profile-img-container:hover {
      transform: scale(1.05);
      box-shadow: 
        10px 10px 20px -1px rgba(0,0,0,0.4), 
        -10px -10px 20px -1px rgba(255,255,255,0.8),
        inset 5px 5px 15px rgba(0,0,0,0.1),
        inset -5px -5px 15px rgba(255,255,255,0.5);
    }

    .profile-img:hover {
      transform: scale(1.03);
      box-shadow: 0 0 30px rgba(0,0,0,0.2);
      border-color: rgba(255,255,255,0.5);
    }

    /* Shake and Bounce Animation */
    @keyframes shakeAndBounce {
      0%, 100% {
        transform: translateX(0) translateY(0);
      }
      10%, 30%, 50%, 70%, 90% {
        transform: translateX(-10px) translateY(-10px);
      }
      20%, 40%, 60%, 80% {
        transform: translateX(10px) translateY(10px);
      }
    }

    .profile-img.shake-and-bounce {
      animation: shakeAndBounce 0.5s ease 3;
    }

    .bio {
      font-size: 1.2rem;
      color: #777;
      text-shadow: inset 7px 7px 10px -2px rgba(0,0,0,0.5), inset -7px -7px 10px -2px rgba(255,255,255,0.7);
      transition: all 0.5s ease;
    }

    /* About Me Section */
    .info {
      margin: 30px 0;
    }

    .info h2 {
      font-size: 2rem;
      margin-bottom: 15px;
      color: #333;
      transition: all 0.5s ease;
    }

    .info p {
      font-size: 1rem;
      line-height: 1.6;
      color: #555;
      transition: all 0.5s ease;
    }

    /* Social Media Icons */
    .social-media {
      margin: 30px 0;
    }

    .social-media h2 {
      font-size: 2rem;
      margin-bottom: 15px;
      color: #333;
      transition: all 0.5s ease;
    }

    .icons {
      display: flex;
      justify-content: center;
      gap: 10px;
      flex-wrap: wrap;
    }

    .icons a {
      color: #333;
      font-size: 1.5rem;
      transition: all 0.3s ease;
      text-decoration: none;
      box-shadow: 7px 7px 17px -2px rgba(0,0,0,0.5), -7px -7px 17px -2px rgba(255,255,255,0.7);
      border-radius: 50%;
      padding: 8px;
      background-color: #d1d9eb;
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .icons a:hover {
      transform: translateY(-5px);
      box-shadow: inset 1px 1px 8px -2px rgba(0,0,0,0.5), inset -2px -2px 8px -2px rgba(255,255,255,0.7);
    }

    .icons a:hover i {
      font-size: 1.8rem;
    }

    .fa-tiktok {
      color: #000;
    }
    .fa-facebook {
      color: #0077b5;
    }
    .fa-whatsapp {
      color: green;
    }
    .fa-phone {
      color: #25D366;
    }
    .fa-instagram {
      color: #e1306c;
    }
    .fa-envelope {
      color: #d44638;
    }

    /* Stats */
    .stats {
      display: flex;
      justify-content: center;
      gap: 40px;
      margin: 20px 0;
    }

    .stat-item {
      text-align: center;
      cursor: pointer;
    }

    .stat-item i {
      font-size: 1.5rem;
      margin-bottom: 5px;
    }

    .stat-item span {
      display: block;
      font-size: 0.9rem;
    }

    .stat-value {
      font-weight: bold;
      display: none;
    }

    /* Navigation */
    .nav {
      position: absolute;
      top: 20px;
      right: 20px;
      display: flex;
      justify-content: flex-end;
    }

    .nav a {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 7px 7px 17px -2px rgba(0,0,0,0.5), -7px -7px 17px -2px rgba(255,255,255,0.7);
      color: #333;
      text-decoration: none;
      transition: all 0.5s ease;
    }

    .nav a:hover {
      box-shadow: inset 1px 1px 8px -2px rgba(0,0,0,0.5), inset -2px -2px 8px -2px rgba(255,255,255,0.7);
    }

    /* Theme Toggle Icon */
    .theme-toggle {
      font-size: 1.2rem;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    .theme-toggle:hover {
      transform: rotate(30deg);
    }

    /* Sermons Section */
    .sermons {
      display: none;
      margin-top: 20px;
      padding: 15px 0;
      background-color: #d1d9eb;
      border-radius: 30px;
      box-shadow: inset 7px 7px 17px -2px rgba(0,0,0,0.3), inset -7px -7px 17px -2px rgba(255,255,255,0.7);
      transition: all 0.5s ease;
    }

    .sermons.active {
      display: block;
    }

    .sermons-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 15px;
      margin-top: 15px;
      padding: 0 15px;
    }

    .sermon-item {
      width: 100%;
      position: relative;
      overflow: hidden;
      border-radius: 15px;
      box-shadow: 7px 7px 17px -2px rgba(0,0,0,0.3), -7px -7px 17px -2px rgba(255,255,255,0.7);
      transition: all 0.3s ease;
    }

    .sermon-video {
      width: 100%;
      height: 0;
      padding-bottom: 56.25%; /* 16:9 aspect ratio */
      position: relative;
    }

    .sermon-video video {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      border: none;
      border-radius: 15px 15px 0 0;
      object-fit: cover;
    }

    .sermon-info {
      padding: 10px;
      text-align: left;
    }

    .sermon-title {
      font-weight: bold;
      margin-bottom: 5px;
    }

    .sermon-date {
      font-size: 0.8rem;
      color: #777;
    }

    .sermon-item:hover {
      transform: scale(1.03);
      box-shadow: 7px 7px 20px -2px rgba(0,0,0,0.4), -7px -7px 20px -2px rgba(255,255,255,0.8);
    }

    .sermons-title {
      font-size: 1.5rem;
      margin-bottom: 15px;
      color: #333;
      padding: 0 15px;
      transition: all 0.5s ease;
    }

    /* Testimonies Section */
    .testimonies {
      display: none;
      margin-top: 20px;
      padding: 15px 0;
      background-color: #d1d9eb;
      border-radius: 30px;
      box-shadow: inset 7px 7px 17px -2px rgba(0,0,0,0.3), inset -7px -7px 17px -2px rgba(255,255,255,0.7);
      transition: all 0.5s ease;
    }

    .testimonies.active {
      display: block;
    }

    .testimonies-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 15px;
      margin-top: 15px;
      padding: 0 15px;
    }

    .testimony-item {
      width: 100%;
      position: relative;
      overflow: hidden;
      border-radius: 15px;
      box-shadow: 7px 7px 17px -2px rgba(0,0,0,0.3), -7px -7px 17px -2px rgba(255,255,255,0.7);
      transition: all 0.3s ease;
    }

    .testimony-video {
      width: 100%;
      height: 0;
      padding-bottom: 56.25%; /* 16:9 aspect ratio */
      position: relative;
    }

    .testimony-video video {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      border: none;
      border-radius: 15px 15px 0 0;
      object-fit: cover;
    }

    .testimony-info {
      padding: 10px;
      text-align: left;
    }

    .testimony-title {
      font-weight: bold;
      margin-bottom: 5px;
    }

    .testimony-date {
      font-size: 0.8rem;
      color: #777;
    }

    .testimony-item:hover {
      transform: scale(1.03);
      box-shadow: 7px 7px 20px -2px rgba(0,0,0,0.4), -7px -7px 20px -2px rgba(255,255,255,0.8);
    }

    .testimonies-title {
      font-size: 1.5rem;
      margin-bottom: 15px;
      color: #333;
      padding: 0 15px;
      transition: all 0.5s ease;
    }

    /* Message Form Section */
    .message-form {
      display: none;
      margin-top: 20px;
      padding: 20px;
      background-color: #d1d9eb;
      border-radius: 30px;
      box-shadow: inset 7px 7px 17px -2px rgba(0,0,0,0.3), inset -7px -7px 17px -2px rgba(255,255,255,0.7);
      transition: all 0.5s ease;
    }

    .message-form.active {
      display: block;
    }

    /* Prayer Form Section */
    .prayer-form {
      display: none;
      margin-top: 20px;
      padding: 20px;
      background-color: #d1d9eb;
      border-radius: 30px;
      box-shadow: inset 7px 7px 17px -2px rgba(0,0,0,0.3), inset -7px -7px 17px -2px rgba(255,255,255,0.7);
      transition: all 0.5s ease;
    }

    .prayer-form.active {
      display: block;
    }

    .form-group {
      margin-bottom: 15px;
      text-align: left;
    }

    .form-group label {
      display: block;
      margin-bottom: 5px;
      font-weight: bold;
    }

    .form-group input,
    .form-group textarea,
    .form-group select {
      width: 100%;
      padding: 10px;
      border: none;
      border-radius: 15px;
      background-color: #d1d9eb;
      box-shadow: inset 7px 7px 17px -2px rgba(0,0,0,0.3), inset -7px -7px 17px -2px rgba(255,255,255,0.7);
      font-family: 'Montserrat', sans-serif;
      transition: all 0.5s ease;
    }

    .form-group textarea {
      min-height: 100px;
      resize: vertical;
    }

    .file-upload-label {
      display: block;
      margin-top: 5px;
      font-size: 0.8rem;
      color: #777;
    }

    .audio-recording {
      display: flex;
      align-items: center;
      gap: 10px;
      margin-top: 10px;
    }

    .record-btn {
      padding: 8px 15px;
      background-color: #0077b5;
      color: white;
      border: none;
      border-radius: 20px;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 5px;
    }

    .record-btn i {
      font-size: 1rem;
    }

    .audio-visualizer {
      flex-grow: 1;
      height: 20px;
      background-color: #f0f0f0;
      border-radius: 10px;
      overflow: hidden;
    }

    .audio-visualizer-bar {
      height: 100%;
      width: 0%;
      background-color: #0077b5;
      transition: width 0.1s ease;
    }

    .submit-btn {
      width: 100%;
      padding: 10px;
      border: none;
      border-radius: 15px;
      background-color: #d1d9eb;
      box-shadow: 7px 7px 17px -2px rgba(0,0,0,0.5), -7px -7px 17px -2px rgba(255,255,255,0.7);
      font-family: 'Montserrat', sans-serif;
      font-weight: bold;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    .submit-btn:hover {
      box-shadow: inset 1px 1px 8px -2px rgba(0,0,0,0.5), inset -2px -2px 8px -2px rgba(255,255,255,0.7);
    }

    /* Chat Icon and Window Styles */
    .chat-icon {
      position: fixed;
      bottom: 30px;
      right: 30px;
      width: 60px;
      height: 60px;
      background-color: #0077b5;
      color: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
      cursor: pointer;
      z-index: 1000;
      transition: all 0.3s ease;
    }

    .chat-icon:hover {
      transform: scale(1.1);
      box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
    }

    .chat-window {
      position: fixed;
      bottom: 100px;
      right: 30px;
      width: 85%;
      height: 85%;
      background-color: #d1d9eb;
      border-radius: 20px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
      z-index: 1001;
      display: none;
      flex-direction: column;
      transform: scale(0.8);
      opacity: 0;
      transition: all 0.3s ease;
      overflow: hidden;
    }

    .chat-window.active {
      display: flex;
      transform: scale(1);
      opacity: 1;
    }

    .chat-header {
      padding: 15px;
      background-color: #0077b5;
      color: white;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-radius: 20px 20px 0 0;
    }

    .chat-close {
      cursor: pointer;
      font-size: 1.5rem;
    }

    .chat-messages {
      flex: 1;
      padding: 15px;
      overflow-y: auto;
    }

    .chat-input {
      display: flex;
      padding: 15px;
      background-color: #f0f0f0;
      border-radius: 0 0 20px 20px;
    }

    .chat-input input {
      flex: 1;
      padding: 10px;
      border: none;
      border-radius: 20px;
      margin-right: 10px;
    }

    .chat-send {
      background-color: #0077b5;
      color: white;
      border: none;
      border-radius: 50%;
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
    }

    /* Floating Action Buttons */
    .floating-buttons {
      position: fixed;
      bottom: 20px;
      left: 0;
      right: 0;
      display: flex;
      justify-content: center;
      gap: 15px;
      z-index: 999;
      padding: 0 15px;
    }

    .floating-btn {
      border-style: none;
      outline: none;
      height: 50px;
      box-shadow: 7px 7px 17px -2px rgba(0,0,0,0.5), -7px -7px 17px -2px rgba(255,255,255,0.7);
      background-color: #d1d9eb;
      border-radius: 30px;
      cursor: pointer;
      transition: all 0.3s ease;
      font-family: 'Montserrat', sans-serif;
      font-weight: bold;
      font-size: 1rem;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 0 20px;
      min-width: 120px;
      flex-grow: 1;
      max-width: 180px;
    }

    .floating-btn i {
      margin-right: 8px;
    }

    .floating-btn:hover {
      box-shadow: inset 1px 1px 8px -2px rgba(0,0,0,0.5), inset -2px -2px 8px -2px rgba(255,255,255,0.7);
      transform: translateY(-2px);
    }

    /* Dark Mode Chat Styles */
    body.dark-mode .chat-icon {
      background-color: #00b5ad;
    }

    body.dark-mode .chat-window {
      background-color: #16213e;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
    }

    body.dark-mode .chat-header {
      background-color: #00b5ad;
    }

    body.dark-mode .chat-input {
      background-color: #1a1a2e;
    }

    body.dark-mode .chat-input input {
      background-color: #16213e;
      color: #f0f0f0;
    }

    body.dark-mode .chat-send {
      background-color: #00b5ad;
    }

    /* Dark Mode Floating Buttons */
    body.dark-mode .floating-btn {
      background-color: #16213e;
      color: #f0f0f0;
      box-shadow: 7px 7px 17px -2px rgba(0,0,0,0.7), -7px -7px 17px -2px rgba(50,50,70,0.3);
    }

    body.dark-mode .floating-btn:hover {
      box-shadow: inset 1px 1px 8px -2px rgba(0,0,0,0.7), inset -2px -2px 8px -2px rgba(50,50,70,0.3);
    }

    /* Dark Mode Audio Recording */
    body.dark-mode .audio-visualizer {
      background-color: #1a1a2e;
    }

    body.dark-mode .record-btn {
      background-color: #00b5ad;
    }

    /* Responsive Design */
    @media (max-width: 768px) {
      .transforming-text span {
        font-size: 1.2rem;
      }

      .bio {
        font-size: 1rem;
      }

      .info h2, .social-media h2 {
        font-size: 1.5rem;
      }

      .info p {
        font-size: 0.9rem;
      }

      .icons a {
        font-size: 1.3rem;
      }

      .sermons-grid,
      .testimonies-grid {
        grid-template-columns: 1fr;
      }

      .image-slider {
        height: 250px;
      }

      .floating-btn {
        height: 45px;
        font-size: 0.9rem;
        padding: 0 15px;
        min-width: 100px;
      }

      .floating-buttons {
        gap: 10px;
      }

      .chat-window {
        width: 95%;
        height: 80%;
        right: 10px;
      }
    }

    @media (max-width: 480px) {
      .profile-img-container {
        height: 120px;
        width: 120px;
      }

      .transforming-text span {
        font-size: 1rem;
      }

      .bio {
        font-size: 0.9rem;
      }

      .info h2, .social-media h2 {
        font-size: 1.3rem;
      }

      .info p {
        font-size: 0.8rem;
      }

      .icons a {
        font-size: 1.2rem;
      }

      .floating-buttons {
        gap: 8px;
      }

      .floating-btn {
        height: 42px;
        font-size: 0.85rem;
        padding: 0 12px;
        min-width: 90px;
      }

      .floating-btn i {
        margin-right: 5px;
        font-size: 0.9rem;
      }

      .image-slider {
        height: 200px;
      }

      .chat-icon {
        width: 50px;
        height: 50px;
        bottom: 20px;
        right: 20px;
      }

      .chat-window {
        width: 100%;
        height: 85%;
        right: 0;
        bottom: 0;
        border-radius: 20px 20px 0 0;
      }
    }
  </style>
</head>
<body>
  <!-- Advanced Christian-themed Loader with Blurred Background -->
  <div class="loader">
    <div class="loader-content">
      <div class="halo"></div>
      <div class="halo"></div>
      <div class="halo"></div>
      <div class="cross-loader"></div>
    </div>
    <div class="loader-text">Arena Of Grace Ministries</div>
    <div class="bible-verse">"For God so loved the world that he gave his one and only Son..." - John 3:16</div>
    <div class="progress-bar"><div class="progress"></div></div>
  </div>

  <!-- Animated Text at the Upper-Left Side of the Homepage -->
  <div class="top-loader-text">Arena Of Grace</div>

  <!-- Chat Icon -->
  <div class="chat-icon" id="chat-icon">
    <i class="fas fa-comment-dots"></i>
  </div>

  <!-- Chat Window -->
  <div class="chat-window" id="chat-window">
    <div class="chat-header">
      <h3>Chat with Us</h3>
      <div class="chat-close" id="chat-close"><i class="fas fa-times"></i></div>
    </div>
    <div class="chat-messages" id="chat-messages">
      <!-- Messages will appear here -->
    </div>
    <div class="chat-input">
      <input type="text" id="chat-input" placeholder="Type your message...">
      <button class="chat-send" id="chat-send"><i class="fas fa-paper-plane"></i></button>
    </div>
  </div>

  <!-- Floating Action Buttons -->
  <div class="floating-buttons">
    <button class="floating-btn" id="sermons-btn"><i class="fas fa-church"></i> Sermons</button>
    <button class="floating-btn" id="testimonies-btn"><i class="fas fa-hand-holding-heart"></i> Testimonies</button>
    <button class="floating-btn" id="prayer-btn"><i class="fas fa-pray"></i> Prayer</button>
  </div>

  <!-- Main Content -->
  <div class="container">
    <div class="nav">
      <a href="#" class="menu theme-toggle" id="theme-toggle"><i class="fas fa-moon"></i></a>
    </div>

    <div class="profile">
      <div class="profile-img-container">
        <img src="profile.jpg" alt="Profile Picture" class="profile-img">
      </div>
      <h1 class="transforming-text">
        <span>I Am The Konkonsa Prophet</span>
        <span>Man Of God</span>
        <span>Servant Of The Most High</span>
        <span>Messenger Of Truth</span>
      </h1>
      <p class="bio">Prophet | Martin Osei | Mensah</p>
    </div>

    <!-- Image Slider -->
    <div class="image-slider">
      <div class="slider-container" id="slider">
        <div class="slide">
          <img src="imagea.jpg" alt="Church Image 1">
        </div>
        <div class="slide">
          <img src="imageb.jpg" alt="Bible Image">
        </div>
        <div class="slide">
          <img src="imagec.jpg" alt="Worship Image">
        </div>
        <div class="slide">
          <img src="imaged.jpg" alt="Prayer Image">
        </div>
      </div>
      <div class="slider-arrow prev" id="prev"><i class="fas fa-chevron-left"></i></div>
      <div class="slider-arrow next" id="next"><i class="fas fa-chevron-right"></i></div>
      <div class="slider-nav" id="slider-nav">
        <div class="slider-dot active"></div>
        <div class="slider-dot"></div>
        <div class="slider-dot"></div>
        <div class="slider-dot"></div>
      </div>
    </div>

    <div class="stats">
      <div class="stat-item" id="following-stat">
        <i class="fas fa-handshake"></i>
        <span>Nationality</span>
        <span class="stat-value">Ghanaian 🇬🇭</span>
      </div>
      <div class="stat-item" id="followers-stat">
        <i class="fas fa-handshake"></i>
        <span>Residence</span>
        <span class="stat-value">Belgium 🇧🇪</span>
      </div>
    </div>

    <!-- Sermons Section -->
    <div class="sermons" id="sermons">
      <h3 class="sermons-title">Latest Sermons</h3>
      <div class="sermons-grid">
        <div class="sermon-item">
          <div class="sermon-video">
            <video controls>
              <source src="sermon1.mp4" type="video/mp4">
              Your browser does not support the video tag.
            </video>
          </div>
          <div class="sermon-info">
            <div class="sermon-title">The Power of Faith</div>
            <div class="sermon-date">June 15, 2023</div>
          </div>
        </div>
        <div class="sermon-item">
          <div class="sermon-video">
            <video controls>
              <source src="sermon2.mp4" type="video/mp4">
              Your browser does not support the video tag.
            </video>
          </div>
          <div class="sermon-info">
            <div class="sermon-title">Walking in Love</div>
            <div class="sermon-date">June 8, 2023</div>
          </div>
        </div>
        <div class="sermon-item">
          <div class="sermon-video">
            <video controls>
              <source src="sermon3.mp4" type="video/mp4">
              Your browser does not support the video tag.
            </video>
          </div>
          <div class="sermon-info">
            <div class="sermon-title">Overcoming Challenges</div>
            <div class="sermon-date">June 1, 2023</div>
          </div>
        </div>
        <div class="sermon-item">
          <div class="sermon-video">
            <video controls>
              <source src="sermon4.mp4" type="video/mp4">
              Your browser does not support the video tag.
            </video>
          </div>
          <div class="sermon-info">
            <div class="sermon-title">The Joy of Giving</div>
            <div class="sermon-date">May 25, 2023</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Testimonies Section -->
    <div class="testimonies" id="testimonies">
      <h3 class="testimonies-title">Powerful Testimonies</h3>
      <div class="testimonies-grid">
        <div class="testimony-item">
          <div class="testimony-video">
            <video controls>
              <source src="testimony1.mp4" type="video/mp4">
              Your browser does not support the video tag.
            </video>
          </div>
          <div class="testimony-info">
            <div class="testimony-title">Healing Miracle</div>
            <div class="testimony-date">June 12, 2023</div>
          </div>
        </div>
        <div class="testimony-item">
          <div class="testimony-video">
            <video controls>
              <source src="testimony2.mp4" type="video/mp4">
              Your browser does not support the video tag.
            </video>
          </div>
          <div class="testimony-info">
            <div class="testimony-title">Financial Breakthrough</div>
            <div class="testimony-date">June 5, 2023</div>
          </div>
        </div>
        <div class="testimony-item">
          <div class="testimony-video">
            <video controls>
              <source src="testimony3.mp4" type="video/mp4">
              Your browser does not support the video tag.
            </video>
          </div>
          <div class="testimony-info">
            <div class="testimony-title">Family Restoration</div>
            <div class="testimony-date">May 29, 2023</div>
          </div>
        </div>
        <div class="testimony-item">
          <div class="testimony-video">
            <video controls>
              <source src="testimony4.mp4" type="video/mp4">
              Your browser does not support the video tag.
            </video>
          </div>
          <div class="testimony-info">
            <div class="testimony-title">Deliverance Story</div>
            <div class="testimony-date">May 22, 2023</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Message Form Section -->
    <div class="message-form" id="message-form">
      <form action="https://formspree.io/f/YOUR_FORMSPREE_ID" method="POST">
        <div class="form-group">
          <label for="name">Your Name</label>
          <input type="text" id="name" name="name" required>
        </div>
        <div class="form-group">
          <label for="email">Your Email</label>
          <input type="email" id="email" name="email" required>
        </div>
        <div class="form-group">
          <label for="message">Your Message</label>
          <textarea id="message" name="message" required></textarea>
        </div>
        <button type="submit" class="submit-btn">Send Message</button>
      </form>
    </div>

    <!-- Prayer Request Form Section -->
    <div class="prayer-form" id="prayer-form">
      <form action="https://formspree.io/f/YOUR_FORMSPREE_ID" method="POST" enctype="multipart/form-data">
        <div class="form-group">
          <label for="prayer-name">Your Name</label>
          <input type="text" id="prayer-name" name="name" required>
        </div>
        
        <div class="form-group">
          <label for="prayer-location">Your Location</label>
          <select id="prayer-location" name="location" required>
            <option value="">Select Country</option>
            <option value="Afghanistan">Afghanistan</option>
            <option value="Albania">Albania</option>
            <option value="Algeria">Algeria</option>
            <option value="Andorra">Andorra</option>
            <option value="Angola">Angola</option>
            <option value="Antigua and Barbuda">Antigua and Barbuda</option>
            <option value="Argentina">Argentina</option>
            <option value="Armenia">Armenia</option>
            <option value="Australia">Australia</option>
            <option value="Austria">Austria</option>
            <option value="Azerbaijan">Azerbaijan</option>
            <option value="Bahamas">Bahamas</option>
            <option value="Bahrain">Bahrain</option>
            <option value="Bangladesh">Bangladesh</option>
            <option value="Barbados">Barbados</option>
            <option value="Belarus">Belarus</option>
            <option value="Belgium">Belgium</option>
            <option value="Belize">Belize</option>
            <option value="Benin">Benin</option>
            <option value="Bhutan">Bhutan</option>
            <option value="Bolivia">Bolivia</option>
            <option value="Bosnia and Herzegovina">Bosnia and Herzegovina</option>
            <option value="Botswana">Botswana</option>
            <option value="Brazil">Brazil</option>
            <option value="Brunei">Brunei</option>
            <option value="Bulgaria">Bulgaria</option>
            <option value="Burkina Faso">Burkina Faso</option>
            <option value="Burundi">Burundi</option>
            <option value="Côte d'Ivoire">Côte d'Ivoire</option>
            <option value="Cabo Verde">Cabo Verde</option>
            <option value="Cambodia">Cambodia</option>
            <option value="Cameroon">Cameroon</option>
            <option value="Canada">Canada</option>
            <option value="Central African Republic">Central African Republic</option>
            <option value="Chad">Chad</option>
            <option value="Chile">Chile</option>
            <option value="China">China</option>
            <option value="Colombia">Colombia</option>
            <option value="Comoros">Comoros</option>
            <option value="Congo (Congo-Brazzaville)">Congo (Congo-Brazzaville)</option>
            <option value="Costa Rica">Costa Rica</option>
            <option value="Croatia">Croatia</option>
            <option value="Cuba">Cuba</option>
            <option value="Cyprus">Cyprus</option>
            <option value="Czechia (Czech Republic)">Czechia (Czech Republic)</option>
            <option value="Democratic Republic of the Congo">Democratic Republic of the Congo</option>
            <option value="Denmark">Denmark</option>
            <option value="Djibouti">Djibouti</option>
            <option value="Dominica">Dominica</option>
            <option value="Dominican Republic">Dominican Republic</option>
            <option value="Ecuador">Ecuador</option>
            <option value="Egypt">Egypt</option>
            <option value="El Salvador">El Salvador</option>
            <option value="Equatorial Guinea">Equatorial Guinea</option>
            <option value="Eritrea">Eritrea</option>
            <option value="Estonia">Estonia</option>
            <option value="Eswatini">Eswatini</option>
            <option value="Ethiopia">Ethiopia</option>
            <option value="Fiji">Fiji</option>
            <option value="Finland">Finland</option>
            <option value="France">France</option>
            <option value="Gabon">Gabon</option>
            <option value="Gambia">Gambia</option>
            <option value="Georgia">Georgia</option>
            <option value="Germany">Germany</option>
            <option value="Ghana">Ghana</option>
            <option value="Greece">Greece</option>
            <option value="Grenada">Grenada</option>
            <option value="Guatemala">Guatemala</option>
            <option value="Guinea">Guinea</option>
            <option value="Guinea-Bissau">Guinea-Bissau</option>
            <option value="Guyana">Guyana</option>
            <option value="Haiti">Haiti</option>
            <option value="Holy See">Holy See</option>
            <option value="Honduras">Honduras</option>
            <option value="Hungary">Hungary</option>
            <option value="Iceland">Iceland</option>
            <option value="India">India</option>
            <option value="Indonesia">Indonesia</option>
            <option value="Iran">Iran</option>
            <option value="Iraq">Iraq</option>
            <option value="Ireland">Ireland</option>
            <option value="Israel">Israel</option>
            <option value="Italy">Italy</option>
            <option value="Jamaica">Jamaica</option>
            <option value="Japan">Japan</option>
            <option value="Jordan">Jordan</option>
            <option value="Kazakhstan">Kazakhstan</option>
            <option value="Kenya">Kenya</option>
            <option value="Kiribati">Kiribati</option>
            <option value="Kuwait">Kuwait</option>
            <option value="Kyrgyzstan">Kyrgyzstan</option>
            <option value="Laos">Laos</option>
            <option value="Latvia">Latvia</option>
            <option value="Lebanon">Lebanon</option>
            <option value="Lesotho">Lesotho</option>
            <option value="Liberia">Liberia</option>
            <option value="Libya">Libya</option>
            <option value="Liechtenstein">Liechtenstein</option>
            <option value="Lithuania">Lithuania</option>
            <option value="Luxembourg">Luxembourg</option>
            <option value="Madagascar">Madagascar</option>
            <option value="Malawi">Malawi</option>
            <option value="Malaysia">Malaysia</option>
            <option value="Maldives">Maldives</option>
            <option value="Mali">Mali</option>
            <option value="Malta">Malta</option>
            <option value="Marshall Islands">Marshall Islands</option>
            <option value="Mauritania">Mauritania</option>
            <option value="Mauritius">Mauritius</option>
            <option value="Mexico">Mexico</option>
            <option value="Micronesia">Micronesia</option>
            <option value="Moldova">Moldova</option>
            <option value="Monaco">Monaco</option>
            <option value="Mongolia">Mongolia</option>
            <option value="Montenegro">Montenegro</option>
            <option value="Morocco">Morocco</option>
            <option value="Mozambique">Mozambique</option>
            <option value="Myanmar">Myanmar</option>
            <option value="Namibia">Namibia</option>
            <option value="Nauru">Nauru</option>
            <option value="Nepal">Nepal</option>
            <option value="Netherlands">Netherlands</option>
            <option value="New Zealand">New Zealand</option>
            <option value="Nicaragua">Nicaragua</option>
            <option value="Niger">Niger</option>
            <option value="Nigeria">Nigeria</option>
            <option value="North Korea">North Korea</option>
            <option value="North Macedonia">North Macedonia</option>
            <option value="Norway">Norway</option>
            <option value="Oman">Oman</option>
            <option value="Pakistan">Pakistan</option>
            <option value="Palau">Palau</option>
            <option value="Palestine State">Palestine State</option>
            <option value="Panama">Panama</option>
            <option value="Papua New Guinea">Papua New Guinea</option>
            <option value="Paraguay">Paraguay</option>
            <option value="Peru">Peru</option>
            <option value="Philippines">Philippines</option>
            <option value="Poland">Poland</option>
            <option value="Portugal">Portugal</option>
            <option value="Qatar">Qatar</option>
            <option value="Romania">Romania</option>
            <option value="Russia">Russia</option>
            <option value="Rwanda">Rwanda</option>
            <option value="Saint Kitts and Nevis">Saint Kitts and Nevis</option>
            <option value="Saint Lucia">Saint Lucia</option>
            <option value="Saint Vincent and the Grenadines">Saint Vincent and the Grenadines</option>
            <option value="Samoa">Samoa</option>
            <option value="San Marino">San Marino</option>
            <option value="Sao Tome and Principe">Sao Tome and Principe</option>
            <option value="Saudi Arabia">Saudi Arabia</option>
            <option value="Senegal">Senegal</option>
            <option value="Serbia">Serbia</option>
            <option value="Seychelles">Seychelles</option>
            <option value="Sierra Leone">Sierra Leone</option>
            <option value="Singapore">Singapore</option>
            <option value="Slovakia">Slovakia</option>
            <option value="Slovenia">Slovenia</option>
            <option value="Solomon Islands">Solomon Islands</option>
            <option value="Somalia">Somalia</option>
            <option value="South Africa">South Africa</option>
            <option value="South Korea">South Korea</option>
            <option value="South Sudan">South Sudan</option>
            <option value="Spain">Spain</option>
            <option value="Sri Lanka">Sri Lanka</option>
            <option value="Sudan">Sudan</option>
            <option value="Suriname">Suriname</option>
            <option value="Sweden">Sweden</option>
            <option value="Switzerland">Switzerland</option>
            <option value="Syria">Syria</option>
            <option value="Tajikistan">Tajikistan</option>
            <option value="Tanzania">Tanzania</option>
            <option value="Thailand">Thailand</option>
            <option value="Timor-Leste">Timor-Leste</option>
            <option value="Togo">Togo</option>
            <option value="Tonga">Tonga</option>
            <option value="Trinidad and Tobago">Trinidad and Tobago</option>
            <option value="Tunisia">Tunisia</option>
            <option value="Turkey">Turkey</option>
            <option value="Turkmenistan">Turkmenistan</option>
            <option value="Tuvalu">Tuvalu</option>
            <option value="Uganda">Uganda</option>
            <option value="Ukraine">Ukraine</option>
            <option value="United Arab Emirates">United Arab Emirates</option>
            <option value="United Kingdom">United Kingdom</option>
            <option value="United States of America">United States of America</option>
            <option value="Uruguay">Uruguay</option>
            <option value="Uzbekistan">Uzbekistan</option>
            <option value="Vanuatu">Vanuatu</option>
            <option value="Venezuela">Venezuela</option>
            <option value="Vietnam">Vietnam</option>
            <option value="Yemen">Yemen</option>
            <option value="Zambia">Zambia</option>
            <option value="Zimbabwe">Zimbabwe</option>
          </select>
        </div>
        
        <div class="form-group">
          <label for="prayer-attachment">Attachment</label>
          <input type="file" id="prayer-attachment" name="attachment">
          <span class="file-upload-label">Upload screenshots of offerings/donations if any</span>
        </div>
        
        <div class="form-group">
          <label for="prayer-request">Your Prayer Request</label>
          <textarea id="prayer-request" name="prayer_request" required></textarea>
        </div>
        
        <div class="form-group">
          <label>Audio Prayer (Optional)</label>
          <div class="audio-recording">
            <button type="button" class="record-btn" id="record-btn">
              <i class="fas fa-microphone"></i> Record
            </button>
            <div class="audio-visualizer">
              <div class="audio-visualizer-bar" id="audio-visualizer"></div>
            </div>
          </div>
          <audio id="audio-playback" controls style="display: none; width: 100%; margin-top: 10px;"></audio>
          <input type="hidden" id="audio-data" name="audio_data">
        </div>
        
        <button type="submit" class="submit-btn">Submit Prayer Request</button>
      </form>
    </div>

    <div class="info">
      <h2>About Me</h2>
      <p> I'm a visionary leader and spiritual guide who passionately believes in the power of God to transform lives and communities. With a profound understanding of faith, I emphasizes that true strength comes not from material possessions or superficial pursuits, but from a deep, unwavering connection to the divine.It's POWER, not POWDER.</p>
    </div>

    <div class="social-media">
      <h2>Connect with Me</h2>
      <div class="icons">
        <a href="https://www.tiktok.com/@gideon.boadu8?_t=ZM-8v7gG3yH9CX&_r=1" target="_blank"><i class="fab fa-tiktok"></i></a>
        <a href="https://www.facebook.com/share/1KNfcvwwdo/?mibextid=wwXIfr" target="_blank"><i class="fab fa-facebook"></i></a>
        <a href="https://wa.me/971522189683" target="_blank"><i class="fab fa-whatsapp"></i></a>
        <a href="tel:+971522189683" target="_blank"><i class="fas fa-phone"></i></a>
        <a href="https://instagram.com" target="_blank"><i class="fab fa-instagram"></i></a>
        <a href="mailto:gideonboadu59@gmail.com" target="_blank"><i class="fas fa-envelope"></i></a>
      </div>
    </div>
  </div>

  <!-- Audio Element for Background Music -->
  <audio id="background-music" loop>
    <source src="music.mp3" type="audio/mpeg">
    Your browser does not support the audio element.
  </audio>

  <script>
    // JavaScript for Interactive Features
    const profileImg = document.querySelector('.profile-img');
    const sermonsBtn = document.getElementById('sermons-btn');
    const sermons = document.getElementById('sermons');
    const testimoniesBtn = document.getElementById('testimonies-btn');
    const testimonies = document.getElementById('testimonies');
    const prayerBtn = document.getElementById('prayer-btn');
    const prayerForm = document.getElementById('prayer-form');
    const messageForm = document.getElementById('message-form');
    const themeToggle = document.getElementById('theme-toggle');
    const body = document.body;
    const backgroundMusic = document.getElementById('background-music');
    let isMusicPlaying = false;

    // Audio recording variables
    const recordBtn = document.getElementById('record-btn');
    const audioVisualizer = document.getElementById('audio-visualizer');
    const audioPlayback = document.getElementById('audio-playback');
    const audioDataInput = document.getElementById('audio-data');
    let mediaRecorder;
    let audioChunks = [];
    let isRecording = false;
    let visualizerInterval;

    // Chat functionality
    const chatIcon = document.getElementById('chat-icon');
    const chatWindow = document.getElementById('chat-window');
    const chatClose = document.getElementById('chat-close');
    const chatMessages = document.getElementById('chat-messages');
    const chatInput = document.getElementById('chat-input');
    const chatSend = document.getElementById('chat-send');

    // Toggle chat window
    chatIcon.addEventListener('click', () => {
      chatWindow.classList.toggle('active');
    });

    // Close chat window
    chatClose.addEventListener('click', () => {
      chatWindow.classList.remove('active');
    });

    // Send message
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
        addMessage('You', message, 'user');
        chatInput.value = '';
        
        // Simulate reply after 1 second
        setTimeout(() => {
          addMessage('Support', 'Thank you for your message. How can we help you today?', 'support');
        }, 1000);
      }
    }

    function addMessage(sender, text, type) {
      const messageDiv = document.createElement('div');
      messageDiv.classList.add('message', type);
      messageDiv.innerHTML = `<strong>${sender}:</strong> ${text}`;
      chatMessages.appendChild(messageDiv);
      chatMessages.scrollTop = chatMessages.scrollHeight;
    }

    // Theme Toggle Functionality
    themeToggle.addEventListener('click', () => {
      body.classList.toggle('dark-mode');
      
      // Change icon based on theme
      if (body.classList.contains('dark-mode')) {
        themeToggle.innerHTML = '<i class="fas fa-sun"></i>';
      } else {
        themeToggle.innerHTML = '<i class="fas fa-moon"></i>';
      }
    });

    // Play Music and Shake Animation on Profile Image Click
    profileImg.addEventListener('click', () => {
      // Toggle music playback
      if (isMusicPlaying) {
        backgroundMusic.pause();
        isMusicPlaying = false;
      } else {
        backgroundMusic.play().catch(e => console.log("Auto-play prevented:", e));
        isMusicPlaying = true;
      }
      
      // Add shake animation
      profileImg.classList.add('shake-and-bounce');
      setTimeout(() => {
        profileImg.classList.remove('shake-and-bounce');
      }, 1500);
    });

    // Image Slider Functionality
    const slider = document.getElementById('slider');
    const slides = document.querySelectorAll('.slide');
    const prevBtn = document.getElementById('prev');
    const nextBtn = document.getElementById('next');
    const dots = document.querySelectorAll('.slider-dot');
    
    let currentIndex = 0;
    const slideCount = slides.length;
    let slideInterval;

    function updateSlider() {
      slider.style.transform = `translateX(-${currentIndex * 100}%)`;
      
      // Update dots
      dots.forEach((dot, index) => {
        dot.classList.toggle('active', index === currentIndex);
      });
    }

    function goToSlide(index) {
      currentIndex = (index + slideCount) % slideCount;
      updateSlider();
      resetInterval();
    }

    function nextSlide() {
      goToSlide(currentIndex + 1);
    }

    function prevSlide() {
      goToSlide(currentIndex - 1);
    }

    function startInterval() {
      slideInterval = setInterval(nextSlide, 5000);
    }

    function resetInterval() {
      clearInterval(slideInterval);
      startInterval();
    }

    // Event listeners
    nextBtn.addEventListener('click', nextSlide);
    prevBtn.addEventListener('click', prevSlide);

    dots.forEach((dot, index) => {
      dot.addEventListener('click', () => goToSlide(index));
    });

    // Start the slider
    updateSlider();
    startInterval();

    // Audio Recording Functionality
    recordBtn.addEventListener('click', toggleRecording);

    function toggleRecording() {
      if (!isRecording) {
        startRecording();
      } else {
        stopRecording();
      }
    }

    function startRecording() {
      audioChunks = [];
      navigator.mediaDevices.getUserMedia({ audio: true })
        .then(stream => {
          mediaRecorder = new MediaRecorder(stream);
          mediaRecorder.start();
          
          mediaRecorder.ondataavailable = function(e) {
            audioChunks.push(e.data);
          };
          
          mediaRecorder.onstop = function() {
            const audioBlob = new Blob(audioChunks, { type: 'audio/wav' });
            const audioUrl = URL.createObjectURL(audioBlob);
            audioPlayback.src = audioUrl;
            audioPlayback.style.display = 'block';
            
            // Convert blob to base64 for form submission
            const reader = new FileReader();
            reader.readAsDataURL(audioBlob);
            reader.onloadend = function() {
              audioDataInput.value = reader.result;
            };
          };
          
          // Visualizer animation
          visualizerInterval = setInterval(() => {
            const randomWidth = Math.floor(Math.random() * 100);
            audioVisualizer.style.width = `${randomWidth}%`;
          }, 100);
          
          isRecording = true;
          recordBtn.innerHTML = '<i class="fas fa-stop"></i> Stop';
          recordBtn.style.backgroundColor = '#d44638';
        })
        .catch(err => {
          console.error('Error accessing microphone:', err);
          swal("Error", "Could not access microphone. Please check permissions.", "error");
        });
    }

    function stopRecording() {
      if (mediaRecorder && mediaRecorder.state !== 'inactive') {
        mediaRecorder.stop();
        clearInterval(visualizerInterval);
        audioVisualizer.style.width = '0%';
        isRecording = false;
        recordBtn.innerHTML = '<i class="fas fa-microphone"></i> Record';
        recordBtn.style.backgroundColor = '#0077b5';
        
        // Stop all tracks in the stream
        mediaRecorder.stream.getTracks().forEach(track => track.stop());
      }
    }

    // Stats toggle
    $(document).ready(function(){
      $('#following-stat').click(function(){
        $(this).find('.stat-value').toggle();
      });
      $('#followers-stat').click(function(){
        $(this).find('.stat-value').toggle();
      });
      
      // Sermons toggle
      $('#sermons-btn').click(function(){
        $('#testimonies').removeClass('active');
        $('#message-form').removeClass('active');
        $('#prayer-form').removeClass('active');
        
        if ($('#sermons').hasClass('active')) {
          $('#sermons').removeClass('active');
          $(this).html('<i class="fas fa-church"></i> Sermons');
        } else {
          $('#sermons').addClass('active');
          $(this).html('<i class="fas fa-church"></i> Close Sermons');
          $('#testimonies-btn').html('<i class="fas fa-hand-holding-heart"></i> Testimonies');
          $('#prayer-btn').html('<i class="fas fa-pray"></i> Prayer');
        }
      });
      
      // Testimonies toggle
      $('#testimonies-btn').click(function(){
        $('#sermons').removeClass('active');
        $('#message-form').removeClass('active');
        $('#prayer-form').removeClass('active');
        
        if ($('#testimonies').hasClass('active')) {
          $('#testimonies').removeClass('active');
          $(this).html('<i class="fas fa-hand-holding-heart"></i> Testimonies');
        } else {
          $('#testimonies').addClass('active');
          $(this).html('<i class="fas fa-hand-holding-heart"></i> Close Testimonies');
          $('#sermons-btn').html('<i class="fas fa-church"></i> Sermons');
          $('#prayer-btn').html('<i class="fas fa-pray"></i> Prayer');
        }
      });
      
      // Prayer toggle
      $('#prayer-btn').click(function(){
        $('#sermons').removeClass('active');
        $('#testimonies').removeClass('active');
        $('#message-form').removeClass('active');
        
        if ($('#prayer-form').hasClass('active')) {
          $('#prayer-form').removeClass('active');
          $(this).html('<i class="fas fa-pray"></i> Prayer');
        } else {
          $('#prayer-form').addClass('active');
          $(this).html('<i class="fas fa-pray"></i> Close Prayer');
          $('#sermons-btn').html('<i class="fas fa-church"></i> Sermons');
          $('#testimonies-btn').html('<i class="fas fa-hand-holding-heart"></i> Testimonies');
        }
      });
      
      // Form submission handling
      $('form').submit(function(e) {
        e.preventDefault();
        var form = $(this);
        var formData = new FormData(form[0]);
        
        $.ajax({
          url: form.attr('action'),
          method: form.attr('method'),
          data: formData,
          processData: false,
          contentType: false,
          dataType: 'json',
          success: function() {
            swal("Success!", "Your request has been submitted!", "success");
            form.trigger('reset');
            audioPlayback.style.display = 'none';
            audioDataInput.value = '';
            
            // Close the form if it's the prayer form
            if (form.attr('id') === 'prayer-form') {
              $('#prayer-form').removeClass('active');
              $('#prayer-btn').html('<i class="fas fa-pray"></i> Prayer');
            }
          },
          error: function() {
            swal("Oops!", "Something went wrong. Please try again.", "error");
          }
        });
      });
    });
  </script>
</body>
</html>
