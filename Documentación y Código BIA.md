# 🕊️ BIA - Velas y Wax Melts | Catálogo Interactivo

Bienvenido/a al repositorio oficial del catálogo digital de **BIA - Velas y Wax Melts**. Esta aplicación web está diseñada en una estética beige, blanca y rosa terracota, permitiendo gestionar el catálogo de productos (crear, editar, subir fotos y eliminar) y ofrecer a los clientes una experiencia fácil para consultar productos y realizar pedidos vía WhatsApp.

---

## 📋 Categorías Incluidas

1. **Wax Melts**
2. **Pebeteros**
3. **Placas Aromáticas**
4. **Bouquets**
5. **Aromas**
6. **Formas / Figuras**

---

## 🚀 Guía Rápidas de Publicación en GitHub Pages

1. Crea o abre tu repositorio en GitHub (ej. `catalogo-bia`).
2. Sube el código que aparece abajo dentro de un archivo llamado exactamente **`index.html`**.
3. Ve a **Settings** > **Pages** en tu repositorio de GitHub.
4. En **Branch**, selecciona `main` (o `master`) y guarda (`Save`).
5. En 1-2 minutos tendrás tu enlace público listo para enviar a tus clientes (ej. `https://tu-usuario.github.io/catalogo-bia/`).

---

## 💻 Código Completo de la Aplicación (`index.html`)

