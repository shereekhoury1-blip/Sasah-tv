# Sasah-tv
https://username.github.io/shasha-tv
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SHASHA TV - الرئيسية</title>
    <link rel="stylesheet" href="style.css">
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>
<body>

<!-- ===== شاشة تسجيل الدخول ===== -->
<div id="loginScreen" class="login-screen">
    <div class="login-box">
        <div class="logo">
            <i class="fas fa-tv"></i>
            <h1>SHASHA TV</h1>
        </div>
        <p class="subtitle">أدخل كود الدخول للمتابعة</p>
        <form id="loginForm">
            <div class="input-group">
                <i class="fas fa-key"></i>
                <input type="text" id="accessCode" placeholder="كود الدخول" maxlength="8" required>
            </div>
            <button type="submit" class="btn-login">
                <i class="fas fa-sign-in-alt"></i> دخول
            </button>
        </form>
        <div id="loginError" class="error-msg"></div>
        <p class="hint">كود تجريبي: <span>1234</span></p>
    </div>
</div>

<!-- ===== التطبيق الرئيسي ===== -->
<div id="mainApp" class="main-app hidden">

    <!-- القائمة الجانبية -->
    <aside class="sidebar">
        <div class="sidebar-logo">
            <i class="fas fa-tv"></i>
            <span>SHASHA TV</span>
        </div>
        <nav class="sidebar-nav">
            <a href="#" class="nav-item active" data-section="home">
                <i class="fas fa-home"></i> الرئيسية
            </a>
            <a href="#" class="nav-item" data-section="movies">
                <i class="fas fa-film"></i> أفلام
            </a>
            <a href="#" class="nav-item" data-section="series">
                <i class="fas fa-video"></i> مسلسلات
            </a>
            <a href="#" class="nav-item" data-section="channels">
                <i class="fas fa-broadcast-tower"></i> قنوات
            </a>
            <a href="#" class="nav-item" data-section="settings">
                <i class="fas fa-cog"></i> الإعدادات
            </a>
        </nav>
        <div class="sidebar-footer">
            <button id="logoutBtn" class="logout-btn">
                <i class="fas fa-sign-out-alt"></i> خروج
            </button>
        </div>
    </aside>

    <!-- المحتوى الرئيسي -->
    <main class="content">
        
        <!-- قسم الرئيسية -->
        <section id="home" class="section active">
            <div class="hero">
                <div class="hero-content">
                    <span class="badge">جديد</span>
                    <h2>مرحباً بك في SHASHA TV</h2>
                    <p>استمتع بمشاهدة أفضل الأفلام والمسلسلات والقنوات</p>
                    <button class="btn-watch"><i class="fas fa-play"></i> شاهد الآن</button>
                </div>
            </div>
            <h3 class="section-title"><i class="fas fa-fire"></i> الأكثر مشاهدة</h3>
            <div class="cards-grid" id="trendingGrid"></div>
            <h3 class="section-title"><i class="fas fa-star"></i> مضاف حديثاً</h3>
            <div class="cards-grid" id="recentGrid"></div>
        </section>

        <!-- قسم الأفلام -->
        <section id="movies" class="section">
            <h2 class="page-title"><i class="fas fa-film"></i> الأفلام</h2>
            <div class="search-bar">
                <i class="fas fa-search"></i>
                <input type="text" id="movieSearch" placeholder="ابحث عن فيلم...">
            </div>
            <div class="filter-tags">
                <button class="tag active" data-genre="all">الكل</button>
                <button class="tag" data-genre="action">أكشن</button>
                <button class="tag" data-genre="drama">دراما</button>
                <button class="tag" data-genre="comedy">كوميديا</button>
                <button class="tag" data-genre="horror">رعب</button>
            </div>
            <div class="cards-grid" id="moviesGrid"></div>
        </section>

        <!-- قسم المسلسلات -->
        <section id="series" class="section">
            <h2 class="page-title"><i class="fas fa-video"></i> المسلسلات</h2>
            <div class="search-bar">
                <i class="fas fa-search"></i>
                <input type="text" id="seriesSearch" placeholder="ابحث عن مسلسل...">
            </div>
            <div class="cards-grid" id="seriesGrid"></div>
        </section>

        <!-- قسم القنوات -->
        <section id="channels" class="section">
            <h2 class="page-title"><i class="fas fa-broadcast-tower"></i> القنوات</h2>
            <div class="cards-grid" id="channelsGrid"></div>
        </section>

        <!-- قسم الإعدادات -->
        <section id="settings" class="section">
            <h2 class="page-title"><i class="fas fa-cog"></i> الإعدادات</h2>
            <div class="settings-container">
                <div class="settings-group">
                    <h3><i class="fas fa-user"></i> الحساب</h3>
                    <div class="setting-item">
                        <span>كود الدخول الحالي</span>
                        <span class="setting-value" id="currentCode">1234</span>
                    </div>
                    <div class="setting-item">
                        <span>تغيير كود الدخول</span>
                        <button class="btn-small" onclick="changeCode()">تغيير</button>
                    </div>
                </div>
                <div class="settings-group">
                    <h3><i class="fas fa-palette"></i> المظهر</h3>
                    <div class="setting-item">
                        <span>الوضع الليلي</span>
                        <label class="switch">
                            <input type="checkbox" id="darkMode" checked onchange="toggleDarkMode()">
                            <span class="slider"></span>
                        </label>
                    </div>
                </div>
                <div class="settings-group">
                    <h3><i class="fas fa-play"></i> التشغيل</h3>
                    <div class="setting-item">
                        <span>التشغيل التلقائي</span>
                        <label class="switch">
                            <input type="checkbox" id="autoplay" onchange="toggleAutoplay()">
                            <span class="slider"></span>
                        </label>
                    </div>
                    <div class="setting-item">
                        <span>جودة الفيديو</span>
                        <select class="select-box">
                            <option>تلقائي</option>
                            <option>عالية 1080p</option>
                            <option>متوسطة 720p</option>
                            <option>منخفضة 480p</option>
                        </select>
                    </div>
                </div>
                <div class="settings-group">
                    <h3><i class="fas fa-info-circle"></i> حول</h3>
                    <div class="setting-item">
                        <span>الإصدار</span>
                        <span class="setting-value">1.0.0</span>
                    </div>
                    <div class="setting-item">
                        <span>تواصل معنا</span>
                        <button class="btn-small" onclick="contactUs()">مراسلة</button>
                    </div>
                </div>
            </div>
        </section>

    </main>
</div>

<!-- نافذة المشاهدة -->
<div id="playerModal" class="modal hidden">
    <div class="modal-content">
        <button class="close-modal" onclick="closePlayer()"><i class="fas fa-times"></i></button>
        <div class="player-box">
            <div class="player-placeholder">
                <i class="fas fa-play-circle"></i>
                <p id="playerTitle">اسم المحتوى</p>
            </div>
        </div>
        <div class="player-info">
            <h3 id="playerName"></h3>
            <p id="playerDesc"></p>
        </div>
    </div>
</div>

<script src="script.js"></script>
</body>
</html>
