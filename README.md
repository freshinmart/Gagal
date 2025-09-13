<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fresh.in - Belanja Kebutuhan Sehari-hari</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Montserrat:wght@700;800;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #00B14F;
            --primary-dark: #009440;
            --primary-light: #E0F6E9;
            --primary-gradient: linear-gradient(135deg, #00B14F 0%, #00D25B 100%);
            --accent: #FF6B00;
            --secondary: #2196F3;
            --light: #FFFFFF;
            --dark: #1E272E;
            --gray-light: #F5F7FA;
            --gray: #A6A6A6;
            --gray-dark: #687176;
            --success: #28C76F;
            --warning: #FF9F43;
            --error: #EA5455;
            --border-radius: 16px;
            --border-radius-sm: 8px;
            --box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
            --box-shadow-lg: 0 10px 30px rgba(0, 0, 0, 0.12);
            --transition: all 0.3s ease;
            --header-height: 70px;
            --bottom-nav-height: 65px;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background-color: var(--gray-light);
            color: var(--dark);
            overflow-x: hidden;
            line-height: 1.6;
            padding-top: var(--header-height);
            padding-bottom: var(--bottom-nav-height);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header Styles */
        header {
            background-color: var(--light);
            box-shadow: var(--box-shadow);
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            height: var(--header-height);
            transition: var(--transition);
        }

        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 100%;
            padding: 0 20px;
        }

        .header-left {
            display: flex;
            align-items: center;
        }

        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            font-size: 20px;
            color: var(--dark);
            cursor: pointer;
            margin-right: 15px;
        }

        .logo {
            display: flex;
            align-items: center;
        }

        .logo h1 {
            font-family: 'Montserrat', sans-serif;
            font-size: 24px;
            font-weight: 800;
            letter-spacing: -0.5px;
        }

        .fresh {
            color: var(--primary);
        }

        .dot-in {
            color: var(--accent);
        }

        .header-center {
            flex: 1;
            max-width: 500px;
            margin: 0 20px;
            position: relative;
        }

        .search-bar {
            position: relative;
        }

        .search-bar input {
            width: 100%;
            padding: 12px 50px 12px 20px;
            border: 1px solid #e0e0e0;
            border-radius: 30px;
            font-size: 14px;
            transition: var(--transition);
            background-color: var(--gray-light);
            box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.05);
        }

        .search-bar input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 2px rgba(0, 177, 79, 0.2);
            background-color: var(--light);
        }

        .search-bar button {
            position: absolute;
            right: 4px;
            top: 4px;
            background: var(--primary-gradient);
            color: white;
            border: none;
            border-radius: 20px;
            padding: 8px 16px;
            cursor: pointer;
            transition: var(--transition);
            font-weight: 500;
            font-size: 14px;
        }

        .search-bar button:hover {
            opacity: 0.9;
            transform: translateY(-1px);
        }

        .search-suggestions {
            position: absolute;
            top: 100%;
            left: 0;
            right: 0;
            background: white;
            border-radius: 0 0 var(--border-radius) var(--border-radius);
            box-shadow: var(--box-shadow-lg);
            z-index: 1000;
            max-height: 300px;
            overflow-y: auto;
            display: none;
        }
        
        .search-suggestions.active {
            display: block;
        }
        
        .suggestion-item {
            padding: 12px 15px;
            cursor: pointer;
            display: flex;
            align-items: center;
            border-bottom: 1px solid #f0f0f0;
            transition: var(--transition);
        }
        
        .suggestion-item:hover {
            background-color: var(--primary-light);
        }
        
        .suggestion-item i {
            margin-right: 10px;
            color: var(--gray);
        }
        
        .search-filters {
            display: flex;
            gap: 10px;
            margin-top: 10px;
            flex-wrap: wrap;
            display: none;
        }
        
        .search-filters.active {
            display: flex;
        }
        
        .filter-chip {
            background: var(--gray-light);
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 12px;
            cursor: pointer;
            transition: var(--transition);
        }
        
        .filter-chip.active {
            background: var(--primary);
            color: white;
        }

        .header-right {
            display: flex;
            gap: 15px;
        }

        .icon-link {
            position: relative;
            color: var(--dark);
            font-size: 18px;
            text-decoration: none;
            transition: var(--transition);
            display: flex;
            align-items: center;
            padding: 8px;
            border-radius: 50%;
        }

        .icon-link:hover {
            color: var(--primary);
            background-color: var(--primary-light);
        }

        .icon-link .label {
            font-size: 14px;
            margin-left: 5px;
            display: none;
        }

        .cart-count, .wishlist-count {
            position: absolute;
            top: -2px;
            right: -2px;
            background: var(--primary);
            color: white;
            font-size: 11px;
            width: 18px;
            height: 18px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 600;
        }

        /* Bottom Navigation */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            height: var(--bottom-nav-height);
            background: var(--light);
            box-shadow: 0 -4px 20px rgba(0, 0, 0, 0.08);
            display: flex;
            justify-content: space-around;
            align-items: center;
            z-index: 1000;
            padding: 0 5px;
        }

        .nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-decoration: none;
            color: var(--gray);
            font-size: 12px;
            padding: 8px 12px;
            border-radius: var(--border-radius-sm);
            transition: var(--transition);
            flex: 1;
            max-width: 80px;
        }

        .nav-item.active {
            color: var(--primary);
        }

        .nav-item i {
            font-size: 20px;
            margin-bottom: 4px;
        }

        .nav-item.active i {
            transform: translateY(-2px);
        }

        .nav-item .nav-label {
            font-weight: 500;
        }

        /* Bottom Cart */
        .bottom-cart {
            position: fixed;
            bottom: 80px;
            left: 50%;
            transform: translateX(-50%);
            background: var(--primary);
            color: white;
            padding: 12px 25px;
            border-radius: 30px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.15);
            z-index: 999;
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
            transition: var(--transition);
        }
        
        .bottom-cart:hover {
            background: var(--primary-dark);
            transform: translateX(-50%) scale(1.05);
        }
        
        .bottom-cart-count {
            background: white;
            color: var(--primary);
            width: 24px;
            height: 24px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 12px;
        }
        
        .bottom-cart-text {
            font-weight: 600;
        }
        
        .bottom-cart-price {
            margin-left: auto;
            font-weight: 700;
        }

        /* Mobile Menu */
        .mobile-menu {
            position: fixed;
            top: var(--header-height);
            left: -100%;
            width: 80%;
            height: calc(100vh - var(--header-height) - var(--bottom-nav-height));
            background: var(--light);
            z-index: 999;
            transition: var(--transition);
            overflow-y: auto;
            box-shadow: 2px 0 10px rgba(0, 0, 0, 0.1);
        }

        .mobile-menu.active {
            left: 0;
        }

        .mobile-menu-header {
            padding: 15px;
            background: var(--primary-gradient);
            color: white;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .mobile-menu-close {
            background: none;
            border: none;
            color: white;
            font-size: 20px;
            cursor: pointer;
        }

        .mobile-menu-categories {
            padding: 15px;
        }

        .mobile-menu-category {
            margin-bottom: 15px;
        }

        .mobile-menu-category-title {
            font-weight: 600;
            margin-bottom: 10px;
            padding-bottom: 5px;
            border-bottom: 1px solid #eee;
            color: var(--primary);
        }

        .mobile-menu-links {
            list-style: none;
        }

        .mobile-menu-links li {
            margin-bottom: 8px;
        }

        .mobile-menu-links a {
            display: block;
            padding: 10px;
            color: var(--dark);
            text-decoration: none;
            border-radius: 6px;
            transition: var(--transition);
        }

        .mobile-menu-links a:hover {
            background: var(--primary-light);
            color: var(--primary);
        }

        .mobile-menu-links a i {
            margin-right: 10px;
            width: 20px;
            text-align: center;
        }

        /* Navigation Categories */
        .nav-categories {
            background: var(--light);
            padding: 15px 0;
            border-bottom: 1px solid #eee;
            overflow-x: auto;
            white-space: nowrap;
            scrollbar-width: none;
        }

        .nav-categories::-webkit-scrollbar {
            display: none;
        }

        .category-scroll {
            display: flex;
            gap: 15px;
            padding: 0 20px;
        }

        .category-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-decoration: none;
            color: var(--dark);
            min-width: 70px;
            transition: var(--transition);
            padding: 10px 5px;
            border-radius: var(--border-radius-sm);
        }

        .category-item:hover {
            color: var(--primary);
            background-color: var(--primary-light);
        }

        .category-icon {
            width: 40px;
            height: 40px;
            border-radius: 12px;
            background: var(--primary-light);
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 8px;
            font-size: 18px;
            color: var(--primary);
            transition: var(--transition);
        }

        .category-item:hover .category-icon {
            background: var(--primary-gradient);
            color: white;
            transform: translateY(-3px);
        }

        .category-name {
            font-size: 12px;
            text-align: center;
            font-weight: 500;
        }

        /* Hero Carousel */
        .hero-carousel {
            margin: 20px 0;
            border-radius: var(--border-radius);
            overflow: hidden;
            position: relative;
            height: 180px;
            box-shadow: var(--box-shadow);
        }

        .carousel-container {
            position: relative;
            width: 100%;
            height: 100%;
            overflow: hidden;
        }

        .carousel-slides {
            display: flex;
            transition: transform 0.5s ease;
            height: 100%;
        }

        .carousel-slide {
            min-width: 100%;
            height: 100%;
            position: relative;
        }

        .carousel-slide img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .carousel-content {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            color: white;
            z-index: 2;
            padding: 20px;
            background: linear-gradient(transparent, rgba(0, 0, 0, 0.7));
        }

        .carousel-content h2 {
            font-size: 18px;
            font-weight: 700;
            margin-bottom: 8px;
        }

        .carousel-content p {
            font-size: 13px;
            opacity: 0.9;
            margin-bottom: 12px;
        }

        .hero-btn {
            display: inline-block;
            background: white;
            color: var(--primary);
            text-decoration: none;
            padding: 8px 16px;
            border-radius: 20px;
            font-weight: 600;
            font-size: 13px;
            transition: var(--transition);
            width: fit-content;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        .hero-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.15);
        }

        .carousel-controls {
            position: absolute;
            top: 50%;
            width: 100%;
            display: flex;
            justify-content: space-between;
            transform: translateY(-50%);
            z-index: 3;
            padding: 0 10px;
        }

        .carousel-control {
            background: rgba(0,0,0,0.5);
            color: white;
            border: none;
            padding: 10px;
            cursor: pointer;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 18px;
            transition: var(--transition);
        }

        .carousel-control:hover {
            background: rgba(0,0,0,0.7);
            transform: scale(1.1);
        }

        .carousel-dots {
            position: absolute;
            bottom: 10px;
            width: 100%;
            display: flex;
            justify-content: center;
            z-index: 3;
            gap: 8px;
        }

        .carousel-dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: rgba(255,255,255,0.5);
            cursor: pointer;
            transition: var(--transition);
        }

        .carousel-dot.active {
            background: white;
            transform: scale(1.2);
        }

        /* Products Grid */
        .products-section {
            padding: 20px 0;
        }

        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 16px;
        }

        .section-title {
            font-size: 18px;
            font-weight: 700;
            color: var(--dark);
            position: relative;
            padding-left: 12px;
        }

        .section-title::before {
            content: '';
            position: absolute;
            left: 0;
            top: 50%;
            transform: translateY(-50%);
            width: 4px;
            height: 18px;
            background: var(--primary-gradient);
            border-radius: 10px;
        }

        .view-all {
            color: var(--primary);
            text-decoration: none;
            font-size: 14px;
            font-weight: 500;
            display: flex;
            align-items: center;
        }

        .view-all i {
            margin-left: 5px;
            transition: var(--transition);
        }

        .view-all:hover i {
            transform: translateX(3px);
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
        }

        @media (min-width: 480px) {
            .products-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        @media (min-width: 768px) {
            .products-grid {
                grid-template-columns: repeat(4, 1fr);
            }
        }

        .product-card {
            background: var(--light);
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: var(--box-shadow);
            transition: var(--transition);
            position: relative;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--box-shadow-lg);
        }

        .product-badge {
            position: absolute;
            top: 10px;
            left: 10px;
            background: var(--primary);
            color: white;
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 10px;
            font-weight: 600;
            z-index: 2;
        }

        .product-badge.sale {
            background: var(--error);
        }

        .product-badge.new {
            background: var(--secondary);
        }

        .product-image {
            height: 160px;
            width: 100%;
            background-color: var(--gray-light);
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            position: relative;
        }

        .product-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s;
        }

        .product-card:hover .product-image img {
            transform: scale(1.05);
        }

        .like-button {
            position: absolute;
            top: 10px;
            right: 10px;
            background: rgba(255, 255, 255, 0.9);
            border: none;
            border-radius: 50%;
            width: 32px;
            height: 32px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            z-index: 3;
            transition: var(--transition);
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .like-button:hover {
            background: white;
            transform: scale(1.1);
        }

        .like-button i {
            color: #ccc;
            font-size: 16px;
            transition: var(--transition);
        }

        .like-button.liked i {
            color: var(--error);
        }

        .product-info {
            padding: 12px;
        }

        .product-title {
            font-size: 14px;
            font-weight: 500;
            margin-bottom: 8px;
            color: var(--dark);
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
            height: 40px;
        }

        .product-price {
            display: flex;
            align-items: center;
            margin-bottom: 12px;
        }

        .current-price {
            font-size: 16px;
            font-weight: 700;
            color: var(--dark);
        }

        .original-price {
            font-size: 13px;
            color: var(--gray);
            text-decoration: line-through;
            margin-left: 8px;
        }

        .discount {
            background: var(--primary-light);
            color: var(--primary);
            font-size: 11px;
            font-weight: 600;
            padding: 3px 6px;
            border-radius: 4px;
            margin-left: 8px;
        }

        .add-to-cart {
            display: block;
            width: 100%;
            background: var(--primary-gradient);
            color: white;
            border: none;
            padding: 10px;
            border-radius: var(--border-radius-sm);
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            font-size: 14px;
            box-shadow: 0 4px 10px rgba(0, 177, 79, 0.25);
        }

        .add-to-cart:hover {
            opacity: 0.9;
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(0, 177, 79, 0.3);
        }

        /* Flash Sale Section */
        .flash-sale {
            background: var(--light);
            border-radius: var(--border-radius);
            padding: 15px;
            margin: 20px 0;
            box-shadow: var(--box-shadow);
        }

        .flash-sale-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }

        .flash-sale-timer {
            display: flex;
            align-items: center;
            background: #FFF6E9;
            padding: 8px 12px;
            border-radius: 20px;
            color: var(--accent);
            font-weight: 600;
        }

        .flash-sale-timer i {
            margin-right: 8px;
        }

        .timer-count {
            display: flex;
            gap: 5px;
        }

        .timer-unit {
            background: var(--accent);
            color: white;
            padding: 2px 5px;
            border-radius: 4px;
            min-width: 20px;
            text-align: center;
        }

        /* Footer */
        footer {
            background: var(--light);
            padding: 30px 0 15px;
            margin-top: 30px;
        }

        .footer-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 30px;
        }

        @media (min-width: 768px) {
            .footer-grid {
                grid-template-columns: repeat(4, 1fr);
            }
        }

        .footer-logo {
            font-family: 'Montserrat', sans-serif;
            font-size: 20px;
            font-weight: 800;
            margin-bottom: 12px;
            display: block;
            text-decoration: none;
        }

        .footer-fresh {
            color: var(--primary);
        }

        .footer-in {
            color: var(--accent);
        }

        .footer-about p {
            color: var(--gray);
            margin-bottom: 15px;
            line-height: 1.7;
            font-size: 14px;
        }

        .social-links {
            display: flex;
            gap: 10px;
        }

        .social-links a {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 36px;
            height: 36px;
            background: var(--gray-light);
            color: var(--dark);
            border-radius: 50%;
            text-decoration: none;
            transition: var(--transition);
            font-size: 14px;
        }

        .social-links a:hover {
            background: var(--primary);
            color: white;
            transform: translateY(-3px);
        }

        .footer-title {
            font-size: 16px;
            font-weight: 600;
            margin-bottom: 15px;
            color: var(--dark);
            position: relative;
            padding-bottom: 8px;
        }

        .footer-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 30px;
            height: 3px;
            background: var(--primary);
            border-radius: 10px;
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 10px;
        }

        .footer-links a {
            color: var(--gray);
            text-decoration: none;
            transition: var(--transition);
            font-size: 14px;
            display: flex;
            align-items: center;
        }

        .footer-links a i {
            margin-right: 8px;
            font-size: 12px;
        }

        .footer-links a:hover {
            color: var(--primary);
            transform: translateX(5px);
        }

        .copyright {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid #eee;
            color: var(--gray);
            font-size: 13px;
            margin-top: 20px;
        }

        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 2000;
            align-items: center;
            justify-content: center;
            padding: 15px;
            backdrop-filter: blur(5px);
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: white;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow-lg);
            width: 100%;
            max-width: 500px;
            overflow: hidden;
            animation: modalSlideUp 0.3s ease;
            max-height: 90vh;
            display: flex;
            flex-direction: column;
        }

        @keyframes modalSlideUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .modal-header {
            padding: 15px 20px;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: var(--primary-gradient);
            color: white;
        }

        .modal-header h3 {
            font-size: 18px;
            font-weight: 600;
            flex: 1;
        }

        .modal-close {
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: white;
            opacity: 0.8;
            transition: var(--transition);
        }

        .modal-close:hover {
            opacity: 1;
            transform: rotate(90deg);
        }

        .modal-body {
            padding: 20px;
            overflow-y: auto;
            flex: 1;
        }

        /* Cart Modal */
        .cart-item {
            display: flex;
            padding: 15px 0;
            border-bottom: 1px solid #eee;
        }

        .cart-item:last-child {
            border-bottom: none;
        }

        .cart-item-image {
            width: 80px;
            height: 80px;
            background: var(--gray-light);
            border-radius: var(--border-radius-sm);
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 15px;
            overflow: hidden;
        }

        .cart-item-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .cart-item-details {
            flex: 1;
        }

        .cart-item-title {
            font-weight: 500;
            margin-bottom: 5px;
            font-size: 14px;
        }

        .cart-item-price {
            color: var(--dark);
            font-weight: 600;
            margin-bottom: 8px;
            font-size: 15px;
        }

        .cart-item-actions {
            display: flex;
            gap: 8px;
            align-items: center;
        }

        .quantity-control {
            display: flex;
            align-items: center;
            border: 1px solid #ddd;
            border-radius: 20px;
            overflow: hidden;
        }

        .quantity-btn {
            background: none;
            border: none;
            width: 30px;
            height: 30px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 16px;
            transition: var(--transition);
        }

        .quantity-btn:hover {
            background: var(--gray-light);
        }

        .quantity-input {
            width: 30px;
            text-align: center;
            border: none;
            background: transparent;
            font-size: 14px;
            font-weight: 600;
        }

        .remove-btn {
            background: none;
            border: none;
            color: var(--error);
            cursor: pointer;
            font-size: 13px;
            display: flex;
            align-items: center;
            transition: var(--transition);
        }

        .remove-btn:hover {
            color: #c53030;
        }

        .remove-btn i {
            margin-right: 4px;
        }

        .cart-summary {
            padding: 15px 20px;
            border-top: 1px solid #eee;
            background: var(--gray-light);
        }

        .summary-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-size: 14px;
        }

        .summary-total {
            display: flex;
            justify-content: space-between;
            font-weight: 700;
            font-size: 16px;
            margin-top: 12px;
            padding-top: 12px;
            border-top: 1px solid #ddd;
        }

        .checkout-btn {
            display: block;
            width: 100%;
            background: var(--primary-gradient);
            color: white;
            border: none;
            padding: 12px;
            border-radius: var(--border-radius-sm);
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            font-size: 15px;
            text-align: center;
            text-decoration: none;
            margin-top: 15px;
            box-shadow: 0 4px 10px rgba(0, 177, 79, 0.25);
        }

        .checkout-btn:hover {
            opacity: 0.9;
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(0, 177, 79, 0.3);
        }

        .empty-cart {
            text-align: center;
            padding: 40px 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            color: var(--gray);
        }

        .empty-cart i {
            font-size: 60px;
            color: #ddd;
            margin-bottom: 15px;
        }

        .empty-cart h4 {
            font-size: 18px;
            margin-bottom: 10px;
            color: var(--dark);
        }

        .empty-cart p {
            margin-bottom: 20px;
        }

        /* Checkout Modal */
        .checkout-steps {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
            position: relative;
        }

        .checkout-steps::before {
            content: '';
            position: absolute;
            top: 14px;
            left: 0;
            right: 0;
            height: 2px;
            background: #eee;
            z-index: 1;
        }

        .step {
            position: relative;
            z-index: 2;
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 25%;
        }

        .step-icon {
            width: 30px;
            height: 30px;
            border-radius: 50%;
            background: white;
            border: 2px solid #eee;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 13px;
            margin-bottom: 5px;
            transition: var(--transition);
        }

        .step.active .step-icon {
            background: var(--primary);
            border-color: var(--primary);
            color: white;
            transform: scale(1.1);
        }

        .step.completed .step-icon {
            background: var(--success);
            border-color: var(--success);
            color: white;
        }

        .step-text {
            font-size: 11px;
            text-align: center;
            color: var(--gray);
            font-weight: 500;
        }

        .step.active .step-text {
            color: var(--primary);
            font-weight: 600;
        }

        .checkout-form {
            margin-top: 15px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            font-size: 14px;
        }

        .form-control {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: var(--border-radius-sm);
            font-size: 14px;
            transition: var(--transition);
        }

        .form-control:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 2px rgba(0, 177, 79, 0.2);
        }

        .payment-options {
            margin-top: 15px;
        }

        .payment-option {
            display: flex;
            align-items: center;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: var(--border-radius-sm);
            margin-bottom: 10px;
            cursor: pointer;
            transition: var(--transition);
        }

        .payment-option:hover {
            border-color: var(--primary);
        }

        .payment-option.selected {
            border-color: var(--primary);
            background-color: var(--primary-light);
        }

        .payment-option input {
            margin-right: 10px;
        }

        .payment-option-icon {
            margin-right: 10px;
            font-size: 20px;
            color: var(--primary);
        }

        .qris-preview {
            text-align: center;
            margin-top: 15px;
            padding: 15px;
            background: var(--gray-light);
            border-radius: var(--border-radius-sm);
            display: none;
        }

        .qris-preview img {
            max-width: 180px;
            margin-bottom: 10px;
            border-radius: var(--border-radius-sm);
        }

        .payment-actions {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
            gap: 10px;
        }

        .btn {
            padding: 12px 20px;
            border-radius: var(--border-radius-sm);
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            border: none;
            flex: 1;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .btn-secondary {
            background: #e0e0e0;
            color: var(--dark);
        }

        .btn-secondary:hover {
            background: #d0d0d0;
        }

        .btn-primary {
            background: var(--primary-gradient);
            color: white;
            box-shadow: 0 4px 10px rgba(0, 177, 79, 0.25);
        }

        .btn-primary:hover {
            opacity: 0.9;
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(0, 177, 79, 0.3);
        }

        .btn:disabled {
            opacity: 0.6;
            cursor: not-allowed;
            transform: none !important;
        }

        /* QRIS Payment Verification */
        .payment-verification {
            margin-top: 15px;
            padding: 15px;
            background: var(--gray-light);
            border-radius: var(--border-radius-sm);
            text-align: center;
        }

        .verification-status {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 10px;
            font-size: 14px;
            font-weight: 500;
        }

        .verification-status i {
            font-size: 24px;
            margin-right: 10px;
        }

        .verification-status.verifying i {
            color: var(--warning);
            animation: spin 1s linear infinite;
        }

        .verification-status.success i {
            color: var(--success);
        }

        .verification-status.error i {
            color: var(--error);
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Wishlist Page */
        .wishlist-page {
            display: none;
            padding: 20px 0;
        }

        .wishlist-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
        }

        @media (min-width: 768px) {
            .wishlist-grid {
                grid-template-columns: repeat(4, 1fr);
            }
        }

        /* Profile Page */
        .profile-page {
            display: none;
            padding: 20px 0;
        }

        .profile-card {
            background: white;
            border-radius: var(--border-radius);
            padding: 20px;
            box-shadow: var(--box-shadow);
        }

        .profile-form {
            display: grid;
            grid-template-columns: 1fr;
            gap: 15px;
        }

        @media (min-width: 768px) {
            .profile-form {
                grid-template-columns: 1fr 1fr;
            }
        }

        .profile-form .form-group.full-width {
            grid-column: 1 / -1;
        }

        /* Orders Page */
        .orders-page {
            display: none;
            padding: 20px 0;
        }

        .order-card {
            background: white;
            border-radius: var(--border-radius);
            padding: 15px;
            margin-bottom: 15px;
            box-shadow: var(--box-shadow);
        }

        .order-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
        }

        .order-id {
            font-weight: 600;
            color: var(--primary);
        }

        .order-date {
            color: var(--gray);
            font-size: 14px;
        }

        .order-status {
            padding: 4px 8px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 500;
        }

        .status-pending {
            background-color: #FFF6E9;
            color: var(--warning);
        }

        .status-completed {
            background-color: var(--primary-light);
            color: var(--success);
        }

        .order-details {
            margin-top: 10px;
        }

        .order-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
        }

        .order-total {
            display: flex;
            justify-content: space-between;
            font-weight: 700;
            margin-top: 10px;
            padding-top: 10px;
            border-top: 1px solid #eee;
        }

        /* History Page with Receipts */
        .history-page {
            display: none;
            padding: 20px 0;
        }

        .receipt-card {
            background: white;
            border-radius: var(--border-radius);
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: var(--box-shadow);
            position: relative;
        }

        .receipt-header {
            text-align: center;
            margin-bottom: 20px;
            border-bottom: 2px dashed #eee;
            padding-bottom: 15px;
        }

        .receipt-header h3 {
            font-family: 'Montserrat', sans-serif;
            color: var(--primary);
            margin-bottom: 5px;
            font-size: 22px;
        }

        .receipt-details {
            margin-bottom: 15px;
        }

        .receipt-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            padding-bottom: 8px;
            border-bottom: 1px dashed #eee;
        }

        .receipt-total {
            display: flex;
            justify-content: space-between;
            font-weight: 700;
            margin-top: 15px;
            padding-top: 15px;
            border-top: 2px dashed #eee;
        }

        .receipt-footer {
            text-align: center;
            margin-top: 20px;
            color: var(--gray);
            font-size: 12px;
        }

        .print-receipt {
            position: absolute;
            top: 15px;
            right: 15px;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: var(--transition);
        }

        .print-receipt:hover {
            background: var(--primary-gradient);
            transform: scale(1.1);
        }

        /* Search Results Section */
        .search-results-section {
            display: none;
            padding: 20px 0;
        }
        
        .no-results {
            grid-column: 1 / -1;
            text-align: center;
            padding: 40px;
        }
        
        .no-results i {
            font-size: 48px;
            color: #ccc;
            margin-bottom: 16px;
        }
        
        /* Page container */
        .page {
            display: none;
        }
        
        .page.active {
            display: block;
        }
        
        /* Back button */
        .back-button {
            display: inline-flex;
            align-items: center;
            margin-bottom: 15px;
            color: var(--primary);
            text-decoration: none;
            font-weight: 500;
            padding: 8px 0;
            transition: var(--transition);
        }
        
        .back-button:hover {
            color: var(--accent);
            transform: translateX(-3px);
        }
        
        .back-button i {
            margin-right: 5px;
        }

        /* Floating action button */
        .fab {
            position: fixed;
            bottom: 80px;
            right: 20px;
            width: 60px;
            height: 60px;
            background: var(--primary-gradient);
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            box-shadow: 0 4px 15px rgba(0, 177, 79, 0.3);
            z-index: 999;
            transition: var(--transition);
            text-decoration: none;
        }
        
        .fab:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 8px 20px rgba(0, 177, 79, 0.4);
        }

        /* Help Page Styles */
        .faq-item {
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 1px solid #eee;
        }

        .faq-question {
            font-weight: 600;
            margin-bottom: 8px;
            color: var(--dark);
        }

        .faq-answer {
            color: var(--gray-dark);
            line-height: 1.6;
        }

        .contact-form {
            margin-top: 30px;
        }

        /* Admin Login Page */
        .admin-login {
            max-width: 400px;
            margin: 50px auto;
            padding: 20px;
            background: white;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
        }
        
        .admin-page {
            display: none;
        }
        
        .admin-sidebar {
            background: var(--dark);
            color: white;
            width: 250px;
            height: 100vh;
            position: fixed;
            top: 0;
            left: 0;
            padding-top: var(--header-height);
        }
        
        .admin-menu {
            list-style: none;
            padding: 0;
        }
        
        .admin-menu li {
            margin-bottom: 5px;
        }
        
        .admin-menu a {
            display: block;
            padding: 12px 20px;
            color: white;
            text-decoration: none;
            transition: var(--transition);
        }
        
        .admin-menu a:hover,
        .admin-menu a.active {
            background: var(--primary);
        }
        
        .admin-menu a i {
            margin-right: 10px;
            width: 20px;
            text-align: center;
        }
        
        .admin-content {
            margin-left: 250px;
            padding: 20px;
            padding-top: calc(var(--header-height) + 20px);
        }
        
        .admin-section {
            display: none;
            background: white;
            padding: 20px;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            margin-bottom: 20px;
        }
        
        .admin-section.active {
            display: block;
        }
        
        .admin-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }
        
        .admin-table th,
        .admin-table td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #eee;
        }
        
        .admin-table th {
            background: var(--gray-light);
            font-weight: 600;
        }
        
        .admin-form {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }
        
        .admin-form .full-width {
            grid-column: 1 / -1;
        }
        
        .admin-actions {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }
        
        .admin-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
        }

        /* Additional fee management */
        .fee-item {
            background: var(--gray-light);
            padding: 15px;
            border-radius: var(--border-radius-sm);
            margin-bottom: 15px;
        }
        
        .fee-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }
        
        .fee-title {
            font-weight: 600;
        }
        
        .fee-details {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 10px;
            font-size: 14px;
        }

        /* Responsive - Perbaikan khusus untuk tampilan mobile */
        @media (max-width: 768px) {
            :root {
                --header-height: 60px;
                --bottom-nav-height: 60px;
            }
            
            .header-container {
                padding: 0 10px;
            }
            
            .mobile-menu-btn {
                display: flex;
            }
            
            .header-center {
                margin: 0 10px;
            }
            
            .search-bar input {
                padding: 10px 15px;
                font-size: 14px;
            }
            
            .search-bar button {
                padding: 6px 12px;
                font-size: 12px;
            }
            
            .header-right {
                gap: 8px;
            }
            
            .icon-link {
                font-size: 16px;
                padding: 6px;
            }
            
            .hero-carousel {
                height: 160px;
            }
            
            .carousel-content h2 {
                font-size: 16px;
            }
            
            .products-grid, .wishlist-grid {
                grid-template-columns: repeat(2, 1fr);
                gap: 10px;
            }
            
            .product-image {
                height: 140px;
            }
            
            /* Bottom navigation */
            .nav-item {
                font-size: 10px;
                padding: 6px 8px;
            }
            
            .nav-item i {
                font-size: 18px;
            }
            
            /* Bottom cart */
            .bottom-cart {
                bottom: 70px;
                padding: 10px 20px;
            }
            
            /* Admin sidebar */
            .admin-sidebar {
                width: 100%;
                height: auto;
                position: relative;
                padding-top: 0;
            }
            
            .admin-content {
                margin-left: 0;
                padding-top: 20px;
            }
            
            /* Header saat di-scroll */
            header.scrolled {
                box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            }
        }

        @media (max-width: 480px) {
            .logo h1 {
                font-size: 18px;
            }
            
            .search-bar input {
                padding: 8px 12px;
                font-size: 13px;
            }
            
            .search-bar button {
                padding: 5px 10px;
                font-size: 11px;
            }
            
            .icon-link {
                font-size: 15px;
            }
            
            .hero-carousel {
                height: 140px;
            }
            
            .carousel-content {
                padding: 10px;
            }
            
            .carousel-content h2 {
                font-size: 15px;
            }
            
            .carousel-content p {
                font-size: 12px;
            }
            
            .products-grid, .wishlist-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .footer-grid {
                grid-template-columns: 1fr;
            }
            
            .nav-item {
                max-width: 60px;
            }
            
            .bottom-cart {
                font-size: 14px;
                padding: 8px 15px;
            }
        }

        /* Loading animation */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .product-card, .category-item {
            animation: fadeIn 0.5s ease forwards;
        }

        /* Notification */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            background: var(--primary);
            color: white;
            padding: 15px 20px;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow-lg);
            z-index: 9999;
            opacity: 0;
            transform: translateX(100px);
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
        }

        .notification i {
            margin-right: 10px;
            font-size: 20px;
        }

        .notification.show {
            opacity: 1;
            transform: translateX(0);
        }
    </style>
