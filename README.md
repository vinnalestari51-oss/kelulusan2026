<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pengumuman Kelulusan Siswa SMPN 1 Lingga</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --bg-pastel: #f0f4f8; /* Biru abu pastel lembut */
            --card-bg: #ffffff;
            --primary-pastel: #aec6cf; /* Biru pastel utama */
            --primary-dark: #4a6984;
            --success-pastel: #b2e2b2; /* Hijau pastel untuk kelulusan */
            --success-text: #2b5e2b;
            --info-pastel: #e0f2fe; /* Biru pastel untuk info pengumuman */
            --info-text: #0369a1;
            --error-pastel: #fbc4c4;
            --error-text: #721c24;
            --text-color: #4f5d75;
            --border-color: #e2e8f0;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Inter', sans-serif;
        }

        body {
            background-color: var(--bg-pastel);
            color: var(--text-color);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            width: 100%;
            max-width: 550px;
            background: var(--card-bg);
            border-radius: 24px;
            box-shadow: 0 12px 30px rgba(0, 0, 0, 0.04);
            overflow: hidden;
            border: 1px solid var(--border-color);
        }

        /* Header Nuansa Pastel */
        .header {
            background: linear-gradient(135deg, #d3e0ea, #bcccda);
            padding: 30px 20px;
            text-align: center;
            border-bottom: 1px solid var(--border-color);
        }
        .header i {
            font-size: 2.5rem;
            color: var(--primary-dark);
            margin-bottom: 10px;
        }
        .header h1 {
            font-size: 1.3rem;
            font-weight: 700;
            color: var(--primary-dark);
            letter-spacing: 0.5px;
        }
        .header p {
            font-size: 0.85rem;
            color: #617185;
            margin-top: 4px;
            font-weight: 500;
        }

        /* Konten */
        .content {
            padding: 30px 24px;
        }

        .search-box {
            background: #fdfdfd;
            border-radius: 18px;
            padding: 20px;
            border: 1px solid var(--border-color);
        }

        .label-title {
            font-size: 0.9rem;
            font-weight: 600;
            margin-bottom: 10px;
            color: var(--primary-dark);
            display: block;
        }

        /* Input Form */
        .input-group {
            position: relative;
            display: flex;
            align-items: center;
            background: #ffffff;
            border: 2px solid #cbd5e1;
            border-radius: 12px;
            padding: 0 14px;
            transition: all 0.3s ease;
        }
        .input-group:focus-within {
            border-color: var(--primary-dark);
            box-shadow: 0 0 0 4px rgba(74, 105, 132, 0.12);
        }
        .input-group i {
            color: #94a3b8;
            margin-right: 12px;
            font-size: 1.1rem;
        }
        .input-nisn {
            width: 100%;
            border: none;
            outline: none;
            padding: 14px 0;
            font-size: 1rem;
            font-weight: 600;
            color: #334155;
            letter-spacing: 1px;
        }

        /* Tombol Pastel */
        .btn-submit {
            width: 100%;
            background-color: var(--primary-dark);
            color: #ffffff;
            border: none;
            border-radius: 12px;
            padding: 14px;
            font-size: 0.95rem;
            font-weight: 600;
            margin-top: 14px;
            cursor: pointer;
            transition: all 0.2s ease;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 8px;
        }
        .btn-submit:hover {
            background-color: #3b536b;
            transform: translateY(-1px);
        }

        /* Pesan Error */
        .error-box {
            display: none;
            background: var(--error-pastel);
            color: var(--error-text);
            border-radius: 12px;
            padding: 14px;
            margin-top: 16px;
            font-size: 0.85rem;
            font-weight: 500;
            gap: 10px;
            align-items: center;
        }

        /* Efek Loading Animasi */
        .loading {
            display: none;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 30px 0;
            gap: 12px;
        }
        .spinner {
            width: 32px;
            height: 32px;
            border: 4px solid #e2e8f0;
            border-top-color: var(--primary-dark);
            border-radius: 50%;
            animation: spin 0.8s linear infinite;
        }

        /* Tampilan Amplop Kelulusan */
        .result-box {
            display: none;
            margin-top: 24px;
            animation: fadeInUp 0.40s ease-out;
        }

        .graduation-card {
            background: #ffffff;
            border: 1px solid var(--border-color);
            border-radius: 18px;
            padding: 24px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.01);
        }

        .alert-status {
            background-color: var(--success-pastel);
            color: var(--success-text);
            padding: 16px;
            border-radius: 12px;
            text-align: center;
            font-weight: 700;
            font-size: 1.05rem;
            margin-bottom: 20px;
            box-shadow: inset 0 2px 4px rgba(0,0,0,0.02);
        }

        /* Pengumuman Pengambilan SKL & Rapor */
        .info-distribution {
            background-color: var(--info-pastel);
            color: var(--info-text);
            padding: 14px;
            border-radius: 12px;
            font-size: 0.85rem;
            line-height: 1.5;
            margin-bottom: 20px;
            border: 1px solid #bae6fd;
        }
        .info-distribution strong {
            color: #0369a1;
        }

        .student-title {
            font-size: 1.1rem;
            font-weight: 700;
            color: #1e293b;
            text-transform: uppercase;
            border-bottom: 2px dashed var(--border-color);
            padding-bottom: 10px;
            margin-bottom: 16px;
            text-align: center;
        }

        .data-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
            background: #f8fafc;
            padding: 12px 16px;
            border-radius: 10px;
            border: 1px solid #f1f5f9;
        }

        .data-label {
            font-size: 0.85rem;
            font-weight: 500;
            color: #64748b;
        }

        .data-value {
            font-size: 0.95rem;
            font-weight: 700;
            color: #334155;
        }

        .data-value.highlight {
            color: #16a34a;
            font-size: 1.1rem;
        }

        @keyframes spin { to { transform: rotate(360deg); } }
        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(15px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>

<div class="container">
    <div class="header">
        <i class="fa-solid fa-graduation-cap"></i>
        <h1>SMP NEGERI 1 LINGGA</h1>
        <p>Sistem Pengumuman Kelulusan Online TA 2025/2026</p>
    </div>

    <div class="content">
        <div class="search-box">
            <label class="label-title" for="input-nisn">Masukkan NISN Lengkap Siswa</label>
            <div class="input-group">
                <i class="fa-solid fa-id-card"></i>
                <input type="text" id="input-nisn" class="input-nisn" placeholder="Contoh: 0115557747" maxlength="10">
            </div>
            <button class="btn-submit" onclick="cekKelulusan()">
                <i class="fa-solid fa-envelope-open"></i> Periksa Kelulusan
            </button>
        </div>

        <div id="error-container" class="error-box"></div>

        <div id="loading-container" class="loading">
            <div class="spinner"></div>
            <p style="font-size: 0.85rem; color: #64748b; font-weight: 500;">Membuka berkas kelulusan...</p>
        </div>

        <div id="result-container" class="result-box"></div>
    </div>
</div>

<script>
// DATABASE INTEGRASI DATA KELULUSAN DAN RATA-RATA NILAI KURIKULUM MERDEKA
const GRADUATION_DATABASE = [
    { nisn: "0115557747", name: "ADELIA DWI NURMANSYAH", average: "86.02" },
    { nisn: "0101111863", name: "ANANDA IBNU FAHREZI", average: "78.53" },
    { nisn: "0112631039", name: "DAFITRA ARIANSYAH", average: "78.38" },
    { nisn: "0097680988", name: "DELVRY ANGGARA PANJAITAN", average: "83.22" },
    { nisn: "0117042213", name: "DYRA ALTHA FUNISYA", average: "90.60" },
    { nisn: "0111647237", name: "FAQIHA TAZKIATUN NUFUS", average: "84.51" },
    { nisn: "0109121124", name: "GHASTAN GAUTAMA GINARDA", average: "88.94" },
    { nisn: "0112426972", name: "JEANTRIKA SAPUTERA", average: "77.58" },
    { nisn: "0114122561", name: "LIYANA ZAHIRA", average: "80.52" },
    { nisn: "0128826786", name: "M.BAYU RIZKITULLAH", average: "82.00" },
    { nisn: "0118177962", name: "MARWA DWI RAMADANI", average: "84.26" },
    { nisn: "0118552573", name: "MUHAMMAD FADHIL ARDIANSYAH", average: "83.04" },
    { nisn: "0102053051", name: "MUHAMMAD GIBRAN ASSYAFARI", average: "79.62" },
    { nisn: "0118730407", name: "MULHUDA", average: "80.54" },
    { nisn: "0113332240", name: "NUR RAFNI YASMADI", average: "80.58" },
    { nisn: "0117775355", name: "QIAN FERDINAND", average: "79.46" },
    { nisn: "0114103715", name: "RAFADIL ANANTA", average: "74.70" },
    { nisn: "0118789434", name: "RAJA FATHUR ABDILLAH", average: "82.50" },
    { nisn: "0112333526", name: "RINA RIYANTI", average: "84.20" },
    { nisn: "0113962310", name: "RISNA ULKA ARYANI", average: "81.44" },
    { nisn: "0113067688", name: "RISKA SARI", average: "80.12" },
    { nisn: "0114699199", name: "RISKY ARDIAN MISKA SACHPUTRA", average: "77.42" },
    { nisn: "0115867734", name: "RIZKA ALFIA AZ ZAHRA", average: "87.94" },
    { nisn: "0117587242", name: "SAPINAH", average: "80.34" },
    { nisn: "0114766625", name: "SHERIL GIANDA UTAMI", average: "78.96" },
    { nisn: "0112026378", name: "SILA ADELIA", average: "80.82" },
    { nisn: "0116317492", name: "SUKMASARI", average: "82.68" },
    { nisn: "0111751808", name: "SYARIFAH IZZATI AQILA", average: "84.92" },
    { nisn: "0113394958", name: "SYARIFAH NAFIA SAFIZ", average: "86.82" },
    { nisn: "0116942061", name: "SYARIFAH NAJWA SAFIZ", average: "87.58" },
    { nisn: "0116938426", name: "SYARIFAH ZILFA NATASYA", average: "83.44" },
    { nisn: "0112757766", name: "ZALFA MUFIDAH INAYAH", average: "85.22" },
    { nisn: "0115755742", name: "ZATIA MAYSYA", average: "87.88" },
    { nisn: "0105395625", name: "ZIFARA OKTIA GISKA", average: "84.84" }
];

function cekKelulusan() {
    const inputField = document.getElementById('input-nisn');
    const resultBox = document.getElementById('result-container');
    const errorBox = document.getElementById('error-container');
    const loadingBox = document.getElementById('loading-container');

    // Reset Tampilan
    resultBox.style.display = 'none';
    errorBox.style.display = 'none';
    errorBox.innerHTML = '';

    const queryNisn = inputField.value.trim();

    // 1. Validasi Input Kosong
    if (queryNisn === "") {
        errorBox.style.display = 'flex';
        errorBox.innerHTML = '<i class="fa-solid fa-circle-exclamation"></i> Silakan ketik nomor NISN siswa terlebih dahulu.';
        return;
    }

    // 2. Validasi Angka Keras 10 Digit
    if (queryNisn.length !== 10 || isNaN(queryNisn)) {
        errorBox.style.display = 'flex';
        errorBox.innerHTML = '<i class="fa-solid fa-triangle-exclamation"></i> NISN harus berjumlah persis 10 digit angka.';
        return;
    }

    // 3. Pencarian Berdasarkan Kesamaan Mutlak (===)
    const matchStudent = GRADUATION_DATABASE.find(student => student.nisn === queryNisn);

    // 4. Jika NISN Tidak Ditemukan
    if (!matchStudent) {
        errorBox.style.display = 'flex';
        errorBox.innerHTML = '<i class="fa-solid fa-circle-xmark"></i> Maaf, Nomor NISN tidak ditemukan dalam database kelulusan sekolah.';
        return;
    }

    // 5. Jalankan Efek Animasi Loading
    loadingBox.style.display = 'flex';

    setTimeout(() => {
        loadingBox.style.display = 'none';
        
        // Memunculkan data kelulusan serta teks instruksi pembagian SKL dan Rapor
        resultBox.innerHTML = `
            <div class="graduation-card">
                <div class="alert-status">
                    <i class="fa-solid fa-circle-check"></i> Selamat, Anda dinyatakan LULUS!
                </div>

                <div class="info-distribution">
                    <i class="fa-solid fa-circle-info"></i> <strong>Informasi Sekolah:</strong><br>
                    Surat Keterangan Lulus (SKL) dan Rapor akan dibagikan pada hari <strong>Sabtu, 6 Juni 2026 Jam 09.00 WIB</strong> di ruang <strong>TU SMP Negeri 1 Lingga</strong>.
                </div>

                <div class="student-title">${matchStudent.name}</div>
                
                <div class="data-row">
                    <span class="data-label">Nomor NISN</span>
                    <span class="data-value">${matchStudent.nisn}</span>
                </div>
                <div class="data-row">
                    <span class="data-label">Rata-Rata Nilai</span>
                    <span class="data-value highlight">${matchStudent.average}</span>
                </div>
                <div class="data-row">
                    <span class="data-label">Status Kelulusan</span>
                    <span class="data-value" style="color: #16a34a;">LULUS</span>
                </div>
            </div>
        `;
        
        resultBox.style.display = 'block';
    }, 1200);
}
</script>

</body>
</html>
