<!DOCTYPE html>
<html lang="bn">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Flipkart BD - Online Shopping Site for Mobiles, Electronics, Furniture & More</title>
  <link rel="icon" type="image/svg+xml" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><rect width='100' height='100' rx='22' fill='%232874f0'/><path d='M35 28h32l-4 14H45l-2 10h18l-3 13H40l-4 17H22L35 28z' fill='%23ffe500'/><text x='56' y='83' font-family='Arial' font-weight='900' font-size='18' fill='%23ffffff'>BD</text></svg>">
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Roboto, Arial, sans-serif; }
    body { background: #f1f3f6; color: #212121; padding-bottom: 70px; }

    /* Navbar */
    .navbar { background: #2874f0; color: white; padding: 10px 12px; position: sticky; top: 0; z-index: 100; box-shadow: 0 2px 6px rgba(0,0,0,0.18); }
    .nav-top { display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px; gap: 6px; }
    .brand { display: flex; align-items: center; gap: 7px; cursor: pointer; }
    .app-icon { width: 32px; height: 32px; background: #ffe500; border-radius: 8px; display: flex; align-items: center; justify-content: center; font-weight: 900; color: #2874f0; font-size: 20px; font-style: italic; box-shadow: 0 2px 4px rgba(0,0,0,0.25); }
    .brand-text { display: flex; flex-direction: column; line-height: 1.05; }
    .brand-title { font-size: 17px; font-weight: 800; font-style: italic; }
    .brand-title span { color: #ffe500; }
    .brand-sub { font-size: 9.5px; color: #ffe500; font-style: italic; font-weight: 600; }
    .nav-actions { display: flex; gap: 6px; align-items: center; }
    .nav-btn { background: none; border: none; color: white; font-size: 12px; font-weight: 600; cursor: pointer; position: relative; }
    .sell-pill { background: #ffe500; color: #212121; padding: 4px 8px; border-radius: 3px; font-weight: 800; font-size: 11px; }
    .login-pill { background: white; color: #2874f0; padding: 4px 8px; border-radius: 3px; font-weight: 700; font-size: 11px; }
    .coin-pill { background: rgba(0,0,0,0.22); color: #ffe500; padding: 3px 6px; border-radius: 12px; font-size: 10.5px; font-weight: 700; }
    .badge { position: absolute; top: -6px; right: -7px; background: #ff6161; color: white; font-size: 9px; padding: 1px 5px; border-radius: 10px; font-weight: bold; }
    .search-box { width: 100%; background: white; border-radius: 4px; display: flex; align-items: center; padding: 7px 10px; }
    .search-box input { border: none; outline: none; width: 100%; font-size: 13px; margin-left: 7px; }

    /* Location Bar */
    .loc-bar { background: #1c5dc9; color: white; padding: 6px 12px; font-size: 11.5px; display: flex; justify-content: space-between; align-items: center; cursor: pointer; }

    /* Categories */
    .categories { display: flex; overflow-x: auto; background: white; padding: 10px 8px; gap: 15px; border-bottom: 1px solid #e0e0e0; }
    .categories::-webkit-scrollbar { display: none; }
    .cat-item { display: flex; flex-direction: column; align-items: center; min-width: 58px; font-size: 11px; font-weight: 600; color: #333; cursor: pointer; }
    .cat-icon { width: 42px; height: 42px; background: #f0f5ff; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 20px; margin-bottom: 4px; border: 1px solid #dce8ff; }

    /* Slider Banner */
    .banner-wrap { margin: 10px; border-radius: 8px; overflow: hidden; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
    .banner-slide { background: linear-gradient(135deg, #2874f0, #133b82); color: white; padding: 15px; display: flex; justify-content: space-between; align-items: center; min-height: 105px; }
    .banner-tag { background: #ffe500; color: #212121; font-size: 10px; font-weight: 800; padding: 2px 7px; border-radius: 3px; display: inline-block; margin-bottom: 5px; }
    .banner-slide h2 { font-size: 16px; margin-bottom: 3px; }
    .banner-slide p { font-size: 11.5px; opacity: 0.92; }
    .timer-box { background: rgba(0,0,0,0.3); border: 1px dashed #ffe500; padding: 6px 8px; border-radius: 5px; text-align: center; font-size: 11px; color: #ffe500; font-weight: 700; min-width: 86px; }

    /* Filter & Sort Bar */
    .filter-bar { background: white; padding: 8px 12px; display: flex; justify-content: space-between; align-items: center; border-top: 1px solid #eee; border-bottom: 1px solid #eee; }
    .filter-bar span { font-size: 13px; font-weight: 700; }
    .sort-select { border: 1px solid #ccc; border-radius: 4px; padding: 4px 8px; font-size: 12px; background: #fafafa; }

    /* Product Grid */
    .grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 8px; padding: 8px; }
    .card { background: white; border-radius: 4px; padding: 10px; display: flex; flex-direction: column; justify-content: space-between; box-shadow: 0 1px 3px rgba(0,0,0,0.08); position: relative; }
    .wish-btn { position: absolute; top: 8px; right: 8px; background: white; border: 1px solid #eee; width: 26px; height: 26px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 13px; cursor: pointer; z-index: 5; box-shadow: 0 1px 3px rgba(0,0,0,0.1); }
    .p-img { height: 120px; background: #f8f9fa; border-radius: 4px; display: flex; align-items: center; justify-content: center; font-size: 48px; margin-bottom: 8px; position: relative; cursor: pointer; overflow: hidden; }
    .p-img img, .p-img video { width: 100%; height: 100%; object-fit: cover; }
    .vid-pill { position: absolute; bottom: 5px; right: 5px; background: rgba(0,0,0,0.72); color: #ffe500; font-size: 9.5px; font-weight: 700; padding: 2px 5px; border-radius: 3px; }
    .discount-pill { position: absolute; top: 5px; left: 5px; background: #388e3c; color: white; font-size: 10px; font-weight: bold; padding: 2px 5px; border-radius: 2px; z-index: 2; }
    .assured-badge { font-size: 10px; font-weight: 800; color: #2874f0; font-style: italic; margin-bottom: 2px; }
    .seller-tag { font-size: 10px; color: #666; margin-bottom: 3px; }
    .p-title { font-size: 13px; font-weight: 600; margin-bottom: 4px; line-height: 1.3; cursor: pointer; }
    .rating-row { display: flex; align-items: center; gap: 5px; margin-bottom: 5px; }
    .rating-badge { background: #388e3c; color: white; font-size: 11px; font-weight: bold; padding: 1px 5px; border-radius: 3px; }
    .rating-count { font-size: 11px; color: #878787; }
    .price-row { display: flex; align-items: baseline; gap: 6px; margin-bottom: 4px; }
    .price { font-size: 15px; font-weight: 700; color: #212121; }
    .old-price { font-size: 11px; color: #878787; text-decoration: line-through; }
    .replace-tag { font-size: 10px; color: #2874f0; background: #eef4ff; padding: 2px 5px; border-radius: 3px; margin-bottom: 6px; display: inline-block; font-weight: 600; }
    .btn-group { display: flex; gap: 5px; }
    .btn-cart { flex: 1; background: #ff9f00; color: white; border: none; padding: 7px 4px; border-radius: 3px; font-size: 11px; font-weight: 700; cursor: pointer; }
    .btn-buy { flex: 1; background: #fb641b; color: white; border: none; padding: 7px 4px; border-radius: 3px; font-size: 11px; font-weight: 700; cursor: pointer; }
    .seller-manage-row { display: flex; gap: 5px; margin-top: 6px; }
    .btn-edit { flex: 1; background: #eef4ff; color: #2874f0; border: 1px solid #2874f0; padding: 4px; border-radius: 3px; font-size: 10.5px; font-weight: 700; cursor: pointer; }
    .btn-del { background: #ffebee; color: #c62828; border: 1px solid #ef9a9a; padding: 4px 7px; border-radius: 3px; font-size: 10.5px; font-weight: 700; cursor: pointer; }

    /* Modals */
    .modal { display: none; position: fixed; inset: 0; background: rgba(0,0,0,0.65); z-index: 200; justify-content: center; align-items: flex-end; }
    .modal.active { display: flex; }
    .modal-box { background: white; width: 100%; max-height: 92vh; border-radius: 14px 14px 0 0; padding: 16px; overflow-y: auto; }
    .modal-header { display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid #eee; padding-bottom: 10px; margin-bottom: 12px; }
    .close-btn { background: #eee; border: none; width: 28px; height: 28px; border-radius: 50%; font-weight: bold; cursor: pointer; }

    /* Business Account Banner & Box */
    .biz-banner { background: linear-gradient(135deg, #102a56, #2874f0); color: #ffe500; padding: 14px; border-radius: 8px; margin-bottom: 14px; }
    .biz-card { background: #eef4ff; border: 1px solid #bcd4ff; border-radius: 8px; padding: 12px; margin-bottom: 12px; }
    .biz-badge { display: inline-block; background: #ffe500; color: #102a56; font-size: 10px; font-weight: 800; padding: 2px 7px; border-radius: 3px; margin-bottom: 5px; }

    /* Seller Form & Media Preview */
    .form-label { font-size: 12px; font-weight: 700; color: #333; display: block; margin-bottom: 4px; }
    .form-input { width: 100%; padding: 9px; margin-bottom: 9px; border: 1px solid #ccc; border-radius: 4px; font-size: 13px; background: white; }
    .media-preview-box { background: #f8f9fa; border: 1px dashed #2874f0; border-radius: 6px; padding: 8px; margin-bottom: 10px; text-align: center; }
    .media-preview-box img, .media-preview-box video { max-width: 100%; max-height: 150px; border-radius: 4px; margin-top: 6px; }
    .seller-item-row { display: flex; justify-content: space-between; align-items: center; border: 1px solid #e0e0e0; border-radius: 6px; padding: 8px; margin-bottom: 8px; gap: 8px; }

    /* Product Details Modal (PDP) */
    .pdp-hero { background: #f8f9fa; border-radius: 8px; min-height: 170px; max-height: 240px; display: flex; align-items: center; justify-content: center; font-size: 72px; margin-bottom: 12px; position: relative; overflow: hidden; }
    .pdp-hero img, .pdp-hero video { width: 100%; max-height: 230px; object-fit: contain; }
    .spec-box { background: #f9fafb; border: 1px solid #eee; border-radius: 6px; padding: 10px; margin: 10px 0; font-size: 12px; }
    .review-item { border-bottom: 1px solid #f0f0f0; padding: 8px 0; font-size: 12px; }

    /* Login & OTP */
    .login-banner { background: #2874f0; color: white; padding: 14px; border-radius: 8px; margin-bottom: 14px; }
    .otp-hint { background: #fff8e1; border: 1px solid #ffe082; color: #5d4037; padding: 8px 10px; border-radius: 6px; font-size: 12px; margin-bottom: 10px; display: none; }
    .otp-input { letter-spacing: 6px; font-size: 18px; font-weight: 700; text-align: center; }
    .link-btn { background: none; border: none; color: #2874f0; font-size: 12px; font-weight: 600; cursor: pointer; text-decoration: underline; }
    .profile-box { background: #f0f5ff; border: 1px solid #cce0ff; padding: 14px; border-radius: 8px; text-align: center; }
    .logout-btn { margin-top: 10px; background: #d32f2f; color: white; border: none; padding: 8px 16px; border-radius: 4px; font-size: 12px; font-weight: bold; cursor: pointer; }

    /* Cart & Checkout */
    .cart-item { display: flex; justify-content: space-between; align-items: center; padding: 8px 0; border-bottom: 1px solid #f0f0f0; }
    .coupon-box { display: flex; gap: 6px; margin: 12px 0; }
    .coupon-box input { flex: 1; padding: 8px; border: 1px solid #ccc; border-radius: 4px; font-size: 13px; text-transform: uppercase; }
    .coupon-box button { background: #2874f0; color: white; border: none; padding: 0 14px; border-radius: 4px; font-weight: bold; cursor: pointer; }
    .bill-box { background: #f8f9fa; padding: 10px; border-radius: 6px; font-size: 13px; margin-bottom: 12px; }
    .bill-row { display: flex; justify-content: space-between; margin-bottom: 5px; }
    .bill-total { font-weight: 800; font-size: 15px; border-top: 1px dashed #ccc; padding-top: 6px; margin-top: 4px; }
    .place-order-btn { width: 100%; background: #fb641b; color: white; border: none; padding: 12px; border-radius: 4px; font-size: 15px; font-weight: bold; cursor: pointer; }

    /* Orders & Tracking */
    .order-card { border: 1px solid #e0e0e0; border-radius: 6px; padding: 10px; margin-bottom: 10px; }
    .order-status { font-size: 11px; font-weight: bold; color: #388e3c; background: #e8f5e9; padding: 2px 6px; border-radius: 3px; }
    .track-steps { display: flex; justify-content: space-between; margin: 10px 0; font-size: 10px; color: #388e3c; font-weight: 700; background: #f4fbf4; padding: 6px; border-radius: 4px; }
    .replace-btn { margin-top: 6px; background: white; border: 1px solid #2874f0; color: #2874f0; padding: 5px 10px; border-radius: 4px; font-size: 12px; font-weight: 600; cursor: pointer; }

    /* Helpline */
    .helpline-card { background: #f0f5ff; border: 1px solid #cce0ff; border-radius: 8px; padding: 12px; margin-bottom: 12px; }
    .helpline-num { font-size: 16px; font-weight: 800; color: #2874f0; margin: 6px 0; }
    .call-btn { display: inline-block; background: #388e3c; color: white; text-decoration: none; padding: 7px 14px; border-radius: 4px; font-size: 12px; font-weight: bold; margin-right: 6px; }
    .copy-btn { background: #2874f0; color: white; border: none; padding: 7px 12px; border-radius: 4px; font-size: 12px; font-weight: bold; cursor: pointer; }
    .ticket-item { background: #fafafa; border-left: 3px solid #2874f0; padding: 8px; margin-bottom: 8px; font-size: 12px; border-radius: 4px; }

    /* Bottom Nav */
    .bottom-nav { position: fixed; bottom: 0; left: 0; right: 0; background: white; border-top: 1px solid #ddd; display: flex; justify-content: space-around; padding: 7px 0; z-index: 90; }
    .b-item { display: flex; flex-direction: column; align-items: center; font-size: 10.5px; color: #555; cursor: pointer; font-weight: 600; }
    .b-item.active { color: #2874f0; }
  </style>
</head>
<body>

  <!-- Top Navbar -->
  <div class="navbar">
    <div class="nav-top">
      <div class="brand" onclick="filterCat('All')">
        <div class="app-icon">f</div>
        <div class="brand-text">
          <div class="brand-title">Flipkart <span>BD</span></div>
          <div class="brand-sub">Explore Plus ✦</div>
        </div>
      </div>
      <div class="nav-actions">
        <button class="sell-pill" id="headerBizBtn" onclick="openBusinessGateway()">🏢 Business</button>
        <span class="coin-pill">🪙 <span id="coinCount">50</span></span>
        <button class="nav-btn login-pill" id="headerLoginBtn" onclick="openModal('loginModal')">🔐 Login</button>
        <button class="nav-btn" onclick="openModal('wishlistModal')">❤️ <span class="badge" id="wishCount">0</span></button>
        <button class="nav-btn" onclick="openModal('cartModal')">🛒 <span class="badge" id="cartCount">0</span></button>
      </div>
    </div>
    <div class="search-box">
      <span>🔍</span>
      <input type="text" id="searchInput" onkeyup="filterProducts()" placeholder="Flipkart BD-তে মোবাইল, ফ্যাশন, গ্যাজেট খুঁজুন...">
    </div>
  </div>

  <!-- Delivery Location Bar -->
  <div class="loc-bar" onclick="changeLocation()">
    <span>📍 ডেলিভারি লোকেশন: <strong id="userLocation">Dhaka - 1200</strong></span>
    <span style="text-decoration:underline;">পরিবর্তন করুন ▾</span>
  </div>

  <!-- Categories -->
  <div class="categories">
    <div class="cat-item" onclick="filterCat('All')"><div class="cat-icon">🏪</div>All</div>
    <div class="cat-item" onclick="filterCat('Mobile')"><div class="cat-icon">📱</div>Mobiles</div>
    <div class="cat-item" onclick="filterCat('Fashion')"><div class="cat-icon">👕</div>Fashion</div>
    <div class="cat-item" onclick="filterCat('Electronics')"><div class="cat-icon">🎧</div>Electronics</div>
    <div class="cat-item" onclick="filterCat('Watch')"><div class="cat-icon">⌚</div>Watches</div>
    <div class="cat-item" onclick="filterCat('Home')"><div class="cat-icon">🏠</div>Home</div>
  </div>

  <!-- Rotating Offer Banner + Live Flash Timer -->
  <div class="banner-wrap">
    <div class="banner-slide">
      <div>
        <span class="banner-tag" id="bannerTag">BIG BANGLADESH SALE</span>
        <h2 id="bannerTitle">সকল পণ্যে বিশাল ছাড়!</h2>
        <p id="bannerSub">কুপন: BD100 | FLIP500 | SUPER50</p>
      </div>
      <div class="timer-box">
        <div>ENDS IN</div>
        <div id="flashTimer" style="font-size:13px; color:white; margin-top:2px;">05:59:59</div>
      </div>
    </div>
  </div>

  <!-- Sort & Filter Bar -->
  <div class="filter-bar">
    <span id="gridHeading">সেরা ডিলসমূহ (Best Deals)</span>
    <select class="sort-select" id="sortSelect" onchange="sortProducts()">
      <option value="default">Sort: Popularity</option>
      <option value="low">Price: Low to High</option>
      <option value="high">Price: High to Low</option>
      <option value="rating">Top Rated ★</option>
    </select>
  </div>

  <!-- Products Grid -->
  <div class="grid" id="productGrid"></div>

  <!-- Dedicated Business Account Login & Registration Modal -->
  <div class="modal" id="bizLoginModal">
    <div class="modal-box">
      <div class="modal-header">
        <h3>🏢 Business Account Login</h3>
        <button class="close-btn" onclick="closeModal('bizLoginModal')">✕</button>
      </div>

      <div id="bizLoggedOutArea">
        <div class="biz-banner">
          <span class="biz-badge">FLIPKART BD SELLER PORTAL</span>
          <h4 style="font-size:15px; color:white; margin-bottom:4px;">আলাদা বিজনেস অ্যাকাউন্টে লগইন করুন</h4>
          <p style="font-size:11.5px; color:#dce8ff;">শুধুমাত্র ভেরিফায়েড বিজনেস/সেলার অ্যাকাউন্ট দিয়ে ছবি-ভিডিওসহ প্রোডাক্ট পোস্ট ও এডিট করা যাবে।</p>
        </div>

        <div id="bizStepDetails">
          <label class="form-label">Business / Shop Name *</label>
          <input type="text" id="bizShopName" class="form-input" placeholder="যেমন: Habib Enterprise BD">

          <label class="form-label">Trade License / Business Reg No (ঐচ্ছিক)</label>
          <input type="text" id="bizLicense" class="form-input" placeholder="যেমন: TRAD/DHK/12345">

          <label class="form-label">Business Mobile Number *</label>
          <input type="tel" id="bizPhone" class="form-input" maxlength="11" placeholder="017XXXXXXXX">

          <button class="place-order-btn" style="background:#102a56;" onclick="sendBizOTP()">Business OTP পাঠান</button>
        </div>

        <div id="bizStepOTP" style="display:none;">
          <div class="otp-hint" id="bizDemoOtpBox"></div>
          <label class="form-label">৪ ডিজিটের Business OTP লিখুন</label>
          <input type="tel" id="bizOtpInput" class="form-input otp-input" maxlength="4" placeholder="• • • •">
          <button class="place-order-btn" onclick="verifyBizOTP()">Verify & Open Seller Studio</button>
          <div style="display:flex; justify-content:space-between; margin-top:10px;">
            <button class="link-btn" onclick="resetBizLoginSteps()">বিজনেস তথ্য পরিবর্তন করুন</button>
            <button class="link-btn" onclick="sendBizOTP()">Resend OTP</button>
          </div>
        </div>
      </div>

      <div id="bizActiveArea" class="biz-card" style="display:none;">
        <span class="biz-badge">VERIFIED BUSINESS ACCOUNT</span>
        <h4 style="font-size:15px; margin-bottom:4px;" id="activeBizName"></h4>
        <div style="font-size:12px; color:#333;" id="activeBizPhone"></div>
        <div style="font-size:11.5px; color:#555; margin-top:2px;" id="activeBizLicense"></div>
        <div style="display:flex; gap:8px; margin-top:12px;">
          <button class="place-order-btn" style="background:#2874f0; padding:9px; font-size:13px;" onclick="closeModal('bizLoginModal'); openSellerModal();">🛍️ Seller Studio খুলুন</button>
          <button class="logout-btn" style="margin:0;" onclick="logoutBusiness()">Biz Logout</button>
        </div>
      </div>
    </div>
  </div>

  <!-- Seller Post & Edit Product Modal -->
  <div class="modal" id="sellerModal">
    <div class="modal-box">
      <div class="modal-header">
     
