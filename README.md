<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ASC Portfolio by Mohit</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.11.4/gsap.min.js"></script>
    <style>
        :root {
            --primary: #3a4a6d;
            --secondary: #5d6d8a;
            --accent: #a2b5d0;
            --light-accent: #f5f7fa;
            --dark-accent: #2c3e50;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: var(--light-accent);
            color: var(--dark-accent);
            overflow-x: hidden;
        }

        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        
        ::-webkit-scrollbar-track {
            background: rgba(255, 255, 255, 0.8);
        }
        
        ::-webkit-scrollbar-thumb {
            background: var(--primary);
            border-radius: 4px;
        }
        
        /* Navigation */
        .nav-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 5%;
            background: rgba(255, 255, 255, 0.95);
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
            transition: all 0.4s ease;
        }
        
        .logo {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary);
            text-decoration: none;
            display: flex;
            align-items: center;
        }
        
        .logo span {
            color: var(--accent);
            margin-left: 5px;
        }
        
        .nav-logo-icon {
            width: 30px;
            height: 30px;
            background: var(--primary);
            border-radius: 50%;
            margin-right: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 16px;
            color: white;
        }
        
        .nav-links {
            display: flex;
            list-style: none;
        }
        
        .nav-links li {
            margin-left: 30px;
        }
        
        .nav-links a {
            color: var(--dark-accent);
            text-decoration: none;
            font-size: 15px;
            font-weight: 500;
            position: relative;
            transition: all 0.3s ease;
            padding: 5px 0;
        }
        
        .nav-links a:hover {
            color: var(--primary);
        }
        
        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary);
            transition: width 0.3s ease;
        }
        
        .nav-links a:hover::after {
            width: 100%;
        }
        
        .menu-toggle {
            display: none;
            cursor: pointer;
            font-size: 24px;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            width: 100%;
            position: relative;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            background: linear-gradient(135deg, var(--light-accent), var(--accent));
        }
        
        .hero-content {
            text-align: center;
            padding: 0 20px;
            max-width: 1000px;
            z-index: 2;
        }
        
        .hero h1 {
            font-size: 48px;
            font-weight: 700;
            margin-bottom: 20px;
            line-height: 1.2;
            color: var(--dark-accent);
        }
        
        .hero p {
            font-size: 18px;
            margin-bottom: 40px;
            color: var(--dark-accent);
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .btn {
            display: inline-flex;
            align-items: center;
            background: transparent;
            color: var(--dark-accent);
            padding: 12px 30px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
            border: 2px solid var(--primary);
            margin: 0 10px;
            position: relative;
            overflow: hidden;
        }
        
        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: var(--primary);
            transition: all 0.4s ease;
            z-index: -1;
        }
        
        .btn:hover {
            color: #fff;
        }
        
        .btn:hover::before {
            left: 0;
        }
        
        .btn i {
            margin-right: 10px;
            transition: transform 0.3s ease;
        }
        
        .btn:hover i {
            transform: translateX(5px);
        }
        
        /* Portfolio Section */
        .portfolio-section {
            padding: 100px 5%;
            background-color: var(--light-accent);
        }
        
        .section-title {
            font-size: 36px;
            margin-bottom: 20px;
            position: relative;
            display: inline-block;
            color: var(--dark-accent);
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            left: 0;
            bottom: -10px;
            width: 60px;
            height: 4px;
            background: var(--primary);
        }
        
        .portfolio-filters {
            display: flex;
            justify-content: center;
            margin-bottom: 40px;
            flex-wrap: wrap;
        }
        
        .filter-btn {
            background: transparent;
            border: 2px solid var(--primary);
            color: var(--dark-accent);
            padding: 8px 20px;
            cursor: pointer;
            margin: 5px;
            font-size: 16px;
            transition: all 0.3s ease;
            position: relative;
            border-radius: 30px;
        }
        
        .filter-btn:hover,
        .filter-btn.active {
            background: var(--primary);
            color: white;
        }
        
        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 30px;
        }
        
        .portfolio-item {
            position: relative;
            border-radius: 10px;
            overflow: hidden;
            cursor: pointer;
            height: 400px;
            background: white;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            transition: all 0.5s ease;
        }
        
        .portfolio-item:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(58, 74, 109, 0.15);
        }
        
        .portfolio-content {
            padding: 30px;
            height: 100%;
            display: flex;
            flex-direction: column;
        }
        
        .portfolio-icon {
            width: 60px;
            height: 60px;
            background: var(--primary);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 20px;
            font-size: 24px;
            color: white;
        }
        
        .portfolio-title {
            font-size: 24px;
            margin-bottom: 15px;
            color: var(--dark-accent);
        }
        
        .portfolio-category {
            color: var(--primary);
            margin-bottom: 15px;
            font-size: 14px;
        }
        
        .portfolio-description {
            color: var(--dark-accent);
            line-height: 1.6;
            margin-bottom: 20px;
            flex-grow: 1;
        }
        
        .portfolio-tech-stack {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 20px;
        }
        
        .tech-tag {
            font-size: 11px;
            padding: 5px 15px;
            background: var(--accent);
            color: var(--dark-accent);
            border-radius: 10px;
        }
        
        .portfolio-links {
            display: flex;
            gap: 15px;
        }
        
        .portfolio-link {
            display: inline-flex;
            align-items: center;
            color: var(--primary);
            text-decoration: none;
            transition: all 0.3s ease;
            font-size: 14px;
        }
        
        .portfolio-link i {
            margin-right: 8px;
            transition: transform 0.3s ease;
        }
        
        .portfolio-item:hover .portfolio-link {
            color: var(--dark-accent);
        }
        
        .portfolio-link:hover i {
            transform: translateX(5px);
        }

        /* Project Modal */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 100;
            opacity: 0;
            visibility: hidden;
            transition: all 0.4s ease;
        }
        
        .modal.active {
            opacity: 1;
            visibility: visible;
        }
        
        .modal-content {
            width: 80%;
            max-width: 1000px;
            background: white;
            border-radius: 15px;
            overflow: hidden;
            position: relative;
            transform: scale(0.8);
            transition: all 0.4s ease;
        }
        
        .modal.active .modal-content {
            transform: scale(1);
        }
        
        .modal-close {
            position: absolute;
            top: 20px;
            right: 20px;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(0, 0, 0, 0.5);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            cursor: pointer;
            z-index: 10;
        }
        
        .modal-header {
            padding: 30px;
            border-bottom: 1px solid rgba(0, 0, 0, 0.1);
        }
        
        .modal-title {
            font-size: 28px;
            font-weight: 700;
            margin-bottom: 10px;
            color: var(--dark-accent);
        }
        
        .modal-category {
            font-size: 16px;
            color: var(--primary);
        }
        
        .modal-body {
            padding: 30px;
        }
        
        .modal-image {
            width: 100%;
            height: 300px;
            background-size: cover;
            background-position: center;
            margin-bottom: 30px;
            border-radius: 10px;
        }
        
        .modal-description {
            font-size: 16px;
            color: var(--dark-accent);
            line-height: 1.8;
            margin-bottom: 30px;
        }
        
        .modal-tech-stack {
            margin-bottom: 30px;
        }
        
        .modal-tech-title {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 15px;
            color: var(--dark-accent);
        }
        
        .modal-tech-list {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .modal-tech-tag {
            font-size: 14px;
            padding: 8px 16px;
            background: var(--accent);
            color: var(--dark-accent);
            border-radius: 15px;
        }
        
        .modal-features {
            margin-bottom: 30px;
        }
        
        .modal-feature-title {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 15px;
            color: var(--dark-accent);
        }
        
        .modal-feature-list {
            list-style: none;
        }
        
        .modal-feature-list li {
            margin-bottom: 10px;
            padding-left: 25px;
            position: relative;
            color: var(--dark-accent);
        }
        
        .modal-feature-list li::before {
            content: '\f00c';
            font-family: 'Font Awesome 5 Free';
            font-weight: 900;
            position: absolute;
            left: 0;
            color: var(--primary);
        }
        
        .modal-links {
            display: flex;
            gap: 15px;
        }
        
        .modal-link {
            padding: 12px 25px;
            background: var(--primary);
            color: white;
            border-radius: 50px;
            text-decoration: none;
            transition: all 0.3s ease;
            font-weight: 500;
        }
        
        .modal-link:hover {
            background: var(--secondary);
            transform: translateY(-3px);
        }
        
        /* CTA Section */
        .cta-section {
            padding: 100px 5%;
            text-align: center;
            background-color: var(--primary);
            color: white;
        }
        
        .cta-section h2 {
            font-size: 28px;
            margin-bottom: 20px;
        }
        
        .cta-section p {
            font-size: 18px;
            margin-bottom: 30px;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
        }
        
        /* Footer */
        .footer {
            padding: 50px 5%;
            background: var(--primary);
            text-align: center;
            color: white;
        }
        
        .footer-logo {
            font-size: 24px;
            font-weight: 700;
            color: white;
            margin-bottom: 20px;
            display: inline-block;
        }
        
        .footer-logo span {
            color: var(--accent);
        }
        
        .footer-text {
            color: rgba(255, 255, 255, 0.8);
            line-height: 1.6;
            margin-bottom: 30px;
        }
        
        .footer-social {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .footer-social-link {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            transition: all 0.3s ease;
            text-decoration: none;
        }
        
        .footer-social-link:hover {
            background: var(--accent);
            color: var(--dark-accent);
            transform: translateY(-5px);
        }
        
        .footer-bottom {
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            padding-top: 30px;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
        }
        
        .footer-copyright {
            color: rgba(255, 255, 255, 0.8);
            margin-right: 20px;
        }
        
        /* Back to Top Button */
        .back-to-top {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 50px;
            height: 50px;
            background: var(--primary);
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            text-decoration: none;
            z-index: 999;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .back-to-top.active {
            opacity: 1;
            visibility: visible;
        }
        
        .back-to-top:hover {
            background: var(--secondary);
            transform: translateY(-5px);
        }
        
        /* Responsive Design */
        @media (max-width: 1024px) {
            .portfolio-grid {
                grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            }
        }
        
        @media (max-width: 768px) {
            .nav-links {
                position: fixed;
                top: 0;
                right: -100%;
                width: 70%;
                height: 100vh;
                background: white;
                flex-direction: column;
                align-items: center;
                justify-content: center;
                transition: right 0.3s ease;
                z-index: 1000;
                box-shadow: -5px 0 15px rgba(0, 0, 0, 0.1);
            }
            
            .nav-links.active {
                right: 0;
            }
            
            .nav-links li {
                margin: 20px 0;
            }
            
            .menu-toggle {
                display: block;
                z-index: 1001;
            }
            
            .hero h1 {
                font-size: 36px;
            }
            
            .hero p {
                font-size: 16px;
            }
        }
        
        @media (max-width: 576px) {
            .hero h1 {
                font-size: 28px;
            }
            
            .btn {
                padding: 10px 20px;
                font-size: 14px;
            }
            
            .portfolio-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <div class="nav-container">
        <a href="#" class="logo">
            <div class="nav-logo-icon">AS</div>
            Anant<span>Soft Computing</span>
        </a>
        
        <div class="menu-toggle">
            <i class="fas fa-bars"></i>
        </div>
        
        <ul class="nav-links">
            <li><a href="#home">Home</a></li>
            <li><a href="#portfolio">Portfolio</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </div>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="hero-content">
            <h1>Anant Soft Computing</h1>
            <h1>Project Portfolio</h1>
            <p>Explore our innovative solutions that transform businesses and industries.</p>
            <div>
                <a href="#portfolio" class="btn"><i class="fas fa-rocket"></i> Explore Projects</a>
            </div>
        </div>
    </section>

    <!-- Portfolio Section -->
    <section id="portfolio" class="portfolio-section">
        <div class="container">
            <h2 class="section-title">Featured Projects</h2>
            <div class="portfolio-filters">
                <button class="filter-btn active" data-filter="all">All</button>
                <button class="filter-btn" data-filter="crm">CRM Solutions</button>
                <button class="filter-btn" data-filter="education">Education</button>
                <button class="filter-btn" data-filter="social">Social Welfare</button>
                <button class="filter-btn" data-filter="ai">AI/ML</button>
            </div>
            <div class="portfolio-grid">
                <div class="portfolio-item" data-category="crm">
                    <div class="portfolio-content">
                        <div class="portfolio-icon">
                            <i class="fas fa-tasks"></i>
                        </div>
                        <h3 class="portfolio-title">FlyUrDream</h3>
                        
                        <p class="portfolio-category">CRM & Website Solution</p>
                        <p class="portfolio-description">Empowering businesses to manage and nurture customer relationships effectively, driving growth and customer loyalty.</p>
                        <div class="portfolio-tech-stack">
                            <span class="tech-tag">Bootstrap</span>
                            <span class="tech-tag">CSS</span>
                            <span class="tech-tag">Django</span>
                            <span class="tech-tag">HTML</span>
                            <span class="tech-tag">JavaScript</span>
                            <span class="tech-tag">NodeJS</span>
                            <span class="tech-tag">Python</span>
                            <span class="tech-tag">ReactJS</span>
                        </div>
                        <div class="portfolio-links">
                            <a href="https://flyurdream.com" class="portfolio-link"><i class="fas fa-link"></i> Live Demo</a>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item" data-category="crm">
                    <div class="portfolio-content">
                        <div class="portfolio-icon">
                            <i class="fas fa-users"></i>
                        </div>
                        <h3 class="portfolio-title">OEC</h3>
                        <p class="portfolio-category">CRM & Website Solution</p>
                        <p class="portfolio-description">Providing virtual classroom experiences with live classes and collaborative tools for enhanced learning experiences.</p>
                        <div class="portfolio-tech-stack">
                            <span class="tech-tag">Firebase</span>
                            <span class="tech-tag">NodeJS</span>
                            <span class="tech-tag">VueJS</span>
                        </div>
                        <div class="portfolio-links">
                            <a href="https://oecindia.com" class="portfolio-link"><i class="fas fa-link"></i> Live Demo</a>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item" data-category="education">
                    <div class="portfolio-content">
                        <div class="portfolio-icon">
                            <i class="fas fa-chalkboard-teacher"></i>
                        </div>
                        <h3 class="portfolio-title">ESPI online</h3>
                        <p class="portfolio-category">E-Learning Platform</p>
                        <p class="portfolio-description">Real-time virtual classroom for remote learning, offering interactive live classes and attendance tracking.</p>
                        <div class="portfolio-tech-stack">
                            <span class="tech-tag">Firebase</span>
                            <span class="tech-tag">NodeJS</span>
                            <span class="tech-tag">VueJS</span>
                        </div>
                        <div class="portfolio-links">
                            <a href="https://espionline.in" class="portfolio-link"><i class="fas fa-link"></i> Live Demo</a>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item" data-category="social">
                    <div class="portfolio-content">
                        <div class="portfolio-icon">
                            <i class="fas fa-hands-helping"></i>
                        </div>
                        <h3 class="portfolio-title">Indraprasth Foundation</h3>
                        <p class="portfolio-category">Social Welfare</p>
                        <p class="portfolio-description">Empowering communities through social welfare initiatives focusing on education, healthcare, and skill development.</p>
                        <div class="portfolio-tech-stack">
                            <span class="tech-tag">MUI</span>
                            <span class="tech-tag">ReactJS</span>
                        </div>
                        <div class="portfolio-links">
                            <a href="https://indraprasthfoundation.org/" class="portfolio-link"><i class="fas fa-link"></i> Live Demo</a>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item" data-category="education">
                    <div class="portfolio-content">
                        <div class="portfolio-icon">
                            <i class="fas fa-graduation-cap"></i>
                        </div>
                        <h3 class="portfolio-title">Edustation</h3>
                        <p class="portfolio-category">Educational Tools</p>
                        <p class="portfolio-description">Cutting-edge educational tools and platforms to enhance learning experiences with personalized learning paths.</p>
                        <div class="portfolio-tech-stack">
                            <span class="tech-tag">Bootstrap</span>
                            <span class="tech-tag">PHP</span>
                        </div>
                        <div class="portfolio-links">
                            <a href="https://www.edustation.online/" class="portfolio-link"><i class="fas fa-link"></i> Live Demo</a>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item" data-category="ai">
                    <div class="portfolio-content">
                        <div class="portfolio-icon">
                            <i class="fas fa-brain"></i>
                        </div>
                        <h3 class="portfolio-title">StudyStreak</h3>
                        <p class="portfolio-category">AI-Powered Learning</p>
                        <p class="portfolio-description">Helping students stay focused and build lasting study routines through personalized study plans and analytics.</p>
                        <div class="portfolio-tech-stack">
                            <span class="tech-tag">NodeJS</span>
                            <span class="tech-tag">Python</span>
                            <span class="tech-tag">ReactJS</span>
                            <span class="tech-tag">Tailwind</span>
                        </div>
                        <div class="portfolio-links">
                            <a href="https://studystreak.in" class="portfolio-link"><i class="fas fa-link"></i> Live Demo</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- CTA Section -->
    <section class="cta-section">
        <div class="container">
            <p>If you want to grow your business then click below</p>
            <a href="tel:+916351484373" class="btn">Connect with Us</a>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <a href="#" class="footer-logo">Anant<span> Soft Computing</span></a>
            <p class="footer-text">Transforming businesses through innovative software solutions and digital excellence.</p>
            <div class="footer-social">
                <a href="https://www.facebook.com/anantsoftcomputing/" class="footer-social-link"><i class="fab fa-facebook-f"></i></a>
                <a href="https://twitter.com/anantsoftcomp" class="footer-social-link"><i class="fab fa-twitter"></i></a>
                <a href="https://in.linkedin.com/company/anant-soft-computing" class="footer-social-link"><i class="fab fa-linkedin-in"></i></a>
                <a href="https://www.instagram.com/anantsoftcomputing/" class="footer-social-link"><i class="fab fa-instagram"></i></a>
            </div>
            <div class="footer-bottom">
                <p class="footer-copyright">© 2023 Anant Soft Computing. All Rights Reserved.</p>
            </div>
        </div>
    </footer>

    <!-- Project Modal -->
    <div id="project-modal" class="modal">
        <div class="modal-content">
            <div class="modal-close">
                <i class="fas fa-times"></i>
            </div>
            <div class="modal-header">
                <h2 class="modal-title"></h2>
                <p class="modal-category"></p>
            </div>
            <div class="modal-body">
                <div class="modal-image"></div>
                <p class="modal-description"></p>
                <div class="modal-tech-stack">
                    <h3 class="modal-tech-title">Technologies Used</h3>
                    <div class="modal-tech-list"></div>
                </div>
                <div class="modal-features">
                    <h3 class="modal-feature-title">Key Features</h3>
                    <ul class="modal-feature-list"></ul>
                </div>
                <div class="modal-links">
                    <a href="#" class="modal-link">View Demo</a>
                    <a href="#" class="modal-link">View Code</a>
                </div>
            </div>
        </div>
    </div>

    <!-- Back to Top Button -->
    <a href="#" class="back-to-top">
        <i class="fas fa-arrow-up"></i>
    </a>

    <script>
        // Project Data
        const projects = [
            {
                id: 1,
                title: "FlyUrDream CRM",
                category: "CRM Solution",
                description: "Empowering businesses to manage and nurture customer relationships effectively, driving growth and customer loyalty.",
                image: "https://via.placeholder.com/600x400",
                technologies: ["Bootstrap", "CSS", "Django", "HTML", "JavaScript", "NodeJS", "Python", "ReactJS"],
                features: [
                    "Comprehensive customer management",
                    "Lead and opportunity tracking",
                    "Customizable dashboards",
                    "Mobile accessibility",
                    "Secure data management"
                ],
                demoUrl: "https://flyurdream.example.com",
                codeUrl: "#"
            },
            {
                id: 2,
                title: "OEC CRM",
                category: "CRM Solution",
                description: "Providing virtual classroom experiences with live classes and collaborative tools for enhanced learning experiences.",
                image: "https://via.placeholder.com/600x400",
                technologies: ["Firebase", "NodeJS", "VueJS"],
                features: [
                    "Interactive live classes",
                    "Recorded sessions",
                    "Assignment management",
                    "Teacher and student dashboards",
                    "Multi-device support"
                ],
                demoUrl: "https://oec-crm.example.com",
                codeUrl: "#"
            },
            {
                id: 3,
                title: "Espionline",
                category: "E-Learning Platform",
                description: "Real-time virtual classroom for remote learning, offering interactive live classes and attendance tracking.",
                image: "https://via.placeholder.com/600x400",
                technologies: ["Firebase", "NodeJS", "VueJS"],
                features: [
                    "Interactive live classes",
                    "Recorded sessions",
                    "Attendance tracking",
                    "Integration with learning management systems"
                ],
                demoUrl: "https://espionline.example.com",
                codeUrl: "#"
            },
            {
                id: 4,
                title: "Indraprasth Foundation",
                category: "Social Welfare",
                description: "Empowering communities through social welfare initiatives focusing on education, healthcare, and skill development.",
                image: "https://via.placeholder.com/600x400",
                technologies: ["MUI", "ReactJS"],
                features: [
                    "Education initiatives",
                    "Healthcare programs",
                    "Skill development training",
                    "Women empowerment projects",
                    "Community infrastructure development"
                ],
                demoUrl: "https://indraprasth.example.com",
                codeUrl: "#"
            },
            {
                id: 5,
                title: "Edustation",
                category: "Educational Tools",
                description: "Cutting-edge educational tools and platforms to enhance learning experiences with personalized learning paths.",
                image: "https://via.placeholder.com/600x400",
                technologies: ["Bootstrap", "PHP"],
                features: [
                    "Personalized learning paths",
                    "Interactive learning tools",
                    "Comprehensive resource libraries",
                    "Progress tracking and analytics",
                    "Adaptive assessments"
                ],
                demoUrl: "https://edustation.example.com",
                codeUrl: "#"
            },
            {
                id: 6,
                title: "StudyStreak",
                category: "AI-Powered Learning",
                description: "Helping students stay focused and build lasting study routines through personalized study plans and analytics.",
                image: "https://via.placeholder.com/600x400",
                technologies: ["NodeJS", "Python", "ReactJS", "Tailwind"],
                features: [
                    "Personalized study plans",
                    "Progress tracking",
                    "Goal setting",
                    "Task management",
                    "Study analytics",
                    "Resource integration"
                ],
                demoUrl: "https://studystreak.example.com",
                codeUrl: "#"
            }
        ];

        // DOM Elements
        const modal = document.getElementById('project-modal');
        const modalTitle = modal.querySelector('.modal-title');
        const modalCategory = modal.querySelector('.modal-category');
        const modalImage = modal.querySelector('.modal-image');
        const modalDescription = modal.querySelector('.modal-description');
        const modalTechList = modal.querySelector('.modal-tech-list');
        const modalFeatureList = modal.querySelector('.modal-feature-list');
        const modalLinks = modal.querySelectorAll('.modal-link');
        const modalClose = document.querySelector('.modal-close');

        // Initialize Projects
        function initProjects() {
            const portfolioItems = document.querySelectorAll('.portfolio-item');
            
            portfolioItems.forEach(item => {
                item.addEventListener('click', function() {
                    const category = this.getAttribute('data-category');
                    const title = this.querySelector('.portfolio-title').textContent;
                    const description = this.querySelector('.portfolio-description').textContent;
                    
                    // Find matching project
                    const project = projects.find(p => {
                        return p.title === title && p.category === category;
                    });
                    
                    if (project) {
                        openModal(project);
                    }
                });
            });
            
            // Filter functionality
            const filterBtns = document.querySelectorAll('.filter-btn');
            
            filterBtns.forEach(btn => {
                btn.addEventListener('click', function() {
                    // Remove active class from all buttons
                    filterBtns.forEach(btn => btn.classList.remove('active'));
                    // Add active class to clicked button
                    this.classList.add('active');
                    
                    const filter = this.getAttribute('data-filter');
                    
                    portfolioItems.forEach(item => {
                        if (filter === 'all' || item.getAttribute('data-category') === filter) {
                            item.style.display = 'block';
                        } else {
                            item.style.display = 'none';
                        }
                    });
                });
            });
        }

        function openModal(project) {
            modalTitle.textContent = project.title;
            modalCategory.textContent = project.category;
            modalImage.style.backgroundImage = `url(${project.image})`;
            modalDescription.textContent = project.description;
            
            // Update technologies
            modalTechList.innerHTML = '';
            project.technologies.forEach(tech => {
                const techTag = document.createElement('span');
                techTag.className = 'modal-tech-tag';
                techTag.textContent = tech;
                modalTechList.appendChild(techTag);
            });
            
            // Update features
            modalFeatureList.innerHTML = '';
            project.features.forEach(feature => {
                const li = document.createElement('li');
                li.textContent = feature;
                modalFeatureList.appendChild(li);
            });
            
            // Update links
            modalLinks[0].href = project.demoUrl;
            modalLinks[1].href = project.codeUrl;
            
            // Show modal
            modal.classList.add('active');
        }

        function closeModal() {
            modal.classList.remove('active');
        }

        // Close modal when clicking outside
        modal.addEventListener('click', function(e) {
            if (e.target === modal) {
                closeModal();
            }
        });

        // Close modal when clicking the close button
        modalClose.addEventListener('click', closeModal);

        // Initialize the projects when DOM is loaded
        document.addEventListener('DOMContentLoaded', initProjects);

        // Navigation scroll effect
        window.addEventListener('scroll', function() {
            const nav = document.querySelector('.nav-container');
            if (window.scrollY > 50) {
                nav.classList.add('nav-scrolled');
            } else {
                nav.classList.remove('nav-scrolled');
            }
            
            // Back to top button
            const backToTop = document.querySelector('.back-to-top');
            if (window.scrollY > 300) {
                backToTop.classList.add('active');
            } else {
                backToTop.classList.remove('active');
            }
        });

        // Mobile menu toggle
        const menuToggle = document.querySelector('.menu-toggle');
        const navLinks = document.querySelector('.nav-links');
        
        menuToggle.addEventListener('click', function() {
            navLinks.classList.toggle('active');
        });

        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);
                
                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 70,
                        behavior: 'smooth'
                    });
                    
                    // Close mobile menu if open
                    navLinks.classList.remove('active');
                }
            });
        });
    </script>
</body>
</html>
