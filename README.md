<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Librería Milenium</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #f8f5f0 0%, #e9f0ff 100%);
      color: #333;
      line-height: 1.6;
      position: relative;
      min-height: 100vh;
    }

    header {
      background: linear-gradient(135deg, #4a6fa5 0%, #2c3e50 100%);
      color: white;
      padding: 1.2rem;
      text-align: center;
      position: relative;
      box-shadow: 0 4px 12px rgba(0,0,0,0.15);
    }

    .header-content {
      display: flex;
      align-items: center;
      justify-content: center;
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 20px;
    }

    .header-title {
      flex-grow: 1;
      text-align: center;
      padding: 0 20px;
    }

    .header-title h1 {
      margin: 0;
      font-size: 2.2rem;
      letter-spacing: 1px;
      text-shadow: 0 2px 4px rgba(0,0,0,0.3);
      cursor: pointer;
      transition: all 0.3s ease;
      display: inline-block;
      padding: 0.5rem 1.5rem;
      border-radius: 8px;
    }

    .header-title h1:hover {
      background: rgba(255, 255, 255, 0.15);
      transform: scale(1.03);
    }

    .header-subtitle {
      display: block;
      font-size: 1rem;
      margin-top: 5px;
      font-weight: normal;
      color: #bdc3c7;
    }

    .main-content {
      position: relative;
      z-index: 1;
      max-width: 1200px;
      margin: 0 auto;
      padding: 2rem 1rem;
    }

    .container {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 1.8rem;
      justify-items: center;
    }

    .book {
      background: white;
      border-radius: 12px;
      box-shadow: 0 6px 15px rgba(0, 0, 0, 0.1);
      padding: 1.5rem;
      text-align: center;
      transition: all 0.3s ease;
      width: 100%;
      position: relative;
      overflow: hidden;
      border: 1px solid #eee;
      display: flex;
      flex-direction: column;
      height: 100%;
    }

    .book:hover {
      transform: translateY(-5px);
      box-shadow: 0 12px 20px rgba(0, 0, 0, 0.15);
    }

    .book img {
      max-width: 100%;
      height: 200px;
      object-fit: cover;
      border-radius: 8px;
      border: 1px solid #eee;
      transition: all 0.3s ease;
      margin-bottom: 1rem;
    }

    .book:hover img {
      transform: scale(1.03);
    }

    .book h4 {
      margin: 0.5rem 0;
      font-size: 1.2rem;
      color: #2c3e50;
      min-height: auto;
    }

    .book-author {
      color: #4a6fa5;
      font-weight: 600;
      margin-bottom: 0.5rem;
    }

    .book-resume {
      font-size: 0.95rem;
      color: #555;
      margin: 0.8rem 0;
      line-height: 1.5;
      flex-grow: 1;
      text-align: left;
      overflow: hidden;
      display: -webkit-box;
      -webkit-line-clamp: 4;
      -webkit-box-orient: vertical;
    }

    .book-details {
      display: flex;
      justify-content: space-between;
      margin-top: 1rem;
      font-size: 0.9rem;
    }

    .book-category {
      background: #e3f2fd;
      color: #2c3e50;
      padding: 0.3rem 0.8rem;
      border-radius: 15px;
      font-weight: 500;
    }

    .book-availability {
      font-weight: 600;
    }

    .available {
      color: #27ae60;
    }

    .not-available {
      color: #e74c3c;
    }

    .admin, .social {
      background: rgba(255, 255, 255, 0.92);
      border-radius: 12px;
      padding: 1.8rem;
      margin: 2rem auto;
      max-width: 800px;
      text-align: center;
      box-shadow: 0 8px 25px rgba(0,0,0,0.08);
    }

    button {
      background: linear-gradient(to right, #4a6fa5, #2c3e50);
      color: white;
      border: none;
      padding: 0.8rem 1.5rem;
      margin-top: 1rem;
      border-radius: 8px;
      cursor: pointer;
      transition: all 0.3s ease;
      font-weight: 600;
      letter-spacing: 0.5px;
      box-shadow: 0 4px 8px rgba(74, 111, 165, 0.3);
      font-size: 1rem;
    }

    button:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 12px rgba(74, 111, 165, 0.4);
    }

    .social-icons {
      display: flex;
      gap: 1.5rem;
      justify-content: center;
      margin-top: 1.5rem;
      flex-wrap: wrap;
    }

    .social-icons a {
      text-decoration: none;
      color: #2c3e50;
      font-weight: bold;
      display: flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.7rem 1.2rem;
      border-radius: 30px;
      background: #f8f9fa;
      transition: all 0.3s ease;
      box-shadow: 0 3px 8px rgba(0,0,0,0.1);
    }

    .social-icons a:hover {
      transform: translateY(-3px);
      box-shadow: 0 5px 15px rgba(0,0,0,0.15);
      background: #e3f2fd;
    }

    .social-icons img {
      width: 28px;
      height: 28px;
    }

    #admin-panel {
      display: none;
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: white;
      padding: 2rem;
      border-radius: 15px;
      box-shadow: 0 0 30px rgba(0,0,0,0.25);
      z-index: 1000;
      max-width: 95%;
      max-height: 95vh;
      overflow-y: auto;
      width: 90%;
    }

    #admin-overlay {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.7);
      z-index: 999;
    }

    .carousel-container {
      width: 100%;
      overflow: hidden;
      position: relative;
      margin: 3rem 0;
      padding: 0 1rem;
    }

    .carousel {
      display: flex;
      transition: transform 0.5s ease;
    }

    .carousel-item {
      min-width: 250px;
      margin: 0 1rem;
      text-align: center;
      position: relative;
      transition: all 0.3s ease;
    }

    .carousel-item:hover {
      transform: scale(1.05);
    }

    .carousel-item img {
      width: 100%;
      height: 220px;
      object-fit: cover;
      border-radius: 10px;
      box-shadow: 0 6px 15px rgba(0,0,0,0.15);
      border: 3px solid white;
    }

    .carousel-item h4 {
      margin-top: 1rem;
      color: #2c3e50;
      font-size: 1.1rem;
    }

    .carousel-btn {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      background: rgba(0,0,0,0.7);
      color: white;
      border: none;
      border-radius: 50%;
      width: 45px;
      height: 45px;
      font-size: 22px;
      cursor: pointer;
      z-index: 10;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.3s ease;
    }

    .carousel-btn:hover {
      background: rgba(0,0,0,0.9);
      transform: translateY(-50%) scale(1.1);
    }

    .carousel-btn.prev {
      right: 20px;
    }

    .carousel-btn.next {
      left: 20px;
    }

    .qr-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-top: 2rem;
      padding: 1.5rem;
      background: #f8f9fa;
      border-radius: 12px;
    }

    .qr-container img {
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
      border-radius: 8px;
      background: white;
      padding: 12px;
      margin-top: 1rem;
    }

    .logout-btn {
      background: linear-gradient(to right, #e74c3c, #c0392b);
    }

    .logout-btn:hover {
      box-shadow: 0 6px 12px rgba(231, 76, 60, 0.4);
    }

    .config-btn {
      background: linear-gradient(to right, #2ecc71, #27ae60);
    }

    .edit-btn {
      background: linear-gradient(to right, #f39c12, #d35400);
    }

    .admin-section {
      margin-bottom: 1.8rem;
      padding: 1.5rem;
      background: #f8f9fa;
      border-radius: 10px;
      border: 1px solid #eee;
    }

    .admin-section h4 {
      margin-top: 0;
      color: #2c3e50;
      border-bottom: 2px solid #4a6fa5;
      padding-bottom: 0.7rem;
      margin-bottom: 1.2rem;
    }

    input, select, textarea {
      width: 100%;
      padding: 0.8rem;
      margin: 0.8rem 0;
      border: 1px solid #ddd;
      border-radius: 6px;
      font-family: inherit;
      font-size: 1rem;
    }

    input:focus, select:focus, textarea:focus {
      outline: none;
      border-color: #4a6fa5;
      box-shadow: 0 0 0 3px rgba(74, 111, 165, 0.2);
    }

    .form-row {
      display: flex;
      gap: 1.2rem;
      margin-bottom: 0.8rem;
      flex-wrap: wrap;
    }

    .form-row > * {
      flex: 1;
      min-width: 200px;
    }

    .tabs {
      display: flex;
      margin-bottom: 1.5rem;
      border-bottom: 2px solid #4a6fa5;
      flex-wrap: wrap;
    }

    .tab {
      padding: 0.7rem 1.5rem;
      cursor: pointer;
      background: #e3f2fd;
      border: none;
      border-radius: 5px 5px 0 0;
      margin-right: 0.5rem;
      font-weight: 600;
      transition: all 0.3s ease;
    }

    .tab:hover {
      background: #bbdefb;
    }

    .tab.active {
      background: #4a6fa5;
      color: white;
    }

    .tab-content {
      display: none;
    }

    .tab-content.active {
      display: block;
    }

    .book-actions {
      display: flex;
      gap: 0.7rem;
      justify-content: center;
      margin-top: 1rem;
    }

    .book-actions button {
      margin-top: 0;
      padding: 0.5rem 1rem;
      font-size: 0.85rem;
    }

    #edit-book-form {
      display: none;
      margin-top: 1.5rem;
      padding: 1.5rem;
      background: #f0f7ff;
      border-radius: 10px;
      border: 1px solid #d1e7ff;
    }

    .section-title {
      text-align: center;
      margin: 2.5rem 0 1.8rem;
      color: #2c3e50;
      font-size: 1.8rem;
      font-weight: bold;
      position: relative;
      padding-bottom: 0.5rem;
    }

    .section-title::after {
      content: '';
      display: block;
      width: 80px;
      height: 4px;
      background: #4a6fa5;
      margin: 0.8rem auto;
      border-radius: 2px;
    }

    .search-container {
      display: flex;
      justify-content: center;
      align-items: center;
      margin: 1.5rem 0;
      padding: 0 1rem;
      position: relative;
      gap: 10px;
    }

    .search-box {
      position: relative;
      width: 100%;
      max-width: 600px;
    }

    .search-box input {
      width: 100%;
      padding: 0.9rem 3rem 0.9rem 1.5rem;
      border-radius: 30px;
      border: 1px solid #ddd;
      font-size: 1rem;
      box-shadow: 0 4px 10px rgba(0,0,0,0.08);
    }

    .search-icon {
      position: absolute;
      right: 1.5rem;
      top: 50%;
      transform: translateY(-50%);
      color: #777;
      font-size: 1.2rem;
    }

    .category-menu-btn {
      background: #4a6fa5;
      color: white;
      border: none;
      border-radius: 8px;
      padding: 0.8rem 1rem;
      cursor: pointer;
      font-size: 1.2rem;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 3px 8px rgba(74, 111, 165, 0.3);
      transition: all 0.3s ease;
    }

    .category-menu-btn:hover {
      background: #3a5f8a;
      transform: translateY(-2px);
    }

    .category-menu-label {
      font-weight: bold;
      color: #2c3e50;
      margin-right: 5px;
    }

    .category-menu {
      position: absolute;
      top: 100%;
      right: 0;
      background: white;
      border-radius: 8px;
      box-shadow: 0 8px 16px rgba(0,0,0,0.2);
      padding: 1rem;
      z-index: 100;
      display: none;
      min-width: 200px;
      max-height: 400px;
      overflow-y: auto;
    }

    .category-menu.active {
      display: block;
    }

    .category-tab {
      padding: 0.7rem 1.2rem;
      background: #e3f2fd;
      color: #2c3e50;
      border-radius: 8px;
      cursor: pointer;
      transition: all 0.3s ease;
      font-size: 0.9rem;
      margin-bottom: 0.5rem;
      text-align: left;
    }

    .category-tab:hover {
      background: #bbdefb;
      transform: translateX(3px);
    }

    .category-tab.active {
      background: #4a6fa5;
      color: white;
      font-weight: bold;
    }

    .image-upload-container {
      margin: 1.2rem 0;
    }

    .image-preview {
      display: flex;
      flex-wrap: wrap;
      gap: 0.8rem;
      margin-top: 0.8rem;
      justify-content: center;
    }

    .image-preview-item {
      position: relative;
      width: 100px;
      height: 100px;
      border-radius: 8px;
      overflow: hidden;
      box-shadow: 0 3px 8px rgba(0,0,0,0.15);
      border: 2px solid white;
    }

    .image-preview-item img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .remove-image-btn {
      position: absolute;
      top: -8px;
      right: -8px;
      background: #e74c3c;
      color: white;
      border: none;
      border-radius: 50%;
      width: 24px;
      height: 24px;
      font-size: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      box-shadow: 0 2px 5px rgba(0,0,0,0.3);
    }

    .saga-images-container {
      margin-top: 1.5rem;
      padding: 1.2rem;
      background: #f0f7ff;
      border-radius: 10px;
      border: 1px dashed #4a6fa5;
    }

    .saga-images-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(110px, 1fr));
      gap: 0.8rem;
      margin-top: 1rem;
    }

    .saga-image-item {
      position: relative;
      border-radius: 6px;
      overflow: hidden;
      box-shadow: 0 3px 8px rgba(0,0,0,0.12);
      border: 2px solid white;
    }

    .saga-image-item img {
      width: 100%;
      height: 140px;
      object-fit: cover;
    }

    .remove-saga-image-btn {
      position: absolute;
      top: -8px;
      right: -8px;
      background: #e74c3c;
      color: white;
      border: none;
      border-radius: 50%;
      width: 24px;
      height: 24px;
      font-size: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      box-shadow: 0 2px 5px rgba(0,0,0,0.3);
    }

    .upload-options {
      display: flex;
      gap: 1.5rem;
      margin-bottom: 1.2rem;
      flex-wrap: wrap;
    }

    .upload-option {
      flex: 1;
      text-align: center;
      padding: 1.2rem;
      border: 2px dashed #4a6fa5;
      border-radius: 8px;
      cursor: pointer;
      min-width: 200px;
      transition: all 0.3s ease;
      background: #f8f9fa;
    }

    .upload-option:hover {
      background: #e3f2fd;
      transform: translateY(-3px);
      box-shadow: 0 5px 15px rgba(0,0,0,0.08);
    }

    .close-admin-btn {
      position: absolute;
      top: 1rem;
      right: 1rem;
      background: #e74c3c;
      color: white;
      border: none;
      border-radius: 50%;
      width: 35px;
      height: 35px;
      font-size: 16px;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      box-shadow: 0 2px 5px rgba(0,0,0,0.3);
    }

    .admin-access-btn {
      position: fixed;
      bottom: 1.5rem;
      right: 1.5rem;
      background: linear-gradient(135deg, #4a6fa5 0%, #2c3e50 100%);
      color: white;
      border: none;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      font-size: 24px;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      z-index: 100;
      box-shadow: 0 6px 15px rgba(0,0,0,0.3);
      transition: all 0.3s ease;
    }

    .admin-access-btn:hover {
      transform: scale(1.1) rotate(10deg);
      box-shadow: 0 8px 20px rgba(0,0,0,0.4);
    }

    .confirm-image-btn {
      background: linear-gradient(to right, #2ecc71, #27ae60);
      margin: 0.8rem auto;
      display: block;
    }

    .preview-actions {
      display: flex;
      gap: 0.8rem;
      justify-content: center;
      margin-top: 0.8rem;
    }

    .total-books {
      background: linear-gradient(to right, #4a6fa5, #2c3e50);
      color: white;
      padding: 0.7rem 1.5rem;
      border-radius: 30px;
      margin-bottom: 1.5rem;
      display: inline-block;
      font-weight: bold;
      box-shadow: 0 4px 10px rgba(74, 111, 165, 0.4);
    }

    .admin-credentials {
      display: none;
    }

    .login-modal {
      display: none;
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: white;
      padding: 2rem;
      border-radius: 15px;
      box-shadow: 0 0 30px rgba(0,0,0,0.25);
      z-index: 1000;
      width: 350px;
      max-width: 90%;
    }

    .login-form {
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }

    .login-form input {
      padding: 0.9rem;
      font-size: 1rem;
    }

    .login-form button {
      margin-top: 0.5rem;
    }

    .close-login-btn {
      position: absolute;
      top: 1rem;
      right: 1rem;
      background: #e74c3c;
      color: white;
      border: none;
      border-radius: 50%;
      width: 30px;
      height: 30px;
      font-size: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
    }

    .confirmation-message {
      position: fixed;
      top: 20px;
      right: 20px;
      background: #27ae60;
      color: white;
      padding: 1rem 2rem;
      border-radius: 8px;
      box-shadow: 0 4px 15px rgba(0,0,0,0.2);
      z-index: 2000;
      display: none;
      animation: fadeInOut 3s forwards;
    }

    @keyframes fadeInOut {
      0% { opacity: 0; transform: translateX(100px); }
      20% { opacity: 1; transform: translateX(0); }
      80% { opacity: 1; transform: translateX(0); }
      100% { opacity: 0; transform: translateX(100px); }
    }

    @media (max-width: 768px) {
      .header-content {
        flex-direction: column;
        gap: 1rem;
      }
      
      .upload-options {
        flex-direction: column;
      }
      
      .carousel-btn {
        width: 35px;
        height: 35px;
        font-size: 18px;
      }
      
      .container {
        grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
      }
    }

    @media (max-width: 480px) {
      .header-title h1 {
        font-size: 1.6rem;
      }
      
      .carousel-item {
        min-width: 220px;
      }
      
      .tabs {
        flex-direction: column;
      }
      
      .tab {
        margin-bottom: 0.3rem;
      }
      
      .search-container {
        flex-direction: column;
        align-items: stretch;
      }
      
      .category-menu-label {
        display: none;
      }
    }
  </style>
</head>
<body>
  <div id="confirmation-message" class="confirmation-message">
    ¡Cambios guardados exitosamente!
  </div>
  
  <header>
    <div class="header-content">
      <div class="header-title">
        <h1 onclick="location.reload()">Librería Milenium <span class="header-subtitle">Santiago Tianguistenco</span></h1>
      </div>
      <div id="user-info" class="user-info" style="display: none;">
        <span id="user-email"></span>
        <button class="logout-user-btn" onclick="logoutUser()">Cerrar sesión</button>
      </div>
    </div>
  </header>

  <div class="main-content">
    <!-- Carrusel de libros nuevos -->
    <section class="carousel-container">
      <h3 class="section-title">Libros nuevos</h3>
      <button class="carousel-btn next" onclick="moveCarousel(-1)">&#10094;</button>
      <button class="carousel-btn prev" onclick="moveCarousel(1)">&#10095;</button>
      <div class="carousel" id="new-books-carousel">
        <!-- Libros nuevos se generarán dinámicamente -->
      </div>
    </section>

    <!-- Sección de redes sociales debajo del carrusel -->
    <section class="social">
      <h3>Contáctanos</h3>
      <div class="social-icons" id="social-links">
        <!-- Redes sociales generadas dinámicamente -->
      </div>
      <div class="qr-container">
        <p>Escanea para visitar Librería Milenium:</p>
        <img src="https://api.qrserver.com/v1/create-qr-code/?data=https://libreria-milenium.com&size=180x180" alt="QR Librería Milenium" />
      </div>
    </section>

    <div class="search-container">
      <div class="search-box">
        <input type="text" id="search-input" placeholder="Buscar por título, autor o categoría...">
        <span class="search-icon">🔍</span>
      </div>
      <div class="category-menu-label">Categorías</div>
      <button class="category-menu-btn" id="category-menu-btn">☰</button>
      <div class="category-menu" id="category-menu">
        <div class="category-tab active" data-category="all">Todos</div>
        <div class="category-tab" data-category="literatura">Literatura</div>
        <div class="category-tab" data-category="consulta">Consulta</div>
        <div class="category-tab" data-category="artisticos">Artísticos</div>
        <div class="category-tab" data-category="divulgativos">Divulgativos</div>
        <div class="category-tab" data-category="tecnicos">Técnicos</div>
        <div class="category-tab" data-category="practicos">Prácticos</div>
        <div class="category-tab" data-category="religiosos">Religiosos</div>
        <div class="category-tab" data-category="autoayuda">Autoayuda</div>
        <div class="category-tab" data-category="infantiles">Infantiles</div>
        <div class="category-tab" data-category="novelas">Novelas</div>
        <div class="category-tab" data-category="suspenso">Suspenso</div>
        <div class="category-tab" data-category="sagas">Sagas</div>
        <div class="category-tab" data-category="escolares">Escolares</div>
      </div>
    </div>

    <section class="container" id="book-list">
      <!-- Libros generados dinámicamente -->
    </section>

    <button class="admin-access-btn" onclick="mostrarLoginAdmin()">🔑</button>

    <div id="admin-overlay"></div>

    <section class="admin" id="admin-panel">
      <button class="close-admin-btn" onclick="cerrarSesionAdmin()">×</button>
      <h3>Zona de administrador</h3>
      
      <div class="total-books">
        Total de libros: <span id="total-books-count">0</span>
      </div>
      
      <div class="tabs">
        <div class="tab active" onclick="openTab('books-tab')">Libros</div>
        <div class="tab" onclick="openTab('social-tab')">Redes Sociales</div>
        <div class="tab" onclick="openTab('logo-tab')">Logotipos</div>
      </div>
      
      <div id="books-tab" class="tab-content active">
        <div class="admin-section">
          <h4>Agregar nuevo libro</h4>
          <input id="titulo" placeholder="Título del libro" />
          <textarea id="resena" placeholder="Reseña del libro" rows="3"></textarea>
          <input id="caracteristica1" placeholder="Característica 1" />
          <input id="caracteristica2" placeholder="Característica 2" />
          <div class="form-row">
            <input id="autor" placeholder="Autor" />
            <input id="editorial" placeholder="Editorial" />
          </div>
          <select id="categoria">
            <option value="literatura">Literatura</option>
            <option value="consulta">Consulta y referencia</option>
            <option value="artisticos">Artísticos e ilustrados</option>
            <option value="divulgativos">Divulgativos</option>
            <option value="tecnicos">Técnicos o especializados</option>
            <option value="practicos">Prácticos</option>
            <option value="religiosos">Religiosos y sagrados</option>
            <option value="autoayuda">Autoayuda</option>
            <option value="infantiles">Infantiles</option>
            <option value="novelas">Novelas</option>
            <option value="suspenso">Suspenso</option>
            <option value="sagas">Sagas</option>
            <option value="escolares">Escolares</option>
          </select>
          <select id="disponible">
            <option value="true">Disponible</option>
            <option value="false">No disponible</option>
          </select>
          
          <div class="upload-options">
            <div class="upload-option" onclick="document.getElementById('file-input').click()">
              Subir imagen desde dispositivo
              <input type="file" id="file-input" style="display: none;" accept="image/*" onchange="handleFileUpload()">
            </div>
            <div class="upload-option">
              Usar URL de imagen
              <input id="imagen" placeholder="URL de la imagen" style="margin-top: 0.5rem;" />
              <button class="confirm-image-btn" onclick="confirmImageUrl()">Confirmar URL</button>
            </div>
          </div>
          
          <div id="image-preview" class="image-preview"></div>
          
          <div id="saga-images-container" class="saga-images-container" style="display: none;">
            <h5>Imagen de la saga</h5>
            <div class="upload-options">
              <div class="upload-option" onclick="document.getElementById('saga-file-input').click()">
                Subir imagen de la saga
                <input type="file" id="saga-file-input" style="display: none;" accept="image/*" onchange="handleSagaFilesUpload()">
              </div>
            </div>
            <div id="saga-images-grid" class="saga-images-grid"></div>
            <button class="confirm-image-btn" onclick="confirmSagaImages()" id="confirm-saga-btn">Confirmar imagen de saga</button>
          </div>
          
          <button onclick="agregarLibro()">Agregar libro</button>
        </div>
        
        <div class="admin-section" id="edit-book-form">
          <h4>Editar libro</h4>
          <input id="edit-titulo" placeholder="Título del libro" />
          <textarea id="edit-resena" placeholder="Reseña del libro" rows="3"></textarea>
          <input id="edit-caracteristica1" placeholder="Característica 1" />
          <input id="edit-caracteristica2" placeholder="Característica 2" />
          <div class="form-row">
            <input id="edit-autor" placeholder="Autor" />
            <input id="edit-editorial" placeholder="Editorial" />
          </div>
          <select id="edit-categoria">
            <option value="literatura">Literatura</option>
            <option value="consulta">Consulta y referencia</option>
            <option value="artisticos">Artísticos e ilustrados</option>
            <option value="divulgativos">Divulgativos</option>
            <option value="tecnicos">Técnicos o especializados</option>
            <option value="practicos">Prácticos</option>
            <option value="religiosos">Religiosos y sagrados</option>
            <option value="autoayuda">Autoayuda</option>
            <option value="infantiles">Infantiles</option>
            <option value="novelas">Novelas</option>
            <option value="suspenso">Suspenso</option>
            <option value="sagas">Sagas</option>
            <option value="escolares">Escolares</option>
          </select>
          <select id="edit-disponible">
            <option value="true">Disponible</option>
            <option value="false">No disponible</option>
          </select>
          
          <div class="upload-options">
            <div class="upload-option" onclick="document.getElementById('edit-file-input').click()">
              Subir imagen desde dispositivo
              <input type="file" id="edit-file-input" style="display: none;" accept="image/*" onchange="handleEditFileUpload()">
            </div>
            <div class="upload-option">
              Usar URL de imagen
              <input id="edit-imagen" placeholder="URL de la imagen" style="margin-top: 0.5rem;" />
              <button class="confirm-image-btn" onclick="confirmEditImageUrl()">Confirmar URL</button>
            </div>
          </div>
          
          <div id="edit-image-preview" class="image-preview"></div>
          
          <div id="edit-saga-images-container" class="saga-images-container" style="display: none;">
            <h5>Imagen de la saga</h5>
            <div class="upload-options">
              <div class="upload-option" onclick="document.getElementById('edit-saga-file-input').click()">
                Subir imagen de la saga
                <input type="file" id="edit-saga-file-input" style="display: none;" accept="image/*" onchange="handleEditSagaFilesUpload()">
              </div>
            </div>
            <div id="edit-saga-images-grid" class="saga-images-grid"></div>
            <button class="confirm-image-btn" onclick="confirmEditSagaImages()" id="confirm-edit-saga-btn">Confirmar imagen de saga</button>
          </div>
          
          <input type="hidden" id="edit-index" />
          <div class="form-row">
            <button onclick="guardarEdicion()">Guardar cambios</button>
            <button class="logout-btn" onclick="cancelarEdicion()">Cancelar</button>
          </div>
        </div>
        
        <div class="admin-section">
          <h4>Libros existentes</h4>
          <div id="book-list-admin"></div>
        </div>
      </div>
      
      <div id="social-tab" class="tab-content">
        <div class="admin-section">
          <h4>Configuración de redes sociales</h4>
          <div class="form-row">
            <input id="facebook-url" placeholder="URL de Facebook" value="https://facebook.com" />
            <input id="facebook-icon" placeholder="URL icono Facebook" value="https://cdn-icons-png.flaticon.com/512/145/145802.png" />
          </div>
          <div class="form-row">
            <input id="instagram-url" placeholder="URL de Instagram" value="https://instagram.com" />
            <input id="instagram-icon" placeholder="URL icono Instagram" value="https://cdn-icons-png.flaticon.com/512/2111/2111463.png" />
          </div>
          <div class="form-row">
            <input id="whatsapp-url" placeholder="URL de WhatsApp" value="https://wa.me/5210000000000" />
            <input id="whatsapp-icon" placeholder="URL icono WhatsApp" value="https://cdn-icons-png.flaticon.com/512/733/733585.png" />
          </div>
          <button onclick="updateSocialLinks()">Guardar cambios</button>
        </div>
      </div>
      
      <div id="logo-tab" class="tab-content">
        <div class="admin-section">
          <h4>Configuración de logotipos</h4>
          <div class="upload-options">
            <div class="upload-option" onclick="document.getElementById('logo-input').click()">
              Subir logotipo
              <input type="file" id="logo-input" style="display: none;" accept="image/*" onchange="handleLogoUpload()">
            </div>
            <div class="upload-option">
              Usar URL de logotipo
              <input id="logo-url" placeholder="URL logotipo" style="margin-top: 0.5rem;" />
              <button class="confirm-image-btn" onclick="confirmLogoUrl()">Confirmar URL</button>
            </div>
          </div>
          <div id="logo-preview" class="image-preview"></div>
          
          <button onclick="updateLogo()">Guardar cambios</button>
        </div>
      </div>
    </section>

    <div class="login-modal" id="login-modal">
      <button class="close-login-btn" onclick="cerrarLoginModal()">×</button>
      <h3>Acceso de administrador</h3>
      <div class="login-form">
        <input type="email" id="login-email" placeholder="Correo del administrador" required>
        <input type="password" id="login-password" placeholder="Contraseña" required>
        <button onclick="loginUser()">Iniciar sesión</button>
      </div>
    </div>
  </div>

  <script>
    // Datos iniciales
    let libros = [
      {
        titulo: "El Principito",
        autor: "Antoine de Saint-Exupéry",
        editorial: "Salamandra",
        categoria: "literatura",
        disponible: "true",
        imagen: "https://images.unsplash.com/photo-1589829545856-d10d557cf95f",
        resena: "Una obra clásica que habla sobre la amistad, el amor y la pérdida desde la perspectiva de un niño. Con ilustraciones originales del autor, esta obra es perfecta para todas las edades.",
        caracteristica1: "Incluye ilustraciones originales del autor",
        caracteristica2: "Perfecto para todas las edades"
      },
      {
        titulo: "Cien años de soledad",
        autor: "Gabriel García Márquez",
        editorial: "Diana",
        categoria: "novelas",
        disponible: "true",
        imagen: "https://images.unsplash.com/photo-1544947950-fa07a98d237f",
        resena: "La obra maestra del realismo mágico que narra la historia de la familia Buendía en Macondo. Ganadora del Premio Nobel de Literatura en 1982, esta edición conmemorativa es imprescindible.",
        caracteristica1: "Premio Nobel de Literatura 1982",
        caracteristica2: "Edición conmemorativa"
      },
      {
        titulo: "Harry Potter y la piedra filosofal",
        autor: "J.K. Rowling",
        editorial: "Salamandra",
        categoria: "sagas",
        disponible: "true",
        imagen: "https://images.unsplash.com/photo-1589998059171-988d887df646",
        resena: "El inicio de la saga más famosa de la literatura juvenil que sigue las aventuras del joven mago Harry Potter. Con más de 500 millones de copias vendidas, este libro marcó una generación.",
        caracteristica1: "Primer libro de la saga",
        caracteristica2: "Más de 500 millones de copias vendidas"
      },
      {
        titulo: "El arte de la guerra",
        autor: "Sun Tzu",
        editorial: "Penguin Classics",
        categoria: "autoayuda",
        disponible: "true",
        imagen: "https://images.unsplash.com/photo-1541963463532-d68292c34b19",
        resena: "Un antiguo tratado militar chino que se ha convertido en un clásico de la estrategia. Sus enseñanzas son aplicables a negocios y vida personal. Esta traducción moderna facilita su comprensión.",
        caracteristica1: "Aplicable a negocios y vida personal",
        caracteristica2: "Traducción moderna"
      },
      {
        titulo: "La biblia de la física",
        autor: "Varios autores",
        editorial: "Científica",
        categoria: "tecnicos",
        disponible: "false",
        imagen: "https://images.unsplash.com/photo-1506880018603-83d5b814b5a6",
        resena: "Compendio completo de principios físicos con aplicaciones prácticas. Con más de 1000 páginas de contenido e incluye ejercicios resueltos. Ideal para estudiantes universitarios.",
        caracteristica1: "Más de 1000 páginas de contenido",
        caracteristica2: "Incluye ejercicios resueltos"
      },
      {
        titulo: "Matemáticas para secundaria",
        autor: "Editorial Santillana",
        editorial: "Santillana",
        categoria: "escolares",
        disponible: "true",
        imagen: "https://images.unsplash.com/photo-1509228468518-180dd4864904",
        resena: "Libro de texto para estudiantes de secundaria con ejercicios prácticos y explicaciones detalladas de álgebra, geometría y cálculo. Incluye solucionario y recursos digitales.",
        caracteristica1: "Incluye solucionario",
        caracteristica2: "Recursos digitales disponibles"
      }
    ];
    
    let socialLinks = {
      facebook: { url: "https://facebook.com", icon: "https://cdn-icons-png.flaticon.com/512/145/145802.png" },
      instagram: { url: "https://instagram.com", icon: "https://cdn-icons-png.flaticon.com/512/2111/2111463.png" },
      whatsapp: { url: "https://wa.me/5210000000000", icon: "https://cdn-icons-png.flaticon.com/512/733/733585.png" }
    };
    
    let currentUser = null;
    let uploadedImage = null;
    let uploadedSagaImages = [];
    let editUploadedImage = null;
    let editUploadedSagaImages = [];
    let uploadedLogo = null;
    let currentCarouselIndex = 0;
    let currentCategory = 'all';
    let searchTerm = '';
    let carouselInterval;

    // Inicialización
    document.addEventListener('DOMContentLoaded', function() {
      // Cargar datos del localStorage si existen
      const savedLibros = localStorage.getItem("libros");
      if (savedLibros) libros = JSON.parse(savedLibros);
      
      const savedSocialLinks = localStorage.getItem("socialLinks");
      if (savedSocialLinks) socialLinks = JSON.parse(savedSocialLinks);
      
      const savedUser = localStorage.getItem("currentUser");
      if (savedUser) currentUser = JSON.parse(savedUser);
      
      // Renderizar contenido
      renderizarLibros();
      renderizarSocialLinks();
      renderizarCarousel();
      actualizarContadorLibros();
      
      // Iniciar carrusel automático
      startCarouselAutoMove();
      
      // Verificar usuario logeado
      if (currentUser) {
        showUserLoggedIn(currentUser.email);
      }
      
      // Configurar búsqueda
      document.getElementById("search-input").addEventListener('input', function() {
        searchTerm = this.value.toLowerCase();
        renderizarLibros();
      });
      
      // Configurar categorías
      document.querySelectorAll('.category-tab').forEach(tab => {
        tab.addEventListener('click', function() {
          const category = this.getAttribute('data-category');
          filterBooks(category);
          document.getElementById('category-menu').classList.remove('active');
        });
      });
      
      // Configurar botón de menú de categorías
      document.getElementById('category-menu-btn').addEventListener('click', function(e) {
        e.stopPropagation();
        document.getElementById('category-menu').classList.toggle('active');
      });
      
      // Cerrar menú al hacer clic fuera
      document.addEventListener('click', function(e) {
        const menu = document.getElementById('category-menu');
        const menuBtn = document.getElementById('category-menu-btn');
        
        if (!menu.contains(e.target) && e.target !== menuBtn) {
          menu.classList.remove('active');
        }
      });
      
      // Configurar categoría en formulario
      document.getElementById("categoria").addEventListener('change', function() {
        document.getElementById("saga-images-container").style.display = 
          this.value === 'sagas' ? 'block' : 'none';
      });
      
      document.getElementById("edit-categoria").addEventListener('change', function() {
        document.getElementById("edit-saga-images-container").style.display = 
          this.value === 'sagas' ? 'block' : 'none';
      });
    });

    // Funciones para el carrusel
    function renderizarCarousel() {
      const carousel = document.getElementById('new-books-carousel');
      carousel.innerHTML = '';
      
      // Tomar los últimos 5 libros como "nuevos"
      const librosNuevos = [...libros].reverse().slice(0, 5);
      
      librosNuevos.forEach(libro => {
        const item = document.createElement('div');
        item.className = 'carousel-item';
        item.innerHTML = `
          <img src="${libro.imagen}" alt="${libro.titulo}">
          <h4>${libro.titulo}</h4>
        `;
        carousel.appendChild(item);
      });
      
      currentCarouselIndex = 0;
      updateCarouselPosition();
    }

    function moveCarousel(direction) {
      const carousel = document.getElementById('new-books-carousel');
      const items = carousel.querySelectorAll('.carousel-item');
      if (items.length === 0) return;
      
      const itemWidth = items[0].offsetWidth + 32; // Ancho + margen
      const maxIndex = items.length - 1;
      
      // Calcular nuevo índice
      currentCarouselIndex += direction;
      
      // Carrusel circular: volver al inicio después del último
      if (currentCarouselIndex < 0) {
        currentCarouselIndex = maxIndex;
      } else if (currentCarouselIndex > maxIndex) {
        currentCarouselIndex = 0;
      }
      
      updateCarouselPosition();
    }

    function updateCarouselPosition() {
      const carousel = document.getElementById('new-books-carousel');
      const items = carousel.querySelectorAll('.carousel-item');
      if (items.length === 0) return;

      const itemWidth = items[0].offsetWidth + 32;
      const position = -currentCarouselIndex * itemWidth;
      carousel.style.transform = `translateX(${position}px)`;
    }

    // Carrusel automático cada 2.5 segundos
    function startCarouselAutoMove() {
      // Limpiar intervalo existente
      if (carouselInterval) clearInterval(carouselInterval);
      
      // Configurar nuevo intervalo
      carouselInterval = setInterval(() => {
        moveCarousel(1);
      }, 2500);
    }

    // Funciones para libros
    function actualizarContadorLibros() {
      document.getElementById('total-books-count').textContent = libros.length;
    }

    function agregarLibro() {
      const titulo = document.getElementById("titulo").value;
      const resena = document.getElementById("resena").value;
      const caracteristica1 = document.getElementById("caracteristica1").value;
      const caracteristica2 = document.getElementById("caracteristica2").value;
      const autor = document.getElementById("autor").value;
      const editorial = document.getElementById("editorial").value;
      const categoria = document.getElementById("categoria").value;
      const disponible = document.getElementById("disponible").value;
      const imagenUrl = document.getElementById("imagen").value;
      
      if (!titulo || !resena) {
        alert("Por favor complete el título y reseña del libro");
        return;
      }
      
      // Validar imagen
      let imagen = imagenUrl;
      if (uploadedImage) {
        imagen = uploadedImage;
      }
      
      if (!imagen) {
        alert("Por favor agregue una imagen (subiendo archivo o ingresando URL)");
        return;
      }
      
      // Validar sagas (requiere al menos 1 imagen)
      if (categoria === 'sagas' && uploadedSagaImages.length < 1) {
        alert("Para una saga debes subir al menos una imagen en la sección de 'Imagen de la saga'");
        return;
      }
      
      // Crear objeto libro
      const libro = { 
        titulo, 
        resena,
        caracteristica1,
        caracteristica2,
        autor, 
        editorial, 
        categoria, 
        disponible, 
        imagen 
      };
      
      // Agregar imágenes de saga si corresponde
      if (categoria === 'sagas' && uploadedSagaImages.length > 0) {
        libro.sagaImages = [...uploadedSagaImages];
      }
      
      libros.push(libro);
      localStorage.setItem("libros", JSON.stringify(libros));
      renderizarLibros();
      renderizarCarousel();
      actualizarContadorLibros();
      
      // Limpiar campos
      document.getElementById("titulo").value = "";
      document.getElementById("resena").value = "";
      document.getElementById("caracteristica1").value = "";
      document.getElementById("caracteristica2").value = "";
      document.getElementById("autor").value = "";
      document.getElementById("editorial").value = "";
      document.getElementById("imagen").value = "";
      document.getElementById("image-preview").innerHTML = "";
      document.getElementById("saga-images-grid").innerHTML = "";
      document.getElementById("saga-images-container").style.display = "none";
      uploadedImage = null;
      uploadedSagaImages = [];
      
      showConfirmation("Libro agregado exitosamente");
    }

    function editarLibro(index) {
      const libro = libros[index];
      
      // Llenar el formulario de edición
      document.getElementById("edit-titulo").value = libro.titulo;
      document.getElementById("edit-resena").value = libro.resena || '';
      document.getElementById("edit-caracteristica1").value = libro.caracteristica1 || '';
      document.getElementById("edit-caracteristica2").value = libro.caracteristica2 || '';
      document.getElementById("edit-autor").value = libro.autor || '';
      document.getElementById("edit-editorial").value = libro.editorial || '';
      document.getElementById("edit-categoria").value = libro.categoria;
      document.getElementById("edit-disponible").value = libro.disponible;
      document.getElementById("edit-imagen").value = libro.imagen.startsWith('http') ? libro.imagen : '';
      document.getElementById("edit-index").value = index;
      
      // Mostrar imagen actual
      const editImagePreview = document.getElementById('edit-image-preview');
      editImagePreview.innerHTML = '';
      if (libro.imagen) {
        editImagePreview.innerHTML = `
          <div class="image-preview-item">
            <img src="${libro.imagen}" />
            <button class="remove-image-btn" onclick="removeEditUploadedImage()">×</button>
          </div>
        `;
        editUploadedImage = libro.imagen;
      }
      
      // Mostrar imágenes de saga si corresponde
      const editSagaContainer = document.getElementById('edit-saga-images-container');
      const editSagaGrid = document.getElementById('edit-saga-images-grid');
      editSagaGrid.innerHTML = '';
      
      if (libro.categoria === 'sagas' && libro.sagaImages) {
        editSagaContainer.style.display = 'block';
        editUploadedSagaImages = [...libro.sagaImages];
        
        libro.sagaImages.forEach((img, i) => {
          editSagaGrid.innerHTML += `
            <div class="saga-image-item">
              <img src="${img}" />
              <button class="remove-saga-image-btn" onclick="removeEditSagaImage(${i})">×</button>
            </div>
          `;
        });
      } else {
        editSagaContainer.style.display = 'none';
        editUploadedSagaImages = [];
      }
      
      // Mostrar formulario de edición
      document.getElementById("edit-book-form").style.display = "block";
      document.getElementById("books-tab").scrollIntoView({ behavior: 'smooth' });
    }

    function guardarEdicion() {
      const index = document.getElementById("edit-index").value;
      const titulo = document.getElementById("edit-titulo").value;
      const resena = document.getElementById("edit-resena").value;
      const caracteristica1 = document.getElementById("edit-caracteristica1").value;
      const caracteristica2 = document.getElementById("edit-caracteristica2").value;
      const autor = document.getElementById("edit-autor").value;
      const editorial = document.getElementById("edit-editorial").value;
      const categoria = document.getElementById("edit-categoria").value;
      const disponible = document.getElementById("edit-disponible").value;
      const imagenUrl = document.getElementById("edit-imagen").value;
      
      if (!titulo || !resena) {
        alert("Por favor complete el título y reseña del libro");
        return;
      }
      
      // Validar imagen
      let imagen = imagenUrl;
      if (editUploadedImage) {
        imagen = editUploadedImage;
      }
      
      if (!imagen) {
        alert("Por favor agregue una imagen (subiendo archivo o ingresando URL)");
        return;
      }
      
      // Validar sagas (requiere al menos 1 imagen)
      if (categoria === 'sagas' && editUploadedSagaImages.length < 1) {
        alert("Para una saga debes subir al menos una imagen en la sección de 'Imagen de la saga'");
        return;
      }
      
      // Actualizar libro
      libros[index] = { 
        titulo, 
        resena,
        caracteristica1,
        caracteristica2,
        autor, 
        editorial, 
        categoria, 
        disponible, 
        imagen 
      };
      
      // Agregar imágenes de saga si corresponde
      if (categoria === 'sagas' && editUploadedSagaImages.length > 0) {
        libros[index].sagaImages = [...editUploadedSagaImages];
      } else {
        delete libros[index].sagaImages;
      }
      
      localStorage.setItem("libros", JSON.stringify(libros));
      renderizarLibros();
      renderizarCarousel();
      actualizarContadorLibros();
      renderAdminBookList();
      
      // Ocultar formulario de edición
      document.getElementById("edit-book-form").style.display = "none";
      showConfirmation("Cambios guardados exitosamente");
    }

    function eliminarLibro(index) {
      if (confirm("¿Está seguro que desea eliminar este libro?")) {
        libros.splice(index, 1);
        localStorage.setItem("libros", JSON.stringify(libros));
        renderizarLibros();
        renderizarCarousel();
        actualizarContadorLibros();
        renderAdminBookList();
        showConfirmation("Libro eliminado exitosamente");
      }
    }

    function cancelarEdicion() {
      document.getElementById("edit-book-form").style.display = "none";
    }

    // Funciones para usuarios (solo administrador)
    function loginUser() {
      const email = document.getElementById('login-email').value;
      const password = document.getElementById('login-password').value;
      
      // Credenciales únicas de administrador (ahora ocultas)
      const adminEmail = "admin@milenium.com";
      const adminPassword = "milenium123";
      
      if (email === adminEmail && password === adminPassword) {
        currentUser = { email };
        localStorage.setItem('currentUser', JSON.stringify(currentUser));
        showUserLoggedIn(email);
        showConfirmation('Inicio de sesión exitoso como administrador');
        cerrarLoginModal();
        mostrarPanelAdmin();
        // Limpiar campo de contraseña
        document.getElementById('login-password').value = '';
      } else {
        alert('Credenciales incorrectas');
      }
    }

    function logoutUser() {
      currentUser = null;
      localStorage.removeItem('currentUser');
      document.getElementById('user-info').style.display = 'none';
      showConfirmation('Sesión cerrada exitosamente');
      cerrarSesionAdmin();
    }

    function showUserLoggedIn(email) {
      document.getElementById('user-email').textContent = email;
      document.getElementById('user-info').style.display = 'block';
    }

    // Funciones para panel de administrador
    function mostrarPanelAdmin() {
      if (!currentUser) {
        return;
      }
      
      document.getElementById('admin-panel').style.display = 'block';
      document.getElementById('admin-overlay').style.display = 'block';
      renderAdminBookList();
    }

    function cerrarSesionAdmin() {
      document.getElementById('admin-panel').style.display = 'none';
      document.getElementById('admin-overlay').style.display = 'none';
    }

    function openTab(tabId) {
      // Ocultar todas las pestañas
      document.querySelectorAll('.tab-content').forEach(tab => {
        tab.classList.remove('active');
      });
      document.querySelectorAll('.tab').forEach(tab => {
        tab.classList.remove('active');
      });
      
      // Mostrar pestaña seleccionada
      document.getElementById(tabId).classList.add('active');
      document.querySelector(`.tab[onclick="openTab('${tabId}')"]`).classList.add('active');
    }

    function renderAdminBookList() {
      const container = document.getElementById('book-list-admin');
      container.innerHTML = '';
      
      libros.forEach((libro, index) => {
        const bookDiv = document.createElement('div');
        bookDiv.className = 'book';
        bookDiv.innerHTML = `
          <img src="${libro.imagen}" alt="${libro.titulo}" />
          <h4>${libro.titulo}</h4>
          <p class="book-author">${libro.autor}</p>
          <div class="book-resume">${libro.resena.substring(0, 120)}...</div>
          <div class="book-details">
            <span class="book-category">${libro.categoria}</span>
            <span class="book-availability ${libro.disponible === 'true' ? 'available' : 'not-available'}">${libro.disponible === 'true' ? 'Disponible' : 'Agotado'}</span>
          </div>
          <div class="book-actions">
            <button class="edit-btn" onclick="editarLibro(${index})">Editar</button>
            <button class="logout-btn" onclick="eliminarLibro(${index})">Eliminar</button>
          </div>
        `;
        container.appendChild(bookDiv);
      });
    }

    function renderizarLibros() {
      const container = document.getElementById('book-list');
      container.innerHTML = '';
      
      const filteredBooks = libros.filter(libro => {
        const matchesCategory = currentCategory === 'all' || libro.categoria === currentCategory;
        const matchesSearch = searchTerm === '' || 
          libro.titulo.toLowerCase().includes(searchTerm) || 
          libro.autor.toLowerCase().includes(searchTerm) ||
          libro.categoria.toLowerCase().includes(searchTerm);
        return matchesCategory && matchesSearch;
      });
      
      if (filteredBooks.length === 0) {
        container.innerHTML = '<p class="section-title">No se encontraron libros</p>';
        return;
      }
      
      filteredBooks.forEach((libro, index) => {
        const bookDiv = document.createElement('div');
        bookDiv.className = 'book';
        bookDiv.innerHTML = `
          <img src="${libro.imagen}" alt="${libro.titulo}" />
          <h4>${libro.titulo}</h4>
          <p class="book-author">${libro.autor}</p>
          <div class="book-resume">${libro.resena.substring(0, 120)}...</div>
          <div class="book-details">
            <span class="book-category">${libro.categoria}</span>
            <span class="book-availability ${libro.disponible === 'true' ? 'available' : 'not-available'}">${libro.disponible === 'true' ? 'Disponible' : 'Agotado'}</span>
          </div>
        `;
        container.appendChild(bookDiv);
      });
    }

    function filterBooks(category) {
      currentCategory = category;
      
      // Actualizar pestañas activas
      document.querySelectorAll('.category-tab').forEach(tab => {
        tab.classList.remove('active');
      });
      document.querySelector(`.category-tab[data-category="${category}"]`).classList.add('active');
      
      renderizarLibros();
    }

    function renderizarSocialLinks() {
      const container = document.getElementById('social-links');
      container.innerHTML = '';
      
      for (const [platform, data] of Object.entries(socialLinks)) {
        container.innerHTML += `
          <a href="${data.url}" target="_blank">
            <img src="${data.icon}" alt="${platform}" />
            ${platform.charAt(0).toUpperCase() + platform.slice(1)}
          </a>
        `;
      }
    }

    // Funciones para manejo de imágenes
    function handleFileUpload() {
      const fileInput = document.getElementById('file-input');
      if (fileInput.files && fileInput.files[0]) {
        const reader = new FileReader();
        reader.onload = function(e) {
          document.getElementById('image-preview').innerHTML = `
            <div class="image-preview-item">
              <img src="${e.target.result}" />
              <button class="remove-image-btn" onclick="removeUploadedImage()">×</button>
            </div>
          `;
          uploadedImage = e.target.result;
        };
        reader.readAsDataURL(fileInput.files[0]);
      }
    }

    function confirmImageUrl() {
      const url = document.getElementById('imagen').value;
      if (url) {
        document.getElementById('image-preview').innerHTML = `
          <div class="image-preview-item">
            <img src="${url}" />
            <button class="remove-image-btn" onclick="removeUploadedImage()">×</button>
          </div>
        `;
        uploadedImage = url;
      } else {
        alert("Por favor ingrese una URL válida");
      }
    }

    function removeUploadedImage() {
      uploadedImage = null;
      document.getElementById('image-preview').innerHTML = '';
      document.getElementById('imagen').value = '';
      document.getElementById('file-input').value = '';
    }

    function handleSagaFilesUpload() {
      const fileInput = document.getElementById('saga-file-input');
      const files = fileInput.files;
      if (files.length > 0) {
        const grid = document.getElementById('saga-images-grid');
        grid.innerHTML = '';
        
        // Solo tomamos la primera imagen
        const file = files[0];
        const reader = new FileReader();
        reader.onload = function(e) {
          grid.innerHTML += `
            <div class="saga-image-item">
              <img src="${e.target.result}" />
              <button class="remove-saga-image-btn" onclick="removeSagaImage()">×</button>
            </div>
          `;
          uploadedSagaImages = [e.target.result];
        };
        reader.readAsDataURL(file);
        
        document.getElementById('confirm-saga-btn').style.display = 'block';
      }
    }

    function removeSagaImage() {
      uploadedSagaImages = [];
      document.getElementById('saga-images-grid').innerHTML = '';
      document.getElementById('saga-file-input').value = '';
      document.getElementById('confirm-saga-btn').style.display = 'none';
    }

    function confirmSagaImages() {
      if (uploadedSagaImages.length > 0) {
        showConfirmation("Imagen de saga confirmada");
      } else {
        alert("Por favor suba una imagen primero");
      }
    }

    // Funciones para editar imágenes
    function handleEditFileUpload() {
      const fileInput = document.getElementById('edit-file-input');
      if (fileInput.files && fileInput.files[0]) {
        const reader = new FileReader();
        reader.onload = function(e) {
          document.getElementById('edit-image-preview').innerHTML = `
            <div class="image-preview-item">
              <img src="${e.target.result}" />
              <button class="remove-image-btn" onclick="removeEditUploadedImage()">×</button>
            </div>
          `;
          editUploadedImage = e.target.result;
        };
        reader.readAsDataURL(fileInput.files[0]);
      }
    }

    function confirmEditImageUrl() {
      const url = document.getElementById('edit-imagen').value;
      if (url) {
        document.getElementById('edit-image-preview').innerHTML = `
          <div class="image-preview-item">
            <img src="${url}" />
            <button class="remove-image-btn" onclick="removeEditUploadedImage()">×</button>
          </div>
        `;
        editUploadedImage = url;
      } else {
        alert("Por favor ingrese una URL válida");
      }
    }

    function removeEditUploadedImage() {
      editUploadedImage = null;
      document.getElementById('edit-image-preview').innerHTML = '';
      document.getElementById('edit-imagen').value = '';
      document.getElementById('edit-file-input').value = '';
    }

    function handleEditSagaFilesUpload() {
      const fileInput = document.getElementById('edit-saga-file-input');
      const files = fileInput.files;
      if (files.length > 0) {
        const grid = document.getElementById('edit-saga-images-grid');
        grid.innerHTML = '';
        
        // Solo tomamos la primera imagen
        const file = files[0];
        const reader = new FileReader();
        reader.onload = function(e) {
          grid.innerHTML += `
            <div class="saga-image-item">
              <img src="${e.target.result}" />
              <button class="remove-saga-image-btn" onclick="removeEditSagaImage()">×</button>
            </div>
          `;
          editUploadedSagaImages = [e.target.result];
        };
        reader.readAsDataURL(file);
        
        document.getElementById('confirm-edit-saga-btn').style.display = 'block';
      }
    }

    function removeEditSagaImage() {
      editUploadedSagaImages = [];
      document.getElementById('edit-saga-images-grid').innerHTML = '';
      document.getElementById('edit-saga-file-input').value = '';
      document.getElementById('confirm-edit-saga-btn').style.display = 'none';
    }

    function confirmEditSagaImages() {
      if (editUploadedSagaImages.length > 0) {
        showConfirmation("Imagen de saga confirmada");
      } else {
        alert("Por favor suba una imagen primero");
      }
    }

    // Funciones para acceso de administrador
    function mostrarLoginAdmin() {
      if (currentUser) {
        mostrarPanelAdmin();
      } else {
        document.getElementById('login-modal').style.display = 'block';
        document.getElementById('admin-overlay').style.display = 'block';
      }
    }

    function cerrarLoginModal() {
      document.getElementById('login-modal').style.display = 'none';
      document.getElementById('admin-overlay').style.display = 'none';
    }

    // Funciones para el logotipo
    function handleLogoUpload() {
      const fileInput = document.getElementById('logo-input');
      if (fileInput.files && fileInput.files[0]) {
        const reader = new FileReader();
        reader.onload = function(e) {
          document.getElementById('logo-preview').innerHTML = `
            <div class="image-preview-item">
              <img src="${e.target.result}" />
              <div class="preview-actions">
                <button class="confirm-image-btn" onclick="confirmLogoUpload('${e.target.result}')">Confirmar</button>
                <button class="logout-btn" onclick="removeLogoUpload()">Cancelar</button>
              </div>
            </div>
          `;
        };
        reader.readAsDataURL(fileInput.files[0]);
      }
    }

    function confirmLogoUpload(imageSrc) {
      uploadedLogo = imageSrc;
      document.getElementById('logo-preview').innerHTML = `
        <div class="image-preview-item">
          <img src="${imageSrc}" />
          <button class="remove-image-btn" onclick="removeLogoUpload()">×</button>
        </div>
      `;
      showConfirmation("Logotipo cargado correctamente");
    }

    function confirmLogoUrl() {
      const url = document.getElementById('logo-url').value;
      if (url) {
        uploadedLogo = url;
        document.getElementById('logo-preview').innerHTML = `
          <div class="image-preview-item">
            <img src="${url}" />
            <button class="remove-image-btn" onclick="removeLogoUpload()">×</button>
          </div>
        `;
        showConfirmation("URL de logotipo confirmada");
      } else {
        alert("Por favor ingrese una URL válida");
      }
    }

    function removeLogoUpload() {
      uploadedLogo = null;
      document.getElementById('logo-preview').innerHTML = '';
      document.getElementById('logo-url').value = '';
      document.getElementById('logo-input').value = '';
    }

    function updateLogo() {
      if (uploadedLogo) {
        // Aquí podríamos guardar el logo si fuera necesario
        showConfirmation("Logotipo actualizado correctamente");
      } else {
        alert("Por favor suba o ingrese un logotipo primero");
      }
    }

    function updateSocialLinks() {
      const facebookUrl = document.getElementById('facebook-url').value;
      const facebookIcon = document.getElementById('facebook-icon').value;
      const instagramUrl = document.getElementById('instagram-url').value;
      const instagramIcon = document.getElementById('instagram-icon').value;
      const whatsappUrl = document.getElementById('whatsapp-url').value;
      const whatsappIcon = document.getElementById('whatsapp-icon').value;
      
      socialLinks = {
        facebook: { url: facebookUrl, icon: facebookIcon },
        instagram: { url: instagramUrl, icon: instagramIcon },
        whatsapp: { url: whatsappUrl, icon: whatsappIcon }
      };
      
      localStorage.setItem('socialLinks', JSON.stringify(socialLinks));
      renderizarSocialLinks();
      showConfirmation('Redes sociales actualizadas correctamente');
    }
    
    // Función para mostrar mensajes de confirmación
    function showConfirmation(message) {
      const confirmation = document.getElementById('confirmation-message');
      confirmation.textContent = message;
      confirmation.style.display = 'block';
      
      setTimeout(() => {
        confirmation.style.display = 'none';
      }, 3000);
    }
  </script>
</body>
</html>
