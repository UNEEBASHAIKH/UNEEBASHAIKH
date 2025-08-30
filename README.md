<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Uneeba Shaikh - GitHub Profile</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: #0d1117;
            color: #e6edf3;
            line-height: 1.5;
            overflow-x: hidden;
        }

        .container {
            max-width: 1280px;
            margin: 0 auto;
            padding: 20px;
            display: grid;
            grid-template-columns: 1fr 3fr;
            gap: 20px;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 0.8s ease-out forwards;
        }

        .sidebar {
            background-color: #161b22;
            border-radius: 6px;
            padding: 20px;
            border: 1px solid #30363d;
            height: fit-content;
            transform: translateX(-20px);
            opacity: 0;
            animation: slideInLeft 0.8s ease-out 0.3s forwards;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
        }

        .profile-img {
            width: 100%;
            border-radius: 50%;
            border: 3px solid #30363d;
            margin-bottom: 20px;
            transition: all 0.5s ease;
            transform: scale(0.9);
            animation: scaleIn 0.8s ease-out 0.5s forwards;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }

        .profile-img:hover {
            transform: scale(1.05);
            border-color: #58a6ff;
            box-shadow: 0 0 20px rgba(88, 166, 255, 0.4);
        }

        .username {
            font-size: 1.5rem;
            font-weight: 600;
            margin-bottom: 5px;
            background: linear-gradient(90deg, #58a6ff, #8b949e);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            animation: colorShift 5s infinite alternate;
        }

        .bio {
            color: #7d8590;
            margin-bottom: 20px;
            font-size: 0.9rem;
        }

        .follow-btn {
            width: 100%;
            background-color: #21262d;
            color: #c9d1d9;
            border: 1px solid #363b42;
            border-radius: 6px;
            padding: 5px 16px;
            font-weight: 500;
            margin-bottom: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .follow-btn:hover {
            background-color: #30363d;
            border-color: #8b949e;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }

        .follow-btn:active {
            transform: translateY(0);
        }

        .follow-btn::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 5px;
            height: 5px;
            background: rgba(255, 255, 255, 0.5);
            opacity: 0;
            border-radius: 100%;
            transform: scale(1, 1) translate(-50%);
            transform-origin: 50% 50%;
        }

        .follow-btn:focus:not(:active)::after {
            animation: ripple 1s ease-out;
        }

        .profile-details {
            margin-bottom: 20px;
        }

        .detail-item {
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            color: #7d8590;
            font-size: 0.9rem;
            opacity: 0;
            transform: translateX(-10px);
            animation: fadeInRight 0.5s ease-out forwards;
        }

        .detail-item:nth-child(1) { animation-delay: 0.6s; }
        .detail-item:nth-child(2) { animation-delay: 0.7s; }
        .detail-item:nth-child(3) { animation-delay: 0.8s; }
        .detail-item:nth-child(4) { animation-delay: 0.9s; }
        .detail-item:nth-child(5) { animation-delay: 1.0s; }

        .detail-item i {
            margin-right: 8px;
            width: 16px;
            transition: transform 0.3s ease;
        }

        .detail-item:hover i {
            transform: scale(1.2);
            color: #58a6ff;
        }

        .social-links {
            margin-top: 20px;
        }

        .social-link {
            display: flex;
            align-items: center;
            color: #7d8590;
            text-decoration: none;
            margin-bottom: 10px;
            font-size: 0.9rem;
            transition: all 0.3s ease;
            opacity: 0;
            transform: translateX(-10px);
            animation: fadeInRight 0.5s ease-out forwards;
        }

        .social-link:nth-child(1) { animation-delay: 1.1s; }
        .social-link:nth-child(2) { animation-delay: 1.2s; }

        .social-link:hover {
            color: #2f81f7;
            transform: translateX(5px);
        }

        .social-link i {
            margin-right: 8px;
            width: 16px;
        }

        .main-content {
            display: flex;
            flex-direction: column;
            gap: 20px;
            opacity: 0;
            transform: translateX(20px);
            animation: slideInRight 0.8s ease-out 0.5s forwards;
        }

        .nav {
            display: flex;
            border-bottom: 1px solid #21262d;
        }

        .nav-item {
            padding: 16px 8px;
            margin-right: 16px;
            font-size: 0.9rem;
            color: #7d8590;
            text-decoration: none;
            cursor: pointer;
            position: relative;
            transition: color 0.3s ease;
        }

        .nav-item::after {
            content: '';
            position: absolute;
            bottom: -1px;
            left: 0;
            width: 0;
            height: 2px;
            background: linear-gradient(90deg, #58a6ff, #f78166);
            transition: width 0.3s ease;
        }

        .nav-item.active {
            color: #e6edf3;
            font-weight: 600;
        }

        .nav-item.active::after {
            width: 100%;
        }

        .nav-item:hover {
            color: #e6edf3;
        }

        .nav-item:hover::after {
            width: 100%;
        }

        .section {
            background-color: #161b22;
            border-radius: 6px;
            border: 1px solid #30363d;
            padding: 20px;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }

        .section:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
        }

        .section-title {
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 16px;
            position: relative;
            display: inline-block;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 40px;
            height: 3px;
            background: linear-gradient(90deg, #58a6ff, #f78166);
            border-radius: 3px;
            transition: width 0.3s ease;
        }

        .section:hover .section-title::after {
            width: 100px;
        }

        .pinned-repos {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 16px;
        }

        .repo-card {
            background-color: #21262d;
            border: 1px solid #30363d;
            border-radius: 6px;
            padding: 16px;
            height: 100%;
            transition: all 0.3s ease;
            transform: translateY(20px);
            opacity: 0;
            animation: fadeInUp 0.5s ease-out forwards;
        }

        .repo-card:nth-child(1) { animation-delay: 0.6s; }
        .repo-card:nth-child(2) { animation-delay: 0.7s; }
        .repo-card:nth-child(3) { animation-delay: 0.8s; }
        .repo-card:nth-child(4) { animation-delay: 0.9s; }

        .repo-card:hover {
            transform: translateY(-5px);
            border-color: #58a6ff;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
        }

        .repo-header {
            display: flex;
            align-items: center;
            margin-bottom: 12px;
        }

        .repo-name {
            color: #2f81f7;
            font-weight: 600;
            font-size: 0.9rem;
            margin-left: 8px;
            transition: color 0.3s ease;
        }

        .repo-card:hover .repo-name {
            color: #58a6ff;
        }

        .repo-desc {
            color: #7d8590;
            font-size: 0.8rem;
            margin-bottom: 16px;
        }

        .repo-meta {
            display: flex;
            align-items: center;
            font-size: 0.75rem;
            color: #7d8590;
        }

        .repo-language {
            display: flex;
            align-items: center;
            margin-right: 16px;
        }

        .language-color {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background-color: #e34c26;
            margin-right: 4px;
            transition: transform 0.3s ease;
        }

        .repo-card:hover .language-color {
            transform: scale(1.5);
        }

        .activity-graph {
            background-color: #21262d;
            border-radius: 6px;
            padding: 16px;
            margin-bottom: 20px;
            transform: translateY(20px);
            opacity: 0;
            animation: fadeInUp 0.5s ease-out 1s forwards;
        }

        .graph-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 16px;
        }

        .graph-title {
            font-size: 0.9rem;
            font-weight: 600;
        }

        .graph-months {
            display: flex;
            justify-content: space-between;
            margin-bottom: 4px;
            font-size: 0.7rem;
            color: #7d8590;
        }

        .graph-grid {
            display: grid;
            grid-template-columns: repeat(53, 1fr);
            grid-template-rows: repeat(7, 1fr);
            gap: 2px;
        }

        .graph-cell {
            width: 10px;
            height: 10px;
            border-radius: 2px;
            background-color: #161b22;
            transition: all 0.3s ease;
        }

        .graph-cell.low {
            background-color: #0e4429;
        }

        .graph-cell.medium {
            background-color: #006d32;
        }

        .graph-cell.high {
            background-color: #26a641;
        }

        .graph-cell.very-high {
            background-color: #39d353;
        }

        .graph-cell:hover {
            transform: scale(1.5);
            border: 1px solid #e6edf3;
        }

        .stats-container {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 16px;
        }

        .stat-card {
            background-color: #21262d;
            border-radius: 6px;
            padding: 16px;
            transform: translateY(20px);
            opacity: 0;
            animation: fadeInUp 0.5s ease-out forwards;
        }

        .stat-card:nth-child(1) { animation-delay: 1.1s; }
        .stat-card:nth-child(2) { animation-delay: 1.2s; }

        .stat-title {
            font-size: 0.9rem;
            color: #7d8590;
            margin-bottom: 8px;
        }

        .stat-value {
            font-size: 1.5rem;
            font-weight: 600;
            transition: all 0.5s ease;
        }

        .stat-card:hover .stat-value {
            color: #58a6ff;
            transform: scale(1.1);
        }

        .languages-container {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .language-bar {
            display: flex;
            align-items: center;
            justify-content: space-between;
            opacity: 0;
            transform: translateX(-20px);
            animation: fadeInRight 0.5s ease-out forwards;
        }

        .language-bar:nth-child(1) { animation-delay: 1.3s; }
        .language-bar:nth-child(2) { animation-delay: 1.4s; }
        .language-bar:nth-child(3) { animation-delay: 1.5s; }
        .language-bar:nth-child(4) { animation-delay: 1.6s; }

        .language-name {
            font-size: 0.9rem;
            color: #7d8590;
            width: 80px;
        }

        .language-progress {
            flex-grow: 1;
            height: 8px;
            background-color: #21262d;
            border-radius: 4px;
            overflow: hidden;
            margin: 0 8px;
            position: relative;
        }

        .language-progress-fill {
            height: 100%;
            border-radius: 4px;
            transform: scaleX(0);
            transform-origin: left;
            animation: fillProgress 1.5s ease-out forwards;
        }

        .language-bar:nth-child(1) .language-progress-fill { animation-delay: 1.7s; }
        .language-bar:nth-child(2) .language-progress-fill { animation-delay: 1.8s; }
        .language-bar:nth-child(3) .language-progress-fill { animation-delay: 1.9s; }
        .language-bar:nth-child(4) .language-progress-fill { animation-delay: 2.0s; }

        .language-percent {
            font-size: 0.9rem;
            color: #7d8590;
            width: 40px;
            text-align: right;
            opacity: 0;
            animation: fadeIn 0.5s ease-out forwards;
        }

        .language-bar:nth-child(1) .language-percent { animation-delay: 2.1s; }
        .language-bar:nth-child(2) .language-percent { animation-delay: 2.2s; }
        .language-bar:nth-child(3) .language-percent { animation-delay: 2.3s; }
        .language-bar:nth-child(4) .language-percent { animation-delay: 2.4s; }

        /* Animations */
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

        @keyframes fadeInRight {
            from {
                opacity: 0;
                transform: translateX(-20px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes slideInLeft {
            from {
                opacity: 0;
                transform: translateX(-20px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes slideInRight {
            from {
                opacity: 0;
                transform: translateX(20px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes scaleIn {
            from {
                transform: scale(0.9);
            }
            to {
                transform: scale(1);
            }
        }

        @keyframes colorShift {
            0% {
                background: linear-gradient(90deg, #58a6ff, #8b949e);
                -webkit-background-clip: text;
                background-clip: text;
                color: transparent;
            }
            50% {
                background: linear-gradient(90deg, #f78166, #58a6ff);
                -webkit-background-clip: text;
                background-clip: text;
                color: transparent;
            }
            100% {
                background: linear-gradient(90deg, #8b949e, #f78166);
                -webkit-background-clip: text;
                background-clip: text;
                color: transparent;
            }
        }

        @keyframes fillProgress {
            from {
                transform: scaleX(0);
            }
            to {
                transform: scaleX(1);
            }
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        @keyframes ripple {
            0% {
                transform: scale(0, 0);
                opacity: 1;
            }
            20% {
                transform: scale(25, 25);
                opacity: 1;
            }
            100% {
                opacity: 0;
                transform: scale(40, 40);
            }
        }

        @media (max-width: 768px) {
            .container {
                grid-template-columns: 1fr;
            }
            
            .pinned-repos {
                grid-template-columns: 1fr;
            }
            
            .stats-container {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="sidebar">
            <img src="https://avatars.githubusercontent.com/u/99280019?v=4" alt="Uneeba Shaikh" class="profile-img">
            <h1 class="username">Uneeba Shaikh</h1>
            <p class="bio">Front-end developer</p>
            <button class="follow-btn">Follow</button>
            
            <div class="profile-details">
                <div class="detail-item">
                    <i class="fas fa-user"></i>
                    <span>UNEEBASHAIKH</span>
                </div>
                <div class="detail-item">
                    <i class="fas fa-map-marker-alt"></i>
                    <span>Hyderabad, Sindh</span>
                </div>
                <div class="detail-item">
                    <i class="fas fa-link"></i>
                    <span>https://www.linkedin.com/in/uneeba-shaikh</span>
                </div>
            </div>
            
            <div class="profile-details">
                <div class="detail-item">
                    <i class="fas fa-briefcase"></i>
                    <span>Front-end Developer</span>
                </div>
                <div class="detail-item">
                    <i class="fas fa-graduation-cap"></i>
                    <span>Mehran University of Engineering</span>
                </div>
            </div>
            
            <hr style="border: 0.5px solid #30363d; margin: 20px 0;">
            
            <div class="profile-details">
                <div class="detail-item">
                    <i class="fas fa-users"></i>
                    <span><b>1</b> follower · <b>2</b> following</span>
                </div>
            </div>
            
            <div class="social-links">
                <a href="#" class="social-link">
                    <i class="fab fa-linkedin"></i>
                    <span>LinkedIn</span>
                </a>
                <a href="mailto:uneebashaikh33@gmail.com" class="social-link">
                    <i class="fas fa-envelope"></i>
                    <span>uneebashaikh33@gmail.com</span>
                </a>
            </div>
        </div>
        
        <div class="main-content">
            <div class="nav">
                <a href="#" class="nav-item active">Overview</a>
                <a href="#" class="nav-item">Repositories</a>
                <a href="#" class="nav-item">Projects</a>
                <a href="#" class="nav-item">Packages</a>
            </div>
            
            <div class="section">
                <h2 class="section-title">Pinned repositories</h2>
                <div class="pinned-repos">
                    <div class="repo-card">
                        <div class="repo-header">
                            <i class="far fa-bookmark"></i>
                            <span class="repo-name">HTML_CSS_JavaScript</span>
                        </div>
                        <p class="repo-desc">E-commerce website using react and javascript</p>
                        <div class="repo-meta">
                            <div class="repo-language">
                                <span class="language-color"></span>
                                <span>JavaScript</span>
                            </div>
                        </div>
                    </div>
                    
                    <div class="repo-card">
                        <div class="repo-header">
                            <i class="far fa-bookmark"></i>
                            <span class="repo-name">ShoppingCart</span>
                        </div>
                        <p class="repo-desc">E-commerce website using react and javascript</p>
                        <div class="repo-meta">
                            <div class="repo-language">
                                <span class="language-color" style="background-color: #e34c26;"></span>
                                <span>HTML</span>
                            </div>
                        </div>
                    </div>
                    
                    <div class="repo-card">
                        <div class="repo-header">
                            <i class="far fa-bookmark"></i>
                            <span class="repo-name">Data-Science-Projects</span>
                        </div>
                        <p class="repo-desc">Data Science projects collection with ML, data analysis and more</p>
                        <div class="repo-meta">
                            <div class="repo-language">
                                <span class="language-color" style="background-color: #3572A5;"></span>
                                <span>Python</span>
                            </div>
                        </div>
                    </div>
                    
                    <div class="repo-card">
                        <div class="repo-header">
                            <i class="far fa-bookmark"></i>
                            <span class="repo-name">final-project</span>
                        </div>
                        <p class="repo-desc">Make-node recipes - HTML</p>
                        <div class="repo-meta">
                            <div class="repo-language">
                                <span class="language-color" style="background-color: #e34c26;"></span>
                                <span>HTML</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="section">
                <div class="activity-graph">
                    <div class="graph-header">
                        <span class="graph-title">31 contributions in the last year</span>
                    </div>
                    
                    <div class="graph-months">
                        <span>Oct</span>
                        <span>Nov</span>
                        <span>Dec</span>
                        <span>Jan</span>
                        <span>Feb</span>
                        <span>Mar</span>
                        <span>Apr</span>
                        <span>May</span>
                        <span>Jun</span>
                        <span>Jul</span>
                        <span>Aug</span>
                    </div>
                    
                    <div class="graph-grid">
                        <!-- This would be generated with JavaScript in a real implementation -->
                        <!-- Simplified version for demo -->
                        <div class="graph-cell"></div>
                        <div class="graph-cell low"></div>
                        <div class="graph-cell"></div>
                        <div class="graph-cell medium"></div>
                        <div class="graph-cell"></div>
                        <div class="graph-cell"></div>
                        <div class="graph-cell"></div>
                        <!-- ... more cells would be here ... -->
                    </div>
                </div>
            </div>
            
            <div class="section">
                <h2 class="section-title">My skills</h2>
                <div class="stats-container">
                    <div class="stat-card">
                        <h3 class="stat-title">Most Used Languages</h3>
                        <div class="languages-container">
                            <div class="language-bar">
                                <span class="language-name">HTML</span>
                                <div class="language-progress">
                                    <div class="language-progress-fill" style="width: 42.1%; background-color: #e34c26;"></div>
                                </div>
                                <span class="language-percent">42.1%</span>
                            </div>
                            <div class="language-bar">
                                <span class="language-name">JavaScript</span>
                                <div class="language-progress">
                                    <div class="language-progress-fill" style="width: 42.2%; background-color: #f1e05a;"></div>
                                </div>
                                <span class="language-percent">42.2%</span>
                            </div>
                            <div class="language-bar">
                                <span class="language-name">CSS</span>
                                <div class="language-progress">
                                    <div class="language-progress-fill" style="width: 14.1%; background-color: #563d7c;"></div>
                                </div>
                                <span class="language-percent">14.1%</span>
                            </div>
                            <div class="language-bar">
                                <span class="language-name">Python</span>
                                <div class="language-progress">
                                    <div class="language-progress-fill" style="width: 1.6%; background-color: #3572A5;"></div>
                                </div>
                                <span class="language-percent">1.6%</span>
                            </div>
                        </div>
                    </div>
                    
                    <div class="stat-card">
                        <h3 class="stat-title">GitHub Stats</h3>
                        <div class="stats-grid">
                            <div class="stat-item">
                                <span class="stat-title">Total Stars Earned:</span>
                                <span class="stat-value">0</span>
                            </div>
                            <div class="stat-item">
                                <span class="stat-title">Total Commits (2025):</span>
                                <span class="stat-value">2</span>
                            </div>
                            <div class="stat-item">
                                <span class="stat-title">Total PRs:</span>
                                <span class="stat-value">0</span>
                            </div>
                            <div class="stat-item">
                                <span class="stat-title">Total Issues:</span>
                                <span class="stat-value">0</span>
                            </div>
                            <div class="stat-item">
                                <span class="stat-title">Contributed to (last year):</span>
                                <span class="stat-value">0</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Add ripple effect to buttons
        document.querySelectorAll('.follow-btn').forEach(button => {
            button.addEventListener('click', function(e) {
                let x = e.clientX - e.target.getBoundingClientRect().left;
                let y = e.clientY - e.target.getBoundingClientRect().top;
                
                let ripple = document.createElement('span');
                ripple.classList.add('ripple');
                ripple.style.left = `${x}px`;
                ripple.style.top = `${y}px`;
                this.appendChild(ripple);
                
                setTimeout(() => {
                    ripple.remove();
                }, 600);
            });
        });

        // Add hover effect to graph cells
        document.querySelectorAll('.graph-cell').forEach(cell => {
            cell.addEventListener('mouseenter', () => {
                cell.style.transform = 'scale(1.5)';
                cell.style.border = '1px solid #e6edf3';
            });
            
            cell.addEventListener('mouseleave', () => {
                cell.style.transform = 'scale(1)';
                cell.style.border = 'none';
            });
        });
    </script>
</body>
</html>
