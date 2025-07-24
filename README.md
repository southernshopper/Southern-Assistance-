<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Southern Assist - Personal Shopping Service</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --soft-navy: #4A5568;
            --light-coral: #FF7A7A;
            --cream: #FFF8E7;
            --slate-gray: #718096;
            --cream-white: #FFFEF7;
            --navy-dark: #2D3748;
            --coral-light: #FFB3B3;
            --coral-dark: #E53E3E;
        }

        body {
            font-family: 'Arial', sans-serif;
            font-size: 18px;
            line-height: 1.6;
            color: var(--navy-dark);
            background: linear-gradient(135deg, var(--cream) 0%, var(--cream-white) 50%, #F7FAFC 100%);
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .header {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            padding: 1rem 0;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 20px rgba(74, 85, 104, 0.1);
            border-bottom: 3px solid var(--light-coral);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
        }

        .logo {
            font-size: 2rem;
            font-weight: bold;
            color: var(--soft-navy);
            text-decoration: none;
        }

        .nav-buttons {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .nav-btn {
            background: var(--soft-navy);
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
        }

        .nav-btn:hover {
            background: var(--navy-dark);
            transform: translateY(-2px);
        }

        .nav-btn.coral {
            background: var(--light-coral);
        }

        .nav-btn.coral:hover {
            background: var(--coral-dark);
        }

        .main-content {
            padding: 2rem 0;
        }

        .section {
            background: rgba(255, 255, 255, 0.95);
            margin: 2rem 0;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 8px 32px rgba(74, 85, 104, 0.1);
            backdrop-filter: blur(10px);
            display: none;
            border: 1px solid rgba(255, 122, 122, 0.2);
        }

        .section.active {
            display: block;
        }

        .section h2 {
            color: var(--soft-navy);
            margin-bottom: 1.5rem;
            font-size: 2rem;
            border-bottom: 3px solid var(--light-coral);
            padding-bottom: 0.5rem;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: bold;
            color: var(--soft-navy);
        }

        .form-group input,
        .form-group select,
        .form-group textarea {
            width: 100%;
            padding: 12px;
            border: 2px solid var(--slate-gray);
            border-radius: 8px;
            font-size: 16px;
            transition: border-color 0.3s ease;
            background: var(--cream-white);
        }

        .form-group input:focus,
        .form-group select:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--light-coral);
            box-shadow: 0 0 0 3px rgba(255, 122, 122, 0.1);
        }

        .form-group textarea {
            height: 120px;
            resize: vertical;
        }

        .btn {
            background: var(--light-coral);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 18px;
            font-weight: bold;
            transition: all 0.3s ease;
            margin: 10px 5px;
        }

        .btn:hover {
            background: var(--coral-dark);
            transform: translateY(-2px);
        }

        .btn-navy {
            background: var(--soft-navy);
        }

        .btn-navy:hover {
            background: var(--navy-dark);
        }

        .btn-secondary {
            background: var(--slate-gray);
            color: white;
        }

        .btn-secondary:hover {
            background: var(--soft-navy);
        }

        .schedule-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
            margin: 1rem 0;
        }

        .time-slot {
            background: var(--cream);
            border: 2px solid var(--slate-gray);
            border-radius: 8px;
            padding: 1rem;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .time-slot:hover {
            border-color: var(--light-coral);
            transform: translateY(-2px);
        }

        .time-slot.selected {
            background: var(--light-coral);
            color: white;
            border-color: var(--coral-dark);
        }

        .time-slot.unavailable {
            background: var(--coral-light);
            color: var(--coral-dark);
            cursor: not-allowed;
        }

        .payment-methods {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 1rem;
            margin: 1rem 0;
        }

        .payment-method {
            background: var(--cream);
            border: 2px solid var(--slate-gray);
            border-radius: 8px;
            padding: 1rem;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .payment-method:hover {
            border-color: var(--light-coral);
            transform: translateY(-2px);
        }

        .payment-method.selected {
            background: var(--light-coral);
            color: white;
            border-color: var(--coral-dark);
        }

        .order-summary {
            background: var(--cream);
            border: 2px solid var(--slate-gray);
            border-radius: 8px;
            padding: 1.5rem;
            margin: 1rem 0;
        }

        .order-item {
            display: flex;
            justify-content: space-between;
            padding: 0.5rem 0;
            border-bottom: 1px solid var(--slate-gray);
        }

        .order-item:last-child {
            border-bottom: none;
        }

        .welcome-section {
            text-align: center;
            padding: 3rem 0;
            background: var(--cream-white);
            border-radius: 15px;
            margin: 2rem 0;
            box-shadow: 0 8px 32px rgba(74, 85, 104, 0.1);
            border: 1px solid rgba(255, 122, 122, 0.2);
        }

        .welcome-section h1 {
            font-size: 3rem;
            color: var(--soft-navy);
            margin-bottom: 1rem;
        }

        .welcome-section p {
            font-size: 1.3rem;
            color: var(--slate-gray);
            margin-bottom: 2rem;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }

        .hours-section {
            background: var(--cream);
            border: 2px solid var(--light-coral);
            border-radius: 10px;
            padding: 2rem;
            margin: 2rem 0;
            text-align: center;
        }

        .hours-section h3 {
            color: var(--soft-navy);
            margin-bottom: 1rem;
            font-size: 1.5rem;
        }

        .hours-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
            margin-top: 1rem;
        }

        .hours-item {
            background: white;
            padding: 1rem;
            border-radius: 8px;
            border: 1px solid var(--slate-gray);
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin: 3rem 0;
        }

        .feature-card {
            background: rgba(255, 255, 255, 0.95);
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 8px 32px rgba(74, 85, 104, 0.1);
            border: 1px solid rgba(255, 122, 122, 0.2);
            transition: transform 0.3s ease;
        }

        .feature-card:hover {
            transform: translateY(-5px);
        }

        .feature-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .feature-card h3 {
            color: var(--soft-navy);
            margin-bottom: 1rem;
        }

        .feature-card p {
            color: var(--slate-gray);
        }

        .invoice-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem;
            background: var(--cream);
            border-radius: 8px;
            margin-bottom: 1rem;
            border: 1px solid var(--slate-gray);
        }

        .invoice-status {
            padding: 0.5rem 1rem;
            border-radius: 20px;
            font-weight: bold;
            text-transform: uppercase;
            font-size: 0.9rem;
        }

        .invoice-status.pending {
            background: var(--coral-light);
            color: var(--coral-dark);
        }

        .invoice-status.paid {
            background: #68D391;
            color: #22543D;
        }

        .profile-display {
            background: var(--cream);
            border: 2px solid var(--slate-gray);
            border-radius: 8px;
            padding: 1.5rem;
            margin: 1rem 0;
        }

        .profile-section {
            margin-bottom: 1.5rem;
        }

        .profile-section h3 {
            color: var(--soft-navy);
            margin-bottom: 0.5rem;
            font-size: 1.2rem;
        }

        .profile-section p {
            color: var(--slate-gray);
            margin-bottom: 0.3rem;
        }

        .package-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.5rem;
            margin: 2rem 0;
        }

        .package-card {
            background: linear-gradient(135deg, var(--cream) 0%, var(--cream-white) 100%);
            border: 2px solid var(--slate-gray);
            border-radius: 15px;
            padding: 2rem;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .package-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 122, 122, 0.1), transparent);
            transition: left 0.6s;
        }

        .package-card:hover::before {
            left: 100%;
        }

        .package-card:hover {
            border-color: var(--light-coral);
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(255, 122, 122, 0.15);
        }

        .package-card.selected {
            background: linear-gradient(135deg, var(--light-coral) 0%, var(--coral-dark) 100%);
            color: white;
            border-color: var(--coral-dark);
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(255, 122, 122, 0.3);
        }

        .package-card h4 {
            font-size: 1.4rem;
            margin-bottom: 1rem;
            color: var(--soft-navy);
        }

        .package-card.selected h4 {
            color: white;
        }

        .package-price {
            font-size: 2rem;
            font-weight: bold;
            color: var(--light-coral);
            margin-bottom: 1rem;
        }

        .package-card.selected .package-price {
            color: white;
        }

        .package-card p {
            margin-bottom: 0.5rem;
            color: var(--slate-gray);
        }

        .package-card.selected p {
            color: rgba(255, 255, 255, 0.9);
        }

        .auth-section {
            max-width: 400px;
            margin: 3rem auto;
            background: var(--cream-white);
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 8px 32px rgba(74, 85, 104, 0.1);
            border: 1px solid rgba(255, 122, 122, 0.2);
        }

        .auth-section h2 {
            text-align: center;
            color: var(--soft-navy);
            margin-bottom: 2rem;
            border-bottom: 3px solid var(--light-coral);
            padding-bottom: 1rem;
        }

        .auth-toggle {
            text-align: center;
            margin-top: 1rem;
        }

        .auth-toggle a {
            color: var(--light-coral);
            text-decoration: none;
            font-weight: bold;
        }

        .auth-toggle a:hover {
            color: var(--coral-dark);
            text-decoration: underline;
        }

        .days-selection {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            gap: 1rem;
            margin-top: 0.5rem;
        }

        .days-selection label {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.5rem;
            background: var(--cream);
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .days-selection label:hover {
            background: var(--coral-light);
        }

        .days-selection input[type="checkbox"]:checked + span {
            font-weight: bold;
            color: var(--coral-dark);
        }

        .service-pricing {
            background: var(--cream);
            border: 2px solid var(--light-coral);
            border-radius: 8px;
            padding: 1rem;
            margin: 1rem 0;
            font-weight: bold;
            color: var(--soft-navy);
        }

        .cost-breakdown {
            background: var(--cream);
            border: 1px solid var(--slate-gray);
            border-radius: 8px;
            padding: 1rem;
            margin: 1rem 0;
        }

        .cost-item {
            display: flex;
            justify-content: space-between;
            padding: 0.5rem 0;
            border-bottom: 1px solid var(--slate-gray);
        }

        .cost-item:last-child {
            border-bottom: none;
            font-weight: bold;
            font-size: 1.1rem;
            color: var(--soft-navy);
        }

        .premium-notice {
            background: var(--coral-light);
            border: 1px solid var(--coral-dark);
            border-radius: 8px;
            padding: 1rem;
            margin: 1rem 0;
            color: var(--coral-dark);
        }

        .hero-actions {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
            margin-top: 2rem;
        }

        @media (max-width: 768px) {
            .package-grid {
                grid-template-columns: 1fr;
            }
            
            .days-selection {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .header-content {
                flex-direction: column;
                gap: 1rem;
            }
            
            .nav-buttons {
                justify-content: center;
            }
            
            .nav-btn {
                padding: 10px 16px;
                font-size: 14px;
            }
            
            .section {
                padding: 1rem;
            }
            
            .welcome-section h1 {
                font-size: 2rem;
            }
            
            .welcome-section p {
                font-size: 1.1rem;
            }

            .hero-actions {
                flex-direction: column;
                align-items: center;
            }
        }
    </style>
</head>
<body>
    <header class="header">
        <div class="container">
            <div class="header-content">
                <a href="#" class="logo" onclick="showSection('home')">Southern Assist</a>
                <nav class="nav-buttons" id="main-nav">
                    <button class="nav-btn coral" onclick="showSection('login')">Login</button>
                    <button class="nav-btn" onclick="showSection('signup')">Sign Up</button>
                </nav>
                <nav class="nav-buttons" id="user-nav" style="display: none;">
                    <button class="nav-btn" onclick="showSection('profile')">Profile</button>
                    <button class="nav-btn" onclick="showSection('orders')">New Order</button>
                    <button class="nav-btn" onclick="showSection('schedule')">Schedule</button>
                    <button class="nav-btn" onclick="showSection('invoices')">Invoices</button>
                    <button class="nav-btn" onclick="showSection('payments')">Payments</button>
                    <button class="nav-btn coral" onclick="logout()">Logout</button>
                </nav>
            </div>
        </div>
    </header>

    <div class="container">
        <div class="main-content">
            <!-- Home Section -->
            <div id="home" class="section active">
                <div class="welcome-section">
                    <h1>Welcome to Southern Assist</h1>
                    <p><strong>Dependable Service You Can Trust!</strong></p>
                    <p>Lynn Saucier | 662-809-9672 | ursouthernassist@gmail.com</p>
                    <p>Your trusted personal assistant for shopping, errands, transportation, and pet care. Choose from convenient weekly packages or book individual services as needed.</p>
                    
                    <div class="hero-actions">
                        <button class="btn" onclick="showSection('signup')">Get Started</button>
                        <button class="btn btn-navy" onclick="showSection('login')">Login</button>
                    </div>
                </div>

                <div class="hours-section">
                    <h3>🕐 Hours of Operation</h3>
                    <div class="hours-grid">
                        <div class="hours-item">
                            <strong>Monday - Friday</strong><br>
                            8:00 AM - 2:00 PM
                        </div>
                        <div class="hours-item">
                            <strong>Saturday - Sunday</strong><br>
                            7:00 AM - 5:00 PM
                        </div>
                    </div>
                </div>
                
                <div class="features-grid">
                    <div class="feature-card">
                        <div class="feature-icon">📦</div>
                        <h3>Weekly Packages</h3>
                        <p>Simple Support ($50), Essential ($100), Premium ($150), or Pup Parent ($100) packages</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">🛒</div>
                        <h3>Shopping & Errands</h3>
                        <p>Grocery shopping, pharmacy runs, post office visits, and personal errands</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">🚗</div>
                        <h3>Transportation</h3>
                        <p>Local trips ($20) and longer distances ($40) - appointments, errands, and more</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">🐕</div>
                        <h3>Pet Care</h3>
                        <p>Vet appointment transport, dog walking, and weekly baths for your furry friends</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">🧹</div>
                        <h3>Light Cleaning</h3>
                        <p>$25/hour cleaning services to keep your space tidy and comfortable</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">💰</div>
                        <h3>Flexible Payment</h3>
                        <p>Cash, Check, CashApp, or Venmo accepted. Tips are always encouraged! 💖</p>
                    </div>
                </div>
            </div>

            <!-- Login Section -->
            <div id="login" class="section">
                <div class="auth-section">
                    <h2>Login</h2>
                    <form id="login-form" onsubmit="handleLogin(event)">
                        <div class="form-group">
                            <label for="login-email">Email Address *</label>
                            <input type="email" id="login-email" name="login-email" required>
                        </div>
                        
                        <div class="form-group">
                            <label for="login-password">Password *</label>
                            <input type="password" id="login-password" name="login-password" required>
                        </div>
                        
                        <button type="submit" class="btn" style="width: 100%;">Login</button>
                        
                        <div class="auth-toggle">
                            <p>Don't have an account? <a href="#" onclick="showSection('signup')">Sign up here</a></p>
                        </div>
                    </form>
                </div>
            </div>

            <!-- Sign Up Section -->
            <div id="signup" class="section">
                <div class="auth-section">
                    <h2>Sign Up</h2>
                    <form id="signup-form" onsubmit="handleSignup(event)">
                        <div class="form-group">
                            <label for="signup-name">Full Name *</label>
                            <input type="text" id="signup-name" name="signup-name" required>
                        </div>
                        
                        <div class="form-group">
                            <label for="signup-email">Email Address *</label>
                            <input type="email" id="signup-email" name="signup-email" required>
                        </div>
                        
                        <div class="form-group">
                            <label for="signup-phone">Phone Number *</label>
                            <input type="tel" id="signup-phone" name="signup-phone" required>
                        </div>
                        
                        <div class="form-group">
                            <label for="signup-password">Password *</label>
                            <input type="password" id="signup-password" name="signup-password" required minlength="6">
                        </div>
                        
                        <div class="form-group">
                            <label for="signup-confirm-password">Confirm Password *</label>
                            <input type="password" id="signup-confirm-password" name="signup-confirm-password" required>
                        </div>
                        
                        <button type="submit" class="btn" style="width: 100%;">Create Account</button>
                        
                        <div class="auth-toggle">
                            <p>Already have an account? <a href="#" onclick="showSection('login')">Login here</a></p>
                        </div>
                    </form>
                </div>
            </div>

            <!-- Profile Section -->
            <div id="profile" class="section">
                <h2>Your Profile</h2>
                <div id="profile-display" class="profile-display" style="display: none;">
                    <div class="profile-section">
                        <h3>Contact Information</h3>
                        <p><strong>Name:</strong> <span id="display-name"></span></p>
                        <p><strong>Phone:</strong> <span id="display-phone"></span></p>
                        <p><strong>Email:</strong> <span id="display-email"></span></p>
                    </div>
                    <div class="profile-section">
                        <h3>Delivery Address</h3>
                        <p id="display-address"></p>
                    </div>
                    <div class="profile-section">
                        <h3>Preferences</h3>
                        <p><strong>Preferred Stores:</strong> <span id="display-stores"></span></p>
                        <p><strong>Preferred Brands:</strong> <span id="display-brands"></span></p>
                        <p><strong>Special Instructions:</strong> <span id="display-instructions"></span></p>
                    </div>
                    <button class="btn" onclick="editProfile()">Edit Profile</button>
                </div>
                
                <form id="profile-form" onsubmit="saveProfile(event)">
                    <div class="form-group">
                        <label for="name">Full Name *</label>
                        <input type="text" id="name" name="name" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="phone">Phone Number *</label>
                        <input type="tel" id="phone" name="phone" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="email">Email Address *</label>
                        <input type="email" id="email" name="email" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="address">Delivery Address *</label>
                        <textarea id="address" name="address" required placeholder="Street Address, City, State, ZIP Code"></textarea>
                    </div>
                    
                    <div class="form-group">
                        <label for="stores">Preferred Stores</label>
                        <input type="text" id="stores" name="stores" placeholder="e.g., Walmart, Kroger, Target">
                    </div>
                    
                    <div class="form-group">
                        <label for="brands">Preferred Brands</label>
                        <input type="text" id="brands" name="brands" placeholder="e.g., Great Value, Tide, Coca-Cola">
                    </div>
                    
                    <div class="form-group">
                        <label for="instructions">Special Instructions</label>
                        <textarea id="instructions" name="instructions" placeholder="Any dietary restrictions, preferences, or special notes"></textarea>
                    </div>
                    
                    <button type="submit" class="btn">Save Profile</button>
                </form>
            </div>

            <!-- Orders Section -->
            <div id="orders" class="section">
                <h2>Select Your Service</h2>
                
                <!-- Service Package Selection -->
                <div class="service-selection">
                    <h3>Weekly Service Packages</h3>
                    <div class="package-grid">
                        <div class="package-card" onclick="selectPackage('pup-parent')">
                            <h4>Pup Parent Package</h4>
                            <div class="package-price">$100/week</div>
                            <p>Vet appointment drop-off/pickup</p>
                            <p>2-4 dog walks + weekly bath</p>
                        </div>
                    </div>
                    
                    <div class="individual-services">
                        <h3>Individual Services</h3>
                        <button class="btn" onclick="showIndividualServices()">Order Individual Services</button>
                    </div>
                </div>

                <!-- Package Order Form -->
                <form id="package-form" style="display: none;" onsubmit="submitPackageOrder(event)">
                    <h3 id="selected-package-title">Selected Package</h3>
                    <input type="hidden" id="selected-package" name="selected-package">
                    
                    <div class="form-group">
                        <label for="start-date">Preferred Start Date *</label>
                        <input type="date" id="start-date" name="start-date" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="preferred-days">Preferred Days of Week</label>
                        <div class="days-selection">
                            <label><input type="checkbox" value="monday"> <span>Monday</span></label>
                            <label><input type="checkbox" value="tuesday"> <span>Tuesday</span></label>
                            <label><input type="checkbox" value="wednesday"> <span>Wednesday</span></label>
                            <label><input type="checkbox" value="thursday"> <span>Thursday</span></label>
                            <label><input type="checkbox" value="friday"> <span>Friday</span></label>
                            <label><input type="checkbox" value="saturday"> <span>Saturday</span></label>
                            <label><input type="checkbox" value="sunday"> <span>Sunday</span></label>
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <label for="package-notes">Special Instructions</label>
                        <textarea id="package-notes" name="package-notes" placeholder="Any specific preferences or instructions for your weekly service"></textarea>
                    </div>
                    
                    <button type="submit" class="btn">Subscribe to Package</button>
                    <button type="button" class="btn btn-secondary" onclick="backToPackageSelection()">Back to Packages</button>
                </form>

                <!-- Individual Services Form -->
                <form id="individual-form" style="display: none;" onsubmit="submitIndividualOrder(event)">
                    <h3>Individual Service Order</h3>
                    
                    <div class="form-group">
                        <label for="service-type">Service Type *</label>
                        <select id="service-type" name="service-type" required onchange="updateServicePricing()">
                            <option value="">Select service type</option>
                            <option value="grocery-local">🛒 Grocery Shopping - Local Trip (1 store)</option>
                            <option value="grocery-extended">🛒 Grocery Shopping - Extended Trip (2+ stores)</option>
                            <option value="transport-local">🚗 Transportation - Local (up to 10 miles)</option>
                            <option value="transport-long">🚗 Transportation - Longer Trip (10-25 miles)</option>
                            <option value="errands-single">📦 Personal Errands - Single Stop</option>
                            <option value="errands-multiple">📦 Personal Errands - Multiple Stops</option>
                            <option value="wait-time">⏰ Wait Time (appointments, etc.)</option>
                            <option value="light-cleaning">🧹 Light Cleaning</option>
                        </select>
                    </div>
                    
                    <div id="service-pricing" class="service-pricing"></div>
                    
                    <div class="form-group" id="wait-time-options" style="display: none;">
                        <label for="wait-duration">Expected Wait Time</label>
                        <select id="wait-duration" name="wait-duration" onchange="updateWaitTimePricing()">
                            <option value="0-15">First 15 minutes (Free with service)</option>
                            <option value="15-30">15-30 minutes</option>
                            <option value="30-60">30-60 minutes</option>
                            <option value="60+">1+ hours</option>
                        </select>
                    </div>
                    
                    <div class="form-group" id="cleaning-hours" style="display: none;">
                        <label for="cleaning-duration">Cleaning Duration (hours)</label>
                        <input type="number" id="cleaning-duration" name="cleaning-duration" min="1" step="0.5" placeholder="1">
                    </div>
                    
                    <div class="form-group">
                        <label for="service-details">Service Details *</label>
                        <textarea id="service-details" name="service-details" required placeholder="Please describe what you need (shopping list, errand details, cleaning tasks, etc.)"></textarea>
                    </div>
                    
                    <div class="form-group">
                        <label for="preferred-date">Preferred Service Date *</label>
                        <input type="date" id="preferred-date" name="preferred-date" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="preferred-time">Preferred Time</label>
                        <select id="preferred-time" name="preferred-time">
                            <option value="">Any time</option>
                            <option value="morning">Morning (8 AM - 12 PM)</option>
                            <option value="afternoon">Afternoon (12 PM - 2 PM) - Weekdays</option>
                            <option value="weekend-morning">Weekend Morning (7 AM - 12 PM)</option>
                            <option value="weekend-afternoon">Weekend Afternoon (12 PM - 5 PM)</option>
                        </select>
                    </div>
                    
                    <div class="form-group">
                        <label>
                            <input type="checkbox" id="weekend-service" name="weekend-service">
                            Weekend/Holiday Service (+20% premium)
                        </label>
                    </div>
                    
                    <div class="form-group">
                        <label for="individual-notes">Additional Notes</label>
                        <textarea id="individual-notes" name="individual-notes" placeholder="Any special instructions or preferences"></textarea>
                    </div>
                    
                    <div id="estimated-cost" class="order-summary"></div>
                    
                    <button type="submit" class="btn">Submit Service Request</button>
                    <button type="button" class="btn btn-secondary" onclick="backToServiceSelection()">Back to Service Selection</button>
                </form>
            </div>

            <!-- Schedule Section -->
            <div id="schedule" class="section">
                <h2>Schedule Your Service</h2>
                <p>Select your preferred date and time for order completion/delivery:</p>
                
                <div class="hours-section">
                    <h3>Available Service Hours</h3>
                    <div class="hours-grid">
                        <div class="hours-item">
                            <strong>Monday - Friday</strong><br>
                            8:00 AM - 2:00 PM
                        </div>
                        <div class="hours-item">
                            <strong>Saturday - Sunday</strong><br>
                            7:00 AM - 5:00 PM
                        </div>
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="service-date">Service Date *</label>
                    <input type="date" id="service-date" name="service-date" required onchange="updateTimeSlots()">
                </div>
                
                <div id="time-slots" class="schedule-grid">
                    <!-- Time slots will be populated by JavaScript -->
                </div>
                
                <div class="form-group">
                    <label for="delivery-notes">Delivery Instructions</label>
                    <textarea id="delivery-notes" name="delivery-notes" placeholder="Any special delivery instructions (e.g., leave at door, call upon arrival)"></textarea>
                </div>
                
                <button class="btn" onclick="scheduleService()">Schedule Service</button>
            </div>

            <!-- Invoices Section -->
            <div id="invoices" class="section">
                <h2>Your Invoices</h2>
                <div id="invoices-list">
                    <!-- Invoices will be populated by JavaScript -->
                </div>
            </div>

            <!-- Payments Section -->
            <div id="payments" class="section">
                <h2>Payment Center</h2>
                <div id="payment-invoices">
                    <!-- Payment-ready invoices will be shown here -->
                </div>
                
                <div class="form-group">
                    <label>Select Payment Method:</label>
                    <div class="payment-methods">
                        <div class="payment-method" data-method="cash" onclick="selectPaymentMethod('cash')">
                            <strong>💵 Cash</strong>
                            <p>Pay in person</p>
                        </div>
                        <div class="payment-method" data-method="check" onclick="selectPaymentMethod('check')">
                            <strong>📝 Check</strong>
                            <p>Mail or deliver</p>
                        </div>
                        <div class="payment-method" data-method="cashapp" onclick="selectPaymentMethod('cashapp')">
                            <strong>💰 CashApp</strong>
                            <p>$southernassist</p>
                        </div>
                        <div class="payment-method" data-method="venmo" onclick="selectPaymentMethod('venmo')">
                            <strong>📱 Venmo</strong>
                            <p>@SouthernAssist</p>
                        </div>
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="payment-amount">Payment Amount *</label>
                    <input type="number" id="payment-amount" name="payment-amount" step="0.01" placeholder="0.00" required>
                </div>
                
                <div class="form-group">
                    <label for="payment-reference">Reference/Invoice Number</label>
                    <input type="text" id="payment-reference" name="payment-reference" placeholder="Invoice #001">
                </div>
                
                <div class="form-group">
                    <label for="tip-amount">Add a Tip (Optional) 💖</label>
                    <input type="number" id="tip-amount" name="tip-amount" step="0.01" placeholder="0.00">
                </div>
                
                <button class="btn" onclick="processPayment()">Submit Payment Info</button>
            </div>
        </div>
    </div>

    <script>
        // Global variables to store data
        let currentUser = null;
        let currentProfile = null;
        let orders = [];
        let invoices = [];
        let selectedPaymentMethod = null;
        let selectedTimeSlot = null;
        let selectedPackage = null;
        let isLoggedIn = false;

        // Service pricing data
        const servicePricing = {
            'grocery-local': { base: 10, name: 'Grocery Shopping - Local Trip (1 store)' },
            'grocery-extended': { base: 20, name: 'Grocery Shopping - Extended Trip (2+ stores)' },
            'transport-local': { base: 20, name: 'Transportation - Local (up to 10 miles)' },
            'transport-long': { base: 40, name: 'Transportation - Longer Trip (10-25 miles)' },
            'errands-single': { base: 15, name: 'Personal Errands - Single Stop' },
            'errands-multiple': { base: 20, name: 'Personal Errands - Multiple Stops' },
            'wait-time': { base: 0, name: 'Wait Time (appointments, etc.)' },
            'light-cleaning': { base: 25, name: 'Light Cleaning', unit: 'per hour' }
        };

        const packagePricing = {
            'simple': { price: 50, name: 'Simple Support', duration: '2 Hours A Week' },
            'essential': { price: 100, name: 'Essential Package', duration: '4 Hours A Week' },
            'premium': { price: 150, name: 'Premium Package', duration: '2 Hours A Week + Transportation' },
            'pup-parent': { price: 100, name: 'Pup Parent Package', duration: 'Pet Care Services' }
        };

        // Authentication functions
        function handleLogin(event) {
            event.preventDefault();
            
            const formData = new FormData(event.target);
            const email = formData.get('login-email');
            const password = formData.get('login-password');
            
            // In a real application, this would validate against a database
            // For demo purposes, we'll simulate successful login
            currentUser = {
                email: email,
                name: 'Demo User',
                loginTime: new Date().toISOString()
            };
            
            isLoggedIn = true;
            updateNavigation();
            showSection('profile');
            
            alert('Login successful! Welcome back.');
            event.target.reset();
        }

        function handleSignup(event) {
            event.preventDefault();
            
            const formData = new FormData(event.target);
            const password = formData.get('signup-password');
            const confirmPassword = formData.get('signup-confirm-password');
            
            if (password !== confirmPassword) {
                alert('Passwords do not match. Please try again.');
                return;
            }
            
            if (password.length < 6) {
                alert('Password must be at least 6 characters long.');
                return;
            }
            
            // In a real application, this would create a new user in the database
            currentUser = {
                name: formData.get('signup-name'),
                email: formData.get('signup-email'),
                phone: formData.get('signup-phone'),
                signupTime: new Date().toISOString()
            };
            
            // Pre-populate profile with signup data
            currentProfile = {
                name: currentUser.name,
                email: currentUser.email,
                phone: currentUser.phone,
                address: '',
                stores: '',
                brands: '',
                instructions: ''
            };
            
            isLoggedIn = true;
            updateNavigation();
            showSection('profile');
            
            alert('Account created successfully! Please complete your profile.');
            event.target.reset();
        }

        function logout() {
            currentUser = null;
            currentProfile = null;
            isLoggedIn = false;
            orders = [];
            invoices = [];
            
            updateNavigation();
            showSection('home');
            
            alert('You have been logged out successfully.');
        }

        function updateNavigation() {
            const mainNav = document.getElementById('main-nav');
            const userNav = document.getElementById('user-nav');
            
            if (isLoggedIn) {
                mainNav.style.display = 'none';
                userNav.style.display = 'flex';
            } else {
                mainNav.style.display = 'flex';
                userNav.style.display = 'none';
            }
        }

        // Package selection functions
        function selectPackage(packageType) {
            if (!isLoggedIn) {
                alert('Please login or sign up to select a package.');
                showSection('login');
                return;
            }
            
            // Remove previous selection
            document.querySelectorAll('.package-card').forEach(card => card.classList.remove('selected'));
            
            // Select new package
            event.target.closest('.package-card').classList.add('selected');
            selectedPackage = packageType;
            
            // Show package form
            document.querySelector('.service-selection').style.display = 'none';
            document.getElementById('package-form').style.display = 'block';
            document.getElementById('selected-package').value = packageType;
            
            const packageInfo = packagePricing[packageType];
            document.getElementById('selected-package-title').textContent = 
                `${packageInfo.name} - $${packageInfo.price}/week`;
        }

        function showIndividualServices() {
            if (!isLoggedIn) {
                alert('Please login or sign up to order services.');
                showSection('login');
                return;
            }
            
            document.querySelector('.service-selection').style.display = 'none';
            document.getElementById('individual-form').style.display = 'block';
        }

        function backToPackageSelection() {
            document.querySelector('.service-selection').style.display = 'block';
            document.getElementById('package-form').style.display = 'none';
            document.getElementById('individual-form').style.display = 'none';
            selectedPackage = null;
            
            // Clear selections
            document.querySelectorAll('.package-card').forEach(card => card.classList.remove('selected'));
        }

        function backToServiceSelection() {
            document.querySelector('.service-selection').style.display = 'block';
            document.getElementById('individual-form').style.display = 'none';
            document.getElementById('package-form').style.display = 'none';
        }

        // Individual service pricing functions
        function updateServicePricing() {
            const serviceType = document.getElementById('service-type').value;
            const pricingDiv = document.getElementById('service-pricing');
            const waitTimeOptions = document.getElementById('wait-time-options');
            const cleaningHours = document.getElementById('cleaning-hours');
            
            // Hide conditional options first
            waitTimeOptions.style.display = 'none';
            cleaningHours.style.display = 'none';
            
            if (!serviceType) {
                pricingDiv.innerHTML = '';
                return;
            }
            
            const service = servicePricing[serviceType];
            let pricingText = `Base Price: $${service.base}`;
            
            if (service.unit) {
                pricingText += ` ${service.unit}`;
            }
            
            if (serviceType === 'wait-time') {
                waitTimeOptions.style.display = 'block';
                pricingText = 'First 15 minutes: Free (included with service)';
            } else if (serviceType === 'light-cleaning') {
                cleaningHours.style.display = 'block';
            }
            
            pricingDiv.innerHTML = pricingText;
            updateEstimatedCost();
        }

        function updateWaitTimePricing() {
            updateEstimatedCost();
        }

        function updateEstimatedCost() {
            const serviceType = document.getElementById('service-type').value;
            const waitDuration = document.getElementById('wait-duration').value;
            const cleaningDuration = parseFloat(document.getElementById('cleaning-duration').value) || 1;
            const isWeekend = document.getElementById('weekend-service').checked;
            const costDiv = document.getElementById('estimated-cost');
            
            if (!serviceType) {
                costDiv.innerHTML = '';
                return;
            }
            
            let baseCost = servicePricing[serviceType].base;
            let breakdown = [`${servicePricing[serviceType].name}: $${baseCost}`];
            
            // Calculate wait time cost
            if (serviceType === 'wait-time' && waitDuration) {
                if (waitDuration === '15-30') {
                    baseCost += 5;
                    breakdown.push('15-30 minutes wait: $5');
                } else if (waitDuration === '30-60') {
                    baseCost += 10;
                    breakdown.push('30-60 minutes wait: $10');
                } else if (waitDuration === '60+') {
                    baseCost += 15;
                    breakdown.push('1+ hours wait: $15/hour');
                }
            }
            
            // Calculate cleaning cost
            if (serviceType === 'light-cleaning') {
                baseCost = 25 * cleaningDuration;
                breakdown = [`Light Cleaning (${cleaningDuration} hours): $${baseCost}`];
            }
            
            // Apply weekend premium
            let totalCost = baseCost;
            if (isWeekend) {
                const premium = baseCost * 0.2;
                totalCost = baseCost + premium;
                breakdown.push(`Weekend/Holiday Premium (20%): $${premium.toFixed(2)}`);
            }
            
            // Display breakdown
            let html = '<div class="cost-breakdown"><h4>Estimated Cost Breakdown:</h4>';
            breakdown.forEach(item => {
                html += `<div class="cost-item"><span>${item}</span></div>`;
            });
            html += `<div class="cost-item"><span>Total Estimated Cost:</span><span>$${totalCost.toFixed(2)}</span></div>`;
            html += '</div>';
            
            if (isWeekend) {
                html += '<div class="premium-notice">📅 Weekend and holiday services include a 20% premium charge.</div>';
            }
            
            costDiv.innerHTML = html;
        }

        // Form submission functions
        function submitPackageOrder(event) {
            event.preventDefault();
            
            const formData = new FormData(event.target);
            const selectedDays = Array.from(document.querySelectorAll('.days-selection input:checked'))
                .map(cb => cb.value);
            
            const order = {
                id: 'PKG-' + Date.now(),
                type: 'package',
                package: selectedPackage,
                packageInfo: packagePricing[selectedPackage],
                startDate: formData.get('start-date'),
                preferredDays: selectedDays,
                notes: formData.get('package-notes'),
                status: 'pending',
                date: new Date().toISOString()
            };
            
            orders.push(order);
            
            // Create weekly invoice
            const invoice = {
                id: 'INV-' + Date.now(),
                orderId: order.id,
                amount: packagePricing[selectedPackage].price,
                status: 'pending',
                date: new Date().toISOString(),
                description: `Weekly ${packagePricing[selectedPackage].name} - ${packagePricing[selectedPackage].duration}`,
                recurring: true
            };
            
            invoices.push(invoice);
            
            saveToStorage();
            event.target.reset();
            backToPackageSelection();
            
            alert(`${packagePricing[selectedPackage].name} subscription created successfully! You will receive weekly invoices of $${packagePricing[selectedPackage].price}.`);
        }

        function submitIndividualOrder(event) {
            event.preventDefault();
            
            const formData = new FormData(event.target);
            const serviceType = formData.get('service-type');
            
            // Calculate final cost
            let cost = servicePricing[serviceType].base;
            const waitDuration = formData.get('wait-duration');
            const cleaningDuration = parseFloat(formData.get('cleaning-duration')) || 1;
            const isWeekend = formData.get('weekend-service') === 'on';
            
            if (serviceType === 'wait-time' && waitDuration) {
                if (waitDuration === '15-30') cost += 5;
                else if (waitDuration === '30-60') cost += 10;
                else if (waitDuration === '60+') cost += 15;
            }
            
            if (serviceType === 'light-cleaning') {
                cost = 25 * cleaningDuration;
            }
            
            if (isWeekend) {
                cost = cost * 1.2; // Add 20% premium
            }
            
            const order = {
                id: 'SRV-' + Date.now(),
                type: 'individual',
                serviceType: serviceType,
                serviceName: servicePricing[serviceType].name,
                details: formData.get('service-details'),
                preferredDate: formData.get('preferred-date'),
                preferredTime: formData.get('preferred-time'),
                isWeekend: isWeekend,
                notes: formData.get('individual-notes'),
                estimatedCost: cost,
                status: 'pending',
                date: new Date().toISOString()
            };
            
            orders.push(order);
            
            // Create invoice
            const invoice = {
                id: 'INV-' + Date.now(),
                orderId: order.id,
                amount: cost,
                status: 'pending',
                date: new Date().toISOString(),
                description: `${servicePricing[serviceType].name} - ${formData.get('preferred-date')}`,
                recurring: false
            };
            
            invoices.push(invoice);
            
            saveToStorage();
            event.target.reset();
            backToServiceSelection();
            
            alert(`Service request submitted successfully! Estimated cost: $${cost.toFixed(2)}. You will receive an invoice once the service is confirmed.`);
        }

        // Navigation functions
        function showSection(sectionId) {
            // Check if user needs to be logged in for this section
            const protectedSections = ['profile', 'orders', 'schedule', 'invoices', 'payments'];
            
            if (protectedSections.includes(sectionId) && !isLoggedIn) {
                alert('Please login or sign up to access this section.');
                showSection('login');
                return;
            }
            
            // Hide all sections
            document.querySelectorAll('.section').forEach(section => {
                section.classList.remove('active');
            });
            
            // Show selected section
            document.getElementById(sectionId).classList.add('active');
            
            // Update specific sections when shown
            if (sectionId === 'invoices') {
                updateInvoicesList();
            } else if (sectionId === 'payments') {
                updatePaymentInvoices();
            } else if (sectionId === 'profile' && currentProfile) {
                displayProfile();
            }
        }

        // Profile management
        function saveProfile(event) {
            event.preventDefault();
            
            const formData = new FormData(event.target);
            currentProfile = {
                name: formData.get('name'),
                phone: formData.get('phone'),
                email: formData.get('email'),
                address: formData.get('address'),
                stores: formData.get('stores'),
                brands: formData.get('brands'),
                instructions: formData.get('instructions')
            };
            
            displayProfile();
            saveToStorage();
            alert('Profile saved successfully!');
        }

        function displayProfile() {
            if (!currentProfile) return;
            
            document.getElementById('display-name').textContent = currentProfile.name;
            document.getElementById('display-phone').textContent = currentProfile.phone;
            document.getElementById('display-email').textContent = currentProfile.email;
            document.getElementById('display-address').textContent = currentProfile.address;
            document.getElementById('display-stores').textContent = currentProfile.stores || 'None specified';
            document.getElementById('display-brands').textContent = currentProfile.brands || 'None specified';
            document.getElementById('display-instructions').textContent = currentProfile.instructions || 'None specified';
            
            document.getElementById('profile-display').style.display = 'block';
            document.getElementById('profile-form').style.display = 'none';
        }

        function editProfile() {
            // Populate form with current data
            if (currentProfile) {
                document.getElementById('name').value = currentProfile.name;
                document.getElementById('phone').value = currentProfile.phone;
                document.getElementById('email').value = currentProfile.email;
                document.getElementById('address').value = currentProfile.address;
                document.getElementById('stores').value = currentProfile.stores;
                document.getElementById('brands').value = currentProfile.brands;
                document.getElementById('instructions').value = currentProfile.instructions;
            }
            
            document.getElementById('profile-display').style.display = 'none';
            document.getElementById('profile-form').style.display = 'block';
        }

        // Scheduling functions
        function updateTimeSlots() {
            const selectedDate = document.getElementById('service-date').value;
            const timeSlotsContainer = document.getElementById('time-slots');
            
            if (!selectedDate) {
                timeSlotsContainer.innerHTML = '<p>Please select a date to see available time slots.</p>';
                return;
            }
            
            const date = new Date(selectedDate);
            const dayOfWeek = date.getDay(); // 0 = Sunday, 1 = Monday, etc.
            
            let timeSlots = [];
            
            // Monday-Friday: 8am-2pm
            if (dayOfWeek >= 1 && dayOfWeek <= 5) {
                timeSlots = [
                    '8:00 AM - 9:00 AM',
                    '9:00 AM - 10:00 AM',
                    '10:00 AM - 11:00 AM',
                    '11:00 AM - 12:00 PM',
                    '12:00 PM - 1:00 PM',
                    '1:00 PM - 2:00 PM'
                ];
            } 
            // Saturday-Sunday: 7am-5pm
            else if (dayOfWeek === 0 || dayOfWeek === 6) {
                timeSlots = [
                    '7:00 AM - 8:00 AM',
                    '8:00 AM - 9:00 AM',
                    '9:00 AM - 10:00 AM',
                    '10:00 AM - 11:00 AM',
                    '11:00 AM - 12:00 PM',
                    '12:00 PM - 1:00 PM',
                    '1:00 PM - 2:00 PM',
                    '2:00 PM - 3:00 PM',
                    '3:00 PM - 4:00 PM',
                    '4:00 PM - 5:00 PM'
                ];
            }
            
            timeSlotsContainer.innerHTML = '';
            
            timeSlots.forEach(slot => {
                const slotElement = document.createElement('div');
                slotElement.className = 'time-slot';
                slotElement.textContent = slot;
                slotElement.onclick = () => selectTimeSlot(slot, slotElement);
                
                // Randomly mark some slots as unavailable for demo
                if (Math.random() < 0.2) {
                    slotElement.classList.add('unavailable');
                    slotElement.onclick = null;
                }
                
                timeSlotsContainer.appendChild(slotElement);
            });
        }

        function selectTimeSlot(slot, element) {
            // Remove previous selection
            document.querySelectorAll('.time-slot').forEach(el => el.classList.remove('selected'));
            
            // Select new slot
            element.classList.add('selected');
            selectedTimeSlot = slot;
        }

        function scheduleService() {
            const selectedDate = document.getElementById('service-date').value;
            const deliveryNotes = document.getElementById('delivery-notes').value;
            
            if (!selectedDate || !selectedTimeSlot) {
                alert('Please select both a date and time slot.');
                return;
            }
            
            alert('Service scheduled successfully! Your personal shopper will be notified.');
            
            // Reset form
            document.getElementById('service-date').value = '';
            document.getElementById('delivery-notes').value = '';
            selectedTimeSlot = null;
            updateTimeSlots();
        }

        // Invoice management
        function updateInvoicesList() {
            const invoicesList = document.getElementById('invoices-list');
            
            if (invoices.length === 0) {
                invoicesList.innerHTML = '<p>No invoices available yet.</p>';
                return;
            }
            
            invoicesList.innerHTML = '';
            
            invoices.forEach(invoice => {
                const invoiceElement = document.createElement('div');
                invoiceElement.className = 'invoice-item';
                invoiceElement.innerHTML = `
                    <div>
                        <strong>Invoice ${invoice.id}</strong>
                        <p>${invoice.description}</p>
                        <p><em>Date: ${new Date(invoice.date).toLocaleDateString()}</em></p>
                    </div>
                    <div>
                        <div class="invoice-status ${invoice.status}">
                            ${invoice.status}
                        </div>
                        <p><strong>$${invoice.amount.toFixed(2)}</strong></p>
                    </div>
                `;
                
                invoicesList.appendChild(invoiceElement);
            });
        }

        // Payment management
        function selectPaymentMethod(method) {
            // Remove previous selection
            document.querySelectorAll('.payment-method').forEach(el => el.classList.remove('selected'));
            
            // Select new method
            document.querySelector(`[data-method="${method}"]`).classList.add('selected');
            selectedPaymentMethod = method;
        }

        function updatePaymentInvoices() {
            const paymentInvoices = document.getElementById('payment-invoices');
            const pendingInvoices = invoices.filter(inv => inv.status === 'pending' && inv.amount > 0);
            
            if (pendingInvoices.length === 0) {
                paymentInvoices.innerHTML = '<p>No pending invoices to pay.</p>';
                return;
            }
            
            paymentInvoices.innerHTML = '<h3>Pending Invoices:</h3>';
            
            pendingInvoices.forEach(invoice => {
                const invoiceElement = document.createElement('div');
                invoiceElement.className = 'order-summary';
                invoiceElement.innerHTML = `
                    <div class="order-item">
                        <span><strong>Invoice ${invoice.id}</strong></span>
                        <span><strong>$${invoice.amount.toFixed(2)}</strong></span>
                    </div>
                    <p>${invoice.description}</p>
                    <button class="btn" onclick="selectInvoiceForPayment('${invoice.id}', ${invoice.amount})">
                        Pay This Invoice
                    </button>
                `;
                
                paymentInvoices.appendChild(invoiceElement);
            });
        }

        function selectInvoiceForPayment(invoiceId, amount) {
            document.getElementById('payment-amount').value = amount.toFixed(2);
            document.getElementById('payment-reference').value = invoiceId;
        }

        function processPayment() {
            const amount = parseFloat(document.getElementById('payment-amount').value);
            const tipAmount = parseFloat(document.getElementById('tip-amount').value) || 0;
            const reference = document.getElementById('payment-reference').value;
            const totalAmount = amount + tipAmount;
            
            if (!selectedPaymentMethod || !amount) {
                alert('Please select a payment method and enter an amount.');
                return;
            }
            
            // Update invoice status if reference matches
            if (reference) {
                const invoice = invoices.find(inv => inv.id === reference);
                if (invoice) {
                    invoice.status = 'paid';
                }
            }
            
            let paymentMessage = `Payment of $${amount.toFixed(2)}`;
            if (tipAmount > 0) {
                paymentMessage += ` + $${tipAmount.toFixed(2)} tip (Total: $${totalAmount.toFixed(2)})`;
            }
            paymentMessage += ` submitted via ${selectedPaymentMethod.charAt(0).toUpperCase() + selectedPaymentMethod.slice(1)}`;
            
            if (selectedPaymentMethod === 'cashapp') {
                paymentMessage += ' to $southernassist';
            } else if (selectedPaymentMethod === 'venmo') {
                paymentMessage += ' to @SouthernAssist';
            }
            
            saveToStorage();
            updateInvoicesList();
            updatePaymentInvoices();
            
            alert(`Payment information submitted successfully! ${paymentMessage}. Your personal shopper will be notified.`);
            
            // Reset form
            document.getElementById('payment-amount').value = '';
            document.getElementById('payment-reference').value = '';
            document.getElementById('tip-amount').value = '';
            selectedPaymentMethod = null;
            document.querySelectorAll('.payment-method').forEach(el => el.classList.remove('selected'));
        }

        // Data persistence
        function saveToStorage() {
            const data = {
                user: currentUser,
                profile: currentProfile,
                orders: orders,
                invoices: invoices,
                isLoggedIn: isLoggedIn
            };
            
            // In a real application, this would be saved to a database
            // For demo purposes, we'll use in-memory storage
            window.appData = data;
        }

        function loadSavedData() {
            if (window.appData) {
                const data = window.appData;
                currentUser = data.user;
                currentProfile = data.profile;
                orders = data.orders || [];
                invoices = data.invoices || [];
                isLoggedIn = data.isLoggedIn || false;
                
                updateNavigation();
                
                if (currentProfile && isLoggedIn) {
                    displayProfile();
                }
            } else {
                // Initialize with sample data for demo
                initializeSampleData();
            }
        }

        function initializeSampleData() {
            // Add sample invoices for demo
            invoices.push({
                id: 'INV-001',
                orderId: 'ORD-001',
                amount: 127.50,
                status: 'pending',
                date: new Date().toISOString(),
                description: 'Grocery shopping - Milk, bread, eggs, fruits, vegetables...'
            });
            
            invoices.push({
                id: 'INV-002',
                orderId: 'ORD-002',
                amount: 85.25,
                status: 'paid',
                date: new Date(Date.now() - 86400000).toISOString(),
                description: 'Pharmacy run - Prescriptions and health essentials'
            });
            
            saveToStorage();
        }

        // Form validation helpers
        function validatePhone(phone) {
            const phoneRegex = /^[\+]?[1-9]?[\d\s\-\(\)]+$/;
            return phoneRegex.test(phone);
        }

        function validateEmail(email) {
            const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            return emailRegex.test(email);
        }

        // Enhanced form validation
        document.addEventListener('DOMContentLoaded', function() {
            // Profile form validation
            const profileForm = document.getElementById('profile-form');
            if (profileForm) {
                profileForm.addEventListener('submit', function(e) {
                    const phone = document.getElementById('phone').value;
                    const email = document.getElementById('email').value;
                    
                    if (!validatePhone(phone)) {
                        e.preventDefault();
                        alert('Please enter a valid phone number.');
                        return;
                    }
                    
                    if (!validateEmail(email)) {
                        e.preventDefault();
                        alert('Please enter a valid email address.');
                        return;
                    }
                });
            }

            // Set minimum dates to today
            const today = new Date().toISOString().split('T')[0];
            const dateInputs = ['service-date', 'start-date', 'preferred-date'];
            dateInputs.forEach(id => {
                const input = document.getElementById(id);
                if (input) input.min = today;
            });

            // Add event listeners for cost updates
            const cleaningDuration = document.getElementById('cleaning-duration');
            if (cleaningDuration) {
                cleaningDuration.addEventListener('input', updateEstimatedCost);
            }
            
            const weekendService = document.getElementById('weekend-service');
            if (weekendService) {
                weekendService.addEventListener('change', updateEstimatedCost);
            }

            // Load saved data
            loadSavedData();
            updateTimeSlots();
            updateInvoicesList();
            updatePaymentInvoices();
        });

        // Mobile-friendly touch events for time slots
        document.addEventListener('touchstart', function(e) {
            if (e.target.classList.contains('time-slot') && !e.target.classList.contains('unavailable')) {
                e.target.style.transform = 'scale(0.95)';
            }
        });

        document.addEventListener('touchend', function(e) {
            if (e.target.classList.contains('time-slot')) {
                e.target.style.transform = '';
            }
        });

        // Accessibility: Keyboard navigation for time slots
        document.addEventListener('keydown', function(e) {
            if (e.target.classList.contains('time-slot') && e.key === 'Enter') {
                e.target.click();
            }
        });

        // Service worker for offline functionality (basic)
        if ('serviceWorker' in navigator) {
            window.addEventListener('load', function() {
                navigator.serviceWorker.register('/sw.js').then(function(registration) {
                    console.log('ServiceWorker registration successful');
                }, function(err) {
                    console.log('ServiceWorker registration failed: ', err);
                });
            });
        }

        // Auto-save form data as user types (for better UX)
        document.addEventListener('input', function(e) {
            if (e.target.form && e.target.form.id === 'profile-form') {
                // Auto-save profile form data
                const formData = new FormData(e.target.form);
                const tempProfile = {};
                for (let [key, value] of formData.entries()) {
                    tempProfile[key] = value;
                }
                // Store temporarily (could be used for auto-recovery)
                window.tempProfileData = tempProfile;
            }
        });

        // Print invoice functionality
        function printInvoice(invoiceId) {
            const invoice = invoices.find(inv => inv.id === invoiceId);
            if (!invoice) return;
            
            const printWindow = window.open('', '_blank');
            printWindow.document.write(`
                <html>
                    <head>
                        <title>Invoice ${invoiceId}</title>
                        <style>
                            body { font-family: Arial, sans-serif; margin: 20px; color: #4A5568; }
                            .header { text-align: center; margin-bottom: 30px; }
                            .header h1 { color: #4A5568; }
                            .header h2 { color: #FF7A7A; }
                            .invoice-details { margin-bottom: 20px; }
                            .total { font-weight: bold; font-size: 1.2em; margin-top: 20px; color: #4A5568; }
                        </style>
                    </head>
                    <body>
                        <div class="header">
                            <h1>Southern Assist</h1>
                            <p>Lynn Saucier | 662-809-9672 | ursouthernassist@gmail.com</p>
                            <h2>Invoice ${invoiceId}</h2>
                        </div>
                        <div class="invoice-details">
                            <p><strong>Date:</strong> ${new Date(invoice.date).toLocaleDateString()}</p>
                            <p><strong>Description:</strong> ${invoice.description}</p>
                            <p><strong>Status:</strong> ${invoice.status}</p>
                        </div>
                        <div class="total">
                            <p>Total Amount: $${invoice.amount.toFixed(2)}</p>
                        </div>
                        <div style="margin-top: 30px; padding: 20px; background: #FFF8E7; border-radius: 8px;">
                            <h3>Payment Methods:</h3>
                            <p><strong>Cash:</strong> Pay in person</p>
                            <p><strong>Check:</strong> Mail or deliver</p>
                            <p><strong>CashApp:</strong> $southernassist</p>
                            <p><strong>Venmo:</strong> @SouthernAssist</p>
                        </div>
                    </body>
                </html>
            `);
            printWindow.document.close();
            printWindow.print();
        }
    </script>
</body>
</html>d" onclick="selectPackage('simple')">
                            <h4>Simple Support</h4>
                            <div class="package-price">$50/week</div>
                            <p>2 Hours A Week</p>
                            <p>Shopping, errands, and light cleaning</p>
                        </div>
                        
                        <div class="package-card" onclick="selectPackage('essential')">
                            <h4>Essential Package</h4>
                            <div class="package-price">$100/week</div>
                            <p>4 Hours A Week</p>
                            <p>Shopping, errands, and light cleaning</p>
                        </div>
                        
                        <div class="package-card" onclick="selectPackage('premium')">
                            <h4>Premium Package</h4>
                            <div class="package-price">$150/week</div>
                            <p>2 Hours A Week + Transportation</p>
                            <p>Up to 2 trips included</p>
                        </div>
                        
                        <div class="package-car