</head>
<body>
    <header id="main-header">
        <div class="header-container">
            <div class="header-left">
                <button class="mobile-menu-btn" id="mobile-menu-btn">
                    <i class="fas fa-bars"></i>
                </button>
                <div class="logo">
                    <h1><span class="fresh">Fresh</span><span class="dot-in">.in</span></h1>
                </div>
            </div>
            
            <div class="header-center">
                <div class="search-bar">
                    <input type="text" placeholder="Cari produk kebutuhan sehari-hari..." id="search-input">
                    <button id="search-btn"><i class="fas fa-search"></i> Cari</button>
                    <div class="search-suggestions" id="search-suggestions">
                        <!-- Suggestions will be populated by JavaScript -->
                    </div>
                </div>
                <div class="search-filters" id="search-filters">
                    <div class="filter-chip active" data-category="all">Semua</div>
                    <div class="filter-chip" data-category="buah">Buah & Sayur</div>
                    <div class="filter-chip" data-category="minuman">Minuman</div>
                    <div class="filter-chip" data-category="makanan">Makanan</div>
                    <div class="filter-chip" data-category="protein">Protein</div>
                </div>
            </div>
            
            <div class="header-right">
                <a href="#" class="icon-link" id="wishlist-link">
                    <i class="far fa-heart"></i>
                    <span class="wishlist-count">0</span>
                </a>
                <a href="#" class="icon-link" id="admin-link">
                    <i class="fas fa-cog"></i>
                </a>
                <a href="#" class="icon-link" id="profile-link">
                    <i class="fas fa-user"></i>
                </a>
            </div>
        </div>
    </header>

    <!-- Bottom Cart -->
    <div class="bottom-cart" id="bottom-cart">
        <div class="bottom-cart-count" id="bottom-cart-count">0</div>
        <div class="bottom-cart-text">Keranjang</div>
        <div class="bottom-cart-price" id="bottom-cart-price">Rp 0</div>
    </div>

    <!-- Bottom Navigation -->
    <nav class="bottom-nav">
        <a href="#" class="nav-item active" data-page="home">
            <i class="fas fa-home"></i>
            <span class="nav-label">Beranda</span>
        </a>
        <a href="#" class="nav-item" data-page="promo">
            <i class="fas fa-percentage"></i>
            <span class="nav-label">Promosi</span>
        </a>
        <a href="#" class="nav-item" data-page="cart">
            <i class="fas fa-shopping-cart"></i>
            <span class="nav-label">Keranjang</span>
        </a>
        <a href="#" class="nav-item" data-page="orders">
            <i class="fas fa-shopping-bag"></i>
            <span class="nav-label">Pesanan</span>
        </a>
        <a href="#" class="nav-item" data-page="profile">
            <i class="fas fa-user"></i>
            <span class="nav-label">Profil</span>
        </a>
    </nav>

    <!-- Mobile Menu -->
    <div class="mobile-menu" id="mobile-menu">
        <div class="mobile-menu-header">
            <h3>Menu</h3>
            <button class="mobile-menu-close" id="mobile-menu-close">&times;</button>
        </div>
        <div class="mobile-menu-categories">
            <div class="mobile-menu-category">
                <h4 class="mobile-menu-category-title">Kategori</h4>
                <ul class="mobile-menu-links">
                    <li><a href="#" data-category="buah"><i class="fas fa-apple-alt"></i> Buah & Sayur</a></li>
                    <li><a href="#" data-category="minuman"><i class="fas fa-wine-bottle"></i> Minuman</a></li>
                    <li><a href="#" data-category="makanan"><i class="fas fa-bread-slice"></i> Makanan</a></li>
                    <li><a href="#" data-category="protein"><i class="fas fa-egg"></i> Protein</a></li>
                    <li><a href="#" data-category="kesehatan"><i class="fas fa-pump-medical"></i> Kesehatan</a></li>
                    <li><a href="#" data-category="rumahtangga"><i class="fas fa-home"></i> Rumah Tangga</a></li>
                </ul>
            </div>
            <div class="mobile-menu-category">
                <h4 class="mobile-menu-category-title">Akun Saya</h4>
                <ul class="mobile-menu-links">
                    <li><a href="#" data-page="profile"><i class="fas fa-user"></i> Profil</a></li>
                    <li><a href="#" data-page="orders"><i class="fas fa-shopping-bag"></i> Pesanan</a></li>
                    <li><a href="#" data-page="wishlist"><i class="fas fa-heart"></i> Wishlist</a></li>
                    <li><a href="#" data-page="history"><i class="fas fa-history"></i> Riwayat</a></li>
                </ul>
            </div>
            <div class="mobile-menu-category">
                <h4 class="mobile-menu-category-title">Lainnya</h4>
                <ul class="mobile-menu-links">
                    <li><a href="#" data-page="about"><i class="fas fa-info-circle"></i> Tentang Kami</a></li>
                    <li><a href="#" data-page="help"><i class="fas fa-headset"></i> Bantuan</a></li>
                    <li><a href="#" data-page="privacy"><i class="fas fa-shield-alt"></i> Kebijakan Privasi</a></li>
                    <li><a href="#" data-page="terms"><i class="fas fa-file-contract"></i> Syarat & Ketentuan</a></li>
                </ul>
            </div>
        </div>
    </div>

    <div class="nav-categories">
        <div class="category-scroll">
            <a href="#" class="category-item" data-category="buah">
                <div class="category-icon">
                    <i class="fas fa-apple-alt"></i>
                </div>
                <span class="category-name">Buah</span>
            </a>
            <a href="#" class="category-item" data-category="sayur">
                <div class="category-icon">
                    <i class="fas fa-carrot"></i>
                </div>
                <span class="category-name">Sayur</span>
            </a>
            <a href="#" class="category-item" data-category="protein">
                <div class="category-icon">
                    <i class="fas fa-egg"></i>
                </div>
                <span class="category-name">Protein</span>
            </a>
            <a href="#" class="category-item" data-category="minuman">
                <div class="category-icon">
                    <i class="fas fa-wine-bottle"></i>
                </div>
                <span class="category-name">Minuman</span>
            </a>
            <a href="#" class="category-item" data-category="roti">
                <div class="category-icon">
                    <i class="fas fa-bread-slice"></i>
                </div>
                <span class="category-name">Roti</span>
            </a>
            <a href="#" class="category-item" data-category="beku">
                <div class="category-icon">
                    <i class="fas fa-ice-cream"></i>
                </div>
                <span class="category-name">Beku</span>
            </a>
            <a href="#" class="category-item" data-category="snack">
                <div class="category-icon">
                    <i class="fas fa-pizza-slice"></i>
                </div>
                <span class="category-name">Snack</span>
            </a>
            <a href="#" class="category-item" data-category="kesehatan">
                <div class="category-icon">
                    <i class="fas fa-pump-medical"></i>
                </div>
                <span class="category-name">Kesehatan</span>
            </a>
        </div>
    </div>

    <!-- Home Page -->
    <div id="home-page" class="page active">
        <div class="container">
            <!-- Hero Carousel -->
            <div class="hero-carousel">
                <div class="carousel-container">
                    <div class="carousel-slides" id="carousel-slides">
                        <!-- Carousel slides will be populated by JavaScript -->
                    </div>
                    <div class="carousel-controls">
                        <button class="carousel-control prev" id="carousel-prev">&#10094;</button>
                        <button class="carousel-control next" id="carousel-next">&#10095;</button>
                    </div>
                    <div class="carousel-dots" id="carousel-dots">
                        <!-- Dots will be populated by JavaScript -->
                    </div>
                </div>
            </div>

            <!-- Flash Sale Section -->
            <div class="flash-sale">
                <div class="flash-sale-header">
                    <h2 class="section-title">Flash Sale</h2>
                    <div class="flash-sale-timer">
                        <i class="fas fa-bolt"></i>
                        <div class="timer-count">
                            <span class="timer-unit" id="hours">00</span>:
                            <span class="timer-unit" id="minutes">00</span>:
                            <span class="timer-unit" id="seconds">00</span>
                        </div>
                    </div>
                </div>
                <div class="products-grid" id="flash-sale-products">
                    <!-- Flash sale products will be populated by JavaScript -->
                </div>
            </div>

            <!-- Search Results Section (Initially Hidden) -->
            <section class="search-results-section" id="search-results">
                <div class="section-header">
                    <h2 class="section-title">Hasil Pencarian</h2>
                </div>
                <div class="products-grid" id="search-results-grid">
                    <!-- Search results will be populated by JavaScript -->
                </div>
            </section>

            <section class="products-section" id="featured-section">
                <div class="section-header">
                    <h2 class="section-title">Produk Terlaris</h2>
                    <a href="#" class="view-all" id="view-all-featured">Lihat Semua <i class="fas fa-chevron-right"></i></a>
                </div>
                <div class="products-grid" id="featured-products">
                    <!-- Products will be populated by JavaScript -->
                </div>
            </section>

            <section class="products-section" id="promo-section">
                <div class="section-header">
                    <h2 class="section-title">Promo Spesial</h2>
                    <a href="#" class="view-all" id="view-all-promo">Lihat Semua <i class="fas fa-chevron-right"></i></a>
                </div>
                <div class="products-grid" id="promo-products">
                    <!-- Products will be populated by JavaScript -->
                </div>
            </section>

            <section class="products-section" id="all-products-section">
                <div class="section-header">
                    <h2 class="section-title">Semua Produk</h2>
                    <a href="#" class="view-all" id="view-all-products">Lihat Semua <i class="fas fa-chevron-right"></i></a>
                </div>
                <div class="products-grid" id="all-products">
                    <!-- All products will be populated by JavaScript -->
                </div>
            </section>
        </div>
    </div>

    <!-- Admin Login Page -->
    <div id="admin-login-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="admin-login">
                <h2 style="text-align: center; margin-bottom: 20px;">Login Administrator</h2>
                <form id="admin-login-form">
                    <div class="form-group">
                        <label for="admin-username">Username</label>
                        <input type="text" id="admin-username" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="admin-password">Password</label>
                        <input type="password" id="admin-password" class="form-control" required>
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%; margin-top: 15px;">Login</button>
                </form>
            </div>
        </div>
    </div>

    <!-- Admin Page -->
    <div id="admin-page" class="page">
        <div class="admin-sidebar">
            <ul class="admin-menu">
                <li><a href="#" class="active" data-section="products"><i class="fas fa-box"></i> Kelola Produk</a></li>
                <li><a href="#" data-section="carousel"><i class="fas fa-images"></i> Kelola Carousel</a></li>
                <li><a href="#" data-section="sales"><i class="fas fa-tag"></i> Kelola Sale</a></li>
                <li><a href="#" data-section="vouchers"><i class="fas fa-ticket-alt"></i> Kelola Voucher</a></li>
                <li><a href="#" data-section="fees"><i class="fas fa-money-bill-wave"></i> Kelola Biaya</a></li>
                <li><a href="#" id="admin-logout"><i class="fas fa-sign-out-alt"></i> Logout</a></li>
            </ul>
        </div>
        <div class="admin-content">
            <!-- Products Management -->
            <div id="admin-products" class="admin-section active">
                <div class="admin-header">
                    <h2>Kelola Produk</h2>
                    <button class="btn btn-primary" id="add-product-btn">Tambah Produk</button>
                </div>
                <table class="admin-table">
                    <thead>
                        <tr>
                            <th>Nama</th>
                            <th>Kategori</th>
                            <th>Harga</th>
                            <th>Stok</th>
                            <th>Aksi</th>
                        </tr>
                    </thead>
                    <tbody id="admin-products-list">
                        <!-- Products will be populated by JavaScript -->
                    </tbody>
                </table>
            </div>

            <!-- Carousel Management -->
            <div id="admin-carousel" class="admin-section">
                <div class="admin-header">
                    <h2>Kelola Carousel</h2>
                    <button class="btn btn-primary" id="add-carousel-btn">Tambah Slide</button>
                </div>
                <table class="admin-table">
                    <thead>
                        <tr>
                            <th>Gambar</th>
                            <th>Judul</th>
                            <th>Deskripsi</th>
                            <th>Aksi</th>
                        </tr>
                    </thead>
                    <tbody id="admin-carousel-list">
                        <!-- Carousel items will be populated by JavaScript -->
                    </tbody>
                </table>
            </div>

            <!-- Sales Management -->
            <div id="admin-sales" class="admin-section">
                <div class="admin-header">
                    <h2>Kelola Sale</h2>
                    <button class="btn btn-primary" id="add-sale-btn">Tambah Sale</button>
                </div>
                <table class="admin-table">
                    <thead>
                        <tr>
                            <th>Produk</th>
                            <th>Diskon</th>
                            <th>Periode</th>
                            <th>Status</th>
                            <th>Aksi</th>
                        </tr>
                    </thead>
                    <tbody id="admin-sales-list">
                        <!-- Sales will be populated by JavaScript -->
                    </tbody>
                </table>
            </div>

            <!-- Vouchers Management -->
            <div id="admin-vouchers" class="admin-section">
                <div class="admin-header">
                    <h2>Kelola Voucher</h2>
                    <button class="btn btn-primary" id="add-voucher-btn">Tambah Voucher</button>
                </div>
                <table class="admin-table">
                    <thead>
                        <tr>
                            <th>Kode</th>
                            <th>Jenis</th>
                            <th>Nilai</th>
                            <th>Min. Belanja</th>
                            <th>Masa Berlaku</th>
                            <th>Aksi</th>
                        </tr>
                    </thead>
                    <tbody id="admin-vouchers-list">
                        <!-- Vouchers will be populated by JavaScript -->
                    </tbody>
                </table>
            </div>

            <!-- Additional Fees Management -->
            <div id="admin-fees" class="admin-section">
                <div class="admin-header">
                    <h2>Kelola Biaya Tambahan</h2>
                    <button class="btn btn-primary" id="add-fee-btn">Tambah Biaya</button>
                </div>
                <div id="admin-fees-list">
                    <!-- Fees will be populated by JavaScript -->
                </div>
            </div>
        </div>
    </div>

    <!-- Modal untuk Form Admin -->
    <div class="modal" id="admin-modal">
        <div class="modal-content" style="max-width: 600px;">
            <div class="modal-header">
                <h3 id="admin-modal-title">Tambah Data</h3>
                <button class="modal-close" id="close-admin-modal">&times;</button>
            </div>
            <div class="modal-body" id="admin-modal-body">
                <!-- Content will be populated by JavaScript -->
            </div>
        </div>
    </div>

    <!-- Promo Page -->
    <div id="promo-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Promo Spesial</h2>
            </div>
            <div class="products-grid" id="promo-page-products">
                <!-- Promo products will be populated by JavaScript -->
            </div>
        </div>
    </div>

    <!-- Cart Page -->
    <div id="cart-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Keranjang Belanja</h2>
            </div>
            <div id="cart-page-content">
                <!-- Cart content will be populated by JavaScript -->
            </div>
        </div>
    </div>

    <!-- Orders Page -->
    <div id="orders-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Pesanan Saya</h2>
            </div>
            <div id="orders-list">
                <!-- Orders will be populated by JavaScript -->
            </div>
        </div>
    </div>

    <!-- Profile Page -->
    <div id="profile-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Profil Saya</h2>
            </div>
            <div class="profile-card">
                <form id="profile-form" class="profile-form">
                    <div class="form-group">
                        <label for="profile-name">Nama Lengkap</label>
                        <input type="text" id="profile-name" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="profile-email">Email</label>
                        <input type="email" id="profile-email" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="profile-phone">Nomor Telepon</label>
                        <input type="tel" id="profile-phone" class="form-control" required>
                    </div>
                    <div class="form-group full-width">
                        <label for="profile-address">Alamat</label>
                        <textarea id="profile-address" class="form-control" rows="3" required></textarea>
                    </div>
                    <div class="form-group full-width">
                        <button type="submit" class="btn btn-primary">Simpan Profil</button>
                    </div>
                </form>
            </div>
        </div>
    </div>

    <!-- Wishlist Page -->
    <div id="wishlist-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Wishlist Saya</h2>
            </div>
            <div class="wishlist-grid" id="wishlist-products">
                <!-- Wishlist products will be populated by JavaScript -->
            </div>
        </div>
    </div>

    <!-- History Page with Receipts -->
    <div id="history-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Riwayat Transaksi</h2>
            </div>
            <div id="history-receipts">
                <!-- Receipts will be populated by JavaScript -->
            </div>
        </div>
    </div>

    <!-- About Page -->
    <div id="about-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Tentang Kami</h2>
            </div>
            <div class="profile-card">
                <p>Fresh.in adalah platform belanja online kebutuhan sehari-hari dengan harga terbaik. Kami menyediakan berbagai produk segar dan kebutuhan rumah tangga dengan kualitas terjamin.</p>
                <p>Visi kami adalah menjadi solusi terdepan untuk kebutuhan sehari-hari masyarakat Indonesia dengan pengiriman cepat dan layanan terbaik.</p>
            </div>
        </div>
    </div>

    <!-- Help Page -->
    <div id="help-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Bantuan</h2>
            </div>
            <div class="profile-card">
                <h3>Pertanyaan Umum</h3>
                
                <div class="faq-item">
                    <div class="faq-question">Bagaimana cara melakukan pembelian?</div>
                    <div class="faq-answer">Pilih produk yang ingin dibeli, tambahkan ke keranjang, lalu lakukan checkout dan ikuti proses pembayaran.</div>
                </div>
                
                <div class="faq-item">
                    <div class="faq-question">Metode pembayaran apa saja yang diterima?</div>
                    <div class="faq-answer">Kami menerima pembayaran melalui QRIS dan Cash on Delivery (COD).</div>
                </div>
                
                <div class="faq-item">
                    <div class="faq-question">Berapa lama waktu pengiriman?</div>
                    <div class="faq-answer">Pengiriman biasanya memakan waktu 1-2 hari kerja tergantung pada lokasi Anda.</div>
                </div>
                
                <div class="faq-item">
                    <div class="faq-question">Bagaimana jika produk yang diterima rusak?</div>
                    <div class="faq-answer">Anda dapat mengajukan komplain dalam waktu 24 jam setelah penerimaan produk dengan menyertakan foto produk yang rusak.</div>
                </div>
                
                <div class="contact-form">
                    <h3>Hubungi Kami</h3>
                    <div
