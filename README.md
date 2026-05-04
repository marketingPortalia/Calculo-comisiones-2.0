
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:'Segoe UI',Arial,sans-serif;background:#f5f4f0;color:#1a1a1a;font-size:14px}
:root{--gold:#C9A84C;--gold-light:#F0D080;--dark:#1C1C1C;--dark2:#2a2a2a;--white:#fff;--gray:#f0ede6;--border:#e0d9cc;--muted:#6b6460;--success:#2d7a4f;--danger:#b94040}

/* AUTH */
.auth-wrap{min-height:100vh;display:flex;align-items:center;justify-content:center;background:#f5f4f0;padding:24px}
.auth-box{background:var(--white);border-radius:14px;border:1px solid var(--border);padding:36px 32px;width:100%;max-width:400px}
.auth-logo{text-align:center;margin-bottom:28px}
.auth-logo-text{font-size:26px;font-weight:900;letter-spacing:3px;color:var(--dark)}
.auth-logo-gold{color:var(--gold)}
.auth-logo-sub{font-size:11px;letter-spacing:2px;color:var(--muted);text-transform:uppercase;margin-top:2px}
.auth-title{font-size:18px;font-weight:700;margin-bottom:4px;color:var(--dark)}
.auth-sub{font-size:13px;color:var(--muted);margin-bottom:24px}
.auth-tab-bar{display:flex;border-bottom:1px solid var(--border);margin-bottom:24px}
.auth-tab{flex:1;padding:10px;text-align:center;cursor:pointer;font-size:13px;font-weight:600;color:var(--muted);border-bottom:2px solid transparent;margin-bottom:-1px;transition:all .2s}
.auth-tab.active{color:var(--gold);border-bottom:2px solid var(--gold)}
.field{margin-bottom:14px}
.field label{display:block;font-size:11px;color:var(--muted);margin-bottom:4px;font-weight:600;letter-spacing:.5px;text-transform:uppercase}
.field input{width:100%;padding:10px 12px;border:1px solid var(--border);border-radius:7px;font-size:13px;outline:none;transition:border .2s;background:var(--white);color:#1a1a1a}
.field input:focus{border-color:var(--gold)}
.btn-full{width:100%;padding:11px;border-radius:7px;border:none;cursor:pointer;font-size:14px;font-weight:700;transition:all .2s}
.btn-auth{background:var(--gold);color:var(--dark);letter-spacing:.5px}
.btn-auth:hover{background:var(--gold-light)}
.btn-auth:disabled{opacity:.6;cursor:not-allowed}
.auth-alert{padding:10px 12px;border-radius:6px;font-size:12px;margin-bottom:14px}
.auth-alert.err{background:#fde8e8;color:var(--danger);border:1px solid #f0bcbc}
.auth-alert.ok{background:#d4edda;color:#2d7a4f;border:1px solid #a3d4b3}
.auth-link{text-align:center;margin-top:14px;font-size:12px;color:var(--muted)}
.auth-link span{color:var(--gold);cursor:pointer;font-weight:600}

/* APP */
.app{min-height:100vh;display:flex;flex-direction:column;display:none}
.header{background:var(--dark);padding:0 24px;display:flex;align-items:center;justify-content:space-between;height:56px;border-bottom:2px solid var(--gold)}
.logo-text{font-size:18px;font-weight:700;letter-spacing:2px;color:var(--gold)}
.logo-sub{font-size:10px;color:#aaa;letter-spacing:1px;text-transform:uppercase}
.user-bar{display:flex;align-items:center;gap:12px}
.user-name{font-size:13px;color:#ddd}
.btn-logout{padding:5px 12px;border-radius:5px;border:1px solid #444;background:transparent;color:#aaa;cursor:pointer;font-size:12px;transition:all .2s}
.btn-logout:hover{border-color:var(--gold);color:var(--gold)}
.nav{background:var(--dark2);display:flex;border-bottom:1px solid #333;overflow-x:auto}
.nav-btn{padding:12px 18px;color:#aaa;background:none;border:none;cursor:pointer;font-size:13px;border-bottom:2px solid transparent;transition:all .2s;white-space:nowrap}
.nav-btn.active{color:var(--gold);border-bottom:2px solid var(--gold)}
.nav-btn:hover{color:#ddd}
.main{flex:1;padding:20px 24px;max-width:1100px;margin:0 auto;width:100%}
.section{display:none}.section.active{display:block}
.card{background:var(--white);border-radius:10px;border:1px solid var(--border);padding:20px;margin-bottom:16px}
.card-title{font-size:13px;font-weight:700;color:var(--dark);margin-bottom:16px;text-transform:uppercase;letter-spacing:1px;display:flex;align-items:center;gap:8px}
.card-title::before{content:'';display:inline-block;width:3px;height:16px;background:var(--gold);border-radius:2px}
.grid2{display:grid;grid-template-columns:1fr 1fr;gap:16px}
.grid3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px}
.grid4{display:grid;grid-template-columns:repeat(4,1fr);gap:12px}
label{display:block;font-size:11px;color:var(--muted);margin-bottom:4px;font-weight:600;letter-spacing:.5px;text-transform:uppercase}
input,select{width:100%;padding:9px 12px;border:1px solid var(--border);border-radius:6px;font-size:13px;background:var(--white);color:#1a1a1a;outline:none;transition:border .2s}
input:focus,select:focus{border-color:var(--gold)}
input[readonly]{background:var(--gray)}
.btn{padding:10px 20px;border-radius:6px;border:none;cursor:pointer;font-size:13px;font-weight:600;transition:all .2s}
.btn-gold{background:var(--gold);color:var(--dark)}.btn-gold:hover{background:var(--gold-light)}
.btn-outline{background:transparent;border:1px solid var(--border);color:var(--muted)}.btn-outline:hover{border-color:var(--gold);color:var(--gold)}
.btn-danger-sm{background:transparent;border:1px solid #e0c0c0;color:var(--danger);font-size:12px;padding:5px 10px;border-radius:6px;cursor:pointer}
.btn-edit{background:transparent;border:1px solid #c0d4e0;color:#1a6fa0;font-size:12px;padding:5px 10px;border-radius:6px;cursor:pointer}
.btn-sm{padding:6px 12px;font-size:12px}
.btn-green{background:#2d7a4f;color:#fff;border:none}.btn-green:hover{background:#256040}
.metric-card{background:var(--gray);border-radius:8px;padding:16px;border:1px solid var(--border)}
.metric-label{font-size:11px;color:var(--muted);text-transform:uppercase;letter-spacing:.5px;margin-bottom:4px}
.metric-value{font-size:22px;font-weight:700;color:var(--dark)}
.metric-sub{font-size:11px;color:var(--muted);margin-top:2px}
.metric-gold .metric-value{color:var(--gold)}
.ticket-row{display:grid;grid-template-columns:1fr 1fr 90px 40px;gap:8px;align-items:end;margin-bottom:8px}
.table-wrap{overflow-x:auto}
table{width:100%;border-collapse:collapse;font-size:13px}
th{background:var(--dark);color:var(--gold);padding:10px 12px;text-align:left;font-size:11px;letter-spacing:.5px;text-transform:uppercase}
td{padding:9px 12px;border-bottom:1px solid var(--border);vertical-align:middle}
tr:hover td{background:#fafaf7}
.badge{display:inline-block;padding:3px 8px;border-radius:4px;font-size:11px;font-weight:600}
.badge-firmado{background:#d4edda;color:#2d7a4f}
.badge-pendiente{background:#fff3cd;color:#856404}
.badge-mandato{background:#d1ecf1;color:#0c5460}
.badge-convenio{background:#e2d9f3;color:#4a237a}
.divider{height:1px;background:var(--border);margin:12px 0}
.total-box{background:var(--dark);color:#fff;border-radius:8px;padding:16px 20px;display:flex;align-items:center;justify-content:space-between}
.total-label{font-size:12px;color:#aaa;text-transform:uppercase;letter-spacing:1px}
.total-value{font-size:28px;font-weight:700;color:var(--gold)}
.radio-group{display:flex;gap:10px}
.radio-btn{flex:1;padding:8px;border:1px solid var(--border);border-radius:6px;cursor:pointer;text-align:center;font-size:12px;font-weight:600;transition:all .2s;color:var(--muted)}
.radio-btn.selected{border-color:var(--gold);background:#fdf8ec;color:var(--dark)}
.section-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:16px;flex-wrap:wrap;gap:8px}
.section-title{font-size:20px;font-weight:700;color:var(--dark)}
.section-sub{font-size:12px;color:var(--muted);margin-top:2px}
.alert{padding:10px 14px;border-radius:6px;font-size:13px;margin-bottom:12px}
.alert-success{background:#d4edda;color:#2d7a4f;border:1px solid #a3d4b3}
.alert-danger{background:#fde8e8;color:var(--danger);border:1px solid #f0bcbc}
.filter-bar{display:flex;gap:10px;align-items:end;flex-wrap:wrap;margin-bottom:16px}
.filter-bar .f{flex:1;min-width:130px}
.obj-bar-wrap{margin-bottom:14px}
.obj-bar-label{display:flex;justify-content:space-between;font-size:12px;color:var(--muted);margin-bottom:4px}
.obj-bar{height:10px;background:#e0d9cc;border-radius:5px;overflow:hidden}
.obj-bar-fill{height:100%;background:var(--gold);border-radius:5px;transition:width .6s}
.obj-bar-fill.over{background:#2d7a4f}
.chart-wrap{position:relative;width:100%;height:220px}
.chart-wrap-sm{position:relative;width:100%;height:190px}
.empty-msg{color:var(--muted);font-size:13px;text-align:center;padding:32px 0}
.drop-zone{border:2px dashed var(--border);border-radius:10px;padding:40px 24px;text-align:center;cursor:pointer;transition:all .2s;background:var(--gray)}
.drop-zone:hover,.drop-zone.drag-over{border-color:var(--gold);background:#fdf8ec}
.preview-table-wrap{max-height:300px;overflow-y:auto;border:1px solid var(--border);border-radius:8px}
.row-ok td:first-child{border-left:3px solid #2d7a4f}
.row-err td:first-child{border-left:3px solid var(--danger)}
.row-warn td:first-child{border-left:3px solid #e8a020}
.import-summary{display:flex;gap:12px;flex-wrap:wrap;margin-bottom:12px}
.imp-badge{padding:6px 14px;border-radius:6px;font-size:12px;font-weight:700}
.imp-ok{background:#d4edda;color:#2d7a4f}.imp-warn{background:#fff3cd;color:#856404}.imp-err{background:#fde8e8;color:var(--danger)}
.template-box{background:var(--gray);border-radius:8px;padding:16px;border:1px solid var(--border);margin-bottom:12px}
.col-def{display:flex;align-items:baseline;gap:8px;margin-bottom:6px;font-size:13px}
.col-name{font-weight:700;color:var(--dark);min-width:190px}
.col-desc{color:var(--muted);font-size:12px}
.col-req{font-size:10px;font-weight:700;padding:2px 6px;border-radius:4px;background:#fde8e8;color:var(--danger)}
.col-opt{font-size:10px;font-weight:700;padding:2px 6px;border-radius:4px;background:#e8f4fd;color:#1a6fa0}
.step{display:flex;gap:12px;margin-bottom:16px;align-items:flex-start}
.step-num{background:var(--gold);color:var(--dark);width:24px;height:24px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;flex-shrink:0;margin-top:1px}
.step-title{font-weight:700;font-size:13px;margin-bottom:3px}
.step-desc{font-size:12px;color:var(--muted);line-height:1.5}
.modal-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,0.5);z-index:1000;align-items:center;justify-content:center}
.modal-overlay.open{display:flex}
.modal{background:var(--white);border-radius:12px;padding:24px;width:94%;max-width:680px;max-height:90vh;overflow-y:auto;border:1px solid var(--border)}
.modal-sm{background:var(--white);border-radius:12px;padding:24px;width:94%;max-width:420px;border:1px solid var(--border)}
.modal-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:20px}
.modal-title{font-size:17px;font-weight:700;color:var(--dark)}
.modal-close{background:none;border:none;cursor:pointer;font-size:20px;color:var(--muted);line-height:1}
.obj-tab-bar{display:flex;gap:8px;margin-bottom:16px;flex-wrap:wrap}
.obj-tab{padding:7px 16px;border-radius:6px;border:1px solid var(--border);cursor:pointer;font-size:12px;font-weight:600;color:var(--muted);background:transparent;transition:all .2s}
.obj-tab.active{border-color:var(--gold);background:#fdf8ec;color:var(--dark)}
.loading-overlay{display:none;position:fixed;inset:0;background:rgba(245,244,240,0.85);z-index:2000;align-items:center;justify-content:center;flex-direction:column;gap:12px}
.loading-overlay.show{display:flex}
.spinner{width:36px;height:36px;border:3px solid var(--border);border-top:3px solid var(--gold);border-radius:50%;animation:spin .7s linear infinite}
@keyframes spin{to{transform:rotate(360deg)}}
.loading-text{font-size:13px;color:var(--muted)}
</style>
</head>
<body>

<!-- LOADING -->
<div class="loading-overlay" id="loadingOverlay">
  <div class="spinner"></div>
  <div class="loading-text" id="loadingText">Cargando...</div>
</div>

<!-- AUTH -->
<div class="auth-wrap" id="authWrap">
  <div class="auth-box">
    <div class="auth-logo">
      <div class="auth-logo-text">PORT<span class="auth-logo-gold">ALIA</span></div>
      <div class="auth-logo-sub">Desarrollos · Comisiones</div>
    </div>
    <div class="auth-tab-bar">
      <div class="auth-tab active" id="tab-login" onclick="switchTab('login')">Iniciar sesión</div>
      <div class="auth-tab" id="tab-registro" onclick="switchTab('registro')">Crear cuenta</div>
    </div>
    <div id="auth_alert"></div>

    <!-- LOGIN -->
    <div id="form-login">
      <div class="field"><label>Correo electrónico</label><input type="email" id="login_email" placeholder="tu@correo.com" onkeydown="if(event.key==='Enter')doLogin()"/></div>
      <div class="field"><label>Contraseña</label><input type="password" id="login_pass" placeholder="••••••••" onkeydown="if(event.key==='Enter')doLogin()"/></div>
      <button class="btn-full btn-auth" id="btn_login" onclick="doLogin()">Entrar</button>
      <div class="auth-link" style="margin-top:10px"><span onclick="switchTab('reset')">¿Olvidaste tu contraseña?</span></div>
    </div>

    <!-- REGISTRO -->
    <div id="form-registro" style="display:none">
      <div class="field"><label>Tu nombre completo</label><input type="text" id="reg_nombre" placeholder="Ej. Sofía Ramírez González"/></div>
      <div class="field"><label>Correo electrónico</label><input type="email" id="reg_email" placeholder="tu@correo.com"/></div>
      <div class="field"><label>Contraseña</label><input type="password" id="reg_pass" placeholder="Mínimo 6 caracteres"/></div>
      <div class="field"><label>Confirmar contraseña</label><input type="password" id="reg_pass2" placeholder="Repite tu contraseña" onkeydown="if(event.key==='Enter')doRegistro()"/></div>
      <button class="btn-full btn-auth" id="btn_registro" onclick="doRegistro()">Crear cuenta</button>
    </div>

    <!-- RESET -->
    <div id="form-reset" style="display:none">
      <div style="font-size:13px;color:var(--muted);margin-bottom:16px">Ingresa tu correo y te enviaremos un enlace para restablecer tu contraseña.</div>
      <div class="field"><label>Correo electrónico</label><input type="email" id="reset_email" placeholder="tu@correo.com" onkeydown="if(event.key==='Enter')doReset()"/></div>
      <button class="btn-full btn-auth" id="btn_reset" onclick="doReset()">Enviar enlace</button>
      <div class="auth-link"><span onclick="switchTab('login')">← Volver al inicio de sesión</span></div>
    </div>
  </div>
</div>

<!-- APP -->
<div class="app" id="appWrap">
  <div class="header">
    <div><div class="logo-text">PORTALIA</div><div class="logo-sub">Desarrollos</div></div>
    <div class="user-bar">
      <div class="user-name" id="headerUserName"></div>
      <button class="btn-logout" onclick="doLogout()">Cerrar sesión</button>
    </div>
  </div>
  <div class="nav">
    <button class="nav-btn active" onclick="showSection('registrar',this)">+ Nueva venta</button>
    <button class="nav-btn" onclick="showSection('importar',this)">Importar</button>
    <button class="nav-btn" onclick="showSection('historial',this)">Historial</button>
    <button class="nav-btn" onclick="showSection('dashboard',this)">Dashboard</button>
    <button class="nav-btn" onclick="showSection('objetivos',this)">Objetivos</button>
  </div>
  <div class="main">

    <!-- REGISTRAR -->
    <div class="section active" id="sec-registrar">
      <div class="section-header">
        <div><div class="section-title">Registrar venta</div><div class="section-sub">Ingresa los datos del inversionista</div></div>
      </div>
      <div id="alertBox"></div>
      <div class="card">
        <div class="card-title">Datos del inversionista</div>
        <div class="grid2" style="margin-bottom:12px">
          <div><label>Nombre del inversionista</label><input id="inv_nombre" placeholder="Ej. Juan García López"/></div>
          <div><label>Fecha de venta</label><input type="date" id="inv_fecha"/></div>
        </div>
        <div class="grid2">
          <div><label>Tipo de contrato</label>
            <div class="radio-group" id="tipo_contrato">
              <div class="radio-btn selected" data-val="mandato" onclick="selectRadio(this,'tipo_contrato')">Mandato</div>
              <div class="radio-btn" data-val="convenio" onclick="selectRadio(this,'tipo_contrato')">Convenio modificatorio</div>
            </div>
          </div>
          <div><label>¿Firmó contrato?</label>
            <div class="radio-group" id="firmo">
              <div class="radio-btn selected" data-val="si" onclick="selectRadio(this,'firmo')">Sí firmó</div>
              <div class="radio-btn" data-val="no" onclick="selectRadio(this,'firmo')">Pendiente</div>
            </div>
          </div>
        </div>
      </div>
      <div class="card">
        <div class="card-title">Tickets de inversión</div>
        <div id="ticketsContainer"></div>
        <button class="btn btn-outline btn-sm" onclick="addTicket()">+ Agregar ticket</button>
        <div class="divider"></div>
        <div class="grid2"><div><label>% Comisión</label><input type="number" id="pct_comision" placeholder="Ej. 3" step="0.1" min="0" max="100" oninput="calcular()"/></div><div></div></div>
      </div>
      <div class="total-box" style="margin-bottom:16px">
        <div><div class="total-label">Total de venta</div><div style="font-size:13px;color:#ccc;margin-top:2px" id="res_tickets">0 tickets</div></div>
        <div style="text-align:right"><div class="total-label">Tu comisión estimada</div><div class="total-value" id="res_comision">$0.00</div></div>
      </div>
      <div style="display:flex;gap:10px;justify-content:flex-end">
        <button class="btn btn-outline" onclick="limpiarForm()">Limpiar</button>
        <button class="btn btn-gold" onclick="guardarVenta()">Guardar venta</button>
      </div>
    </div>

    <!-- IMPORTAR -->
    <div class="section" id="sec-importar">
      <div class="section-header"><div><div class="section-title">Importar datos</div><div class="section-sub">Carga múltiples ventas desde un CSV</div></div></div>
      <div class="card">
        <div class="card-title">Paso 1 — Descarga la plantilla</div>
        <div class="template-box">
          <div style="font-size:12px;font-weight:700;color:var(--dark);margin-bottom:10px;text-transform:uppercase;letter-spacing:.5px">Columnas requeridas</div>
          <div class="col-def"><span class="col-name">fecha</span><span class="col-req">Obligatorio</span><span class="col-desc">AAAA-MM-DD</span></div>
          <div class="col-def"><span class="col-name">nombre_inversionista</span><span class="col-req">Obligatorio</span><span class="col-desc">Nombre completo</span></div>
          <div class="col-def"><span class="col-name">precio_ticket</span><span class="col-req">Obligatorio</span><span class="col-desc">Precio unitario MXN</span></div>
          <div class="col-def"><span class="col-name">cantidad_tickets</span><span class="col-req">Obligatorio</span><span class="col-desc">Número de tickets</span></div>
          <div class="col-def"><span class="col-name">porcentaje_comision</span><span class="col-req">Obligatorio</span><span class="col-desc">Sin % · Ej: 3.5</span></div>
          <div class="col-def"><span class="col-name">tipo_contrato</span><span class="col-opt">Opcional</span><span class="col-desc">mandato / convenio</span></div>
          <div class="col-def"><span class="col-name">firmo_contrato</span><span class="col-opt">Opcional</span><span class="col-desc">si / no</span></div>
        </div>
        <div style="display:flex;gap:10px;flex-wrap:wrap">
          <button class="btn btn-gold" onclick="descargarPlantillaCSV()">Descargar plantilla</button>
          <button class="btn btn-outline" onclick="descargarPlantillaEjemplo()">Descargar con ejemplos</button>
        </div>
      </div>
      <div class="card">
        <div class="card-title">Paso 2 — Sube tu CSV</div>
        <div class="drop-zone" id="dropZone" onclick="document.getElementById('fileInput').click()" ondragover="dragOver(event)" ondragleave="dragLeave()" ondrop="dropFile(event)">
          <div style="font-size:32px;margin-bottom:8px">📂</div>
          <div style="font-size:15px;font-weight:700;color:var(--dark);margin-bottom:4px">Arrastra tu CSV aquí</div>
          <div style="font-size:12px;color:var(--muted)">o haz clic para buscar</div>
        </div>
        <input type="file" id="fileInput" accept=".csv" style="display:none" onchange="handleFile(this.files[0])"/>
      </div>
      <div id="preview_section" style="display:none">
        <div class="card">
          <div class="card-title">Paso 3 — Revisa y confirma</div>
          <div id="import_summary" class="import-summary"></div>
          <div id="import_alert" style="margin-bottom:12px"></div>
          <div class="preview-table-wrap">
            <table><thead><tr><th>#</th><th>Fecha</th><th>Inversionista</th><th>Precio</th><th>Qty</th><th>Total</th><th>Comisión</th><th>Tipo</th><th>Firma</th><th>Estado</th></tr></thead>
            <tbody id="preview_tbody"></tbody></table>
          </div>
          <div style="display:flex;gap:10px;justify-content:flex-end;margin-top:16px" id="import_actions"></div>
        </div>
      </div>
    </div>

    <!-- HISTORIAL -->
    <div class="section" id="sec-historial">
      <div class="section-header">
        <div><div class="section-title">Historial de ventas</div><div class="section-sub">Tus operaciones registradas</div></div>
        <div style="display:flex;gap:8px;flex-wrap:wrap">
          <button class="btn btn-outline btn-sm" onclick="exportCSV()">Exportar CSV</button>
          <button class="btn btn-gold btn-sm" onclick="abrirModalPDF()">Exportar PDF</button>
        </div>
      </div>
      <div class="card">
        <div class="filter-bar">
          <div class="f"><label>Desde</label><input type="date" id="f_desde" onchange="renderHistorial()"/></div>
          <div class="f"><label>Hasta</label><input type="date" id="f_hasta" onchange="renderHistorial()"/></div>
          <div class="f"><label>Tipo</label><select id="f_tipo" onchange="renderHistorial()"><option value="">Todos</option><option value="mandato">Mandato</option><option value="convenio">Convenio</option></select></div>
          <div class="f"><label>Contrato</label><select id="f_firma" onchange="renderHistorial()"><option value="">Todos</option><option value="si">Firmado</option><option value="no">Pendiente</option></select></div>
        </div>
        <div class="table-wrap">
          <table><thead><tr><th>Fecha</th><th>Inversionista</th><th>Tickets</th><th>Total</th><th>Comisión</th><th>Tipo</th><th>Contrato</th><th></th></tr></thead>
          <tbody id="tablaHistorial"><tr><td colspan="8" class="empty-msg">Cargando...</td></tr></tbody></table>
        </div>
        <div id="historial_totales" style="margin-top:12px"></div>
      </div>
    </div>

    <!-- DASHBOARD -->
    <div class="section" id="sec-dashboard">
      <div class="section-header"><div><div class="section-title">Dashboard</div><div class="section-sub">Resultados por período</div></div></div>
      <div class="card">
        <div class="filter-bar">
          <div class="f"><label>Desde</label><input type="date" id="d_desde" onchange="renderDashboard()"/></div>
          <div class="f"><label>Hasta</label><input type="date" id="d_hasta" onchange="renderDashboard()"/></div>
          <button class="btn btn-gold btn-sm" style="margin-bottom:0" onclick="setDashPeriod('mes')">Este mes</button>
          <button class="btn btn-outline btn-sm" style="margin-bottom:0" onclick="setDashPeriod('trimestre')">Trimestre</button>
          <button class="btn btn-outline btn-sm" style="margin-bottom:0" onclick="setDashPeriod('año')">Este año</button>
        </div>
      </div>
      <div class="grid4" style="margin-bottom:16px" id="dash_metrics">
        <div class="metric-card"><div class="metric-label">Total ventas</div><div class="metric-value">—</div></div>
        <div class="metric-card metric-gold"><div class="metric-label">Comisiones</div><div class="metric-value">—</div></div>
        <div class="metric-card"><div class="metric-label">Tickets</div><div class="metric-value">—</div></div>
        <div class="metric-card"><div class="metric-label">Firmados</div><div class="metric-value">—</div></div>
      </div>
      <div class="grid2" style="margin-bottom:16px">
        <div class="card" style="margin-bottom:0"><div class="card-title">Ventas por mes</div><div class="chart-wrap"><canvas id="chartVentas"></canvas></div></div>
        <div class="card" style="margin-bottom:0"><div class="card-title">Comisiones por mes</div><div class="chart-wrap"><canvas id="chartComisiones"></canvas></div></div>
      </div>
      <div class="grid2">
        <div class="card" style="margin-bottom:0"><div class="card-title">Tipo de contrato</div><div class="chart-wrap-sm"><canvas id="chartTipo"></canvas></div></div>
        <div class="card" style="margin-bottom:0"><div class="card-title">Firmados vs pendientes</div><div class="chart-wrap-sm"><canvas id="chartFirma"></canvas></div></div>
      </div>
    </div>

    <!-- OBJETIVOS -->
    <div class="section" id="sec-objetivos">
      <div class="section-header"><div><div class="section-title">Objetivos mensuales</div><div class="section-sub">Define metas por mes y mide tu avance</div></div></div>
      <div class="card">
        <div class="card-title">Seleccionar mes</div>
        <div class="obj-tab-bar" id="obj_tab_bar"></div>
        <div class="grid3">
          <div><label>Objetivo ventas (MXN)</label><input type="number" id="obj_ventas" placeholder="Ej. 5000000" oninput="guardarObjetivo()"/></div>
          <div><label>Objetivo comisiones (MXN)</label><input type="number" id="obj_comisiones" placeholder="Ej. 150000" oninput="guardarObjetivo()"/></div>
          <div><label>Objetivo # de cierres</label><input type="number" id="obj_cierres" placeholder="Ej. 5" oninput="guardarObjetivo()"/></div>
        </div>
      </div>
      <div class="card" id="obj_progreso"><div class="empty-msg">Selecciona un mes y configura tus objetivos</div></div>
      <div class="card"><div class="card-title">Resumen anual</div><div id="obj_resumen_anual"><div class="empty-msg">Sin objetivos configurados</div></div></div>
    </div>

  </div>
</div>

<!-- MODAL editar -->
<div class="modal-overlay" id="modalEditar">
  <div class="modal">
    <div class="modal-header"><div class="modal-title">Editar venta</div><button class="modal-close" onclick="cerrarModal('modalEditar')">✕</button></div>
    <div id="modal_alertBox"></div>
    <div class="card" style="margin-bottom:12px">
      <div class="card-title">Datos del inversionista</div>
      <div class="grid2" style="margin-bottom:12px">
        <div><label>Nombre</label><input id="edit_nombre" placeholder="Nombre completo"/></div>
        <div><label>Fecha</label><input type="date" id="edit_fecha"/></div>
      </div>
      <div class="grid2">
        <div><label>Tipo de contrato</label>
          <div class="radio-group" id="edit_tipo_contrato">
            <div class="radio-btn" data-val="mandato" onclick="selectRadio(this,'edit_tipo_contrato')">Mandato</div>
            <div class="radio-btn" data-val="convenio" onclick="selectRadio(this,'edit_tipo_contrato')">Convenio modificatorio</div>
          </div>
        </div>
        <div><label>¿Firmó contrato?</label>
          <div class="radio-group" id="edit_firmo">
            <div class="radio-btn" data-val="si" onclick="selectRadio(this,'edit_firmo')">Sí firmó</div>
            <div class="radio-btn" data-val="no" onclick="selectRadio(this,'edit_firmo')">Pendiente</div>
          </div>
        </div>
      </div>
    </div>
    <div class="card" style="margin-bottom:12px">
      <div class="card-title">Tickets</div>
      <div id="edit_ticketsContainer"></div>
      <button class="btn btn-outline btn-sm" onclick="addEditTicket()">+ Agregar ticket</button>
      <div class="divider"></div>
      <div class="grid2"><div><label>% Comisión</label><input type="number" id="edit_pct" placeholder="Ej. 3" step="0.1" min="0" max="100" oninput="calcularEdit()"/></div><div></div></div>
    </div>
    <div class="total-box" style="margin-bottom:16px">
      <div><div class="total-label">Total</div><div style="font-size:13px;color:#ccc;margin-top:2px" id="edit_res_tickets">0 tickets</div></div>
      <div style="text-align:right"><div class="total-label">Comisión</div><div class="total-value" id="edit_res_comision">$0.00</div></div>
    </div>
    <div style="display:flex;gap:10px;justify-content:flex-end">
      <button class="btn btn-outline" onclick="cerrarModal('modalEditar')">Cancelar</button>
      <button class="btn btn-gold" onclick="guardarEdicion()">Guardar cambios</button>
    </div>
  </div>
</div>

<!-- MODAL PDF -->
<div class="modal-overlay" id="modalPDF">
  <div class="modal-sm">
    <div class="modal-header"><div class="modal-title">Exportar reporte PDF</div><button class="modal-close" onclick="cerrarModal('modalPDF')">✕</button></div>
    <div style="margin-bottom:16px">
      <label>Nombre del especialista comercial</label>
      <input id="pdf_especialista" placeholder="Ej. Sofía Ramírez González"/>
      <div style="font-size:11px;color:var(--muted);margin-top:5px">Aparecerá en el encabezado del reporte.</div>
    </div>
    <div style="display:flex;gap:10px;justify-content:flex-end">
      <button class="btn btn-outline" onclick="cerrarModal('modalPDF')">Cancelar</button>
      <button class="btn btn-gold" onclick="exportPDFReport()">Generar PDF</button>
    </div>
  </div>
</div>

<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js"></script>
<script>
const SUPA_URL='https://gddwjlwugznlerjjskon.supabase.co';
const SUPA_KEY='sb_publishable_HXTi-5HsUphmKf6KEYLM0A_DyqFn4G0';

let currentUser=null, currentToken=null;
let ventasCache=[], objetivosCache={};
let tickets=[], editTickets=[], editingId=null, parsedRows=[];
let selectedObjMonth=null;
let chartV=null,chartC=null,chartT=null,chartF=null;

const fmt=n=>'$'+Number(n).toLocaleString('es-MX',{minimumFractionDigits:2,maximumFractionDigits:2});
const today=()=>new Date().toISOString().slice(0,10);
const monthKey=(y,m)=>`${y}-${String(m).padStart(2,'0')}`;
const monthLabel=d=>new Date(d+'T12:00:00').toLocaleString('es-MX',{month:'short',year:'2-digit'});
const monthName=key=>{const[y,m]=key.split('-');return new Date(+y,+m-1,1).toLocaleString('es-MX',{month:'long',year:'numeric'});};

// ── LOADING ────────────────────────────────────────────
function setLoading(show,text='Cargando...'){
  document.getElementById('loadingOverlay').classList.toggle('show',show);
  document.getElementById('loadingText').textContent=text;
}

// ── SUPABASE FETCH ─────────────────────────────────────
async function sb(path,method='GET',body=null,token=null){
  const headers={'Content-Type':'application/json','apikey':SUPA_KEY,'Prefer':'return=representation'};
  if(token) headers['Authorization']='Bearer '+token;
  const opts={method,headers};
  if(body) opts.body=JSON.stringify(body);
  const res=await fetch(SUPA_URL+path,opts);
  const text=await res.text();
  let data=null;
  try{data=text?JSON.parse(text):null;}catch(e){}
  return{ok:res.ok,status:res.status,data};
}
async function sbAuth(path,body){
  const res=await fetch(SUPA_URL+'/auth/v1'+path,{method:'POST',headers:{'Content-Type':'application/json','apikey':SUPA_KEY},body:JSON.stringify(body)});
  const data=await res.json();
  return{ok:res.ok,data};
}

// ── AUTH ──────────────────────────────────────────────
function switchTab(tab){
  document.getElementById('form-login').style.display='none';
  document.getElementById('form-registro').style.display='none';
  document.getElementById('form-reset').style.display='none';
  document.getElementById('tab-login').classList.remove('active');
  document.getElementById('tab-registro').classList.remove('active');
  document.getElementById('auth_alert').innerHTML='';
  if(tab==='login'){document.getElementById('form-login').style.display='block';document.getElementById('tab-login').classList.add('active');}
  else if(tab==='registro'){document.getElementById('form-registro').style.display='block';document.getElementById('tab-registro').classList.add('active');}
  else{document.getElementById('form-reset').style.display='block';}
}
function showAuthAlert(msg,type='err'){
  document.getElementById('auth_alert').innerHTML=`<div class="auth-alert ${type}">${msg}</div>`;
}
async function doLogin(){
  const email=document.getElementById('login_email').value.trim();
  const pass=document.getElementById('login_pass').value;
  if(!email||!pass){showAuthAlert('Completa todos los campos');return;}
  const btn=document.getElementById('btn_login');btn.disabled=true;btn.textContent='Entrando...';
  const{ok,data}=await sbAuth('/token?grant_type=password',{email,password:pass});
  btn.disabled=false;btn.textContent='Entrar';
  if(!ok||!data.access_token){showAuthAlert(data.error_description||data.msg||'Correo o contraseña incorrectos');return;}
  await iniciarSesion(data);
}
async function doRegistro(){
  const nombre=document.getElementById('reg_nombre').value.trim();
  const email=document.getElementById('reg_email').value.trim();
  const pass=document.getElementById('reg_pass').value;
  const pass2=document.getElementById('reg_pass2').value;
  if(!nombre||!email||!pass||!pass2){showAuthAlert('Completa todos los campos');return;}
  if(pass!==pass2){showAuthAlert('Las contraseñas no coinciden');return;}
  if(pass.length<6){showAuthAlert('La contraseña debe tener al menos 6 caracteres');return;}
  const btn=document.getElementById('btn_registro');btn.disabled=true;btn.textContent='Creando cuenta...';
  const{ok,data}=await sbAuth('/signup',{email,password:pass});
  btn.disabled=false;btn.textContent='Crear cuenta';
  if(!ok){showAuthAlert(data.error_description||data.msg||'Error al crear cuenta');return;}
  if(data.access_token){
    // Guardar perfil con nombre
    await sb('/rest/v1/perfiles',  'POST',{id:data.user.id,nombre},{Authorization:'Bearer '+data.access_token,...{}});
    await sbWithToken('/rest/v1/perfiles','POST',{id:data.user.id,nombre},data.access_token);
    await iniciarSesion(data,nombre);
  } else {
    showAuthAlert('Cuenta creada. Revisa tu correo para confirmar tu cuenta y luego inicia sesión.','ok');
  }
}
async function sbWithToken(path,method,body,token){
  return sb(path,method,body,token);
}
async function doReset(){
  const email=document.getElementById('reset_email').value.trim();
  if(!email){showAuthAlert('Ingresa tu correo');return;}
  const btn=document.getElementById('btn_reset');btn.disabled=true;btn.textContent='Enviando...';
  await sbAuth('/recover',{email});
  btn.disabled=false;btn.textContent='Enviar enlace';
  showAuthAlert('Si el correo existe, recibirás un enlace en tu bandeja de entrada.','ok');
}
async function iniciarSesion(data,nombreReg=null){
  currentUser=data.user;
  currentToken=data.access_token;
  // Guardar sesión local
  localStorage.setItem('portalia_session',JSON.stringify({user:data.user,token:data.access_token,expires:data.expires_at}));
  // Obtener nombre del perfil
  let nombre=nombreReg;
  if(!nombre){
    const r=await sb(`/rest/v1/perfiles?id=eq.${currentUser.id}&select=nombre`,'GET',null,currentToken);
    nombre=r.data&&r.data[0]?r.data[0].nombre:currentUser.email;
  }
  document.getElementById('headerUserName').textContent=nombre;
  document.getElementById('pdf_especialista').value=nombre;
  document.getElementById('authWrap').style.display='none';
  document.getElementById('appWrap').style.display='flex';
  // Inicializar app
  const n=new Date();
  document.getElementById('inv_fecha').value=today();
  document.getElementById('d_desde').value=`${n.getFullYear()}-${String(n.getMonth()+1).padStart(2,'0')}-01`;
  document.getElementById('d_hasta').value=today();
  addTicket();
  await cargarVentas();
  renderHistorial();
}
async function doLogout(){
  setLoading(true,'Cerrando sesión...');
  await sb('/auth/v1/logout','POST',null,currentToken);
  localStorage.removeItem('portalia_session');
  currentUser=null;currentToken=null;ventasCache=[];objetivosCache={};
  document.getElementById('authWrap').style.display='flex';
  document.getElementById('appWrap').style.display='none';
  setLoading(false);
}

// Restaurar sesión al cargar
window.addEventListener('load',async()=>{
  const saved=localStorage.getItem('portalia_session');
  if(saved){
    try{
      const s=JSON.parse(saved);
      if(s.token&&s.user){
        // Verificar token
        const r=await sb('/rest/v1/perfiles?id=eq.'+s.user.id+'&select=nombre','GET',null,s.token);
        if(r.ok){
          currentUser=s.user;currentToken=s.token;
          const nombre=r.data&&r.data[0]?r.data[0].nombre:s.user.email;
          document.getElementById('headerUserName').textContent=nombre;
          document.getElementById('pdf_especialista').value=nombre;
          document.getElementById('authWrap').style.display='none';
          document.getElementById('appWrap').style.display='flex';
          const n=new Date();
          document.getElementById('inv_fecha').value=today();
          document.getElementById('d_desde').value=`${n.getFullYear()}-${String(n.getMonth()+1).padStart(2,'0')}-01`;
          document.getElementById('d_hasta').value=today();
          tickets=[];addTicket();
          await cargarVentas();
          renderHistorial();
          return;
        }
      }
    }catch(e){}
    localStorage.removeItem('portalia_session');
  }
});

// ── DATOS ──────────────────────────────────────────────
async function cargarVentas(){
  setLoading(true,'Cargando tus datos...');
  const r=await sb('/rest/v1/ventas?user_id=eq.'+currentUser.id+'&order=fecha.desc','GET',null,currentToken);
  if(r.ok&&r.data) ventasCache=r.data;
  // Cargar objetivos
  const o=await sb('/rest/v1/objetivos?user_id=eq.'+currentUser.id,'GET',null,currentToken);
  if(o.ok&&o.data){
    objetivosCache={};
    o.data.forEach(x=>objetivosCache[x.mes]={...x});
  }
  setLoading(false);
}

// ── TICKETS ────────────────────────────────────────────
function addTicket(precio='',cant=''){
  tickets.push({id:'t'+Date.now()+Math.random(),precio,cant});renderTickets();
}
function removeTicket(id){tickets=tickets.filter(t=>t.id!==id);renderTickets();}
function renderTickets(){
  const c=document.getElementById('ticketsContainer');
  if(!tickets.length){addTicket();return;}
  c.innerHTML=tickets.map((t,i)=>`
    <div class="ticket-row">
      <div><label>${i===0?'Precio ticket (MXN)':''}</label><input type="number" placeholder="Precio" value="${t.precio}" oninput="tickets[${i}].precio=this.value;calcular()" min="0"/></div>
      <div><label>${i===0?'Cantidad':''}</label><input type="number" placeholder="Qty" value="${t.cant}" oninput="tickets[${i}].cant=this.value;calcular()" min="1"/></div>
      <div><label>${i===0?'Subtotal':''}</label><input readonly value="${t.precio&&t.cant?fmt(t.precio*t.cant):''}"/></div>
      <div style="padding-top:${i===0?'20px':'0'}"><button class="btn-danger-sm" onclick="removeTicket('${t.id}')">✕</button></div>
    </div>`).join('');
  calcular();
}
function calcular(){
  let total=0,tqty=0;
  tickets.forEach(t=>{const s=parseFloat(t.precio||0)*parseFloat(t.cant||0);total+=s;tqty+=parseFloat(t.cant||0);});
  const pct=parseFloat(document.getElementById('pct_comision').value||0);
  document.getElementById('res_tickets').textContent=`${tqty} ticket${tqty!==1?'s':''} · Total: ${fmt(total)}`;
  document.getElementById('res_comision').textContent=fmt(total*(pct/100));
}

function selectRadio(el,group){document.querySelectorAll(`#${group} .radio-btn`).forEach(b=>b.classList.remove('selected'));el.classList.add('selected');}
function getRadio(group){return(document.querySelector(`#${group} .radio-btn.selected`)||{}).dataset.val||'';}
function setRadio(group,val){document.querySelectorAll(`#${group} .radio-btn`).forEach(b=>b.classList.toggle('selected',b.dataset.val===val));}

// ── GUARDAR VENTA ──────────────────────────────────────
async function guardarVenta(){
  const nombre=document.getElementById('inv_nombre').value.trim();
  const fecha=document.getElementById('inv_fecha').value;
  const pct=parseFloat(document.getElementById('pct_comision').value||0);
  if(!nombre)return showAlert('Ingresa el nombre del inversionista','danger','alertBox');
  if(!fecha)return showAlert('Selecciona la fecha','danger','alertBox');
  if(tickets.every(t=>!t.precio||!t.cant))return showAlert('Agrega al menos un ticket completo','danger','alertBox');
  if(!pct)return showAlert('Ingresa el % de comisión','danger','alertBox');
  let total=0,tqty=0;
  const tks=tickets.filter(t=>t.precio&&t.cant).map(t=>{const s=parseFloat(t.precio)*parseFloat(t.cant);total+=s;tqty+=parseFloat(t.cant);return{precio:parseFloat(t.precio),cant:parseFloat(t.cant),subtotal:s};});
  const payload={user_id:currentUser.id,nombre,fecha,tickets:tks,total,qty:tqty,pct,comision:total*(pct/100),tipo:getRadio('tipo_contrato'),firmo:getRadio('firmo')};
  setLoading(true,'Guardando...');
  const r=await sb('/rest/v1/ventas','POST',payload,currentToken);
  setLoading(false);
  if(!r.ok){showAlert('Error al guardar. Intenta de nuevo.','danger','alertBox');return;}
  if(r.data&&r.data[0]) ventasCache.unshift(r.data[0]);
  showAlert('¡Venta guardada!','success','alertBox');
  limpiarForm();
}
function limpiarForm(){
  document.getElementById('inv_nombre').value='';document.getElementById('inv_fecha').value=today();
  document.getElementById('pct_comision').value='';tickets=[];addTicket();
  setRadio('tipo_contrato','mandato');setRadio('firmo','si');
}
function showAlert(msg,type,boxId){
  const b=document.getElementById(boxId);if(!b)return;
  b.innerHTML=`<div class="alert alert-${type}">${msg}</div>`;
  setTimeout(()=>b.innerHTML='',3500);
}

// ── EDITAR VENTA ───────────────────────────────────────
function abrirEditar(id){
  const v=ventasCache.find(x=>x.id===id);if(!v)return;
  editingId=id;
  editTickets=(v.tickets||[{precio:v.total/v.qty,cant:v.qty,subtotal:v.total}]).map(t=>({...t,id:'et'+Date.now()+Math.random()}));
  document.getElementById('edit_nombre').value=v.nombre;
  document.getElementById('edit_fecha').value=v.fecha;
  document.getElementById('edit_pct').value=v.pct;
  setRadio('edit_tipo_contrato',v.tipo||'mandato');
  setRadio('edit_firmo',v.firmo||'no');
  renderEditTickets();
  document.getElementById('modalEditar').classList.add('open');
}
function cerrarModal(id){document.getElementById(id).classList.remove('open');}
function addEditTicket(precio='',cant=''){editTickets.push({id:'et'+Date.now()+Math.random(),precio,cant});renderEditTickets();}
function removeEditTicket(id){editTickets=editTickets.filter(t=>t.id!==id);renderEditTickets();}
function renderEditTickets(){
  const c=document.getElementById('edit_ticketsContainer');
  if(!editTickets.length){addEditTicket();return;}
  c.innerHTML=editTickets.map((t,i)=>`
    <div class="ticket-row">
      <div><label>${i===0?'Precio (MXN)':''}</label><input type="number" placeholder="Precio" value="${t.precio||''}" oninput="editTickets[${i}].precio=this.value;calcularEdit()" min="0"/></div>
      <div><label>${i===0?'Cantidad':''}</label><input type="number" placeholder="Qty" value="${t.cant||''}" oninput="editTickets[${i}].cant=this.value;calcularEdit()" min="1"/></div>
      <div><label>${i===0?'Subtotal':''}</label><input readonly value="${t.precio&&t.cant?fmt(t.precio*t.cant):''}"/></div>
      <div style="padding-top:${i===0?'20px':'0'}"><button class="btn-danger-sm" onclick="removeEditTicket('${t.id}')">✕</button></div>
    </div>`).join('');
  calcularEdit();
}
function calcularEdit(){
  let total=0,tqty=0;
  editTickets.forEach(t=>{const s=parseFloat(t.precio||0)*parseFloat(t.cant||0);total+=s;tqty+=parseFloat(t.cant||0);});
  const pct=parseFloat(document.getElementById('edit_pct').value||0);
  document.getElementById('edit_res_tickets').textContent=`${tqty} ticket${tqty!==1?'s':''} · Total: ${fmt(total)}`;
  document.getElementById('edit_res_comision').textContent=fmt(total*(pct/100));
}
async function guardarEdicion(){
  const nombre=document.getElementById('edit_nombre').value.trim();
  const fecha=document.getElementById('edit_fecha').value;
  const pct=parseFloat(document.getElementById('edit_pct').value||0);
  if(!nombre)return showAlert('Ingresa el nombre','danger','modal_alertBox');
  if(!fecha)return showAlert('Selecciona la fecha','danger','modal_alertBox');
  if(editTickets.every(t=>!t.precio||!t.cant))return showAlert('Agrega al menos un ticket','danger','modal_alertBox');
  if(!pct)return showAlert('Ingresa el % de comisión','danger','modal_alertBox');
  let total=0,tqty=0;
  const tks=editTickets.filter(t=>t.precio&&t.cant).map(t=>{const s=parseFloat(t.precio)*parseFloat(t.cant);total+=s;tqty+=parseFloat(t.cant);return{precio:parseFloat(t.precio),cant:parseFloat(t.cant),subtotal:s};});
  const payload={nombre,fecha,tickets:tks,total,qty:tqty,pct,comision:total*(pct/100),tipo:getRadio('edit_tipo_contrato'),firmo:getRadio('edit_firmo'),modificado:new Date().toISOString()};
  setLoading(true,'Actualizando...');
  const r=await sb(`/rest/v1/ventas?id=eq.${editingId}&user_id=eq.${currentUser.id}`,'PATCH',payload,currentToken);
  setLoading(false);
  if(!r.ok){showAlert('Error al actualizar','danger','modal_alertBox');return;}
  const idx=ventasCache.findIndex(x=>x.id===editingId);
  if(idx>=0) ventasCache[idx]={...ventasCache[idx],...payload};
  cerrarModal('modalEditar');
  renderHistorial();
  showAlert('Venta actualizada','success','alertBox');
}

// ── IMPORTAR ───────────────────────────────────────────
function dragOver(e){e.preventDefault();document.getElementById('dropZone').classList.add('drag-over');}
function dragLeave(){document.getElementById('dropZone').classList.remove('drag-over');}
function dropFile(e){e.preventDefault();dragLeave();const f=e.dataTransfer.files[0];if(f)handleFile(f);}
function handleFile(file){if(!file||!file.name.endsWith('.csv')){alert('Sube un archivo .csv válido');return;}const r=new FileReader();r.onload=e=>parseCSV(e.target.result);r.readAsText(file,'UTF-8');}
function parseCSV(text){
  const lines=text.trim().split(/\r?\n/).filter(l=>l.trim());
  if(lines.length<2){alert('El archivo está vacío');return;}
  const headers=lines[0].split(',').map(h=>h.trim().toLowerCase().replace(/^"|"$/g,''));
  const required=['fecha','nombre_inversionista','precio_ticket','cantidad_tickets','porcentaje_comision'];
  const missing=required.filter(r=>!headers.includes(r));
  if(missing.length){alert('Faltan columnas: '+missing.join(', '));return;}
  parsedRows=[];
  for(let i=1;i<lines.length;i++){
    const vals=splitCSVLine(lines[i]);const row={};headers.forEach((h,j)=>row[h]=(vals[j]||'').trim().replace(/^"|"$/g,''));
    const errs=[],warns=[];
    if(!row.fecha||!/^\d{4}-\d{2}-\d{2}$/.test(row.fecha))errs.push('Fecha inválida');
    if(!row.nombre_inversionista)errs.push('Nombre vacío');
    const precio=parseFloat(row.precio_ticket);if(isNaN(precio)||precio<=0)errs.push('Precio inválido');
    const cant=parseFloat(row.cantidad_tickets);if(isNaN(cant)||cant<=0)errs.push('Cantidad inválida');
    const pct=parseFloat(row.porcentaje_comision);if(isNaN(pct)||pct<=0||pct>100)errs.push('% inválido');
    const tipo=(row.tipo_contrato||'').toLowerCase()||'mandato';if(tipo&&tipo!=='mandato'&&tipo!=='convenio')warns.push('Tipo no reconocido');
    const firmo=(row.firmo_contrato||'').toLowerCase()||'no';if(firmo&&firmo!=='si'&&firmo!=='no')warns.push('Firma no reconocida');
    const total=isNaN(precio)||isNaN(cant)?0:precio*cant;const comision=isNaN(pct)?0:total*(pct/100);
    parsedRows.push({raw:row,errs,warns,precio:isNaN(precio)?0:precio,cant:isNaN(cant)?0:cant,pct:isNaN(pct)?0:pct,total,comision,tipo:tipo==='convenio'?'convenio':'mandato',firmo:firmo==='si'?'si':'no',lineNum:i});
  }
  renderPreview();
}
function splitCSVLine(line){const r=[];let c='',inQ=false;for(let i=0;i<line.length;i++){if(line[i]==='"')inQ=!inQ;else if(line[i]===','&&!inQ){r.push(c);c='';}else c+=line[i];}r.push(c);return r;}
function renderPreview(){
  const ok=parsedRows.filter(r=>!r.errs.length&&!r.warns.length).length;
  const warn=parsedRows.filter(r=>!r.errs.length&&r.warns.length).length;
  const err=parsedRows.filter(r=>r.errs.length).length;
  document.getElementById('import_summary').innerHTML=`<span class="imp-badge imp-ok">✓ ${ok} correctas</span>`+(warn?`<span class="imp-badge imp-warn">⚠ ${warn} advertencias</span>`:'')+( err?`<span class="imp-badge imp-err">✕ ${err} errores</span>`:'');
  document.getElementById('preview_tbody').innerHTML=parsedRows.map(r=>{
    const cls=r.errs.length?'row-err':r.warns.length?'row-warn':'row-ok';
    const note=r.errs.length?`<span style="color:var(--danger);font-size:11px">${r.errs.join(' · ')}</span>`:r.warns.length?`<span style="color:#856404;font-size:11px">${r.warns.join(' · ')}</span>`:'<span style="color:#2d7a4f;font-size:11px">✓</span>';
    return`<tr class="${cls}"><td>${r.lineNum}</td><td>${r.raw.fecha||'—'}</td><td>${r.raw.nombre_inversionista||'—'}</td><td>${r.precio?fmt(r.precio):'—'}</td><td>${r.cant||'—'}</td><td>${r.total?fmt(r.total):'—'}</td><td style="color:var(--gold);font-weight:700">${r.comision?fmt(r.comision):'—'}</td><td><span class="badge badge-${r.tipo==='mandato'?'mandato':'convenio'}">${r.tipo==='mandato'?'Mandato':'Convenio'}</span></td><td><span class="badge badge-${r.firmo==='si'?'firmado':'pendiente'}">${r.firmo==='si'?'Firmado':'Pendiente'}</span></td><td>${note}</td></tr>`;
  }).join('');
  const vc=parsedRows.filter(r=>!r.errs.length).length;
  document.getElementById('import_alert').innerHTML=err?`<div class="alert alert-danger">Hay errores en algunas filas. Las válidas sí se pueden importar.</div>`:'';
  document.getElementById('import_actions').innerHTML=`<button class="btn btn-outline" onclick="cancelarImport()">Cancelar</button>`+(vc?`<button class="btn btn-green" onclick="confirmarImport()">Importar ${vc} venta${vc!==1?'s':''} válidas</button>`:'');
  document.getElementById('preview_section').style.display='block';
}
async function confirmarImport(){
  const validas=parsedRows.filter(r=>!r.errs.length);
  if(!validas.length)return;
  setLoading(true,`Importando ${validas.length} ventas...`);
  const payloads=validas.map(r=>({user_id:currentUser.id,nombre:r.raw.nombre_inversionista,fecha:r.raw.fecha,tickets:[{precio:r.precio,cant:r.cant,subtotal:r.total}],total:r.total,qty:r.cant,pct:r.pct,comision:r.comision,tipo:r.tipo,firmo:r.firmo}));
  const r=await sb('/rest/v1/ventas','POST',payloads,currentToken);
  setLoading(false);
  if(!r.ok){alert('Error al importar. Intenta de nuevo.');return;}
  if(r.data) ventasCache=[...r.data,...ventasCache];
  document.getElementById('preview_section').style.display='none';parsedRows=[];document.getElementById('fileInput').value='';
  document.getElementById('import_alert').innerHTML=`<div class="alert alert-success">¡${validas.length} venta${validas.length!==1?'s':''} importada${validas.length!==1?'s':''}!</div>`;
  setTimeout(()=>document.getElementById('import_alert').innerHTML='',5000);
}
function cancelarImport(){document.getElementById('preview_section').style.display='none';parsedRows=[];document.getElementById('fileInput').value='';}

// ── PLANTILLAS ─────────────────────────────────────────
function descargarPlantillaCSV(){dlCSV('fecha,nombre_inversionista,precio_ticket,cantidad_tickets,porcentaje_comision,tipo_contrato,firmo_contrato\n','plantilla_portalia.csv');}
function descargarPlantillaEjemplo(){dlCSV(['fecha,nombre_inversionista,precio_ticket,cantidad_tickets,porcentaje_comision,tipo_contrato,firmo_contrato','2025-04-10,Carlos Mendoza,250000,3,3.5,mandato,si','2025-04-14,María López,300000,2,4,convenio,no','2025-04-18,Roberto Juárez,180000,5,3,mandato,si'].join('\n'),'plantilla_portalia_ejemplos.csv');}
function dlCSV(content,filename){const blob=new Blob(['\ufeff'+content],{type:'text/csv;charset=utf-8;'});const url=URL.createObjectURL(blob);const a=document.createElement('a');a.href=url;a.download=filename;a.click();URL.revokeObjectURL(url);}

// ── HISTORIAL ──────────────────────────────────────────
function getFiltered(desde,hasta,tipo,firma){
  return ventasCache.filter(v=>{
    if(desde&&v.fecha<desde)return false;
    if(hasta&&v.fecha>hasta)return false;
    if(tipo&&v.tipo!==tipo)return false;
    if(firma&&v.firmo!==firma)return false;
    return true;
  });
}
function renderHistorial(){
  const data=getFiltered(document.getElementById('f_desde').value,document.getElementById('f_hasta').value,document.getElementById('f_tipo').value,document.getElementById('f_firma').value).sort((a,b)=>b.fecha.localeCompare(a.fecha));
  const tbody=document.getElementById('tablaHistorial');
  if(!data.length){tbody.innerHTML='<tr><td colspan="8" class="empty-msg">Sin resultados</td></tr>';document.getElementById('historial_totales').innerHTML='';return;}
  tbody.innerHTML=data.map(v=>`<tr>
    <td>${v.fecha}</td><td style="font-weight:600">${v.nombre}</td><td>${v.qty}</td>
    <td>${fmt(v.total)}</td><td style="color:var(--gold);font-weight:700">${fmt(v.comision)}</td>
    <td><span class="badge badge-${v.tipo==='mandato'?'mandato':'convenio'}">${v.tipo==='mandato'?'Mandato':'Convenio'}</span></td>
    <td><span class="badge badge-${v.firmo==='si'?'firmado':'pendiente'}">${v.firmo==='si'?'Firmado':'Pendiente'}</span></td>
    <td style="display:flex;gap:6px">
      <button class="btn-edit" onclick="abrirEditar('${v.id}')">Editar</button>
      <button class="btn-danger-sm" onclick="eliminarVenta('${v.id}')">✕</button>
    </td></tr>`).join('');
  const tv=data.reduce((a,b)=>a+b.total,0),tc=data.reduce((a,b)=>a+b.comision,0);
  document.getElementById('historial_totales').innerHTML=`<div class="total-box"><div><div class="total-label">Total ventas</div><div style="font-size:20px;color:#fff;font-weight:700">${fmt(tv)}</div></div><div style="text-align:right"><div class="total-label">Total comisiones</div><div class="total-value">${fmt(tc)}</div></div></div>`;
}
async function eliminarVenta(id){
  if(!confirm('¿Eliminar esta venta?'))return;
  setLoading(true,'Eliminando...');
  const r=await sb(`/rest/v1/ventas?id=eq.${id}&user_id=eq.${currentUser.id}`,'DELETE',null,currentToken);
  setLoading(false);
  if(!r.ok){alert('Error al eliminar');return;}
  ventasCache=ventasCache.filter(v=>v.id!==id);
  renderHistorial();
}

// ── DASHBOARD ──────────────────────────────────────────
function showSection(id,btn){
  document.querySelectorAll('.section').forEach(s=>s.classList.remove('active'));
  document.querySelectorAll('.nav-btn').forEach(b=>b.classList.remove('active'));
  document.getElementById('sec-'+id).classList.add('active');
  btn.classList.add('active');
  if(id==='historial')renderHistorial();
  if(id==='objetivos')renderObjetivos();
  if(id==='dashboard')requestAnimationFrame(()=>requestAnimationFrame(renderDashboard));
}
function setDashPeriod(p){
  const n=new Date();document.getElementById('d_hasta').value=today();
  if(p==='mes')document.getElementById('d_desde').value=`${n.getFullYear()}-${String(n.getMonth()+1).padStart(2,'0')}-01`;
  else if(p==='trimestre'){const s=n.getMonth()-n.getMonth()%3;document.getElementById('d_desde').value=`${n.getFullYear()}-${String(s+1).padStart(2,'0')}-01`;}
  else document.getElementById('d_desde').value=`${n.getFullYear()}-01-01`;
  renderDashboard();
}
function makeChart(id,type,data,options){const canvas=document.getElementById(id);if(!canvas)return;const ex=Chart.getChart(canvas);if(ex)ex.destroy();return new Chart(canvas,{type,data,options});}
function renderDashboard(){
  const data=getFiltered(document.getElementById('d_desde').value,document.getElementById('d_hasta').value,'','');
  const tv=data.reduce((a,b)=>a+b.total,0),tc=data.reduce((a,b)=>a+b.comision,0),nc=data.length,tq=data.reduce((a,b)=>a+b.qty,0);
  document.getElementById('dash_metrics').innerHTML=`
    <div class="metric-card"><div class="metric-label">Total ventas</div><div class="metric-value">${fmt(tv)}</div><div class="metric-sub">${nc} cierre${nc!==1?'s':''}</div></div>
    <div class="metric-card metric-gold"><div class="metric-label">Comisiones</div><div class="metric-value">${fmt(tc)}</div></div>
    <div class="metric-card"><div class="metric-label">Tickets</div><div class="metric-value">${tq}</div></div>
    <div class="metric-card"><div class="metric-label">Firmados</div><div class="metric-value">${data.filter(v=>v.firmo==='si').length}</div><div class="metric-sub">de ${nc}</div></div>`;
  const byMonth={};data.forEach(v=>{const l=monthLabel(v.fecha);if(!byMonth[l])byMonth[l]={v:0,c:0};byMonth[l].v+=v.total;byMonth[l].c+=v.comision;});
  const labels=Object.keys(byMonth),vData=labels.map(l=>byMonth[l].v),cData=labels.map(l=>byMonth[l].c);
  const GOLD='#C9A84C';
  const ax={grid:{color:'#f0ede6'},ticks:{color:'#6b6460',font:{size:11}}};
  const base={responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false}},scales:{x:ax,y:{...ax,ticks:{...ax.ticks,callback:v=>'$'+Number(v/1000).toFixed(0)+'k'}}}};
  const pie={responsive:true,maintainAspectRatio:false,plugins:{legend:{position:'bottom',labels:{font:{size:11},color:'#6b6460',padding:8}}}};
  makeChart('chartVentas','bar',{labels,datasets:[{data:vData,backgroundColor:GOLD,borderRadius:4}]},base);
  makeChart('chartComisiones','line',{labels,datasets:[{data:cData,borderColor:GOLD,backgroundColor:'rgba(201,168,76,0.12)',borderWidth:2,tension:.35,fill:true,pointBackgroundColor:GOLD,pointRadius:4}]},base);
  const m=data.filter(v=>v.tipo==='mandato').length,cv=data.filter(v=>v.tipo==='convenio').length;
  const fi=data.filter(v=>v.firmo==='si').length,pe=data.filter(v=>v.firmo==='no').length;
  makeChart('chartTipo','doughnut',{labels:['Mandato','Convenio'],datasets:[{data:[m,cv],backgroundColor:[GOLD,'#3a3a3a'],borderWidth:0}]},pie);
  makeChart('chartFirma','doughnut',{labels:['Firmado','Pendiente'],datasets:[{data:[fi,pe],backgroundColor:['#2d7a4f','#e8a020'],borderWidth:0}]},pie);
}

// ── OBJETIVOS ──────────────────────────────────────────
function getMeses(){
  const meses=[];const now=new Date();
  for(let i=-6;i<=3;i++){const d=new Date(now.getFullYear(),now.getMonth()+i,1);meses.push(monthKey(d.getFullYear(),d.getMonth()+1));}
  return meses;
}
function renderObjetivos(){
  const meses=getMeses();const now=new Date();
  const currentKey=monthKey(now.getFullYear(),now.getMonth()+1);
  if(!selectedObjMonth)selectedObjMonth=currentKey;
  const bar=document.getElementById('obj_tab_bar');
  bar.innerHTML=meses.map(k=>{const[y,m]=k.split('-');const label=new Date(+y,+m-1,1).toLocaleString('es-MX',{month:'short',year:'2-digit'});return`<button class="obj-tab${k===selectedObjMonth?' active':''}" onclick="seleccionarMesObj('${k}')">${label}${k===currentKey?' ·':''}</button>`;}).join('');
  const obj=objetivosCache[selectedObjMonth]||{};
  document.getElementById('obj_ventas').value=obj.ventas||'';
  document.getElementById('obj_comisiones').value=obj.comisiones||'';
  document.getElementById('obj_cierres').value=obj.cierres||'';
  renderProgresoMes(selectedObjMonth);renderResumenAnual();
}
function seleccionarMesObj(key){selectedObjMonth=key;renderObjetivos();}
let objTimer=null;
function guardarObjetivo(){
  if(!selectedObjMonth)return;
  const vals={ventas:parseFloat(document.getElementById('obj_ventas').value||0)||0,comisiones:parseFloat(document.getElementById('obj_comisiones').value||0)||0,cierres:parseFloat(document.getElementById('obj_cierres').value||0)||0};
  objetivosCache[selectedObjMonth]={...(objetivosCache[selectedObjMonth]||{}),mes:selectedObjMonth,...vals};
  renderProgresoMes(selectedObjMonth);renderResumenAnual();
  clearTimeout(objTimer);
  objTimer=setTimeout(async()=>{
    const existing=objetivosCache[selectedObjMonth];
    if(existing&&existing.id){
      await sb(`/rest/v1/objetivos?id=eq.${existing.id}&user_id=eq.${currentUser.id}`,'PATCH',vals,currentToken);
    } else {
      const r=await sb('/rest/v1/objetivos','POST',{user_id:currentUser.id,mes:selectedObjMonth,...vals},currentToken);
      if(r.ok&&r.data&&r.data[0]) objetivosCache[selectedObjMonth]={...objetivosCache[selectedObjMonth],...r.data[0]};
    }
  },800);
}
function getVentasMes(key){
  const[y,m]=key.split('-');const desde=`${y}-${m}-01`;const lastDay=new Date(+y,+m,0).getDate();const hasta=`${y}-${m}-${String(lastDay).padStart(2,'0')}`;
  return getFiltered(desde,hasta,'','');
}
function renderProgresoMes(key){
  const obj=objetivosCache[key]||{};const data=getVentasMes(key);
  const tv=data.reduce((a,b)=>a+b.total,0),tc=data.reduce((a,b)=>a+b.comision,0),nc=data.length;
  const box=document.getElementById('obj_progreso');const nombre=monthName(key);
  if(!obj.ventas&&!obj.comisiones&&!obj.cierres){box.innerHTML=`<div class="card-title">Progreso — ${nombre}</div><div class="empty-msg">Sin objetivos configurados para este mes</div>`;return;}
  function barHtml(actual,objetivo,label,tipo){
    if(!objetivo)return'';const pct=Math.min((actual/objetivo)*100,100),over=actual>=objetivo;
    return`<div class="obj-bar-wrap"><div class="obj-bar-label"><span>${label}</span><span style="font-weight:700;color:${over?'var(--success)':'var(--dark)'}">${tipo==='mxn'?fmt(actual)+' / '+fmt(objetivo):actual+' / '+objetivo}</span></div><div class="obj-bar"><div class="obj-bar-fill${over?' over':''}" style="width:${pct.toFixed(1)}%"></div></div><div style="font-size:11px;color:${over?'var(--success)':'var(--muted)'};margin-top:3px">${pct.toFixed(1)}%${over?' ✓ Meta alcanzada':''}</div></div>`;
  }
  box.innerHTML=`<div class="card-title">Progreso — ${nombre}</div>
    <div class="grid3" style="margin-bottom:16px">
      <div class="metric-card"><div class="metric-label">Ventas</div><div class="metric-value" style="font-size:16px">${fmt(tv)}</div></div>
      <div class="metric-card metric-gold"><div class="metric-label">Comisiones</div><div class="metric-value" style="font-size:16px">${fmt(tc)}</div></div>
      <div class="metric-card"><div class="metric-label">Cierres</div><div class="metric-value" style="font-size:16px">${nc}</div></div>
    </div>
    ${barHtml(tv,obj.ventas,'Ventas totales','mxn')}${obj.ventas?'<div class="divider"></div>':''}
    ${barHtml(tc,obj.comisiones,'Comisiones','mxn')}${obj.comisiones?'<div class="divider"></div>':''}
    ${barHtml(nc,obj.cierres,'Cierres','num')}`;
}
function renderResumenAnual(){
  const meses=getMeses().filter(k=>objetivosCache[k]&&(objetivosCache[k].ventas||objetivosCache[k].comisiones||objetivosCache[k].cierres));
  const box=document.getElementById('obj_resumen_anual');
  if(!meses.length){box.innerHTML='<div class="empty-msg">Sin objetivos configurados</div>';return;}
  const rows=meses.map(k=>{
    const obj=objetivosCache[k]||{};const data=getVentasMes(k);
    const tv=data.reduce((a,b)=>a+b.total,0),tc=data.reduce((a,b)=>a+b.comision,0),nc=data.length;
    const pv=obj.ventas?Math.min((tv/obj.ventas)*100,100):null;
    const pc=obj.comisiones?Math.min((tc/obj.comisiones)*100,100):null;
    const pk=obj.cierres?Math.min((nc/obj.cierres)*100,100):null;
    const pill=pct=>pct!==null?`<span style="display:inline-block;padding:2px 8px;border-radius:10px;font-size:11px;font-weight:700;background:${pct>=100?'#d4edda':'#f0ede6'};color:${pct>=100?'#2d7a4f':'#6b6460'}">${pct.toFixed(0)}%</span>`:'<span style="color:#bbb;font-size:11px">—</span>';
    return`<tr><td style="font-weight:600">${monthName(k)}</td><td>${fmt(tv)}</td><td style="color:var(--gold);font-weight:700">${fmt(tc)}</td><td>${nc}</td><td>${pill(pv)}</td><td>${pill(pc)}</td><td>${pill(pk)}</td></tr>`;
  }).join('');
  box.innerHTML=`<div class="table-wrap"><table><thead><tr><th>Mes</th><th>Ventas</th><th>Comisiones</th><th>Cierres</th><th>% Meta ventas</th><th>% Meta com.</th><th>% Meta cierres</th></tr></thead><tbody>${rows}</tbody></table></div>`;
}

// ── EXPORTAR ───────────────────────────────────────────
function exportCSV(){
  const data=getFiltered(document.getElementById('f_desde').value,document.getElementById('f_hasta').value,document.getElementById('f_tipo').value,document.getElementById('f_firma').value).sort((a,b)=>b.fecha.localeCompare(a.fecha));
  if(!data.length)return alert('Sin datos para exportar');
  const rows=[['Fecha','Inversionista','Tickets','Total','% Comisión','Comisión','Tipo','Firmado'],...data.map(v=>[v.fecha,v.nombre,v.qty,v.total.toFixed(2),v.pct,v.comision.toFixed(2),v.tipo,v.firmo])];
  dlCSV(rows.map(r=>r.map(c=>`"${c}"`).join(',')).join('\n'),`portalia_ventas_${today()}.csv`);
}
function abrirModalPDF(){document.getElementById('modalPDF').classList.add('open');}
function exportPDFReport(){
  const especialista=document.getElementById('pdf_especialista').value.trim()||'Especialista comercial';
  const data=getFiltered(document.getElementById('f_desde').value,document.getElementById('f_hasta').value,document.getElementById('f_tipo').value,document.getElementById('f_firma').value).sort((a,b)=>b.fecha.localeCompare(a.fecha));
  if(!data.length){cerrarModal('modalPDF');return alert('Sin datos');}
  cerrarModal('modalPDF');
  const tv=data.reduce((a,b)=>a+b.total,0),tc=data.reduce((a,b)=>a+b.comision,0);
  const w=window.open('','_blank');
  w.document.write(`<!DOCTYPE html><html><head><meta charset="UTF-8"><title>Portalia – Reporte</title>
  <style>body{font-family:Arial,sans-serif;color:#1a1a1a;margin:0;padding:32px}.logo{font-size:24px;font-weight:900;letter-spacing:3px}.gold{color:#C9A84C}.sub{font-size:10px;letter-spacing:2px;color:#888;text-transform:uppercase}.divider{height:2px;background:#C9A84C;margin:16px 0}.hrow{display:flex;justify-content:space-between;align-items:flex-end;margin-bottom:8px}.metrics{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin:16px 0}.m{background:#f5f4f0;padding:12px;border-radius:6px;border-left:3px solid #C9A84C}.m-label{font-size:10px;text-transform:uppercase;color:#888}.m-val{font-size:18px;font-weight:700}table{width:100%;border-collapse:collapse;font-size:12px}th{background:#1C1C1C;color:#C9A84C;padding:8px;text-align:left;font-size:10px;text-transform:uppercase}td{padding:7px 8px;border-bottom:1px solid #e8e2d6}tr:nth-child(even) td{background:#fafaf7}.footer{margin-top:24px;font-size:10px;color:#aaa;text-align:center;border-top:1px solid #e0d9cc;padding-top:12px}@media print{body{padding:20px}}</style></head><body>
  <div class="logo">PORTALIA <span class="gold">|</span> DESARROLLOS</div><div class="sub">Reporte de comisiones</div>
  <div class="divider"></div>
  <div class="hrow"><div><div style="font-size:14px;font-weight:700">${especialista}</div><div style="font-size:12px;color:#666;margin-top:2px">Período: ${document.getElementById('f_desde').value||'Inicio'} — ${document.getElementById('f_hasta').value||today()}</div></div><div style="font-size:11px;color:#888">Generado: ${new Date().toLocaleDateString('es-MX')}</div></div>
  <div class="metrics"><div class="m"><div class="m-label">Total ventas</div><div class="m-val">${fmt(tv)}</div></div><div class="m"><div class="m-label">Comisiones</div><div class="m-val" style="color:#8B6914">${fmt(tc)}</div></div><div class="m"><div class="m-label">Operaciones</div><div class="m-val">${data.length}</div></div><div class="m"><div class="m-label">Firmados</div><div class="m-val">${data.filter(v=>v.firmo==='si').length}</div></div></div>
  <table><thead><tr><th>Fecha</th><th>Inversionista</th><th>Tickets</th><th>Total venta</th><th>Comisión</th><th>%</th><th>Tipo</th><th>Contrato</th></tr></thead>
  <tbody>${data.map(v=>`<tr><td>${v.fecha}</td><td>${v.nombre}</td><td>${v.qty}</td><td style="text-align:right">${fmt(v.total)}</td><td style="text-align:right;color:#8B6914;font-weight:700">${fmt(v.comision)}</td><td>${v.pct}%</td><td>${v.tipo}</td><td>${v.firmo==='si'?'Firmado':'Pendiente'}</td></tr>`).join('')}</tbody>
  <tfoot><tr style="background:#1C1C1C;color:#fff"><td colspan="3"><b>TOTALES</b></td><td style="color:#C9A84C;font-weight:700;text-align:right">${fmt(tv)}</td><td style="color:#C9A84C;font-weight:700;text-align:right">${fmt(tc)}</td><td colspan="3"></td></tr></tfoot></table>
  <div class="footer">PORTALIA DESARROLLOS · ${especialista} · Uso interno</div>
  <script>window.onload=()=>window.print()<\/script></body></html>`);
  w.document.close();
}
</script>
</body>
</html>
