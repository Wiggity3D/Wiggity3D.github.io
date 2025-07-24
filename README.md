<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wiggity</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700&family=Open+Sans:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #ffe066;
            --dark: #000000;
            --light: #ffffff;
            --gray: #222222;
            --light-gray: #444444;
            --transition: all 0.3s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Open Sans', sans-serif;
            background-color: var(--dark);
            color: var(--light);
            line-height: 1.6;
            overflow-x: hidden;
        }

        h1, h2, h3, h4, h5 {
            font-family: 'Montserrat', sans-serif;
            font-weight: 600;
            color: var(--primary);
        }

        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }

        section {
            padding: 100px 0;
            position: relative;
        }

        .section-title {
            text-align: center;
            margin-bottom: 60px;
            position: relative;
        }

        .section-title h2 {
            font-size: 2.5rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            display: inline-block;
            padding-bottom: 15px;
            position: relative;
        }

        .section-title h2::after {
            content: '';
            position: absolute;
            width: 60px;
            height: 3px;
            background: var(--primary);
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
        }

        .btn {
            display: inline-block;
            padding: 12px 28px;
            background: transparent;
            border: 2px solid var(--primary);
            color: var(--primary);
            text-decoration: none;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: var(--transition);
            cursor: pointer;
            font-size: 0.9rem;
        }

        .btn:hover {
            background: var(--primary);
            color: var(--dark);
        }

        /* Header & Navigation */
        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            background: rgba(0, 0, 0, 0.9);
            backdrop-filter: blur(10px);
            padding: 20px 0;
            transition: var(--transition);
        }

        header.scrolled {
            padding: 15px 0;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.5);
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--primary);
            text-decoration: none;
        }

        .logo span {
            color: var(--light);
        }

        .nav-links {
            display: flex;
            list-style: none;
        }

        .nav-links li {
            margin-left: 30px;
        }

        .nav-links a {
            color: var(--light);
            text-decoration: none;
            font-weight: 500;
            text-transform: uppercase;
            font-size: 0.9rem;
            letter-spacing: 1px;
            transition: var(--transition);
            position: relative;
        }

        .nav-links a:hover,
        .nav-links a.active {
            color: var(--primary);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            background: var(--primary);
            bottom: -5px;
            left: 0;
            transition: var(--transition);
        }

        .nav-links a:hover::after,
        .nav-links a.active::after {
            width: 100%;
        }

        .hamburger {
            display: none;
            cursor: pointer;
        }

        /* Hero Section */
        #hero {
            height: 100vh;
            display: flex;
            align-items: center;
            background: linear-gradient(rgba(0, 0, 0, 0.8), rgba(0, 0, 0, 0.8)), 
                        url('https://images.unsplash.com/photo-1533134486753-c833f0ed4866?ixlib=rb-4.0.3&auto=format&fit=crop&w=1950&q=80') no-repeat center center/cover;
            text-align: center;
            position: relative;
        }

        .hero-content {
            max-width: 800px;
            margin: 0 auto;
        }

        .hero-content h1 {
            font-size: 4rem;
            margin-bottom: 20px;
            text-transform: uppercase;
            letter-spacing: 3px;
        }

        .hero-content p {
            font-size: 1.2rem;
            margin-bottom: 30px;
            color: #ccc;
        }

        .hero-btns {
            display: flex;
            justify-content: center;
            gap: 20px;
        }

        .scroll-down {
            position: absolute;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            color: var(--light);
            font-size: 2rem;
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {
                transform: translateY(0) translateX(-50%);
            }
            40% {
                transform: translateY(-20px) translateX(-50%);
            }
            60% {
                transform: translateY(-10px) translateX(-50%);
            }
        }

        /* Showreel Section */
        #showreel {
            background: var(--gray);
        }

        .video-wrapper {
            position: relative;
            width: 100%;
            padding-top: 56.25%; /* 16:9 Aspect Ratio */
            border: 3px solid var(--primary);
            border-radius: 5px;
            overflow: hidden;
        }

        .video-wrapper iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }

        /* Gallery Section */
        .gallery-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 25px;
        }

        .gallery-item {
            position: relative;
            overflow: hidden;
            border-radius: 5px;
            aspect-ratio: 16/9;
            background: var(--light-gray);
            cursor: pointer;
            border: 2px solid transparent;
            transition: var(--transition);
        }

        .gallery-item:hover {
            border-color: var(--primary);
            transform: translateY(-10px);
        }

        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: var(--transition);
        }

        .gallery-item:hover img {
            opacity: 0.3;
        }

        .gallery-item .video-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transition: var(--transition);
        }

        .gallery-item:hover .video-overlay {
            opacity: 1;
        }

        .gallery-item .play-icon {
            font-size: 4rem;
            color: var(--primary);
            opacity: 0.8;
        }

        .gallery-item .item-title {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            padding: 15px;
            background: rgba(0, 0, 0, 0.8);
            transform: translateY(100%);
            transition: var(--transition);
        }

        .gallery-item:hover .item-title {
            transform: translateY(0);
        }

        /* Services Section */
        #services {
            background: var(--gray);
        }

        .services-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .service-card {
            background: rgba(255, 224, 102, 0.05);
            padding: 40px 30px;
            text-align: center;
            border-radius: 5px;
            transition: var(--transition);
            border: 1px solid rgba(255, 224, 102, 0.1);
        }

        .service-card:hover {
            transform: translateY(-10px);
            background: rgba(255, 224, 102, 0.1);
            border-color: rgba(255, 224, 102, 0.3);
        }

        .service-icon {
            font-size: 3rem;
            color: var(--primary);
            margin-bottom: 20px;
        }

        .service-card h3 {
            margin-bottom: 15px;
            font-size: 1.4rem;
        }

        /* Clients Section */
        .clients-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 40px;
            margin-top: 50px;
        }

        .client-item {
            width: 150px;
            height: 80px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 5px;
            transition: var(--transition);
        }

        .client-item:hover {
            transform: scale(1.05);
            background: rgba(255, 224, 102, 0.1);
        }

        .client-item img {
            max-width: 100%;
            max-height: 100%;
            filter: grayscale(100%);
            transition: var(--transition);
        }

        .client-item:hover img {
            filter: grayscale(0%);
        }

        /* About Section */
        #about {
            background: var(--gray);
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 50px;
            align-items: center;
        }

        .about-image {
            position: relative;
            border-radius: 5px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }

        .about-image img {
            width: 100%;
            display: block;
        }

        .about-image::before {
            content: '';
            position: absolute;
            top: 20px;
            left: 20px;
            right: 20px;
            bottom: 20px;
            border: 2px solid var(--primary);
            z-index: 1;
            border-radius: 5px;
        }

        .about-text h3 {
            font-size: 2rem;
            margin-bottom: 20px;
        }

        .about-text p {
            margin-bottom: 20px;
            color: #ccc;
        }

        .skills-container {
            margin-top: 30px;
        }

        .skill {
            margin-bottom: 20px;
        }

        .skill-info {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
        }

        .skill-bar {
            height: 8px;
            background: var(--light-gray);
            border-radius: 4px;
            overflow: hidden;
        }

        .skill-progress {
            height: 100%;
            background: var(--primary);
            border-radius: 4px;
        }

        /* Contact Section */
        .contact-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 50px;
        }

        .contact-info h3 {
            font-size: 1.5rem;
            margin-bottom: 20px;
        }

        .contact-details {
            margin-bottom: 30px;
        }

        .contact-item {
            display: flex;
            align-items: flex-start;
            margin-bottom: 20px;
        }

        .contact-icon {
            font-size: 1.2rem;
            color: var(--primary);
            margin-right: 15px;
            min-width: 20px;
        }

        .contact-text h4 {
            color: var(--light);
            margin-bottom: 5px;
        }

        .social-links {
            display: flex;
            gap: 15px;
        }

        .social-links a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(255, 224, 102, 0.1);
            color: var(--primary);
            font-size: 1.2rem;
            transition: var(--transition);
        }

        .social-links a:hover {
            background: var(--primary);
            color: var(--dark);
            transform: translateY(-5px);
        }

        .contact-form .form-group {
            margin-bottom: 20px;
        }

        .contact-form input,
        .contact-form textarea {
            width: 100%;
            padding: 12px 15px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 5px;
            color: var(--light);
            font-family: 'Open Sans', sans-serif;
            transition: var(--transition);
        }

        .contact-form input:focus,
        .contact-form textarea:focus {
            outline: none;
            border-color: var(--primary);
            background: rgba(255, 224, 102, 0.05);
        }

        .contact-form textarea {
            min-height: 150px;
            resize: vertical;
        }

        /* Footer */
        footer {
            background: var(--gray);
            padding: 40px 0;
            text-align: center;
        }

        .footer-content {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .footer-logo {
            font-size: 2rem;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 20px;
        }

        .footer-links {
            display: flex;
            list-style: none;
            margin-bottom: 30px;
        }

        .footer-links li {
            margin: 0 15px;
        }

        .footer-links a {
            color: var(--light);
            text-decoration: none;
            transition: var(--transition);
        }

        .footer-links a:hover {
            color: var(--primary);
        }

        .copyright {
            color: #aaa;
            font-size: 0.9rem;
        }

        /* Responsive Design */
        @media (max-width: 992px) {
            .about-content,
            .contact-container {
                grid-template-columns: 1fr;
                gap: 40px;
            }
            
            .about-image {
                max-width: 500px;
                margin: 0 auto;
            }
        }

        @media (max-width: 768px) {
            .nav-links {
                position: fixed;
                top: 80px;
                right: -100%;
                width: 250px;
                height: calc(100vh - 80px);
                background: rgba(0, 0, 0, 0.9);
                flex-direction: column;
                padding: 40px 0;
                transition: var(--transition);
            }

            .nav-links.active {
                right: 0;
            }

            .nav-links li {
                margin: 15px 0;
                text-align: center;
            }

            .hamburger {
                display: block;
                color: var(--light);
                font-size: 1.5rem;
            }

            .hero-content h1 {
                font-size: 3rem;
            }

            .section-title h2 {
                font-size: 2rem;
            }

            section {
                padding: 70px 0;
            }
        }

        @media (max-width: 576px) {
            .hero-content h1 {
                font-size: 2.2rem;
            }
            
            .hero-btns {
                flex-direction: column;
                gap: 15px;
            }
            
            .gallery-container {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Header & Navigation -->
    <header>
        <div class="container">
            <nav>
                <a href="#" class="logo">Wiggity<span>3D</span></a>
                <ul class="nav-links">
                    <li><a href="#hero" class="active">Home</a></li>
                    <li><a href="#showreel">Showreel</a></li>
                    <li><a href="#gallery">Gallery</a></li>
                    <li><a href="#services">Services</a></li>
                    <li><a href="#clients">Clients</a></li>
                    <li><a href="#about">About</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
                <div class="hamburger">
                    <i class="fas fa-bars"></i>
                </div>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section id="hero">
        <div class="container">
            <div class="hero-content">
                <h1>Creative Visual Storytelling</h1>
                <p>I create compelling video content that engages audiences and tells your brand's story in a memorable way.</p>
                <div class="hero-btns">
                    <a href="#gallery" class="btn">View My Work</a>
                    <a href="#contact" class="btn">Get In Touch</a>
                </div>
            </div>
        </div>
        <a href="#showreel" class="scroll-down">
            <i class="fas fa-chevron-down"></i>
        </a>
    </section>

    <!-- Showreel Section -->
    <section id="showreel">
        <div class="container">
            <div class="section-title">
                <h2>Showreel</h2>
            </div>
            <div class="video-wrapper">
                <iframe src="https://www.youtube.com/embed/dQw4w9WgXcQ?controls=0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
            </div>
        </div>
    </section>

    <!-- Gallery Section -->
    <section id="gallery">
        <div class="container">
            <div class="section-title">
                <h2>Video Gallery</h2>
            </div>
            <div class="gallery-container">
                <!-- Video items will be added here dynamically -->
            </div>
        </div>
    </section>

    <!-- Services Section -->
    <section id="services">
        <div class="container">
            <div class="section-title">
                <h2>Services Offered</h2>
            </div>
            <div class="services-container">
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-video"></i>
                    </div>
                    <h3>Video Production</h3>
                    <p>Full-service video production from concept development to final delivery for commercials, corporate videos, and social media content.</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-film"></i>
                    </div>
                    <h3>Editing & Post-Production</h3>
                    <p>Professional editing, color grading, sound design, and visual effects to bring your footage to life.</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-photo-video"></i>
                    </div>
                    <h3>Motion Graphics</h3>
                    <p>Dynamic animations and graphics that enhance storytelling and engage your audience.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Clients Section -->
    <section id="clients">
        <div class="container">
            <div class="section-title">
                <h2>Clients</h2>
            </div>
            <div class="clients-container">
                <div class="client-item">
                    <img src="https://via.placeholder.com/150x80/333333/FFFFFF?text=Client+1" alt="Client 1">
                </div>
                <div class="client-item">
                    <img src="https://via.placeholder.com/150x80/333333/FFFFFF?text=Client+2" alt="Client 2">
                </div>
                <div class="client-item">
                    <img src="https://via.placeholder.com/150x80/333333/FFFFFF?text=Client+3" alt="Client 3">
                </div>
                <div class="client-item">
                    <img src="https://via.placeholder.com/150x80/333333/FFFFFF?text=Client+4" alt="Client 4">
                </div>
                <div class="client-item">
                    <img src="https://via.placeholder.com/150x80/333333/FFFFFF?text=Client+5" alt="Client 5">
                </div>
                <div class="client-item">
                    <img src="https://via.placeholder.com/150x80/333333/FFFFFF?text=Client+6" alt="Client 6">
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about">
        <div class="container">
            <div class="section-title">
                <h2>About Me</h2>
            </div>
            <div class="about-content">
                <div class="about-image">
                    <img src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80" alt="Wiggity">
                </div>
                <div class="about-text">
                    <h3>Professional Video Creator & Editor</h3>
                    <p>With over 7 years of experience in the video production industry, I specialize in creating compelling visual content that tells stories and engages audiences. My passion lies in transforming ideas into captivating visual experiences.</p>
                    <p>I've worked with diverse clients across multiple industries, helping them communicate their message through high-quality video content. From concept development to final delivery, I ensure every project meets the highest standards.</p>
                    <div class="skills-container">
                        <h4>My Skillset</h4>
                        <div class="skill">
                            <div class="skill-info">
                                <span>Video Editing</span>
                                <span>95%</span>
                            </div>
                            <div class="skill-bar">
                                <div class="skill-progress" style="width: 95%"></div>
                            </div>
                        </div>
                        <div class="skill">
                            <div class="skill-info">
                                <span>Cinematography</span>
                                <span>90%</span>
                            </div>
                            <div class="skill-bar">
                                <div class="skill-progress" style="width: 90%"></div>
                            </div>
                        </div>
                        <div class="skill">
                            <div class="skill-info">
                                <span>Motion Graphics</span>
                                <span>85%</span>
                            </div>
                            <div class="skill-bar">
                                <div class="skill-progress" style="width: 85%"></div>
                            </div>
                        </div>
                        <div class="skill">
                            <div class="skill-info">
                                <span>Color Grading</span>
                                <span>80%</span>
                            </div>
                            <div class="skill-bar">
                                <div class="skill-progress" style="width: 80%"></div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact">
        <div class="container">
            <div class="section-title">
                <h2>Contact Me</h2>
            </div>
            <div class="contact-container">
                <div class="contact-info">
                    <h3>Get In Touch</h3>
                    <div class="contact-details">
                        <div class="contact-item">
                            <div class="contact-icon">
                                <i class="fas fa-map-marker-alt"></i>
                            </div>
                            <div class="contact-text">
                                <h4>Location</h4>
                                <p>London, United Kingdom</p>
                            </div>
                        </div>
                        <div class="contact-item">
                            <div class="contact-icon">
                                <i class="fas fa-envelope"></i>
                            </div>
                            <div class="contact-text">
                                <h4>Email</h4>
                                <p>wiggityvik@gmail.com</p>
                            </div>
                        </div>
                        <div class="contact-item">
                            <div class="contact-icon">
                                <i class="fas fa-phone"></i>
                            </div>
                            <div class="contact-text">
                                <h4>Phone</h4>
                                <p>+44 123 456 7890</p>
                            </div>
                        </div>
                    </div>
                    <div class="social-links">
                        <a href="#"><i class="fab fa-youtube"></i></a>
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fab fa-vimeo-v"></i></a>
                        <a href="#"><i class="fab fa-linkedin-in"></i></a>
                    </div>
                </div>
                <div class="contact-form">
                    <form id="contactForm">
                        <div class="form-group">
                            <input type="text" placeholder="Your Name" required>
                        </div>
                        <div class="form-group">
                            <input type="email" placeholder="Your Email" required>
                        </div>
                        <div class="form-group">
                            <input type="text" placeholder="Subject">
                        </div>
                        <div class="form-group">
                            <textarea placeholder="Your Message" required></textarea>
                        </div>
                        <button type="submit" class="btn">Send Message</button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-logo">Wiggity</div>
                <ul class="footer-links">
                    <li><a href="#hero">Home</a></li>
                    <li><a href="#showreel">Showreel</a></li>
                    <li><a href="#gallery">Gallery</a></li>
                    <li><a href="#services">Services</a></li>
                    <li><a href="#clients">Clients</a></li>
                    <li><a href="#about">About</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
                <div class="copyright">
                    &copy; 2023 Wiggity. All Rights Reserved.
                </div>
            </div>
        </div>
    </footer>

    <script>
        // Sample video data
        const videos = [
            { id: "dQw4w9WgXcQ", title: "Music Video Project", thumbnail: "https://i.ytimg.com/vi/dQw4w9WgXcQ/maxresdefault.jpg" },
            { id: "jNQXAC9IVRw", title: "Commercial Campaign", thumbnail: "https://i.ytimg.com/vi/jNQXAC9IVRw/maxresdefault.jpg" },
            { id: "oHg5SJYRHA0", title: "Corporate Event Coverage", thumbnail: "https://i.ytimg.com/vi/oHg5SJYRHA0/maxresdefault.jpg" },
            { id: "DLzxrzFCyOs", title: "Documentary Short", thumbnail: "https://i.ytimg.com/vi/DLzxrzFCyOs/maxresdefault.jpg" },
            { id: "kfVsfOSbJY0", title: "Product Launch Video", thumbnail: "https://i.ytimg.com/vi/kfVsfOSbJY0/maxresdefault.jpg" },
            { id: "gkTb9GP9lVI", title: "Travel Film", thumbnail: "https://i.ytimg.com/vi/gkTb9GP9lVI/maxresdefault.jpg" }
        ];

        // Generate gallery items
        const galleryContainer = document.querySelector('.gallery-container');
        videos.forEach(video => {
            const galleryItem = document.createElement('div');
            galleryItem.className = 'gallery-item';
            galleryItem.innerHTML = `
                <img src="${video.thumbnail}" alt="${video.title}">
                <div class="video-overlay">
                    <i class="fas fa-play play-icon"></i>
                </div>
                <div class="item-title">
                    <h3>${video.title}</h3>
                </div>
            `;
            galleryContainer.appendChild(galleryItem);

            // Add hover play functionality
            galleryItem.addEventListener('mouseenter', function() {
                const videoPlayer = document.createElement('iframe');
                videoPlayer.src = `https://www.youtube.com/embed/${video.id}?autoplay=1&mute=1&controls=0&loop=1`;
                videoPlayer.setAttribute('frameborder', '0');
                videoPlayer.setAttribute('allow', 'accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture');
                videoPlayer.setAttribute('allowfullscreen', '');
                videoPlayer.style.width = '100%';
                videoPlayer.style.height = '100%';
                videoPlayer.style.position = 'absolute';
                videoPlayer.style.top = '0';
                videoPlayer.style.left = '0';
                
                this.innerHTML = '';
                this.appendChild(videoPlayer);
                this.querySelector('.item-title').style.display = 'none';
            });

            galleryItem.addEventListener('mouseleave', function() {
                this.innerHTML = `
                    <img src="${video.thumbnail}" alt="${video.title}">
                    <div class="video-overlay">
                        <i class="fas fa-play play-icon"></i>
                    </div>
                    <div class="item-title">
                        <h3>${video.title}</h3>
                    </div>
                `;
            });
        });

        // Header scroll effect
        window.addEventListener('scroll', function() {
            const header = document.querySelector('header');
            if (window.scrollY > 50) {
                header.classList.add('scrolled');
            } else {
                header.classList.remove('scrolled');
            }
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
                    
                    // Update active nav link
                    document.querySelectorAll('.nav-links a').forEach(link => {
                        link.classList.remove('active');
                    });
                    this.classList.add('active');
                }
            });
        });

        // Mobile menu toggle
        const hamburger = document.querySelector('.hamburger');
        const navLinks = document.querySelector('.nav-links');
        
        hamburger.addEventListener('click', function() {
            navLinks.classList.toggle('active');
        });

        // Close mobile menu when clicking a link
        document.querySelectorAll('.nav-links a').forEach(link => {
            link.addEventListener('click', function() {
                navLinks.classList.remove('active');
            });
        });

        // Form submission
        const contactForm = document.getElementById('contactForm');
        contactForm.addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Thank you for your message! I will get back to you soon.');
            contactForm.reset();
        });

        // Initialize active nav link based on scroll position
        window.addEventListener('scroll', function() {
            const sections = document.querySelectorAll('section');
            const navLinks = document.querySelectorAll('.nav-links a');
            
            let current = '';
            sections.forEach(section => {
                const sectionTop = section.offsetTop;
                const sectionHeight = section.clientHeight;
                if (pageYOffset >= (sectionTop - 100)) {
                    current = section.getAttribute('id');
                }
            });
            
            navLinks.forEach(link => {
                link.classList.remove('active');
                if (link.getAttribute('href') === `#${current}`) {
                    link.classList.add('active');
                }
            });
        });
    </script>
</body>
</html>
