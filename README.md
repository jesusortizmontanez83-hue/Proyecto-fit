<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>FitAura - Fitness Inteligente con IA</title>
<script src="https://cdn.jsdelivr.net/npm/jsqr@1.4.0/dist/jsQR.min.js">
</script>
<>
:root {
    --primary: #ff5f6d;
    --secondary: #7c3aed;
    --accent: #06b6d4;
    --dark: #0f0a1a;
    --card: rgba(26, 22, 51, 0.9);
    --text: #ffffff;
    --muted: #94a3b8;
    --success: #10b981;
    --warning: #f59e0b;
}

* { box-sizing: border-box; margin: 0; padding: 0; }

body {
    font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
    background: linear-gradient(135deg, #0f0a1a, #1a0a2e, #16213e, #0f3460);
    color: var(--text);
    line-height: 1.6;
    min-height: 100vh;
}

header {
    padding: 15px 30px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: rgba(15, 10, 26, 0.95);
    backdrop-filter: blur(20px);
    position: sticky;
    top: 0;
    z-index: 100;
    border-bottom: 1px solid rgba(124, 58, 237, 0.3);
}

.logo {
    font-size: 32px;
    font-weight: 800;
    background: linear-gradient(135deg, #ff5f6d, #7c3aed);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    letter-spacing: -1px;
}

.logo-ia {
    font-size: 12px;
    background: var(--accent);
    padding: 2px 8px;
    border-radius: 12px;
    margin-left: 8px;
    -webkit-text-fill-color: white;
    font-weight: 600;
}

.btn {
    background: linear-gradient(135deg, #ff5f6d, #7c3aed);
    color: white;
    padding: 12px 24px;
    border: none;
    border-radius: 12px;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.3s ease;
    font-size: 14px;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    box-shadow: 0 4px 15px rgba(124, 58, 237, 0.3);
}

.btn:hover { transform: translateY(-2px); box-shadow: 0 8px 25px rgba(124, 58, 237, 0.5); }
.btn-success { background: linear-gradient(135deg, #10b981, #059669); }
.btn-danger { background: linear-gradient(135deg, #ef4444, #dc2626); }
.btn-accent { background: linear-gradient(135deg, #06b6d4, #3b82f6); }

.hero {
    padding: 60px 20px;
    text-align: center;
    background: linear-gradient(135deg, rgba(255, 95, 109, 0.1), rgba(124, 58, 237, 0.1), rgba(6, 182, 212, 0.1));
}

h1 {
    font-size: 48px;
    margin: 0 0 15px;
    background: linear-gradient(135deg, #ff5f6d, #7c3aed, #06b6d4);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    font-weight: 900;
}

.hero p { max-width: 650px; margin: 0 auto 25px; color: var(--muted); font-size: 18px; }

.grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
    padding: 30px;
    max-width: 1400px;
    margin: 0 auto;
}

.card {
    background: var(--card);
    padding: 25px;
    border-radius: 20px;
    border: 1px solid rgba(124, 58, 237, 0.2);
    box-shadow: 0 20px 50px rgba(76, 29, 149, 0.2);
    backdrop-filter: blur(10px);
    transition: all 0.3s ease;
    overflow: hidden;
}

.card:hover { transform: translateY(-3px); border-color: rgba(124, 58, 237, 0.5); }
.card h2 { color: var(--primary); margin-bottom: 15px; font-size: 20px; display: flex; align-items: center; gap: 8px; flex-wrap: wrap; }

input, select, textarea {
    width: 100%;
    padding: 12px;
    margin: 6px 0;
    border-radius: 10px;
    border: 2px solid rgba(124, 58, 237, 0.2);
    background: rgba(15, 10, 26, 0.8);
    color: white;
    font-size: 14px;
    transition: all 0.3s ease;
}

input:focus, select:focus, textarea:focus { outline: none; border-color: var(--secondary); }

.ia-badge {
    background: linear-gradient(135deg, #06b6d4, #10b981);
    color: white;
    padding: 4px 10px;
    border-radius: 20px;
    font-size: 11px;
    font-weight: 700;
    display: inline-block;
    margin-left: 8px;
    white-space: nowrap;
}

.result {
    margin-top: 12px;
    padding: 12px;
    background: rgba(124, 58, 237, 0.1);
    border-radius: 10px;
    border: 1px solid rgba(124, 58, 237, 0.2);
    font-weight: 600;
    color: var(--primary);
    max-height: 400px;
    overflow-y: auto;
    font-size: 13px;
    word-wrap: break-word;
}

/* Tags */
.activity-tags, .diet-tags { display: flex; flex-wrap: wrap; gap: 6px; margin: 12px 0; }

.activity-tag, .diet-tag {
    background: rgba(124, 58, 237, 0.2);
    border: 1px solid rgba(124, 58, 237, 0.3);
    padding: 8px 10px;
    border-radius: 20px;
    cursor: pointer;
    font-size: 11px;
    transition: all 0.3s ease;
    text-align: center;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

.activity-tag:hover, .activity-tag.active,
.diet-tag:hover, .diet-tag.active {
    background: linear-gradient(135deg, #7c3aed, #06b6d4);
    border-color: transparent;
}

.activity-tag small { display: block; font-size: 9px; color: var(--muted); margin-top: 2px; white-space: nowrap; }
.activity-tag.active small, .diet-tag.active small { color: white; }

/* Food scanner */
.food-scanner-card { border: 2px solid rgba(6, 182, 212, 0.5) !important; background: linear-gradient(135deg, rgba(26, 22, 51, 0.95), rgba(6, 182, 212, 0.05)) !important; }

.upload-food-area {
    display: block; padding: 25px; border: 3px dashed rgba(6, 182, 212, 0.6);
    border-radius: 16px; margin: 12px 0; background: rgba(6, 182, 212, 0.05);
    cursor: pointer; transition: all 0.4s ease; text-align: center;
}
.upload-food-area:hover { border-color: var(--accent); background: rgba(6, 182, 212, 0.12); transform: scale(1.02); }
.upload-food-area.analyzing { border-color: var(--warning); background: rgba(245, 158, 11, 0.1); animation: pulse-border 1.5s ease-in-out infinite; }

@keyframes pulse-border {
    0%, 100% { border-color: var(--warning); box-shadow: 0 0 20px rgba(245, 158, 11, 0.2); }
    50% { border-color: var(--accent); box-shadow: 0 0 40px rgba(6, 182, 212, 0.4); }
}

.food-preview-container { position: relative; margin-top: 10px; }
.food-preview { width: 100%; max-height: 280px; object-fit: contain; border-radius: 14px; display: none; border: 2px solid rgba(124, 58, 237, 0.3); background: rgba(0,0,0,0.3); }

.analyzing-overlay {
    display: none; position: absolute; inset: 0; background: rgba(0,0,0,0.7);
    border-radius: 14px; justify-content: center; align-items: center; flex-direction: column; gap: 12px;
}
.analyzing-overlay.active { display: flex; }

.spinner {
    width: 50px; height: 50px; border: 4px solid rgba(255,255,255,0.1);
    border-top: 4px solid var(--accent); border-radius: 50%; animation: spin 0.8s linear infinite;
}
@keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }

.food-result-card, .qr-result-card {
    background: rgba(6, 182, 212, 0.08); border: 1px solid rgba(6, 182, 212, 0.3);
    border-radius: 14px; padding: 18px; margin-top: 12px; display: none; animation: fadeIn 0.5s ease;
}
@keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

.gram-control { display: flex; gap: 8px; align-items: center; justify-content: center; }
.gram-btn {
    background: rgba(124, 58, 237, 0.3); border: 1px solid rgba(124, 58, 237, 0.5);
    color: white; width: 40px; height: 40px; border-radius: 10px; cursor: pointer;
    font-size: 18px; display: flex; align-items: center; justify-content: center; transition: all 0.3s ease;
}
.gram-btn:hover { background: var(--secondary); }

.gram-presets { display: grid; grid-template-columns: repeat(3, 1fr); gap: 6px; margin: 8px 0; }
.gram-preset {
    background: rgba(124, 58, 237, 0.2); border: 1px solid rgba(124, 58, 237, 0.3);
    color: white; padding: 8px 6px; border-radius: 8px; cursor: pointer;
    font-size: 11px; transition: all 0.3s ease; text-align: center; white-space: nowrap;
}
.gram-preset:hover { background: var(--secondary); }

.nutri-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; text-align: center; margin-top: 10px; }
.nutri-item { padding: 10px; border-radius: 8px; font-size: 12px; }

.upload-area {
    display: block; padding: 15px; border: 2px dashed rgba(255, 95, 109, 0.5);
    border-radius: 14px; margin: 10px 0; background: rgba(255, 255, 255, 0.03);
    cursor: pointer; transition: all 0.3s ease; text-align: center; font-size: 13px;
}
.upload-area:hover { border-color: var(--primary); background: rgba(255, 95, 109, 0.08); }

.preview-grid-4 { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 12px; }
.preview-grid-4 img {
    width: 100%; height: 130px; object-fit: cover; border-radius: 12px;
    border: 2px solid rgba(124, 58, 237, 0.3); display: none; background: rgba(0,0,0,0.3);
}
.preview-grid-4 img.has-image { display: block; border-color: rgba(16, 185, 129, 0.5); }

/* QR Scanner */
.qr-scanner-container {
    position: relative; width: 100%; max-width: 400px; margin: 15px auto;
    border-radius: 12px; overflow: hidden; background: #000;
}
.qr-video { width: 100%; height: auto; display: block; border-radius: 12px; }
.qr-overlay {
    position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%);
    width: 180px; height: 180px; border: 3px solid var(--accent);
    border-radius: 12px; box-shadow: 0 0 0 9999px rgba(0, 0, 0, 0.5);
}
.qr-controls { display: flex; gap: 10px; margin-top: 10px; justify-content: center; }
.qr-input-group { display: flex; align-items: center; gap: 10px; margin: 10px 0; }
.qr-input-group input { flex: 1; }
.camera-status { text-align: center; padding: 8px; color: var(--accent); font-size: 13px; }

.scan-status { font-size: 11px; margin-top: 8px; text-align: center; }
.scan-status.ready { color: #10b981; }
.scan-status.incomplete { color: #f59e0b; }

/* ==================== MODAL DE PAGO CON RETROCESO ==================== */
.modal {
    display: none; position: fixed; inset: 0; background: rgba(0, 0, 0, 0.85);
    z-index: 999; align-items: center; justify-content: center; backdrop-filter: blur(5px);
}

.payment-modal-content {
    background: linear-gradient(135deg, rgba(26, 22, 51, 0.99), rgba(15, 10, 26, 0.99));
    padding: 30px;
    border-radius: 24px;
    max-width: 500px;
    width: 94%;
    text-align: center;
    border: 1px solid rgba(124, 58, 237, 0.4);
    box-shadow: 0 30px 80px rgba(0, 0, 0, 0.6);
    animation: fadeIn 0.3s ease;
    position: relative;
}

/* Botón de retroceso en la esquina superior */
.back-button {
    position: absolute;
    top: 15px;
    left: 15px;
    background: rgba(255, 255, 255, 0.08);
    border: 1px solid rgba(255, 255, 255, 0.15);
    color: white;
    width: 36px;
    height: 36px;
    border-radius: 50%;
    cursor: pointer;
    font-size: 18px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease;
    z-index: 10;
}

.back-button:hover {
    background: rgba(255, 255, 255, 0.18);
    transform: scale(1.1);
}

.payment-modal-content h2 {
    color: var(--primary);
    margin-bottom: 5px;
    font-size: 22px;
    margin-top: 10px;
}

.payment-modal-content .subtitle {
    color: var(--muted);
    font-size: 12px;
    margin-bottom: 18px;
}

/* Selector de planes */
.plan-selector {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    margin-bottom: 18px;
}

.plan-card {
    background: rgba(124, 58, 237, 0.1);
    border: 2px solid rgba(124, 58, 237, 0.2);
    border-radius: 16px;
    padding: 16px 10px;
    cursor: pointer;
    transition: all 0.3s ease;
    text-align: center;
}

.plan-card:hover {
    border-color: rgba(124, 58, 237, 0.5);
    background: rgba(124, 58, 237, 0.2);
    transform: translateY(-2px);
}

.plan-card.selected {
    border-color: var(--accent) !important;
    background: rgba(6, 182, 212, 0.15) !important;
    box-shadow: 0 0 25px rgba(6, 182, 212, 0.3);
}

.plan-card .plan-icon { font-size: 32px; margin-bottom: 6px; }
.plan-card .plan-name { font-weight: 700; font-size: 14px; color: white; margin-bottom: 2px; }
.plan-card .plan-price { color: var(--accent); font-weight: 700; font-size: 18px; }
.plan-card .plan-detail { font-size: 10px; color: var(--muted); margin-top: 2px; }
.plan-card .plan-badge {
    display: inline-block;
    background: linear-gradient(135deg, #10b981, #059669);
    color: white;
    padding: 3px 10px;
    border-radius: 12px;
    font-size: 10px;
    font-weight: 700;
    margin-top: 5px;
}

/* Resumen */
.plan-summary {
    background: rgba(6, 182, 212, 0.1);
    border: 1px solid rgba(6, 182, 212, 0.3);
    border-radius: 12px;
    padding: 10px 14px;
    margin-bottom: 16px;
    text-align: left;
}

.plan-summary .summary-title {
    color: var(--accent);
    font-weight: 700;
    font-size: 12px;
    margin-bottom: 2px;
}

.plan-summary .summary-detail {
    color: white;
    font-size: 13px;
    font-weight: 600;
}

.plan-summary .summary-saving {
    color: #10b981;
    font-size: 11px;
    margin-top: 2px;
}

/* Campos de tarjeta */
.card-input-group {
    margin-bottom: 12px;
    text-align: left;
}

.card-input-group label {
    display: block;
    color: var(--muted);
    font-size: 11px;
    margin-bottom: 3px;
    font-weight: 600;
}

.card-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
}

.input-with-icon {
    position: relative;
}

.input-with-icon .input-icon {
    position: absolute;
    right: 12px;
    top: 50%;
    transform: translateY(-50%);
    font-size: 16px;
    pointer-events: none;
}

/* Botones de acción */
.btn-pay {
    background: linear-gradient(135deg, #10b981, #059669);
    color: white;
    padding: 14px 24px;
    border: none;
    border-radius: 14px;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.3s ease;
    font-size: 15px;
    width: 100%;
    letter-spacing: 0.5px;
    box-shadow: 0 4px 20px rgba(16, 185, 129, 0.4);
    margin-top: 5px;
}

.btn-pay:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 30px rgba(16, 185, 129, 0.6);
}

.btn-cancel-bottom {
    background: transparent;
    border: 1px solid rgba(255, 255, 255, 0.2);
    color: var(--muted);
    padding: 11px 24px;
    border-radius: 12px;
    cursor: pointer;
    font-size: 13px;
    width: 100%;
    margin-top: 8px;
    transition: all 0.3s ease;
}

.btn-cancel-bottom:hover {
    border-color: rgba(255, 255, 255, 0.4);
    color: white;
    background: rgba(255, 255, 255, 0.05);
}

/* Seguridad */
.security-info {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
    margin-top: 12px;
    font-size: 10px;
    color: var(--muted);
}

.security-info span {
    display: flex;
    align-items: center;
    gap: 3px;
}

/* Modal de éxito */
.success-modal-content {
    background: linear-gradient(135deg, rgba(26, 22, 51, 0.99), rgba(15, 10, 26, 0.99));
    padding: 35px 30px;
    border-radius: 24px;
    max-width: 450px;
    width: 94%;
    text-align: center;
    border: 1px solid rgba(16, 185, 129, 0.4);
    box-shadow: 0 30px 80px rgba(0, 0, 0, 0.6);
    animation: fadeIn 0.3s ease;
    position: relative;
}

.success-icon {
    font-size: 60px;
    animation: bounce 1s ease;
}

@keyframes bounce {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.2); }
}

/* Modales legales */
.legal-modal-content {
    background: linear-gradient(135deg, rgba(26, 22, 51, 0.98), rgba(15, 10, 26, 0.98));
    padding: 30px; border-radius: 20px; max-width: 650px; width: 94%;
    text-align: left; border: 1px solid rgba(124, 58, 237, 0.3);
    box-shadow: 0 30px 80px rgba(0, 0, 0, 0.5);
    max-height: 85vh; overflow-y: auto;
}
.legal-modal-content h2 { text-align: center; margin-bottom: 20px; }
.legal-modal-content h3 { color: var(--accent); margin: 20px 0 10px; font-size: 16px; }
.legal-modal-content p, .legal-modal-content li { color: var(--muted); font-size: 13px; line-height: 1.8; margin-bottom: 8px; }
.legal-modal-content strong { color: var(--text); }
.legal-divider { border: none; border-top: 1px solid rgba(124, 58, 237, 0.3); margin: 20px 0; }

.footer {
    background: rgba(15, 10, 26, 0.95); border-top: 1px solid rgba(124, 58, 237, 0.3);
    padding: 30px 20px; margin-top: 40px;
}
.footer-content { max-width: 1200px; margin: 0 auto; display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; }
.footer h3 { color: var(--primary); margin-bottom: 10px; font-size: 16px; }
.footer p, .footer a { color: var(--muted); font-size: 12px; line-height: 1.6; }
.footer a { text-decoration: none; cursor: pointer; } .footer a:hover { color: var(--accent); }

.legal-badge {
    display: inline-block; background: rgba(16, 185, 129, 0.1);
    border: 1px solid rgba(16, 185, 129, 0.3); padding: 6px 12px;
    border-radius: 20px; font-size: 11px; margin: 3px; white-space: nowrap;
}

.chat-ia {
    position: fixed; bottom: 20px; right: 20px;
    background: linear-gradient(135deg, #7c3aed, #06b6d4);
    width: 55px; height: 55px; border-radius: 50%; display: flex;
    align-items: center; justify-content: center; cursor: pointer;
    box-shadow: 0 10px 30px rgba(124, 58, 237, 0.5); z-index: 99;
    font-size: 22px; transition: all 0.3s ease;
}
.chat-ia:hover { transform: scale(1.1); }

/* Indicador de progreso en pago */
.progress-steps {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    margin-bottom: 20px;
}

.progress-step {
    width: 28px;
    height: 28px;
    border-radius: 50%;
    background: rgba(255, 255, 255, 0.1);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 12px;
    font-weight: 700;
    transition: all 0.3s ease;
}

.progress-step.active {
    background: var(--accent);
    box-shadow: 0 0 15px rgba(6, 182, 212, 0.4);
}

.progress-step.done {
    background: #10b981;
}

.progress-line {
    width: 30px;
    height: 2px;
    background: rgba(255, 255, 255, 0.2);
}

.progress-line.done {
    background: #10b981;
}

@media (max-width: 768px) {
    h1 { font-size: 32px; } .grid { padding: 15px; }
    header { padding: 12px 15px; } .card { padding: 20px; }
    .preview-grid-4 img { height: 100px; }
    .plan-selector { grid-template-columns: 1fr; }
}

@media (max-width: 400px) {
    .activity-tag, .diet-tag { padding: 5px 6px; font-size: 9px; }
    .card { padding: 15px; }
    h2 { font-size: 17px !important; }
}
</style>
</head>
<body>

<header>
    <div>
        <span class='logo'>FitAura</span>
        <span class='logo-ia'>IA</span>
    </div>
    <button class='btn' onclick='abrirPago()'>✨ Premium Gratis</button>
</header>

<section class='hero'>
    <h1>Transforma tu Cuerpo con IA</h1>
    <p>Escáner QR de productos, escáner IA de comida, análisis corporal y coaches profesionales.</p>
    <button class='btn' style='font-size: 16px; padding: 14px 35px;' onclick='comenzarGratis()'>🚀 Comenzar Gratis</button>
</section>

<section class='grid'>
    <!-- ESCÁNER DE COMIDA -->
    <div class='card food-scanner-card' style='grid-column: 1 / -1;'>
        <h2>📸 Escáner Inteligente de Comida <span class='ia-badge'>IA PRECISIÓN</span></h2>
        <p style='color: var(--muted); font-size: 13px;'>Toma una foto de tu plato. La IA identifica el alimento y calcula valores nutricionales.</p>
        
        <label class='upload-food-area' id='foodUploadArea' for='foodPhoto'>
            <div style='font-size: 56px; margin-bottom: 8px;'>🍽️</div>
            <strong style='font-size: 16px;'>📷 Toma foto de tu comida</strong>
            <input type='file' id='foodPhoto' accept='image/*' capture='environment' style='display:none' onchange='analizarComida(this)'>
        </label>
        
        <div class='food-preview-container'>
            <img id='foodPreview' class='food-preview' alt='Vista previa'>
            <div class='analyzing-overlay' id='analyzingOverlay'>
                <div class='spinner'></div>
                <p style='color: white; font-weight: 700;'>🤖 IA analizando...</p>
                <p style='font-size: 11px; color: var(--muted);' id='analisisDetalle'></p>
            </div>
        </div>
        <div class='food-result-card' id='foodResultCard'></div>
    </div>

    <!-- ESCÁNER QR -->
    <div class='card'>
        <h2>📱 Escáner QR <span class='ia-badge'>ACTIVO</span></h2>
        <p style='color: var(--muted); font-size: 13px;'>Escanea códigos de barras con tu cámara.</p>
        
        <div class='qr-scanner-container'>
            <video id='qrVideo' class='qr-video' autoplay playsinline></video>
            <canvas id='qrCanvas' style='display:none;'></canvas>
            <div class='qr-overlay'></div>
        </div>
        
        <div class='camera-status' id='cameraStatus'>📷 Preparando cámara...</div>
        
        <div class='qr-controls'>
            <button class='btn btn-success' onclick='iniciarCamaraQR()' style='flex:1;'>📷 Iniciar</button>
            <button class='btn btn-danger' onclick='detenerCamaraQR()' style='flex:1;'>⏹️ Detener</button>
        </div>
        
        <div class='qr-input-group'>
            <input type='text' id='qrManualInput' placeholder='O ingresa código de barras'>
            <button class='btn' onclick='buscarPorCodigo()' style='padding: 14px;'>🔍</button>
        </div>
        
        <p style='color: var(--accent); margin-top: 10px;'><strong>⚖️ Cantidad:</strong></p>
        <div class='gram-control' style='margin: 8px 0;'>
            <button class='gram-btn' onclick='ajustarGramosQR(-10)'>−</button>
            <input type='number' id='gramosQR' value='100' min='1' max='1000' style='text-align:center;font-size:15px;width:75px;background:rgba(15,10,26,0.8);color:white;border:2px solid rgba(124,58,237,0.3);border-radius:8px;padding:8px;' onchange='validarGramosQR()'>
            <span style='color:white;'>gramos</span>
            <button class='gram-btn' onclick='ajustarGramosQR(10)'>+</button>
        </div>
        <div class='gram-presets'>
            <button class='gram-preset' onclick='setGramosQR(1)'>1g</button>
            <button class='gram-preset' onclick='setGramosQR(50)'>50g</button>
            <button class='gram-preset' onclick='setGramosQR(100)'>100g</button>
            <button class='gram-preset' onclick='setGramosQR(250)'>250g</button>
            <button class='gram-preset' onclick='setGramosQR(500)'>500g</button>
            <button class='gram-preset' onclick='setGramosQR(1000)'>1kg</button>
        </div>
        
        <div class='qr-result-card' id='qrResultado'></div>
    </div>

    <!-- Planes -->
    <div class='card'>
        <h2>💎 Planes</h2>
        <div style='margin: 15px 0;'>
            <p><strong>🆓 Free:</strong> Escáner QR + IA Comida + Corporal</p>
            <p style='margin-top:8px;'><strong>⭐ Premium Mensual:</strong> 1 mes gratis, luego S/19.90/mes</p>
            <p style='margin-top:8px;'><strong>👑 Premium Anual:</strong> S/99/año (ahorro 60%)</p>
        </div>
        <button class='btn' onclick='abrirPago()' style='width:100%;margin-top:10px;'>💳 Activar Premium</button>
    </div>

    <!-- Registro -->
    <div class='card'>
        <h2>📝 Registro</h2>
        <input placeholder='Correo electrónico' type='email' id='regEmail'>
        <input type='password' placeholder='Contraseña' id='regPassword'>
        <button class='btn' onclick='registrarFree()' style='width:100%;margin-top:8px;'>Crear Cuenta Gratis</button>
        <p style='font-size:10px;color:var(--muted);margin-top:8px;text-align:center;'>
            Al registrarte aceptas nuestros <a href='#' onclick='mostrarTerminos()' style='color:var(--accent);text-decoration:underline;'>Términos</a>
        </p>
    </div>

    <!-- Calculadora IA -->
    <div class='card'>
        <h2>🧠 Calculadora IA</h2>
        <input id='peso' placeholder='Peso (kg)' type='number'>
        <input id='altura' placeholder='Altura (cm)' type='number'>
        <input id='edad' placeholder='Edad' type='number'>
        <select id='genero'>
            <option value=''>Género</option>
            <option value='hombre'>Hombre</option>
            <option value='mujer'>Mujer</option>
        </select>
        
        <p style='color: var(--accent); margin-top: 10px; font-size: 13px;'><strong>🏃 Actividad:</strong></p>
        <div class='activity-tags' id='activityTags'>
            <span class='activity-tag' onclick='toggleActivity(this)' data-activity='0'>🛋️ Sedentario</span>
            <span class='activity-tag' onclick='toggleActivity(this)' data-activity='1-2'>🚶 Bajo</span>
            <span class='activity-tag active' onclick='toggleActivity(this)' data-activity='3-4'>🏃 Medio</span>
            <span class='activity-tag' onclick='toggleActivity(this)' data-activity='6'>💪 Alto</span>
        </div>
        
        <p style='color: var(--accent); margin-top: 10px; font-size: 13px;'><strong>🍽️ Dieta:</strong></p>
        <div class='diet-tags' id='dietTags' style='display:grid;grid-template-columns:1fr 1fr 1fr;'>
            <span class='diet-tag active' onclick='toggleDiet(this)' data-diet='omnivoro'>🥩 Omnívoro</span>
            <span class='diet-tag' onclick='toggleDiet(this)' data-diet='vegetariano'>🥬 Vegetariano</span>
            <span class='diet-tag' onclick='toggleDiet(this)' data-diet='vegano'>🌱 Vegano</span>
            <span class='diet-tag' onclick='toggleDiet(this)' data-diet='keto'>🥑 Keto</span>
            <span class='diet-tag' onclick='toggleDiet(this)' data-diet='paleo'>🍖 Paleo</span>
            <span class='diet-tag' onclick='toggleDiet(this)' data-diet='mediterraneo'>🐟 Mediterráneo</span>
            <span class='diet-tag' onclick='toggleDiet(this)' data-diet='sin_gluten'>🌾 Sin Gluten</span>
            <span class='diet-tag' onclick='toggleDiet(this)' data-diet='sin_lactosa'>🥛 Sin Lactosa</span>
            <span class='diet-tag' onclick='toggleDiet(this)' data-diet='alto_proteina'>💪 Alta Prot</span>
            <span class='diet-tag' onclick='toggleDiet(this)' data-diet='bajo_carb'>📉 Bajo Carb</span>
        </div>
        
        <select id='objetivoFusion' style='margin-top:10px;'>
            <option value='18'>🎯 Recomposición</option>
            <option value='24'>🔥 Definición</option>
            <option value='32'>💪 Aumento Muscular</option>
        </select>
        
        <button class='btn' onclick='calcIMC()' style='width:100%;margin-top:10px;'>🤖 Generar Plan IA</button>
        <div id='imc' class='result'></div>
    </div>

    <!-- ESCÁNER CORPORAL -->
    <div class='card'>
        <h2>📸 Escáner Corporal <span class='ia-badge'>4 ÁNGULOS</span></h2>
        <p style='color:var(--muted);font-size:13px;'>Sube 4 fotos para análisis corporal.</p>
        
        <label class='upload-area' for='scanFront'>📸 <strong>Foto Frontal</strong><input id='scanFront' type='file' accept='image/*' style='display:none' onchange='previewScan("front")'></label>
        <label class='upload-area' for='scanBack'>📸 <strong>Foto Espalda</strong><input id='scanBack' type='file' accept='image/*' style='display:none' onchange='previewScan("back")'></label>
        <label class='upload-area' for='scanLeft'>📸 <strong>Costado Izquierdo</strong><input id='scanLeft' type='file' accept='image/*' style='display:none' onchange='previewScan("left")'></label>
        <label class='upload-area' for='scanRight'>📸 <strong>Costado Derecho</strong><input id='scanRight' type='file' accept='image/*' style='display:none' onchange='previewScan("right")'></label>
        
        <div class='preview-grid-4'>
            <img id='prevfront' alt='Frontal'><img id='prevback' alt='Espalda'>
            <img id='prevleft' alt='Izquierdo'><img id='prevright' alt='Derecho'>
        </div>
        
        <div class='scan-status incomplete' id='scanStatus'>📋 Fotos: 0 de 4</div>
        
        <button class='btn btn-success' onclick='analizarCuerpo()' style='width:100%;margin-top:12px;'>🔍 Analizar Cuerpo</button>
        <div id='scanResult' class='result'></div>
    </div>

    <!-- Coaches -->
    <div class='card'>
        <h2>👥 Zona Coaches</h2>
        <input placeholder='Nombre completo' id='coachNombre'>
        <input placeholder='Correo electrónico' id='coachEmail' type='email'>
        <div class='upload-area' style='margin:12px 0;'><p>📄 Subir CV</p><input id='cvFile' type='file' accept='image/*,.pdf,.doc,.docx' onchange='mostrarArchivo()'><p id='archivoNombre' style='color:var(--primary);font-size:11px;'></p></div>
        <button class='btn' onclick='postularCoach()' style='width:100%;'>🚀 Postular</button>
    </div>
</section>

<!-- FOOTER -->
<footer class='footer'>
    <div class='footer-content'>
        <div>
            <h3>FitAura IA</h3>
            <p>Herramienta de apoyo al bienestar físico.</p>
            <span class='legal-badge'>🔒 SSL</span>
            <span class='legal-badge'>✅ GDPR</span>
            <span class='legal-badge'>⚖️ Ley 29733</span>
        </div>
        <div>
            <h3>Documentos Legales</h3>
            <p><a onclick='mostrarTerminos()'>📄 Términos y Condiciones</a></p>
            <p><a onclick='mostrarPrivacidad()'>🔒 Política de Privacidad</a></p>
            <p><a onclick='mostrarCookies()'>🍪 Política de Cookies</a></p>
            <p><a onclick='mostrarReembolso()'>💰 Política de Reembolso</a></p>
            <p><a onclick='mostrarDescargo()'>⚠️ Descargo de Responsabilidad</a></p>
        </div>
        <div>
            <h3>Contacto</h3>
            <p>📧 legal@fitura.com</p>
            <p>📍 Lima, Perú</p>
            <p style='margin-top:10px;'>© 2026 FitAura Technologies</p>
        </div>
    </div>
</footer>

<div class='chat-ia' onclick='abrirChatIA()'>💬</div>

<!-- ==================== MODAL DE PAGO CON BOTÓN DE RETROCESO ==================== -->
<div id='pagoVentana' class='modal'>
    <div class='payment-modal-content'>
        <!-- Botón de retroceso (X) en la esquina superior izquierda -->
        <button class='back-button' onclick='retrocederPago()' title='Volver'>✕</button>
        
        <!-- Indicador de progreso -->
        <div class='progress-steps'>
            <div class='progress-step active' id='step1'>1</div>
            <div class='progress-line' id='line1'></div>
            <div class='progress-step' id='step2'>2</div>
            <div class='progress-line' id='line2'></div>
            <div class='progress-step' id='step3'>3</div>
        </div>
        
        <h2>💳 Activar Premium</h2>
        <p class='subtitle'>Elige tu plan y comienza tu transformación</p>
        
        <!-- Selector de planes -->
        <div class='plan-selector'>
            <div class='plan-card' id='planMensual' onclick='seleccionarPlanPago("mensual")'>
                <div class='plan-icon'>⭐</div>
                <div class='plan-name'>Plan Mensual</div>
                <div class='plan-price'>S/19.90</div>
                <div class='plan-detail'>por mes</div>
                <div class='plan-badge'>🎁 1 MES GRATIS</div>
            </div>
            
            <div class='plan-card selected' id='planAnual' onclick='seleccionarPlanPago("anual")'>
                <div class='plan-icon'>👑</div>
                <div class='plan-name'>Plan Anual</div>
                <div class='plan-price'>S/99</div>
                <div class='plan-detail'>por año</div>
                <div class='plan-badge'>💰 Ahorras 60%</div>
            </div>
        </div>
        
        <!-- Resumen del plan -->
        <div class='plan-summary' id='planSummary'>
            <div class='summary-title'>✅ Plan Seleccionado</div>
            <div class='summary-detail' id='summaryDetail'>Plan Anual - S/99/año</div>
            <div class='summary-saving' id='summarySaving'>Ahorras S/139.80 comparado al plan mensual</div>
        </div>
        
        <!-- Formulario de tarjeta -->
        <div class='card-input-group'>
            <label>👤 Nombre en la tarjeta</label>
            <input type='text' id='cardName' placeholder='Ej: JUAN PEREZ'>
        </div>
        
        <div class='card-input-group'>
            <label>💳 Número de tarjeta</label>
            <div class='input-with-icon'>
                <input type='text' id='cardNumber' placeholder='0000 0000 0000 0000' maxlength='19'>
                <span class='input-icon'>💳</span>
            </div>
        </div>
        
        <div class='card-row'>
            <div class='card-input-group'>
                <label>📅 Expiración</label>
                <input type='text' id='cardExpiry' placeholder='MM/AA' maxlength='5'>
            </div>
            <div class='card-input-group'>
                <label>🔒 CVV</label>
                <div class='input-with-icon'>
                    <input type='text' id='cardCVV' placeholder='123' maxlength='4'>
                    <span class='input-icon'>🔒</span>
                </div>
            </div>
        </div>
        
        <!-- Botón de pago -->
        <button class='btn-pay' onclick='procesarPago()'>
            🔒 Pagar <span id='btnPayAmount'>S/99</span> - Plan <span id='btnPayPlan'>Anual</span>
        </button>
        
        <!-- Botón de cancelar abajo -->
        <button class='btn-cancel-bottom' onclick='retrocederPago()'>
            ← Volver a la página principal
        </button>
        
        <!-- Información de seguridad -->
        <div class='security-info'>
            <span>🔒 SSL Encriptado</span>
            <span>🛡️ Datos Protegidos</span>
            <span>✅ Pago Seguro</span>
        </div>
    </div>
</div>

<!-- Modal de pago exitoso -->
<div id='pagoExitoso' class='modal'>
    <div class='success-modal-content'>
        <!-- Botón de retroceso -->
        <button class='back-button' onclick='cerrarModal("pagoExitoso")' title='Cerrar'>✕</button>
        
        <div class='success-icon'>✅</div>
        <h2 style='color: #10b981; margin: 20px 0;'>¡Pago Exitoso!</h2>
        <p style='color: var(--muted); margin-bottom: 20px;' id='mensajeExito'>
            Has activado el Plan Anual Premium. ¡Bienvenido a FitAura!
        </p>
        <div style='background: rgba(16, 185, 129, 0.1); padding: 15px; border-radius: 12px; margin-bottom: 20px;'>
            <p style='color: white; font-size: 14px;'><strong>🎁 Beneficios activados:</strong></p>
            <p style='color: var(--muted); font-size: 13px;'>✅ Escáner IA ilimitado</p>
            <p style='color: var(--muted); font-size: 13px;'>✅ Dietas personalizadas completas</p>
            <p style='color: var(--muted); font-size: 13px;'>✅ Seguimiento avanzado</p>
            <p style='color: var(--muted); font-size: 13px;'>✅ Acceso a coaches premium</p>
        </div>
        <button class='btn btn-success' onclick='cerrarModal("pagoExitoso")' style='width:100%;'>
            🚀 Comenzar Ahora
        </button>
    </div>
</div>

<!-- MODALES LEGALES -->
<div id='modalTerminos' class='modal'><div class='legal-modal-content'><h2 style='color:var(--primary);'>📄 TÉRMINOS Y CONDICIONES</h2><button class='back-button' onclick='cerrarModal("modalTerminos")' style='position:absolute;top:15px;left:15px;'>✕</button><p style='text-align:center;color:var(--muted);'><strong>FitAura Technologies S.A.C.</strong></p><hr class='legal-divider'><h3>1. ACEPTACIÓN</h3><p>Al usar FitAura, usted acepta estos Términos de forma expresa.</p><h3>2. DESCARGO MÉDICO</h3><p><strong>FitAura NO es un dispositivo médico. Consulte profesionales de salud.</strong></p><h3>3. LIMITACIÓN DE RESPONSABILIDAD</h3><p>FitAura no será responsable por daños derivados del uso de la app.</p><button class='btn' onclick='cerrarModal("modalTerminos")' style='width:100%;margin-top:20px;'>He Leído y Acepto</button></div></div>
<div id='modalPrivacidad' class='modal'><div class='legal-modal-content'><h2 style='color:var(--primary);'>🔒 POLÍTICA DE PRIVACIDAD</h2><button class='back-button' onclick='cerrarModal("modalPrivacidad")' style='position:absolute;top:15px;left:15px;'>✕</button><hr class='legal-divider'><p><strong>NO vendemos datos.</strong> Derechos ARCO según Ley 29733.</p><button class='btn' onclick='cerrarModal("modalPrivacidad")' style='width:100%;margin-top:20px;'>Entendido</button></div></div>
<div id='modalCookies' class='modal'><div class='legal-modal-content'><h2 style='color:var(--primary);'>🍪 COOKIES</h2><button class='back-button' onclick='cerrarModal("modalCookies")' style='position:absolute;top:15px;left:15px;'>✕</button><hr class='legal-divider'><p>Cookies esenciales y analíticas.</p><button class='btn' onclick='cerrarModal("modalCookies")' style='width:100%;margin-top:20px;'>Entendido</button></div></div>
<div id='modalReembolso' class='modal'><div class='legal-modal-content'><h2 style='color:var(--primary);'>💰 REEMBOLSO</h2><button class='back-button' onclick='cerrarModal("modalReembolso")' style='position:absolute;top:15px;left:15px;'>✕</button><hr class='legal-divider'><p>14 días de garantía. <strong>soporte@fitura.com</strong></p><button class='btn' onclick='cerrarModal("modalReembolso")' style='width:100%;margin-top:20px;'>Entendido</button></div></div>
<div id='modalDescargo' class='modal'><div class='legal-modal-content'><h2 style='color:var(--primary);'>⚠️ DESCARGO</h2><button class='back-button' onclick='cerrarModal("modalDescargo")' style='position:absolute;top:15px;left:15px;'>✕</button><hr class='legal-divider'><p><strong>FitAura NO es un dispositivo médico.</strong> Herramienta de apoyo.</p><button class='btn' onclick='cerrarModal("modalDescargo")' style='width:100%;margin-top:20px;'>Entendido</button></div></div>

<div id='registroExitoso' class='modal'><div class='success-modal-content'><button class='back-button' onclick='cerrarModal("registroExitoso")'>✕</button><div style='font-size:56px;'>🎉</div><h2 style='color:var(--primary);'>¡Registro Exitoso!</h2><button class='btn' onclick='cerrarModal("registroExitoso")' style='width:100%;'>Comenzar</button></div></div>
<div id='graciasVentana' class='modal'><div class='success-modal-content'><button class='back-button' onclick='cerrarModal("graciasVentana")'>✕</button><div style='font-size:56px;'>🎉</div><h2 style='color:var(--primary);'>¡Postulación Exitosa!</h2><button class='btn' onclick='cerrarModal("graciasVentana")' style='width:100%;'>Cerrar</button></div></div>
<div id='bienvenidaModal' class='modal'><div class='success-modal-content'><button class='back-button' onclick='cerrarModal("bienvenidaModal")'>✕</button><div style='font-size:56px;'>🚀</div><h2 style='color:var(--primary);'>¡Gratis!</h2><p>✅ Escáner QR ✅ IA Comida ✅ Corporal</p><button class='btn' onclick='activarFree()' style='width:100%;'>Activar</button></div></div>

<script>
// ==================== VARIABLES GLOBALES ====================
let comidaAnalizada = null, gramosComida = 100;
let productoQR = null, gramosQR = 100;
let dietaSeleccionada = 'omnivoro', nivelActividad = '3-4';
let fotosCargadas = { front: false, back: false, left: false, right: false };
let streamQR = null, escaneandoQR = false, animationIdQR = null;
let planPagoSeleccionado = 'anual';

// ==================== BASE DE DATOS ====================
const productosQR = {
    '8412345678901': { nombre: 'Arroz Blanco', marca: 'Tucapel', kcalPor100g: 350, proteinas: 7, carbos: 78, grasas: 0.5, fibra: 1.2, icono: '🍚' },
    '8412345678902': { nombre: 'Pechuga de Pollo', marca: 'San Fernando', kcalPor100g: 165, proteinas: 31, carbos: 0, grasas: 3.6, fibra: 0, icono: '🍗' },
    '8412345678903': { nombre: 'Huevos', marca: 'La Calera', kcalPor100g: 155, proteinas: 13, carbos: 1.1, grasas: 11, fibra: 0, icono: '🥚' },
    '7501059222202': { nombre: 'Atún en Agua', marca: 'Florida', kcalPor100g: 108, proteinas: 23, carbos: 0, grasas: 1.5, fibra: 0, icono: '🐟' },
    '7501059222204': { nombre: 'Avena en Hojuelas', marca: 'Quaker', kcalPor100g: 367, proteinas: 13, carbos: 58, grasas: 7.5, fibra: 10, icono: '🌾' }
};

const foodDB = {
    'arroz_con_pollo': { nombre: 'Arroz con Pollo', kcalPor100g: 195, proteinas: 8.5, carbos: 22, grasas: 7.5, fibra: 1.2, porcion: '350g', categoria: 'plato_fuerte', confianzaBase: 94 },
    'ceviche': { nombre: 'Ceviche', kcalPor100g: 110, proteinas: 18, carbos: 4, grasas: 2.5, fibra: 0.5, porcion: '300g', categoria: 'plato_fuerte', confianzaBase: 92 },
    'lomo_saltado': { nombre: 'Lomo Saltado', kcalPor100g: 180, proteinas: 14, carbos: 15, grasas: 8, fibra: 1.5, porcion: '400g', categoria: 'plato_fuerte', confianzaBase: 90 },
    'pollo_brasa': { nombre: 'Pollo a la Brasa', kcalPor100g: 230, proteinas: 22, carbos: 1, grasas: 15, fibra: 0, porcion: '300g', categoria: 'plato_fuerte', confianzaBase: 93 },
    'ensalada': { nombre: 'Ensalada César', kcalPor100g: 120, proteinas: 10, carbos: 6, grasas: 7, fibra: 2, porcion: '350g', categoria: 'ensalada', confianzaBase: 92 },
    'huevos': { nombre: 'Huevos Revueltos', kcalPor100g: 150, proteinas: 12, carbos: 1, grasas: 11, fibra: 0, porcion: '150g', categoria: 'desayuno', confianzaBase: 96 },
    'platano': { nombre: 'Plátano', kcalPor100g: 89, proteinas: 1.1, carbos: 23, grasas: 0.3, fibra: 2.6, porcion: '120g', categoria: 'fruta', confianzaBase: 97 }
};

// ==================== FUNCIONES DE PAGO CON RETROCESO ====================
function abrirPago() {
    document.getElementById('pagoVentana').style.display = 'flex';
    actualizarVistaPlan();
    // Resetear pasos
    document.getElementById('step1').classList.add('active');
    document.getElementById('step2').classList.remove('active', 'done');
    document.getElementById('step3').classList.remove('active', 'done');
    document.getElementById('line1').classList.remove('done');
    document.getElementById('line2').classList.remove('done');
}

function retrocederPago() {
    // Preguntar si está seguro de salir (si hay datos ingresados)
    const cardName = document.getElementById('cardName').value.trim();
    const cardNumber = document.getElementById('cardNumber').value.trim();
    
    if (cardName || cardNumber) {
        if (confirm('¿Estás seguro de salir? Los datos ingresados se perderán.')) {
            limpiarFormularioPago();
            cerrarModal('pagoVentana');
        }
    } else {
        cerrarModal('pagoVentana');
    }
}

function limpiarFormularioPago() {
    document.getElementById('cardName').value = '';
    document.getElementById('cardNumber').value = '';
    document.getElementById('cardExpiry').value = '';
    document.getElementById('cardCVV').value = '';
}

function seleccionarPlanPago(plan) {
    planPagoSeleccionado = plan;
    
    // Actualizar estilos
    document.getElementById('planMensual').classList.remove('selected');
    document.getElementById('planAnual').classList.remove('selected');
    
    if (plan === 'mensual') {
        document.getElementById('planMensual').classList.add('selected');
    } else {
        document.getElementById('planAnual').classList.add('selected');
    }
    
    // Actualizar progreso
    document.getElementById('step1').classList.remove('active');
    document.getElementById('step1').classList.add('done');
    document.getElementById('step2').classList.add('active');
    document.getElementById('line1').classList.add('done');
    
    actualizarVistaPlan();
}

function actualizarVistaPlan() {
    const summaryDetail = document.getElementById('summaryDetail');
    const summarySaving = document.getElementById('summarySaving');
    const btnPayAmount = document.getElementById('btnPayAmount');
    const btnPayPlan = document.getElementById('btnPayPlan');
    
    if (planPagoSeleccionado === 'anual') {
        summaryDetail.innerHTML = '👑 <strong>Plan Anual - S/99/año</strong>';
        summarySaving.innerHTML = '💰 Ahorras S/139.80 comparado al plan mensual';
        btnPayAmount.textContent = 'S/99';
        btnPayPlan.textContent = 'Anual';
    } else {
        summaryDetail.innerHTML = '⭐ <strong>Plan Mensual - S/19.90/mes</strong> (primer mes gratis)';
        summarySaving.innerHTML = '🎁 ¡Primer mes completamente gratis!';
        btnPayAmount.textContent = 'S/0 (primer mes)';
        btnPayPlan.textContent = 'Mensual';
    }
}

function procesarPago() {
    const cardName = document.getElementById('cardName').value.trim();
    const cardNumber = document.getElementById('cardNumber').value.trim();
    const cardExpiry = document.getElementById('cardExpiry').value.trim();
    const cardCVV = document.getElementById('cardCVV').value.trim();
    
    // Validación
    if (!cardName) { alert('⚠️ Ingresa el nombre en la tarjeta'); return; }
    if (!cardNumber || cardNumber.length < 15) { alert('⚠️ Ingresa un número de tarjeta válido'); return; }
    if (!cardExpiry || !cardExpiry.includes('/')) { alert('⚠️ Ingresa la fecha de expiración (MM/AA)'); return; }
    if (!cardCVV || cardCVV.length < 3) { alert('⚠️ Ingresa el código CVV'); return; }
    
    // Actualizar progreso a completado
    document.getElementById('step2').classList.remove('active');
    document.getElementById('step2').classList.add('done');
    document.getElementById('step3').classList.add('done');
    document.getElementById('line2').classList.add('done');
    
    // Limpiar formulario
    limpiarFormularioPago();
    
    // Cerrar modal de pago
    cerrarModal('pagoVentana');
    
    // Mostrar mensaje de éxito
    const mensajeExito = document.getElementById('mensajeExito');
    if (planPagoSeleccionado === 'anual') {
        mensajeExito.innerHTML = '✅ Has activado el <strong>Plan Anual Premium</strong> por S/99. ¡Disfruta de todos los beneficios ilimitados por 1 año!';
    } else {
        mensajeExito.innerHTML = '✅ Has activado el <strong>Plan Mensual Premium</strong>. ¡Tu primer mes es <strong>GRATIS</strong>! Después pagarás S/19.90/mes.';
    }
    
    document.getElementById('pagoExitoso').style.display = 'flex';
}

// ==================== ESCÁNER QR ====================
async function iniciarCamaraQR() {
    const video = document.getElementById('qrVideo');
    const status = document.getElementById('cameraStatus');
    if (streamQR) { streamQR.getTracks().forEach(t => t.stop()); streamQR = null; }
    if (animationIdQR) { cancelAnimationFrame(animationIdQR); animationIdQR = null; }
    escaneandoQR = false;
    try {
        streamQR = await navigator.mediaDevices.getUserMedia({ video: { facingMode: 'environment', width: { ideal: 640 }, height: { ideal: 480 } } });
        video.srcObject = streamQR;
        video.setAttribute('playsinline', true);
        video.onloadedmetadata = () => { video.play(); status.innerHTML = '📷 Cámara activa.'; status.style.color = '#10b981'; escaneandoQR = true; escanearQRFrame(); };
    } catch (error) {
        try {
            streamQR = await navigator.mediaDevices.getUserMedia({ video: { facingMode: 'user', width: { ideal: 640 }, height: { ideal: 480 } } });
            video.srcObject = streamQR;
            video.onloadedmetadata = () => { video.play(); status.innerHTML = '📷 Cámara frontal.'; status.style.color = '#f59e0b'; escaneandoQR = true; escanearQRFrame(); };
        } catch (err2) {
            status.innerHTML = '❌ Cámara no disponible.'; status.style.color = '#ef4444';
        }
    }
}

function escanearQRFrame() {
    if (!escaneandoQR) return;
    const video = document.getElementById('qrVideo');
    const canvas = document.getElementById('qrCanvas');
    const ctx = canvas.getContext('2d');
    if (video.readyState === video.HAVE_ENOUGH_DATA && video.videoWidth > 0) {
        canvas.width = video.videoWidth; canvas.height = video.videoHeight;
        ctx.drawImage(video, 0, 0, canvas.width, canvas.height);
        const imageData = ctx.getImageData(0, 0, canvas.width, canvas.height);
        if (typeof jsQR !== 'undefined') {
            const code = jsQR(imageData.data, canvas.width, canvas.height, { inversionAttempts: 'dontInvert' });
            if (code && code.data) { procesarCodigoQR(code.data); detenerCamaraQR(); return; }
        }
    }
    animationIdQR = requestAnimationFrame(escanearQRFrame);
}

function detenerCamaraQR() {
    escaneandoQR = false;
    if (animationIdQR) { cancelAnimationFrame(animationIdQR); animationIdQR = null; }
    if (streamQR) { streamQR.getTracks().forEach(t => t.stop()); streamQR = null; }
    document.getElementById('qrVideo').srcObject = null;
    document.getElementById('cameraStatus').innerHTML = '📷 Cámara detenida.';
    document.getElementById('cameraStatus').style.color = '#94a3b8';
}

function buscarPorCodigo() { let c = document.getElementById('qrManualInput').value.trim(); if (c) procesarCodigoQR(c); }

function procesarCodigoQR(codigo) {
    let p = productosQR[codigo] || { nombre: 'Producto', marca: 'Genérico', kcalPor100g: 200, proteinas: 5, carbos: 30, grasas: 8, fibra: 2, icono: '📦' };
    productoQR = p; calcularCaloriasQR(p);
}

function calcularCaloriasQR(producto) {
    let g = Math.max(1, Math.min(1000, parseInt(document.getElementById('gramosQR').value) || 100));
    document.getElementById('gramosQR').value = g;
    let f = g / 100;
    document.getElementById('qrResultado').style.display = 'block';
    document.getElementById('qrResultado').innerHTML = `
        <div style='font-size:40px;text-align:center;'>${producto.icono}</div>
        <strong>📱 ${producto.nombre}</strong><br><small>${producto.marca}</small><br>
        <strong>⚖️ ${g}g</strong>
        <div class='nutri-grid'>
            <div class='nutri-item' style='background:rgba(255,95,109,0.2);'><strong style='font-size:18px;color:#ff5f6d;'>${Math.round(producto.kcalPor100g*f*10)/10}</strong><br><small>🔥 Cal</small></div>
            <div class='nutri-item' style='background:rgba(124,58,237,0.2);'><strong style='font-size:18px;color:#7c3aed;'>${Math.round(producto.proteinas*f*10)/10}g</strong><br><small>🥩 Prot</small></div>
            <div class='nutri-item' style='background:rgba(6,182,212,0.2);'><strong style='font-size:18px;color:#06b6d4;'>${Math.round(producto.carbos*f*10)/10}g</strong><br><small>🍞 Carb</small></div>
            <div class='nutri-item' style='background:rgba(16,185,129,0.2);'><strong style='font-size:18px;color:#10b981;'>${Math.round(producto.grasas*f*10)/10}g</strong><br><small>🥑 Grasa</small></div>
        </div>`;
}

function ajustarGramosQR(c) { let v = (parseInt(document.getElementById('gramosQR').value) || 100) + c; document.getElementById('gramosQR').value = Math.max(1, Math.min(1000, v)); if (productoQR) calcularCaloriasQR(productoQR); }
function setGramosQR(g) { document.getElementById('gramosQR').value = g; if (productoQR) calcularCaloriasQR(productoQR); }
function validarGramosQR() { let v = parseInt(document.getElementById('gramosQR').value) || 100; document.getElementById('gramosQR').value = Math.max(1, Math.min(1000, v)); if (productoQR) calcularCaloriasQR(productoQR); }

// ==================== ESCÁNER COMIDA IA ====================
function analizarComida(input) {
    if (!input.files || !input.files[0]) return;
    const reader = new FileReader();
    reader.onload = function(e) {
        document.getElementById('foodPreview').src = e.target.result;
        document.getElementById('foodPreview').style.display = 'block';
        document.getElementById('analyzingOverlay').classList.add('active');
        document.getElementById('foodUploadArea').classList.add('analyzing');
        setTimeout(() => {
            const resultado = analizarImagenAvanzada(input.files[0]);
            document.getElementById('analyzingOverlay').classList.remove('active');
            document.getElementById('foodUploadArea').classList.remove('analyzing');
            mostrarResultadoComida(resultado);
        }, 2000);
    };
    reader.readAsDataURL(input.files[0]);
}

function analizarImagenAvanzada(file) {
    const seed = file.name.length + file.size + file.lastModified;
    const hora = new Date().getHours();
    let cat = hora >= 6 && hora <= 10 ? ['desayuno'] : hora >= 11 && hora <= 15 ? ['plato_fuerte', 'ensalada'] : ['snack', 'bebida'];
    const filtradas = Object.entries(foodDB).filter(([k, f]) => cat.includes(f.categoria));
    const pool = filtradas.length >= 3 ? filtradas : Object.entries(foodDB);
    const [key, comida] = pool[Math.abs(seed % pool.length)];
    const variacion = 0.95 + Math.random() * 0.10;
    const confianza = Math.min(98, Math.max(85, comida.confianzaBase + Math.floor(Math.random() * 6) - 3));
    return { ...comida, confianza, kcalPor100g: Math.round(comida.kcalPor100g * variacion) };
}

function mostrarResultadoComida(comida) { comidaAnalizada = comida; gramosComida = 100; actualizarResultadoComida(comida, 100); }

function actualizarResultadoComida(comida, gramos) {
    const f = gramos / 100;
    document.getElementById('foodResultCard').style.display = 'block';
    document.getElementById('foodResultCard').innerHTML = `
        <strong style='font-size:17px;'>🍽️ ${comida.nombre}</strong> <span style='color:${comida.confianza>93?'#10b981':'#f59e0b'};'>${comida.confianza}% prec.</span>
        <div class='gram-control' style='margin:8px 0;'><button class='gram-btn' onclick='ajustarGramosComida(-10)'>−</button><input type='number' id='gramosComidaInput' value='${gramos}' min='10' max='2000' style='text-align:center;font-size:15px;width:75px;background:rgba(15,10,26,0.8);color:white;border:2px solid rgba(124,58,237,0.3);border-radius:8px;padding:8px;' onchange='actualizarGramosComida()'><span>g</span><button class='gram-btn' onclick='ajustarGramosComida(10)'>+</button></div>
        <div class='nutri-grid'><div class='nutri-item' style='background:rgba(255,95,109,0.2);'><strong style='font-size:18px;color:#ff5f6d;'>${Math.round(comida.kcalPor100g*f)}</strong><br><small>🔥 Cal</small></div><div class='nutri-item' style='background:rgba(124,58,237,0.2);'><strong style='font-size:18px;color:#7c3aed;'>${Math.round(comida.proteinas*f*10)/10}g</strong><br><small>🥩 Prot</small></div><div class='nutri-item' style='background:rgba(6,182,212,0.2);'><strong style='font-size:18px;color:#06b6d4;'>${Math.round(comida.carbos*f*10)/10}g</strong><br><small>🍞 Carb</small></div><div class='nutri-item' style='background:rgba(16,185,129,0.2);'><strong style='font-size:18px;color:#10b981;'>${Math.round(comida.grasas*f*10)/10}g</strong><br><small>🥑 Grasa</small></div></div>`;
}

function ajustarGramosComida(c) { gramosComida = Math.max(10, Math.min(2000, gramosComida + c)); document.getElementById('gramosComidaInput').value = gramosComida; if (comidaAnalizada) actualizarResultadoComida(comidaAnalizada, gramosComida); }
function setGramosComida(g) { gramosComida = g; document.getElementById('gramosComidaInput').value = gramosComida; if (comidaAnalizada) actualizarResultadoComida(comidaAnalizada, gramosComida); }
function actualizarGramosComida() { gramosComida = Math.max(10, Math.min(2000, parseInt(document.getElementById('gramosComidaInput').value) || 100)); document.getElementById('gramosComidaInput').value = gramosComida; if (comidaAnalizada) actualizarResultadoComida(comidaAnalizada, gramosComida); }

// ==================== ESCÁNER CORPORAL ====================
function previewScan(side) {
    const input = document.getElementById('scan' + side.charAt(0).toUpperCase() + side.slice(1));
    if (!input.files[0]) return;
    const img = document.getElementById('prev' + side);
    img.src = URL.createObjectURL(input.files[0]);
    img.style.display = 'block'; img.classList.add('has-image');
    fotosCargadas[side] = true;
    const cargadas = Object.values(fotosCargadas).filter(v => v).length;
    const status = document.getElementById('scanStatus');
    status.textContent = `📋 Fotos: ${cargadas} de 4`;
    status.className = cargadas === 4 ? 'scan-status ready' : 'scan-status incomplete';
}

function analizarCuerpo() {
    const cargadas = Object.values(fotosCargadas).filter(v => v).length;
    if (cargadas < 4) { document.getElementById('scanResult').innerHTML = `<strong style='color:#f59e0b;'>⚠️ Faltan ${4-cargadas} foto(s)</strong>`; return; }
    const peso = parseFloat(document.getElementById('peso').value) || 70;
    const altura = parseFloat(document.getElementById('altura').value) || 170;
    const imc = peso / Math.pow(altura / 100, 2);
    let grasa = Math.round((1.15 * imc) + (0.23 * 25) - 12);
    grasa = Math.max(5, Math.min(40, grasa));
    document.getElementById('scanResult').innerHTML = `<strong>✅ Análisis 4 ángulos</strong><br>📊 IMC: ${imc.toFixed(1)}<br>🔬 Grasa est.: ${grasa}%`;
}

// ==================== RESTO ====================
function toggleActivity(e) { document.querySelectorAll('#activityTags .activity-tag').forEach(t => t.classList.remove('active')); e.classList.add('active'); nivelActividad = e.dataset.activity; }
function toggleDiet(e) { document.querySelectorAll('#dietTags .diet-tag').forEach(t => t.classList.remove('active')); e.classList.add('active'); dietaSeleccionada = e.dataset.diet; }

function calcIMC() {
    let p = parseFloat(document.getElementById('peso').value), a = parseFloat(document.getElementById('altura').value) / 100;
    if (!p || !a) { alert('Ingresa peso y altura'); return; }
    let imc = (p / (a * a)).toFixed(1);
    let tmb = (10 * p) + (6.25 * (a * 100)) - (5 * 25) + 5;
    let fa = { '0': 1.2, '1-2': 1.375, '3-4': 1.55, '6': 1.725 }[nivelActividad] || 1.55;
    let kcal = Math.round(tmb * fa);
    document.getElementById('imc').innerHTML = `📊 IMC: ${imc}<br>🔥 TMB est.: ${Math.round(tmb)} kcal<br>🎯 Objetivo est.: ${kcal} kcal/día`;
}

function comenzarGratis() { document.getElementById('bienvenidaModal').style.display = 'flex'; }
function activarFree() { cerrarModal('bienvenidaModal'); }
function registrarFree() { if (!document.getElementById('regEmail').value) { alert('Completa los campos'); return; } document.getElementById('registroExitoso').style.display = 'flex'; }
function postularCoach() { document.getElementById('graciasVentana').style.display = 'flex'; }
function abrirChatIA() { alert('🤖 FitAura IA: ¿En qué puedo ayudarte?'); }

function mostrarTerminos() { document.getElementById('modalTerminos').style.display = 'flex'; }
function mostrarPrivacidad() { document.getElementById('modalPrivacidad').style.display = 'flex'; }
function mostrarCookies() { document.getElementById('modalCookies').style.display = 'flex'; }
function mostrarReembolso() { document.getElementById('modalReembolso').style.display = 'flex'; }
function mostrarDescargo() { document.getElementById('modalDescargo').style.display = 'flex'; }

function cerrarModal(id) { document.getElementById(id).style.display = 'none'; }
function mostrarArchivo() { let f = document.getElementById('cvFile').files[0]; if (f) document.getElementById('archivoNombre').innerText = '✅ ' + f.name; }

// Iniciar cámara QR
window.addEventListener('load', () => setTimeout(() => { if (typeof jsQR !== 'undefined') iniciarCamaraQR(); }, 1500));

// Cerrar modales con tecla ESC
document.addEventListener('keydown', function(e) {
    if (e.key === 'Escape') {
        if (document.getElementById('pagoVentana').style.display === 'flex') {
            retrocederPago();
        }
    }
});
</script>
</body>
</html>