Copia todo el contenido a continuación y guárdalo como `index.html`:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>BIA | Velas y Wax Melts - Catálogo</title>
  
  <!-- Tipografías de Google -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Alex+Brush&family=Montserrat:wght@300;400;500;600&family=Playfair+Display:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
  
  <!-- Remix Icons -->
  <link href="https://cdn.jsdelivr.net/npm/remixicon@3.5.0/fonts/remixicon.css" rel="stylesheet">

  <style>
    :root {
      --bg-cream: #FDFBF7;
      --bg-card: #FFFFFF;
      --bg-accent: #F4EBE1;
      --terracotta-soft: #C88D83;
      --terracotta-dark: #A36B62;
      --text-main: #4A3E3D;
      --text-muted: #8C7A78;
      --border-color: #E8DFD8;
      --shadow-soft: 0 10px 30px rgba(163, 107, 98, 0.08);
      --shadow-hover: 0 15px 35px rgba(163, 107, 98, 0.15);
      --radius: 16px;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Montserrat', sans-serif;
      background-color: var(--bg-cream);
      color: var(--text-main);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    /* BARRA SUPERIOR (HEADER) */
    header {
      background-color: rgba(253, 251, 247, 0.95);
      backdrop-filter: blur(10px);
      position: sticky;
      top: 0;
      z-index: 100;
      border-bottom: 1px solid var(--border-color);
      padding: 1rem 2rem;
    }

    .header-container {
      max-width: 1200px;
      margin: 0 auto;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    /* LOGO ESTILIZADO DE BIA */
    .brand-logo {
      display: flex;
      flex-direction: column;
      align-items: center;
      text-decoration: none;
      color: var(--terracotta-dark);
    }

    .brand-subtitle {
      font-family: 'Montserrat', sans-serif;
      font-size: 0.65rem;
      letter-spacing: 0.3em;
      text-transform: uppercase;
      color: var(--text-muted);
      margin-bottom: -5px;
    }

    .brand-title-wrap {
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .brand-title {
      font-family: 'Alex Brush', cursive;
      font-size: 3.2rem;
      line-height: 1;
      color: var(--terracotta-soft);
      font-weight: 400;
    }

    .colibri-icon {
      width: 32px;
      height: 32px;
      fill: var(--terracotta-soft);
    }

    /* ACCIONES DEL HEADER */
    .header-actions {
      display: flex;
      align-items: center;
      gap: 1rem;
    }

    .btn {
      padding: 0.6rem 1.2rem;
      border-radius: 30px;
      font-family: 'Montserrat', sans-serif;
      font-size: 0.85rem;
      font-weight: 500;
      cursor: pointer;
      transition: all 0.3s ease;
      border: 1px solid transparent;
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      text-decoration: none;
    }

    .btn-admin {
      background-color: transparent;
      border-color: var(--terracotta-soft);
      color: var(--terracotta-dark);
    }

    .btn-admin:hover, .btn-admin.active {
      background-color: var(--terracotta-soft);
      color: white;
    }

    .btn-cart {
      background-color: var(--terracotta-soft);
      color: white;
      position: relative;
    }

    .btn-cart:hover {
      background-color: var(--terracotta-dark);
    }

    .cart-badge {
      background-color: white;
      color: var(--terracotta-dark);
      font-size: 0.75rem;
      font-weight: 700;
      width: 20px;
      height: 20px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    /* BANNER BARRA ADMIN */
    .admin-bar {
      background-color: var(--bg-accent);
      border-bottom: 1px solid var(--border-color);
      padding: 0.75rem 2rem;
      display: none;
      animation: fadeIn 0.3s ease;
    }

    .admin-bar.show {
      display: block;
    }

    .admin-bar-container {
      max-width: 1200px;
      margin: 0 auto;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 1rem;
    }

    .admin-title {
      font-size: 0.9rem;
      font-weight: 600;
      color: var(--terracotta-dark);
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }

    .admin-tools {
      display: flex;
      gap: 0.5rem;
    }

    .btn-sm {
      padding: 0.4rem 0.8rem;
      font-size: 0.75rem;
    }

    .btn-primary {
      background-color: var(--terracotta-soft);
      color: white;
    }
    .btn-primary:hover {
      background-color: var(--terracotta-dark);
    }

    /* HEROCARD / SECCIÓN PRINCIPAL */
    .hero {
      text-align: center;
      padding: 3rem 1.5rem 2rem;
      max-width: 700px;
      margin: 0 auto;
    }

    .hero h1 {
      font-family: 'Playfair Display', serif;
      font-size: 2.2rem;
      font-weight: 400;
      color: var(--text-main);
      margin-bottom: 0.5rem;
    }

    .hero p {
      color: var(--text-muted);
      font-size: 0.95rem;
      line-height: 1.6;
    }

    /* CONTENEDOR PRINCIPAL Y FILTROS */
    main {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 1.5rem 4rem;
      flex-grow: 1;
      width: 100%;
    }

    .search-filter-section {
      margin-bottom: 2.5rem;
      display: flex;
      flex-direction: column;
      gap: 1.5rem;
      align-items: center;
    }

    .search-box {
      position: relative;
      width: 100%;
      max-width: 450px;
    }

    .search-box input {
      width: 100%;
      padding: 0.8rem 1.2rem 0.8rem 2.8rem;
      border-radius: 30px;
      border: 1px solid var(--border-color);
      background-color: white;
      font-family: 'Montserrat', sans-serif;
      font-size: 0.9rem;
      outline: none;
      transition: all 0.3s ease;
    }

    .search-box input:focus {
      border-color: var(--terracotta-soft);
      box-shadow: 0 0 0 3px rgba(200, 141, 131, 0.15);
    }

    .search-box i {
      position: absolute;
      left: 1rem;
      top: 50%;
      transform: translateY(-50%);
      color: var(--text-muted);
    }

    /* CATEGORÍAS EN CHIPS */
    .categories-tabs {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 0.6rem;
    }

    .cat-chip {
      padding: 0.6rem 1.2rem;
      border-radius: 25px;
      background-color: white;
      border: 1px solid var(--border-color);
      color: var(--text-muted);
      font-size: 0.85rem;
      cursor: pointer;
      transition: all 0.3s ease;
      user-select: none;
    }

    .cat-chip:hover, .cat-chip.active {
      background-color: var(--terracotta-soft);
      color: white;
      border-color: var(--terracotta-soft);
    }

    /* GRILLA DE PRODUCTOS */
    .products-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
      gap: 2rem;
    }

    .product-card {
      background-color: var(--bg-card);
      border-radius: var(--radius);
      overflow: hidden;
      box-shadow: var(--shadow-soft);
      border: 1px solid var(--border-color);
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      display: flex;
      flex-direction: column;
      position: relative;
    }

    .product-card:hover {
      transform: translateY(-5px);
      box-shadow: var(--shadow-hover);
    }

    .product-img-wrap {
      position: relative;
      width: 100%;
      padding-top: 100%; /* Cuadrado perfecto */
      background-color: var(--bg-accent);
      overflow: hidden;
    }

    .product-img {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.5s ease;
    }

    .product-card:hover .product-img {
      transform: scale(1.04);
    }

    .category-badge {
      position: absolute;
      top: 12px;
      left: 12px;
      background-color: rgba(255, 255, 255, 0.9);
      backdrop-filter: blur(4px);
      color: var(--terracotta-dark);
      font-size: 0.7rem;
      font-weight: 600;
      padding: 0.3rem 0.7rem;
      border-radius: 20px;
      text-transform: uppercase;
      letter-spacing: 0.05em;
    }

    .product-info {
      padding: 1.25rem;
      display: flex;
      flex-direction: column;
      flex-grow: 1;
    }

    .product-title {
      font-family: 'Playfair Display', serif;
      font-size: 1.15rem;
      font-weight: 600;
      color: var(--text-main);
      margin-bottom: 0.4rem;
    }

    .product-desc {
      font-size: 0.82rem;
      color: var(--text-muted);
      line-height: 1.5;
      margin-bottom: 1rem;
      flex-grow: 1;
    }

    .product-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: auto;
      padding-top: 0.8rem;
      border-top: 1px dashed var(--border-color);
    }

    .product-price {
      font-size: 1.1rem;
      font-weight: 600;
      color: var(--terracotta-dark);
    }

    .btn-add {
      background-color: var(--bg-accent);
      color: var(--terracotta-dark);
      border: none;
      width: 36px;
      height: 36px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      transition: all 0.2s ease;
    }

    .btn-add:hover {
      background-color: var(--terracotta-soft);
      color: white;
    }

    /* ACCIONES DE ADMIN EN TARJETA */
    .admin-card-actions {
      position: absolute;
      top: 12px;
      right: 12px;
      display: flex;
      gap: 6px;
      z-index: 10;
    }

    .btn-card-action {
      background-color: white;
      color: var(--text-main);
      border: none;
      width: 32px;
      height: 32px;
      border-radius: 50%;
      box-shadow: 0 4px 10px rgba(0,0,0,0.15);
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.2s ease;
    }

    .btn-card-action:hover {
      transform: scale(1.1);
    }

    .btn-card-action.delete:hover {
      background-color: #E57373;
      color: white;
    }

    /* ESTADO VACÍO */
    .empty-state {
      text-align: center;
      padding: 4rem 1rem;
      color: var(--text-muted);
      grid-column: 1 / -1;
    }

    .empty-state i {
      font-size: 3rem;
      color: var(--border-color);
      margin-bottom: 1rem;
    }

    /* MODALES */
    .modal-overlay {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: rgba(74, 62, 61, 0.5);
      backdrop-filter: blur(4px);
      z-index: 200;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 1rem;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s ease;
    }

    .modal-overlay.active {
      opacity: 1;
      pointer-events: auto;
    }

    .modal {
      background-color: white;
      border-radius: var(--radius);
      width: 100%;
      max-width: 500px;
      max-height: 90vh;
      overflow-y: auto;
      box-shadow: 0 20px 40px rgba(0,0,0,0.2);
      padding: 2rem;
      position: relative;
    }

    .modal-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 1.5rem;
      padding-bottom: 0.8rem;
      border-bottom: 1px solid var(--border-color);
    }

    .modal-title {
      font-family: 'Playfair Display', serif;
      font-size: 1.3rem;
      color: var(--terracotta-dark);
    }

    .close-modal {
      background: none;
      border: none;
      font-size: 1.5rem;
      color: var(--text-muted);
      cursor: pointer;
    }

    /* FORMULARIO */
    .form-group {
      margin-bottom: 1.2rem;
    }

    .form-group label {
      display: block;
      font-size: 0.82rem;
      font-weight: 600;
      color: var(--text-main);
      margin-bottom: 0.4rem;
    }

    .form-control {
      width: 100%;
      padding: 0.75rem 1rem;
      border: 1px solid var(--border-color);
      border-radius: 8px;
      font-family: 'Montserrat', sans-serif;
      font-size: 0.9rem;
      outline: none;
    }

    .form-control:focus {
      border-color: var(--terracotta-soft);
    }

    textarea.form-control {
      resize: vertical;
      min-height: 80px;
    }

    .image-preview {
      width: 100%;
      height: 150px;
      border: 2px dashed var(--border-color);
      border-radius: 8px;
      margin-top: 0.5rem;
      display: flex;
      align-items: center;
      justify-content: center;
      overflow: hidden;
      background-color: var(--bg-cream);
    }

    .image-preview img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    /* MODAL CARRITO */
    .cart-item {
      display: flex;
      align-items: center;
      gap: 1rem;
      padding: 0.8rem 0;
      border-bottom: 1px solid var(--border-color);
    }

    .cart-item-img {
      width: 50px;
      height: 50px;
      border-radius: 8px;
      object-fit: cover;
    }

    .cart-item-details {
      flex-grow: 1;
    }

    .cart-item-title {
      font-size: 0.9rem;
      font-weight: 600;
    }

    .cart-item-price {
      font-size: 0.8rem;
      color: var(--terracotta-dark);
    }

    .cart-item-qty {
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }

    .btn-qty {
      background-color: var(--bg-accent);
      border: none;
      width: 24px;
      height: 24px;
      border-radius: 50%;
      cursor: pointer;
      font-weight: 600;
    }

    .cart-summary {
      margin-top: 1.5rem;
      padding-top: 1rem;
      border-top: 2px solid var(--border-color);
    }

    .cart-total-row {
      display: flex;
      justify-content: space-between;
      font-size: 1.1rem;
      font-weight: 600;
      margin-bottom: 1.5rem;
    }

    .btn-whatsapp {
      width: 100%;
      background-color: #25D366;
      color: white;
      justify-content: center;
      padding: 0.8rem;
      font-size: 1rem;

    }

    .btn-whatsapp:hover {
      background-color: #1EBE5D;
    }

    /* FOOTER */
    footer {
      background-color: var(--bg-accent);
      border-top: 1px solid var(--border-color);
      padding: 2rem;
      text-align: center;
      font-size: 0.85rem;
      color: var(--text-muted);
      margin-top: auto;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(-5px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @media (max-width: 600px) {
      header {
        padding: 0.8rem 1rem;
      }
      .brand-title {
        font-size: 2.5rem;
      }
      .colibri-icon {
        width: 26px;
        height: 26px;
      }
      .products-grid {
        grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
        gap: 1rem;
      }
      .product-info {
        padding: 0.8rem;
      }
      .product-title {
        font-size: 1rem;
      }
    }
  </style>
</head>
<body>

  <!-- ENCABEZADO Y LOGO DE BIA -->
  <header>
    <div class="header-container">
      <a href="#" class="brand-logo">
        <span class="brand-subtitle">Velas y Wax Melts</span>
        <div class="brand-title-wrap">
          <span class="brand-title">Bia</span>
          <!-- Colibrí en SVG -->
          <svg class="colibri-icon" viewBox="0 0 24 24">
            <path d="M21.5,4.5 C20,3.5 17.5,4 15,5.5 C13,3.5 10,3.5 8,4.5 C6.5,5.2 5.5,6.8 5,8.5 C3.5,8.5 2,9.5 1,11 C2.5,11.5 4,11 5,10.5 C5.2,13 6.8,15.5 9.5,17 C12,18.4 15,18 17.5,16.5 C19,15.5 20,14 20.5,12 C21.5,11.5 22.5,10 23,8.5 C22.5,8.8 21.5,8.8 20.5,8.5 C21.2,7 21.8,5.5 21.5,4.5 Z"/>
          </svg>
        </div>
      </a>

      <div class="header-actions">
        <button id="toggleAdminBtn" class="btn btn-admin">
          <i class="ri-edit-line"></i> Modo Edición
        </button>
        <button id="openCartBtn" class="btn btn-cart">
          <i class="ri-shopping-bag-line"></i> Pedido
          <span id="cartBadge" class="cart-badge">0</span>
        </button>
      </div>
    </div>
  </header>

  <!-- BARRA DE ADMINISTRACIÓN (SOLO MODAL EDICIÓN) -->
  <div id="adminBar" class="admin-bar">
    <div class="admin-bar-container">
      <div class="admin-title">
        <i class="ri-settings-4-line"></i> Panel de Edición de Productos
      </div>
      <div class="admin-tools">
        <button id="addProductBtn" class="btn btn-sm btn-primary">
          <i class="ri-add-line"></i> Agregar Producto
        </button>
        <button id="exportBtn" class="btn btn-sm btn-admin">
          <i class="ri-download-2-line"></i> Exportar Datos
        </button>
        <button id="importBtn" class="btn btn-sm btn-admin">
          <i class="ri-upload-2-line"></i> Importar
        </button>
        <input type="file" id="importFileInput" accept=".json" style="display: none;">
      </div>
    </div>
  </div>

  <!-- SECCIÓN HERO -->
  <section class="hero">
    <h1>Catálogo de Sostenibilidad & Aroma</h1>
    <p>Descubre nuestros melts y accesorios hechos artesanalmente para envolver tus espacios en sensaciones únicas.</p>
  </section>

  <!-- CONTENIDO PRINCIPAL -->
  <main>
    <!-- BARRA DE BÚSQUEDA Y NAVEGACIÓN DE CATEGORÍAS -->
    <div class="search-filter-section">
      <div class="search-box">
        <i class="ri-search-line"></i>
        <input type="text" id="searchInput" placeholder="Buscar por producto o aroma...">
      </div>

      <div class="categories-tabs" id="categoryTabs">
        <!-- Generado dinámicamente -->
      </div>
    </div>

    <!-- GRILLA DE PRODUCTOS -->
    <div class="products-grid" id="productsGrid">
      <!-- Carga dinámica -->
    </div>
  </main>

  <!-- PIE DE PÁGINA -->
  <footer>
    <p>© BIA - Velas y Wax Melts. Todos los derechos reservados.</p>
  </footer>

  <!-- MODAL: AGREGAR / EDITAR PRODUCTO -->
  <div class="modal-overlay" id="productModal">
    <div class="modal">
      <div class="modal-header">
        <h3 class="modal-title" id="modalTitle">Agregar Producto</h3>
        <button class="close-modal" class="closeProductModal">&times;</button>
      </div>
      <form id="productForm">
        <input type="hidden" id="productId">
        
        <div class="form-group">
          <label for="productName">Nombre del producto *</label>
          <input type="text" id="productName" class="form-control" required placeholder="Ej. Wax Melt Lavanda & Vainilla">
        </div>

        <div class="form-group">
          <label for="productCategory">Categoría *</label>
          <select id="productCategory" class="form-control" required>
            <option value="Wax Melts">Wax Melts</option>
            <option value="Pebeteros">Pebeteros</option>
            <option value="Placas Aromáticas">Placas Aromáticas</option>
            <option value="Bouquets">Bouquets</option>
            <option value="Aromas">Aromas</option>
            <option value="Formas">Formas / Figuras</option>
          </select>
        </div>

        <div class="form-group">
          <label for="productPrice">Precio ($) *</label>
          <input type="number" id="productPrice" class="form-control" required placeholder="Ej. 15000" step="100">
        </div>

        <div class="form-group">
          <label for="productDescription">Descripción o Notas Olfativas</label>
          <textarea id="productDescription" class="form-control" placeholder="Describe los aromas, detalles del producto o presentación..."></textarea>
        </div>

        <div class="form-group">
          <label>Imagen del Producto</label>
          <input type="file" id="productImageFile" class="form-control" accept="image/*">
          <div style="text-align: center; margin: 0.4rem 0; font-size: 0.75rem; color: var(--text-muted);">o mediante enlace web</div>
          <input type="url" id="productImageUrl" class="form-control" placeholder="https://ejemplo.com/imagen.jpg">
          
          <div class="image-preview" id="imagePreview">
            <span style="font-size: 0.8rem; color: var(--text-muted);">Vista previa de imagen</span>
          </div>
        </div>

        <div style="display: flex; gap: 1rem; margin-top: 1.5rem;">
          <button type="button" class="btn btn-admin closeProductModal" style="flex: 1; justify-content: center;">Cancelar</button>
          <button type="submit" class="btn btn-primary" style="flex: 1; justify-content: center;">Guardar Producto</button>
        </div>
      </form>
    </div>
  </div>

  <!-- MODAL: CARRITO DE COMPRAS / PEDIDOS -->
  <div class="modal-overlay" id="cartModal">
    <div class="modal">
      <div class="modal-header">
        <h3 class="modal-title">Tu Pedido</h3>
        <button class="close-modal" id="closeCartModal">&times;</button>
      </div>

      <div id="cartItemsContainer">
        <!-- Productos en carrito -->
      </div>

      <div class="cart-summary">
        <div class="cart-total-row">
          <span>Total estimado:</span>
          <span id="cartTotal">$0</span>
        </div>

        <div class="form-group">
          <label for="whatsappNumber">Número de WhatsApp donde recibirás el pedido:</label>
          <input type="text" id="whatsappNumber" class="form-control" value="573000000000" placeholder="Ej. 573001234567">
          <small style="color: var(--text-muted); font-size: 0.75rem;">(Solo debes guardarlo una vez)</small>
        </div>

        <button id="sendWhatsAppBtn" class="btn btn-whatsapp">
          <i class="ri-whatsapp-line"></i> Enviar Pedido por WhatsApp
        </button>
      </div>
    </div>
  </div>

  <!-- LOGICA JAVASCRIPT -->
  <script>
    // CATEGORÍAS SOLICITADAS
    const CATEGORIES = [
      "Todos",
      "Wax Melts",
      "Pebeteros",
      "Placas Aromáticas",
      "Bouquets",
      "Aromas",
      "Formas"
    ];

    // CATALOGO INICIAL DE MUESTRA
    const DEFAULT_PRODUCTS = [
      {
        id: "1",
        name: "Wax Melt Vainilla Caramel",
        category: "Wax Melts",
        price: 12000,
        description: "Pastillas aromáticas de cera de soya con delicadas notas dulces de vainilla y caramelo tostado.",
        image: "https://images.unsplash.com/photo-1603006905003-be475563bc59?auto=format&fit=crop&w=600&q=80"
      },
      {
        id: "2",
        name: "Pebetero Cerámica Beige Minimal",
        category: "Pebeteros",
        price: 35000,
        description: "Quemador artesanal en cerámica acabado mate beige suave, ideal para derretir tus melts con velas tea-light.",
        image: "https://images.unsplash.com/photo-1547887537-6158d64c35b3?auto=format&fit=crop&w=600&q=80"
      },
      {
        id: "3",
        name: "Placa Aromática Lavanda Real",
        category: "Placas Aromáticas",
        price: 18000,
        description: "Placa de cera decorada con flores botánicas secas para perfumar clósets o cajones.",
        image: "https://images.unsplash.com/photo-1508746829417-e6f548d8d6ed?auto=format&fit=crop&w=600&q=80"
      },
      {
        id: "4",
        name: "Bouquet Aromático Flores Silvestres",
        category: "Bouquets",
        price: 28000,
        description: "Arreglo botánico seco perfumado con esencias naturales para decorar y ambientar.",
        image: "https://images.unsplash.com/photo-1563241527-3004b7be0ffd?auto=format&fit=crop&w=600&q=80"
      },
      {
        id: "5",
        name: "Esencia de Canela y Manzana",
        category: "Aromas",
        price: 15000,
        description: "Gotero de 15ml de aroma concentrado cálido y especiado.",
        image: "https://images.unsplash.com/photo-1608571423902-eed4a5ad8108?auto=format&fit=crop&w=600&q=80"
      },
      {
        id: "6",
        name: "Wax Melt Figuras Corazones",
        category: "Formas",
        price: 14000,
        description: "Set de figuras en forma de corazón con fragancia a algodón de azúcar.",
        image: "https://images.unsplash.com/photo-1572635196237-14b3f281503f?auto=format&fit=crop&w=600&q=80"
      }
    ];

    // ESTADO DE LA APLICACIÓN
    let products = JSON.parse(localStorage.getItem('bia_products')) || DEFAULT_PRODUCTS;
    let cart = JSON.parse(localStorage.getItem('bia_cart')) || [];
    let currentCategory = "Todos";
    let searchQuery = "";
    let isAdmin = false;
    let imageBase64 = "";

    // ELEMENTOS DOM
    const productsGrid = document.getElementById('productsGrid');
    const categoryTabs = document.getElementById('categoryTabs');
    const searchInput = document.getElementById('searchInput');
    const toggleAdminBtn = document.getElementById('toggleAdminBtn');
    const adminBar = document.getElementById('adminBar');
    const productModal = document.getElementById('productModal');
    const productForm = document.getElementById('productForm');
    const imagePreview = document.getElementById('imagePreview');
    const productImageFile = document.getElementById('productImageFile');
    const productImageUrl = document.getElementById('productImageUrl');
    const cartModal = document.getElementById('cartModal');
    const cartBadge = document.getElementById('cartBadge');

    // INICIALIZACIÓN
    function init() {
      renderCategories();
      renderProducts();
      updateCartBadge();
      setupEventListeners();
    }

    // RENDERIZAR CHIPS DE CATEGORÍA
    function renderCategories() {
      categoryTabs.innerHTML = CATEGORIES.map(cat => `
        <div class="cat-chip ${cat === currentCategory ? 'active' : ''}" data-category="${cat}">
          ${cat}
        </div>
      `).join('');

      document.querySelectorAll('.cat-chip').forEach(chip => {
        chip.addEventListener('click', () => {
          currentCategory = chip.dataset.category;
          renderCategories();
          renderProducts();
        });
      });
    }

    // RENDERIZAR PRODUCTOS
    function renderProducts() {
      const filtered = products.filter(p => {
        const matchesCat = currentCategory === "Todos" || p.category === currentCategory;
        const matchesSearch = p.name.toLowerCase().includes(searchQuery.toLowerCase()) || 
                              (p.description && p.description.toLowerCase().includes(searchQuery.toLowerCase()));
        return matchesCat && matchesSearch;
      });

      if (filtered.length === 0) {
        productsGrid.innerHTML = `
          <div class="empty-state">
            <i class="ri-search-eye-line"></i>
            <p>No encontramos productos en esta categoría.</p>
          </div>
        `;
        return;
      }

      productsGrid.innerHTML = filtered.map(product => `
        <div class="product-card">
          ${isAdmin ? `
            <div class="admin-card-actions">
              <button class="btn-card-action edit" onclick="editProduct('${product.id}')" title="Editar">
                <i class="ri-pencil-line"></i>
              </button>
              <button class="btn-card-action delete" onclick="deleteProduct('${product.id}')" title="Eliminar">
                <i class="ri-delete-bin-line"></i>
              </button>
            </div>
          ` : ''}
          <div class="product-img-wrap">
            <span class="category-badge">${product.category}</span>
            <img class="product-img" src="${product.image || 'https://via.placeholder.com/300?text=BIA+Wax+Melts'}" alt="${product.name}" loading="lazy">
          </div>
          <div class="product-info">
            <h3 class="product-title">${product.name}</h3>
            <p class="product-desc">${product.description || ''}</p>
            <div class="product-footer">
              <span class="product-price">$${Number(product.price).toLocaleString('es-CO')}</span>
              <button class="btn-add" onclick="addToCart('${product.id}')" title="Agregar al pedido">
                <i class="ri-add-line"></i>
              </button>
            </div>
          </div>
        </div>
      `).join('');
    }

    // EVENTOS Y NAVEGACIÓN
    function setupEventListeners() {
      // Buscar
      searchInput.addEventListener('input', (e) => {
        searchQuery = e.target.value;
        renderProducts();
      });

      // Alternar Modo Admin
      toggleAdminBtn.addEventListener('click', () => {
        isAdmin = !isAdmin;
        toggleAdminBtn.classList.toggle('active', isAdmin);
        adminBar.classList.toggle('show', isAdmin);
        renderProducts();
      });

      // Abrir modal agregar producto
      document.getElementById('addProductBtn').addEventListener('click', () => {
        openProductModal();
      });

      // Cerrar modales
      document.querySelectorAll('.closeProductModal').forEach(btn => {
        btn.addEventListener('click', () => productModal.classList.remove('active'));
      });
      document.getElementById('closeCartModal').addEventListener('click', () => {
        cartModal.classList.remove('active');
      });

      // Vista previa de imagen subida desde archivo
      productImageFile.addEventListener('change', (e) => {
        const file = e.target.files[0];
        if (file) {
          const reader = new FileReader();
          reader.onload = function(evt) {
            imageBase64 = evt.target.result;
            imagePreview.innerHTML = `<img src="${imageBase64}">`;
            productImageUrl.value = '';
          };
          reader.readAsDataURL(file);
        }
      });

      // Vista previa de imagen desde URL
      productImageUrl.addEventListener('input', (e) => {
        if (e.target.value) {
          imageBase64 = e.target.value;
          imagePreview.innerHTML = `<img src="${imageBase64}">`;
          productImageFile.value = '';
        }
      });

      // Guardar Producto (Crear / Editar)
      productForm.addEventListener('submit', (e) => {
        e.preventDefault();
        const id = document.getElementById('productId').value;
        const name = document.getElementById('productName').value;
        const category = document.getElementById('productCategory').value;
        const price = parseFloat(document.getElementById('productPrice').value);
        const description = document.getElementById('productDescription').value;

        const newProduct = {
          id: id || Date.now().toString(),
          name,
          category,
          price,
          description,
          image: imageBase64 || 'https://via.placeholder.com/300?text=BIA'
        };

        if (id) {
          const index = products.findIndex(p => p.id === id);
          products[index] = newProduct;
        } else {
          products.unshift(newProduct);
        }

        saveProducts();
        renderProducts();
        productModal.classList.remove('active');
      });

      // Carrito
      document.getElementById('openCartBtn').addEventListener('click', openCart);
      document.getElementById('sendWhatsAppBtn').addEventListener('click', sendWhatsAppOrder);

      // Exportar / Importar JSON
      document.getElementById('exportBtn').addEventListener('click', exportData);
      document.getElementById('importBtn').addEventListener('click', () => document.getElementById('importFileInput').click());
      document.getElementById('importFileInput').addEventListener('change', importData);
    }

    // MODAL DE PRODUCTO
    function openProductModal(product = null) {
      productForm.reset();
      imageBase64 = "";
      
      if (product) {
        document.getElementById('modalTitle').textContent = "Editar Producto";
        document.getElementById('productId').value = product.id;
        document.getElementById('productName').value = product.name;
        document.getElementById('productCategory').value = product.category;
        document.getElementById('productPrice').value = product.price;
        document.getElementById('productDescription').value = product.description || '';
        imageBase64 = product.image || '';
        imagePreview.innerHTML = product.image ? `<img src="${product.image}">` : '<span style="font-size: 0.8rem; color: var(--text-muted);">Sin imagen</span>';
      } else {
        document.getElementById('modalTitle').textContent = "Agregar Producto";
        document.getElementById('productId').value = "";
        imagePreview.innerHTML = '<span style="font-size: 0.8rem; color: var(--text-muted);">Vista previa de imagen</span>';
      }
      
      productModal.classList.add('active');
    }

    // EDITAR / ELIMINAR
    window.editProduct = function(id) {
      const prod = products.find(p => p.id === id);
      if (prod) openProductModal(prod);
    };

    window.deleteProduct = function(id) {
      if (confirm('¿Estás seguro de que deseas eliminar este producto?')) {
        products = products.filter(p => p.id !== id);
        saveProducts();
        renderProducts();
      }
    };

    function saveProducts() {
      localStorage.setItem('bia_products', JSON.stringify(products));
    }

    // CARRITO Y WHATSAPP
    window.addToCart = function(id) {
      const prod = products.find(p => p.id === id);
      if (!prod) return;

      const existing = cart.find(item => item.id === id);
      if (existing) {
        existing.qty++;
      } else {
        cart.push({ ...prod, qty: 1 });
      }
      saveCart();
      updateCartBadge();
    };

    function saveCart() {
      localStorage.setItem('bia_cart', JSON.stringify(cart));
    }

    function updateCartBadge() {
      const totalCount = cart.reduce((acc, i) => acc + i.qty, 0);
      cartBadge.textContent = totalCount;
    }

    function openCart() {
      renderCartItems();
      cartModal.classList.add('active');
    }

    function renderCartItems() {
      const container = document.getElementById('cartItemsContainer');
      const totalEl = document.getElementById('cartTotal');

      if (cart.length === 0) {
        container.innerHTML = '<p style="text-align:center; color: var(--text-muted); padding: 2rem 0;">Tu pedido está vacío.</p>';
        totalEl.textContent = '$0';
        return;
      }

      let total = 0;
      container.innerHTML = cart.map(item => {
        const itemTotal = item.price * item.qty;
        total += itemTotal;
        return `
          <div class="cart-item">
            <img src="${item.image}" class="cart-item-img" alt="${item.name}">
            <div class="cart-item-details">
              <div class="cart-item-title">${item.name}</div>
              <div class="cart-item-price">$${Number(item.price).toLocaleString('es-CO')} c/u</div>
            </div>
            <div class="cart-item-qty">
              <button class="btn-qty" onclick="changeQty('${item.id}', -1)">-</button>
              <span>${item.qty}</span>
              <button class="btn-qty" onclick="changeQty('${item.id}', 1)">+</button>
            </div>
          </div>
        `;
      }).join('');

      totalEl.textContent = `$${Number(total).toLocaleString('es-CO')}`;
    }

    window.changeQty = function(id, delta) {
      const item = cart.find(i => i.id === id);
      if (item) {
        item.qty += delta;
        if (item.qty <= 0) {
          cart = cart.filter(i => i.id !== id);
        }
        saveCart();
        updateCartBadge();
        renderCartItems();
      }
    };

    function sendWhatsAppOrder() {
      if (cart.length === 0) {
        alert('Tu pedido está vacío');
        return;
      }

      const phone = document.getElementById('whatsappNumber').value.replace(/[^0-9]/g, '');
      if (!phone) {
        alert('Ingresa un número de WhatsApp válido.');
        return;
      }

      let text = "✨ *NUEVO PEDIDO - BIA WAX MELTS* ✨\n\n";
      let total = 0;

      cart.forEach((item, index) => {
        const subtotal = item.price * item.qty;
        total += subtotal;
        text += `${index + 1}. *${item.name}* (x${item.qty}) - $${Number(subtotal).toLocaleString('es-CO')}\n`;
      });

      text += `\n*TOTAL ESTIMADO:* $${Number(total).toLocaleString('es-CO')}\n\n`;
      text += "¡Hola! Quisiera confirmar este pedido.";

      const url = `https://wa.me/${phone}?text=${encodeURIComponent(text)}`;
      window.open(url, '_blank');
    }

    // EXPORTAR E IMPORTAR DATOS
    function exportData() {
      const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(products, null, 2));
      const dlAnchorElem = document.createElement('a');
      dlAnchorElem.setAttribute("href", dataStr);
      dlAnchorElem.setAttribute("download", `catalogo_bia_${new Date().toISOString().slice(0,10)}.json`);
      dlAnchorElem.click();
    }

    function importData(e) {
      const file = e.target.files[0];
      if (!file) return;

      const reader = new FileReader();
      reader.onload = function(evt) {
        try {
          const imported = JSON.parse(evt.target.result);
          if (Array.isArray(imported)) {
            products = imported;
            saveProducts();
            renderProducts();
            alert('Catálogo importado con éxito.');
          }
        } catch (err) {
          alert('El archivo no es válido.');
        }
      };
      reader.readAsText(file);
    }

    // INICIAR APLICACIÓN
    init();
  </script>
</body>
</html>
```