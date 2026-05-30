<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Amplop Nilai Digital - SMP Negeri 1 Lingga</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css">
    <style>
        /* --- RESET & GLOBAL STYLES --- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: #f0f7ff; /* Biru tipis, super lembut & bersih */
            color: #1e293b;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            min-height: 100vh;
            padding-bottom: 90px; /* Jarak aman agar tidak tertutup bottom navbar */
        }

        /* --- MOBILE CONTAINER (MAX 440px) --- */
        .container-mobile {
            width: 100%;
            max-width: 440px;
            padding: 20px;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        /* --- UI GLASSMORPHISM COMPONENT (MATERIAL 3) --- */
        .m3-glass {
            background: rgba(255, 255, 255, 0.8);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.9);
            border-radius: 24px; /* Sudut melengkung Material 3 tegas */
            padding: 24px;
            box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.04);
        }

        /* --- HEADER BRANDING --- */
        .app-header {
            text-align: center;
            margin-bottom: 10px;
            padding-top: 10px;
        }
        .app-header h1 {
            font-size: 20px;
            font-weight: 800;
            color: #1d4ed8;
            letter-spacing: -0.5px;
        }
        .app-header p {
            font-size: 13px;
            color: #64748b;
            margin-top: 4px;
        }

        /* --- NAVIGASI LAMAN (TAB CONTROL) --- */
        .tab-content {
            display: none;
        }
        .tab-content.active {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        /* --- LAMAN 1: HOME (REKAPITULASI ANONIM) --- */
        .stats-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
            margin-bottom: 8px;
        }
        .stat-box {
            background: rgba(255, 255, 255, 0.5);
            border-radius: 16px;
            padding: 14px;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.6);
        }
        .stat-box span {
            font-size: 12px;
            color: #64748b;
            font-weight: 500;
        }
        .stat-box h3 {
            font-size: 24px;
            font-weight: 700;
            color: #1e3a8a;
            margin-top: 4px;
        }
        .chart-section {
            margin-top: 10px;
        }
        .chart-section h4 {
            font-size: 14px;
            color: #334155;
            margin-bottom: 12px;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .chart-container {
            display: flex;
            flex-direction: column;
            gap: 10px;
            margin-bottom: 20px;
        }
        .chart-row {
            display: flex;
            flex-direction: column;
            gap: 4px;
        }
        .chart-label {
            display: flex;
            justify-content: space-between;
            font-size: 11px;
            font-weight: 500;
            color: #64748b;
        }
        .bar-outer {
            width: 100%;
            height: 10px;
            background: rgba(0, 0, 0, 0.04);
            border-radius: 999px;
            overflow: hidden;
        }
        .bar-inner {
            height: 100%;
            border-radius: 999px;
            transition: width 0.6s ease;
        }
        .bg-baik { background: #10b981; }
        .bg-memadai { background: #3b82f6; }
        .bg-kurang { background: #f43f5e; }

        /* --- LAMAN 2: NILAIKU (PENCARIAN) --- */
        .search-box {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }
        .search-box label {
            font-size: 14px;
            font-weight: 600;
            color: #334155;
        }
        .input-wrapper {
            position: relative;
        }
        .input-wrapper i {
            position: absolute;
            left: 16px;
            top: 50%;
            transform: translateY(-50%);
            color: #94a3b8;
        }
        .input-wrapper input {
            width: 100%;
            height: 48px;
            padding: 0 16px 0 44px;
            border-radius: 16px;
            border: 1px solid #cbd5e1;
            background: rgba(255, 255, 255, 0.9);
            font-size: 15px;
            outline: none;
            transition: all 0.2s;
        }
        .input-wrapper input:focus {
            border-color: #3b82f6;
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.15);
        }
        .btn-search {
            width: 100%;
            height: 48px;
            background: #1d4ed8;
            color: white;
            border: none;
            border-radius: 16px;
            font-size: 15px;
            font-weight: 600;
            cursor: pointer;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            box-shadow: 0 4px 12px rgba(29, 78, 216, 0.2);
            transition: background 0.2s;
        }
        .btn-search:active {
            background: #1e40af;
        }

        /* --- LOADING SPINNER DRAMATIS --- */
        .loading-container {
            display: none;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 30px 0;
            gap: 16px;
        }
        .spinner {
            width: 40px;
            height: 40px;
            border: 4px solid rgba(29, 78, 216, 0.1);
            border-top: 4px solid #1d4ed8;
            border-radius: 50%;
            animation: spin 0.8s linear infinite;
        }
        .pulse-text {
            font-size: 14px;
            color: #1d4ed8;
            font-weight: 600;
            animation: pulse 1.2s ease-in-out infinite;
        }

        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }
        @keyframes pulse { 0%, 100% { opacity: 0.6; } 50% { opacity: 1; } }

        /* --- KARTU HASIL INDIVIDU & VARIASI JUARA --- */
        #result-container {
            display: none;
        }
        .result-card {
            display: flex;
            flex-direction: column;
            gap: 18px;
            position: relative;
            overflow: hidden;
        }

        /* Rank 1 (Juara 1): Hijau Pastel, Shimmer Glow */
        .card-rank-1 {
            background: linear-gradient(135deg, #d1fae5 0%, #a7f3d0 100%) !important;
            border: 2px solid #34d399 !important;
            box-shadow: 0 10px 25px rgba(52, 211, 153, 0.25) !important;
            background-size: 200% 200%;
            animation: shimmer 3s linear infinite;
        }
        /* Rank 2 (Juara 2): Biru Pastel Lembut */
        .card-rank-2 {
            background: linear-gradient(135deg, #dbaefe 0%, #bfdbfe 100%) !important;
            border: 1px solid #93c5fd !important;
        }
        /* Rank 3 (Juara 3): Perunggu / Oranye Pastel Hangat */
        .card-rank-3 {
            background: linear-gradient(135deg, #ffedd5 0%, #fdbb74 100%) !important;
            border: 1px solid #f97316 !important;
        }
        /* Rank 4 Ke Bawah: M3 Glass Standar */
        .card-rank-normal {
            background: rgba(255, 255, 255, 0.85);
        }

        @keyframes shimmer {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Surprise Bounce Effect */
        .bounce-effect {
            animation: surpriseBounce 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275) both;
        }
        @keyframes surpriseBounce {
            0% { transform: scale(0.3); opacity: 0; }
            50% { transform: scale(1.05); }
            70% { transform: scale(0.9); }
            100% { transform: scale(1); opacity: 1; }
        }

        /* Komponen Identitas Kartu */
        .student-profile {
            display: flex;
            align-items: center;
            justify-content: space-between;
            border-bottom: 1px solid rgba(0,0,0,0.06);
            padding-bottom: 12px;
        }
        .profile-info h2 {
            font-size: 16px;
            font-weight: 700;
            color: #0f172a;
        }
        .profile-info p {
            font-size: 12px;
            color: #64748b;
            margin-top: 2px;
        }
        .rank-badge {
            padding: 6px 12px;
            border-radius: 999px;
            font-size: 12px;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        .badge-1 { background: #10b981; color: white; }
        .badge-2 { background: #2563eb; color: white; }
        .badge-3 { background: #ea580c; color: white; }
        .badge-normal { background: #64748b; color: white; }

        /* Tata Letak Nilai Vertikal (Anti-Nabrak di Layar Sempit) */
        .score-rows-container {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        .score-row-item {
            background: rgba(255, 255, 255, 0.4);
            border-radius: 14px;
            padding: 12px 16px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border: 1px solid rgba(255,255,255,0.5);
        }
        .subject-meta {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            gap: 4px;
        }
        .subject-name {
            font-size: 14px;
            font-weight: 600;
            color: #334155;
        }
        .tag-predikat {
            font-size: 10px;
            font-weight: 700;
            padding: 2px 8px;
            border-radius: 6px;
            width: auto;
            text-transform: uppercase;
        }
        .tag-baik { background: #d1fae5; color: #065f46; }
        .tag-memadai { background: #dbeafe; color: #1e40af; }
        .tag-kurang { background: #ffe4e6; color: #991b1b; }
        
        .score-number {
            font-size: 24px;
            font-weight: 800;
            color: #0f172a;
        }

        /* Bagian Kaki Kartu & Info Rata-Rata */
        .card-footer-summary {
            background: rgba(0, 0, 0, 0.03);
            border-radius: 14px;
            padding: 12px;
            text-align: center;
            font-size: 13px;
            font-weight: 600;
            color: #475569;
        }
        .card-footer-summary strong {
            color: #1d4ed8;
            font-size: 15px;
        }

        /* --- KOTAK INFO PENGAMBILAN SKL & RAPOR --- */
        .skl-announcement {
            background: #fff7ed;
            border: 1px dashed #f97316;
            border-radius: 16px;
            padding: 16px;
            margin-top: 4px;
            display: flex;
            flex-direction: column;
            gap: 8px;
        }
        .skl-title {
            font-size: 13px;
            font-weight: 700;
            color: #c2410c;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .skl-details {
            font-size: 12px;
            color: #ea580c;
            line-height: 1.5;
            list-style: none;
        }
        .skl-details li {
            margin-bottom: 4px;
            display: flex;
            align-items: flex-start;
            gap: 6px;
        }
        .skl-details i {
            margin-top: 3px;
            font-size: 10px;
        }

        /* --- FIXED BOTTOM NAVBAR (TINGGI 64px) --- */
        .bottom-navbar {
            position: fixed;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 100%;
            max-width: 440px;
            height: 64px;
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border-top: 1px solid rgba(255, 255, 255, 0.8);
            display: flex;
            justify-content: space-around;
            align-items: center;
            z-index: 999;
        }
        .nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 4px;
            background: none;
            border: none;
            width: 70px;
            height: 100%;
            color: #94a3b8;
            cursor: pointer;
            transition: color 0.2s;
        }
        .nav-item i {
            font-size: 18px;
        }
        .nav-item span {
            font-size: 11px;
            font-weight: 600;
        }
        .nav-item.active {
            color: #1d4ed8;
        }
    </style>
</head>
<body>

    <div class="container-mobile">
        <div class="app-header">
            <h1>SMP NEGERI 1 LINGGA</h1>
            <p>Sistem Pengumuman Ujian Akhir TP 2025/2026</p>
        </div>

        <div id="page-home" class="tab-content">
            <div class="m3-glass">
                <h3 style="font-size:16px; margin-bottom:14px; color:#0f172a;"><i class="fa-solid fa-square-poll-vertical" style="color:#1d4ed8; margin-right:8px;"></i>Ringkasan Nilai Kelas</h3>
                <div class="stats-grid">
                    <div class="stat-box">
                        <span>Rata-Rata MTK</span>
                        <h3 id="avg-mtk">0.00</h3>
                    </div>
                    <div class="stat-box">
                        <span>Rata-Rata B.Indo</span>
                        <h3 id="avg-ind">0.00</h3>
                    </div>
                </div>
            </div>

            <div class="m3-glass chart-section">
                <h4><i class="fa-solid fa-chart-bar" style="color:#10b981;"></i>Distribusi Predikat Matematika</h4>
                <div class="chart-container" id="chart-mtk-container">
                    </div>

                <h4 style="margin-top:10px;"><i class="fa-solid fa-chart-bar" style="color:#3b82f6;"></i>Distribusi Predikat B. Indonesia</h4>
                <div class="chart-container" id="chart-ind-container">
                    </div>
            </div>
        </div>

        <div id="page-nilaiku" class="tab-content">
            <div class="m3-glass search-box">
                <label for="student-search-input">Masukkan NISN Lengkap Siswa</label>
                <div class="input-wrapper">
                    <i class="fa-solid fa-id-card"></i>
                    <input type="tel" id="student-search-input" placeholder="Ketik 10 Digit NISN Resmi..." autocomplete="off" maxlength="10">
                </div>
                <button class="btn-search" onclick="processSearch()"><i class="fa-solid fa-envelope-open-text"></i>Buka Amplop Nilai</button>
            </div>

            <div class="loading-container" id="loading-box">
                <div class="spinner"></div>
                <span class="pulse-text">Membuka Amplop Dokumen...</span>
            </div>

            <div id="result-container">
                </div>
        </div>
    </div>

    <nav class="bottom-navbar">
        <button class="nav-item" id="nav-home" onclick="switchTab('home')">
            <i class="fa-solid fa-chart-simple"></i>
            <span>Home</span>
        </button>
        <button class="nav-item" id="nav-nilaiku" onclick="switchTab('nilaiku')">
            <i class="fa-solid fa-address-card"></i>
            <span>Nilaiku</span>
        </button>
    </nav>

    <script>
        // DATASET UTAMA: Ekstraksi Data Siswa & NISN dari Dokumen DKHTKA
        // Contoh NISN disimulasikan 10-digit unik berurutan berdasarkan nomor absen untuk keperluan operasional proteksi sistem
        const rawStudentsData = [
            { nisn: "0123456701", name: "ADELIA DWI NURMANSYAH", mtk: 89.60, ind: 89.00 },
            { nisn: "0123456702", name: "ANANDA IBNU FAHREZI", mtk: 78.20, ind: 79.60 },
            { nisn: "0123456703", name: "DAFITRA ARIANSYAH", mtk: 76.60, ind: 76.80 },
            { nisn: "0123456704", name: "DELVRY ANGGARA PANJAITAN", mtk: 83.20, ind: 84.00 },
            { nisn: "0123456705", name: "DYRA ALTHA FUNISYA", mtk: 92.20, ind: 92.20 },
            { nisn: "0123456706", name: "FAQIHA TAZKIATUN NUFUS", mtk: 81.80, ind: 80.20 },
            { nisn: "0123456707", name: "GHASTAN GAUTAMA GINARDA", mtk: 85.00, ind: 92.60 },
            { nisn: "0123456708", name: "JEANTRIKA SAPUTERA", mtk: 79.00, ind: 78.00 },
            { nisn: "0123456709", name: "LIYANA ZAHIRA", mtk: 78.00, ind: 80.80 },
            { nisn: "0123456710", name: "M.BAYU RIZKITULLAH", mtk: 84.60, ind: 82.40 },
            { nisn: "0123456711", name: "MARWA DWI RAMADANI", mtk: 78.80, ind: 86.80 },
            { nisn: "0123456712", name: "MUHAMMAD FADHIL ARDIANSYAH", mtk: 83.20, ind: 81.80 },
            { nisn: "0123456713", name: "MUHAMMAD GIBRAN ASSYAFAR", mtk: 78.00, ind: 82.00 },
            { nisn: "0123456714", name: "MUHAMMAD MUFLIH HIBATULLAH", mtk: 77.80, ind: 76.20 },
            { nisn: "0123456715", name: "NATASYA ZULHAFIFAH", mtk: 82.20, ind: 86.40 },
            { nisn: "0123456716", name: "RAFADIL ANANTA", mtk: 73.00, ind: 75.60 },
            { nisn: "0123456717", name: "RAJA FATHUR ABDILLAH", mtk: 83.80, ind: 82.00 },
            { nisn: "0123456718", name: "RATI JUNILA", mtk: 77.00, ind: 82.40 },
            { nisn: "0123456719", name: "REFAN PINANDO", mtk: 77.60, ind: 76.20 },
            { nisn: "0123456720", name: "RINA RIYANTI", mtk: 86.20, ind: 85.60 },
            { nisn: "0123456721", name: "RISNA ULKA ARYANI", mtk: 81.40, ind: 77.80 },
            { nisn: "0123456722", name: "RIZKA INDRI ADELIASA", mtk: 82.00, ind: 77.40 },
            { nisn: "0123456723", name: "SHERIL GIANDA UTAMI", mtk: 78.00, ind: 77.20 },
            { nisn: "0123456724", name: "SILA ADELIA", mtk: 77.60, ind: 77.80 },
            { nisn: "0123456725", name: "SUKMASARI", mtk: 81.40, ind: 83.60 },
            { nisn: "0123456726", name: "SYARIFAH NAFIA SAFIZ", mtk: 80.80, ind: 90.00 },
            { nisn: "0123456727", name: "VIKY ADITYA SYAPUTRA", mtk: 77.80, ind: 76.20 },
            { nisn: "0123456728", name: "ZALFA MUFIDAH INAYAH", mtk: 85.20, ind: 83.40 },
            { nisn: "0123456729", name: "ΖΑΤΙΑ ΜAYSYA", mtk: 91.60, ind: 87.20 },
            { nisn: "0123456730", name: "ADONIA NAJLA RAISSA", mtk: 81.40, ind: 82.80 },
            { nisn: "0123456731", name: "AIRIN DWI RAMADHANI", mtk: 83.00, ind: 87.40 },
            { nisn: "0123456732", name: "AISH GHAZIYA RAFIFA", mtk: 80.40, ind: 81.60 },
            { nisn: "0123456733", name: "ARYA IMAM RISNANDA", mtk: 78.20, ind: 78.60 },
            { nisn: "0123456734", name: "DEBY SEPTIANI", mtk: 90.20, ind: 88.80 },
            { nisn: "0123456735", name: "DZIKRI HARITH HAZIQ", mtk: 79.60, ind: 80.20 },
            { nisn: "0123456736", name: "GUNAWAN FAUZI", mtk: 76.80, ind: 76.20 },
            { nisn: "0123456737", name: "IBNU SHALIM", mtk: 81.40, ind: 76.80 },
            { nisn: "0123456738", name: "IMAM SYAHIBBULLAH", mtk: 76.20, ind: 77.20 },
            { nisn: "0123456739", name: "IRVAN KURNIA", mtk: 77.80, ind: 79.80 },
            { nisn: "0123456740", name: "ISNAINI", mtk: 80.60, ind: 76.80 },
            { nisn: "0123456741", name: "KAFHA AZRI ILHAMSYAH", mtk: 76.00, ind: 76.60 },
            { nisn: "0123456742", name: "KHASBI NOVALDI", mtk: 74.20, ind: 76.80 },
            { nisn: "0123456743", name: "LIPIANA SUCI RAMARANI", mtk: 87.60, ind: 87.80 },
            { nisn: "0123456744", name: "MECA ADELYA CAHYANI", mtk: 85.80, ind: 93.00 },
            { nisn: "0123456745", name: "MEISYA AWALUN NURHASANAH", mtk: 77.40, ind: 77.40 },
            { nisn: "0123456746", name: "MUHAMMAD ERWAN ZARKA", mtk: 78.00, ind: 79.60 },
            { nisn: "0123456747", name: "NUR RAFNI YASMADI", mtk: 77.60, ind: 77.80 },
            { nisn: "0123456748", name: "QIAN FERDINAND", mtk: 80.20, ind: 77.40 },
            { nisn: "0123456749", name: "RAISA IDADI", mtk: 78.80, ind: 85.20 },
            { nisn: "0123456750", name: "RISKA SARI", mtk: 78.00, ind: 78.00 },
            { nisn: "0123456751", name: "SABRINA EMBUN PERTIWI", mtk: 77.60, ind: 78.60 },
            { nisn: "0123456752", name: "SAPINAH", mtk: 78.80, ind: 81.40 },
            { nisn: "0123456753", name: "SHAZIA ZARA ALISHA", mtk: 79.40, ind: 83.00 },
            { nisn: "0123456754", name: "SUHARAYAH", mtk: 85.00, ind: 79.60 },
            { nisn: "0123456755", name: "SYARIFAH NAJWA SAFIZ", mtk: 79.00, ind: 86.20 },
            { nisn: "0123456756", name: "SYARIFAH ZILFA NATASYA", mtk: 80.40, ind: 84.00 },
            { nisn: "0123456757", name: "SYIFA SYAQIRAH", mtk: 78.40, ind: 81.20 },
            { nisn: "0123456758", name: "VANDERSAR MEICHAEL NAINGGOLAN", mtk: 77.80, ind: 78.00 },
            { nisn: "0123456759", name: "ZAI ISRAKMIDIAH", mtk: 79.40, ind: 80.00 },
            { nisn: "0123456760", name: "ACHAI ANDREAS", mtk: 77.80, ind: 80.40 },
            { nisn: "0123456761", name: "ANGGARA PRATAMA", mtk: 77.40, ind: 76.20 },
            { nisn: "0123456762", name: "ANUGRAH AGUSTI RAMADHANI", mtk: 83.20, ind: 82.60 },
            { nisn: "0123456763", name: "ARFA", mtk: 76.40, ind: 76.20 },
            { nisn: "0123456764", name: "DZAKIYYA NAILA SAKHI", mtk: 86.40, ind: 88.80 },
            { nisn: "0123456765", name: "ERINA NAZIRA", mtk: 80.00, ind: 78.60 },
            { nisn: "0123456766", name: "FAIZ FAYZUL HAQ", mtk: 78.00, ind: 78.40 },
            { nisn: "0123456767", name: "HANY BAZLINDA", mtk: 88.40, ind: 90.00 },
            { nisn: "0123456768", name: "HERISUSANTI", mtk: 88.80, ind: 92.20 },
            { nisn: "0123456769", name: "HESTY YOLANDA SIRABANG", mtk: 73.40, ind: 78.00 },
            { nisn: "0123456770", name: "MAHARANI DEWI", mtk: 86.60, ind: 89.80 },
            { nisn: "0123456771", name: "MEGAWATI", mtk: 79.80, ind: 78.60 },
            { nisn: "0123456772", name: "MULHUDA", mtk: 79.00, ind: 78.60 },
            { nisn: "0123456773", name: "NAZILA MAHARANI", mtk: 78.60, ind: 81.60 },
            { nisn: "0123456774", name: "NAZRIEL ALFARIZQY YUNIAR", mtk: 88.40, ind: 93.20 },
            { nisn: "0123456775", name: "NI'A ROSA", mtk: 78.00, ind: 78.80 },
            { nisn: "0123456776", name: "NOVITA ADHA RIAH", mtk: 79.80, ind: 80.40 },
            { nisn: "0123456777", name: "NOVRIAN SAPUTRA", mtk: 80.20, ind: 77.40 },
            { nisn: "0123456778", name: "RAHMANDA PRATAMA", mtk: 76.40, ind: 76.20 },
            { nisn: "0123456779", name: "RISKY ARDIAN MISKA SACHPUTRA", mtk: 75.80, ind: 76.80 },
            { nisn: "0123456780", name: "RIZKA ALFIA AZ ZAHRA", mtk: 86.00, ind: 90.60 },
            { nisn: "0123456781", name: "SAHRINI RAMADANI", mtk: 76.80, ind: 76.80 },
            { nisn: "0123456782", name: "SILVIA FRANSISKA NATALIA", mtk: 78.80, ind: 77.40 },
            { nisn: "0123456783", name: "SUCI SAFIRA PUTRI", mtk: 87.00, ind: 80.80 },
            { nisn: "0123456784", name: "SYARIFAH IZZATI AQILA", mtk: 86.40, ind: 78.00 },
            { nisn: "0123456785", name: "USMAN", mtk: 75.60, ind: 76.20 },
            { nisn: "0123456786", name: "WINDA AULIA", mtk: 77.20, ind: 78.00 },
            { nisn: "0123456787", name: "ZIFARA OKTIA GISKA", mtk: 83.80, ind: 80.40 },
            { nisn: "0123456788", name: "ZURRIATI FARHANA", mtk: 79.60, ind: 81.00 }
        ];

        let processedStudents = [];
        let classStatistics = { mtk: { avg: 0, baik: 0, memadai: 0, kurang: 0 }, ind: { avg: 0, baik: 0, memadai: 0, kurang: 0 } };

        // FUNGSI UTAMA UNTUK PROSES LOGIKA DATA & URUTAN PERINGKAT
        function initData() {
            let totalMtk = 0, totalInd = 0;
            
            let calculated = rawStudentsData.map(s => {
                let avg = (s.mtk + s.ind) / 2;
                totalMtk += s.mtk;
                totalInd += s.ind;
                return {
                    nisn: s.nisn,
                    name: s.name,
                    mtk: s.mtk,
                    ind: s.ind,
                    combinedAvg: avg
                };
            });

            // Urutkan dari rata-rata tertinggi ke terendah
            calculated.sort((a, b) => b.combinedAvg - a.combinedAvg);
            
            processedStudents = calculated.map((item, idx) => {
                item.rank = idx + 1;
                return item;
            });

            let totalSiswa = processedStudents.length;
            classStatistics.mtk.avg = (totalMtk / totalSiswa).toFixed(2);
            classStatistics.ind.avg = (totalInd / totalSiswa).toFixed(2);

            processedStudents.forEach(s => {
                if(s.mtk >= 85) classStatistics.mtk.baik++;
                else if(s.mtk >= 70) classStatistics.mtk.memadai++;
                else classStatistics.mtk.kurang++;

                if(s.ind >= 85) classStatistics.ind.baik++;
                else if(s.ind >= 70) classStatistics.ind.memadai++;
                else classStatistics.ind.kurang++;
            });

            document.getElementById('avg-mtk').innerText = classStatistics.mtk.avg;
            document.getElementById('avg-ind').innerText = classStatistics.ind.avg;

            renderBarChart('chart-mtk-container', classStatistics.mtk, totalSiswa);
            renderBarChart('chart-ind-container', classStatistics.ind, totalSiswa);
        }

        function getPredikatText(score) {
            if(score >= 85) return { text: "Baik", class: "tag-baik" };
            if(score >= 70) return { text: "Memadai", class: "tag-memadai" };
            return { text: "Kurang", class: "tag-kurang" };
        }

        function renderBarChart(containerId, data, total) {
            const container = document.getElementById(containerId);
            const pBaik = ((data.baik / total) * 100).toFixed(1);
            const pMemadai = ((data.memadai / total) * 100).toFixed(1);
            const pKurang = ((data.kurang / total) * 100).toFixed(1);

            container.innerHTML = `
                <div class="chart-row">
                    <div class="chart-label"><span>Baik (&ge;85)</span><span>${data.baik} Siswa (${pBaik}%)</span></div>
                    <div class="bar-outer"><div class="bar-inner bg-baik" style="width: ${pBaik}%"></div></div>
                </div>
                <div class="chart-row">
                    <div class="chart-label"><span>Memadai (70-84.9)</span><span>${data.memadai} Siswa (${pMemadai}%)</span></div>
                    <div class="bar-outer"><div class="bar-inner bg-memadai" style="width: ${pMemadai}%"></div></div>
                </div>
                <div class="chart-row">
                    <div class="chart-label"><span>Kurang (&lt;70)</span><span>${data.kurang} Siswa (${pKurang}%)</span></div>
                    <div class="bar-outer"><div class="bar-inner bg-kurang" style="width: ${pKurang}%"></div></div>
                </div>
            `;
        }

        function switchTab(tabName) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.remove('active'));
            document.querySelectorAll('.nav-item').forEach(el => el.classList.remove('active'));

            if(tabName === 'home') {
                document.getElementById('page-home').classList.add('active');
                document.getElementById('nav-home').classList.add('active');
            } else {
                document.getElementById('page-nilaiku').classList.add('active');
                document.getElementById('nav-nilaiku').classList.add('active');
            }
        }

        // --- LOGIKA PENCARIAN & VALIDASI NISN (10 DIGIT) ---
        function processSearch() {
            const inputVal = document.getElementById('student-search-input').value.trim();
            const resultContainer = document.getElementById('result-container');
            const loadingBox = document.getElementById('loading-box');

            // Validasi format wajib 10 digit angka
            if (inputVal.length !== 10 || isNaN(inputVal)) {
                alert("Akses Ditolak! Harap masukkan 10 digit NISN resmi Anda dengan benar.");
                return;
            }

            resultContainer.style.display = "none";
            loadingBox.style.display = "flex";

            setTimeout(() => {
                loadingBox.style.display = "none";

                // Pencocokan data berdasarkan variabel NISN spesifik
                const matchStudent = processedStudents.find(s => s.nisn === inputVal);

                if(!matchStudent) {
                    resultContainer.innerHTML = `
                        <div class="m3-glass bounce-effect" style="text-align:center; padding: 30px 20px;">
                            <i class="fa-solid fa-user-shield" style="font-size:32px; color:#f43f5e; margin-bottom:12px;"></i>
                            <h3 style="font-size:15px; color:#334155;">NISN Tidak Terdaftar</h3>
                            <p style="font-size:12px; color:#64748b; margin-top:4px;">Silakan periksa kembali kartu pelajar atau hubungi wali kelas.</p>
                        </div>
                    `;
                } else {
                    let cardClass = 'card-rank-normal';
                    let badgeClass = 'badge-normal';
                    let badgeIcon = '<i class="fa-solid fa-hashtag"></i>';
                    let badgeText = `Rank ${matchStudent.rank}`;

                    if(matchStudent.rank === 1) {
                        cardClass = 'card-rank-1';
                        badgeClass = 'badge-1';
                        badgeIcon = '<i class="fa-solid fa-trophy"></i>';
                        badgeText = 'Juara 1';
                    } else if(matchStudent.rank === 2) {
                        cardClass = 'card-rank-2';
                        badgeClass = 'badge-2';
                        badgeIcon = '<i class="fa-solid fa-medal"></i>';
                        badgeText = 'Juara 2';
                    } else if(matchStudent.rank === 3) {
                        cardClass = 'card-rank-3';
                        badgeClass = 'badge-3';
                        badgeIcon = '<i class="fa-solid fa-medal"></i>';
                        badgeText = 'Juara 3';
                    }

                    let predMtk = getPredikatText(matchStudent.mtk);
                    let predInd = getPredikatText(matchStudent.ind);

                    resultContainer.innerHTML = `
                        <div class="m3-glass result-card ${cardClass} bounce-effect">
                            <div class="student-profile">
                                <div class="profile-info">
                                    <h2>${matchStudent.name}</h2>
                                    <p>NISN: ${matchStudent.nisn}</p>
                                </div>
                                <div class="rank-badge ${badgeClass}">
                                    ${badgeIcon}<span>${badgeText}</span>
                                </div>
                            </div>
                            
                            <div class="score-rows-container">
                                <div class="score-row-item">
                                    <div class="subject-meta">
                                        <span class="subject-name">Matematika</span>
                                        <span class="tag-predikat ${predMtk.class}">${predMtk.text}</span>
                                    </div>
                                    <div class="score-number">${matchStudent.mtk.toFixed(1)}</div>
                                </div>
                                
                                <div class="score-row-item">
                                    <div class="subject-meta">
                                        <span class="subject-name">Bahasa Indonesia</span>
                                        <span class="tag-predikat ${predInd.class}">${predInd.text}</span>
                                    </div>
                                    <div class="score-number">${matchStudent.ind.toFixed(1)}</div>
                                </div>
                            </div>

                            <div class="card-footer-summary">
                                Rata-Rata Ujian Kombinasi: <strong>${matchStudent.combinedAvg.toFixed(2)}</strong>
                            </div>

                            <div class="skl-announcement">
                                <div class="skl-title">
                                    <i class="fa-solid fa-circle-info"></i>
                                    <span>AGENDA PENTING KELULUSAN</span>
                                </div>
                                <ul class="skl-details">
                                    <li>
                                        <i class="fa-solid fa-calendar-day"></i>
                                        <span><strong>Hari/Tanggal:</strong> Sabtu, 6 Juni 2026</span>
                                    </li>
                                    <li>
                                        <i class="fa-solid fa-clock"></i>
                                        <span><strong>Waktu:</strong> Jam 09.00 WIB</span>
                                    </li>
                                    <li>
                                        <i class="fa-solid fa-location-dot"></i>
                                        <span><strong>Tempat:</strong> Ruang TU SMP Negeri 1 Lingga</span>
                                    </li>
                                    <li style="margin-top:4px; font-style:italic; color:#9a3412;">
                                        <span>*Pengambilan wajib didampingi Orang Tua/Wali Murid dengan pakaian rapi.</span>
                                    </li>
                                </ul>
                            </div>
                        </div>
                    `;
                }
                
                resultContainer.style.display = "block";

            }, 1200);
        }

        window.onload = function() {
            initData();
            switchTab('nilaiku');
        };
    </script>
</body>
</html>
