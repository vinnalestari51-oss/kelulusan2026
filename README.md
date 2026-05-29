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
                <input type="text" id="input-nisn" class="input-nisn" placeholder="
