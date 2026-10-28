<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Dirección Técnica | Centro de Control</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js"></script>
<style>
:root{--navy:#0b1935;--side:#0c1c39;--teal:#08b6bd;--blue:#3d80f4;--bg:#f3f6fb;--ink:#17233a;--muted:#72809a;--line:#e3eaf3;--red:#df4b62;--amber:#e7a13a;--green:#1ea784}
*{box-sizing:border-box}
body{margin:0;font-family:Inter,Segoe UI,Arial,sans-serif;background:var(--bg);color:var(--ink)}
button,input,select,textarea{font:inherit}
button{cursor:pointer}
a{color:var(--blue)}
.app{display:flex;min-height:100vh}
.sidebar{width:255px;background:var(--side);color:#fff;position:sticky;top:0;height:100vh;padding:24px 15px;flex-shrink:0;display:flex;flex-direction:column}
.brand{padding:8px 13px 22px;border-bottom:1px solid #243754;margin-bottom:16px}
.brand .symbol{width:31px;height:31px;display:inline-grid;place-items:center;background:linear-gradient(135deg,#1dc5bd,#567bfc);border-radius:10px;font-size:19px;margin-right:7px}
.brand b{font-size:16px}
.brand small{display:block;color:#a7b6cc;margin-top:10px;letter-spacing:.07em;font-size:10px}
.nav{display:flex;flex-direction:column;gap:5px;flex:1;overflow-y:auto}
.nav button{border:0;color:#acbdd8;background:none;padding:11px 14px;text-align:left;border-radius:9px;font-weight:600;font-size:13px;display:flex;align-items:center}
.nav button.active,.nav button:hover{background:#1b3557;color:white}
.nav .icon{display:inline-block;width:27px;font-size:16px;flex-shrink:0}
.sideFoot{padding:14px 12px 0;border-top:1px solid #1e314d;color:#a7b6cc;font-size:11px;line-height:1.6}
.main{min-width:0;flex:1;padding:26px 34px 52px;max-width:1700px;margin:auto}
.top{display:flex;justify-content:space-between;align-items:center;gap:20px;margin-bottom:24px}
.eyebrow{color:var(--teal);letter-spacing:.12em;text-transform:uppercase;font-size:10px;font-weight:800}
.top h1{font-size:26px;letter-spacing:-.8px;margin:4px 0 4px}
.subtitle{color:var(--muted);font-size:13px}
.actions{display:flex;gap:9px;flex-wrap:wrap}
.btn{border:1px solid var(--line);background:white;color:var(--ink);border-radius:9px;padding:10px 13px;font-size:12px;font-weight:700;display:inline-flex;align-items:center;gap:7px}
.btn.primary{background:linear-gradient(120deg,#2f81eb,#12b7ba);color:white;border:0}
.btn.danger{color:var(--red)}
.btn:hover{filter:brightness(.97)}
.btn:disabled{opacity:.55;cursor:not-allowed}
.kpis{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:15px;margin:0 0 20px}
.kpi,.panel{background:#fff;border:1px solid var(--line);border-radius:15px;box-shadow:0 5px 22px #18305a08}
.kpi{padding:20px;position:relative;overflow:hidden}
.kpi:after{content:'';position:absolute;right:-28px;top:-34px;border-radius:50%;height:106px;width:106px;background:#f0f7ff}
.kpi .n{font-weight:850;font-size:32px;position:relative;z-index:2;margin-top:9px}
.kpi .l{color:var(--muted);font-size:12px;font-weight:700;position:relative;z-index:2}
.kpi .detail{font-size:11px;color:var(--muted);margin-top:7px;position:relative;z-index:2}
.grid{display:grid;grid-template-columns:1.4fr 1fr;gap:17px;margin-bottom:19px}
.gridEqual{display:grid;grid-template-columns:1fr 1fr;gap:17px;margin-bottom:19px}
.panel{padding:20px;min-width:0}
.panel h3{margin:0 0 15px;font-size:15px}
.muted{color:var(--muted)}
.small{font-size:12px}
.section{display:none}
.section.active{display:block}
.sectionTitle{display:flex;align-items:center;justify-content:space-between;gap:12px;margin:0 0 16px;flex-wrap:wrap}
.sectionTitle h2{font-size:19px;margin:0}
.toolbar{display:flex;flex-wrap:wrap;gap:9px;margin-bottom:14px}
.field{border:1px solid var(--line);border-radius:9px;background:white;min-height:39px;padding:10px;color:var(--ink);font-size:12px;outline-color:var(--teal)}
.search{width:270px;max-width:100%}
.tablewrap{overflow:auto}
.table{width:100%;border-collapse:collapse;text-align:left;font-size:12px}
.table th{font-size:10px;text-transform:uppercase;color:#8590a5;letter-spacing:.08em;padding:12px;border-bottom:1px solid var(--line);white-space:nowrap}
.table td{padding:13px 12px;border-bottom:1px solid #eff3f8;vertical-align:middle}
.table tr:last-child td{border-bottom:0}
.table td:first-child{font-weight:700}
.pill{display:inline-flex;border-radius:30px;padding:5px 8px;font-size:10px;font-weight:800;white-space:nowrap;background:#ebf3ff;color:#3877d3}
.pill.ok{background:#e7f7f0;color:#15856c}
.pill.bad{background:#ffedf0;color:#c43e55}
.pill.warn{background:#fff5e6;color:#a9741d}
.pill.gray{background:#eef1f5;color:#69778d}
.rowactions{display:flex;gap:5px;flex-wrap:wrap}
.linkBtn{border:none;background:#ecf5ff;color:#216cb1;padding:6px 9px;border-radius:7px;font-size:11px;font-weight:600;display:inline-flex;align-items:center;gap:4px}
.linkBtn.teal{background:#e6faf8;color:#0e7c80}
.linkBtn.red{background:#ffedf0;color:#bf354e}
.fileBadge{display:inline-flex;align-items:center;gap:5px;background:#f2f8ff;color:#1f68c4;border:1px solid #cce0fc;padding:4px 8px;border-radius:7px;font-size:11px;font-weight:700;cursor:pointer}
.fileBadge:hover{background:#e5f1ff}
.subItemBox{background:#f8fbff;border:1px solid #d4def2;border-radius:8px;padding:10px;margin-top:6px}
.subItemRow{display:flex;justify-content:space-between;align-items:center;gap:8px;padding:4px 0;border-bottom:1px dashed #e2eaf5;font-size:11.5px}
.subItemRow:last-child{border-bottom:0}
.subTabs{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:16px;border-bottom:1px solid var(--line);padding-bottom:12px}
.subTabBtn{border:1px solid var(--line);background:white;color:var(--muted);padding:8px 14px;border-radius:8px;font-size:12px;font-weight:700;cursor:pointer}
.subTabBtn.active{background:var(--navy);color:white;border-color:var(--navy)}
.checklistContainer{display:grid;gap:10px;margin-top:12px}
.checkItemRow{background:#fafbfd;border:1px solid var(--line);border-radius:10px;padding:12px 14px;display:flex;flex-direction:column;gap:8px}
.checkItemTop{display:flex;justify-content:space-between;align-items:center;gap:10px;flex-wrap:wrap}
.checkItemFiles{display:flex;gap:6px;flex-wrap:wrap;align-items:center;margin-top:4px}
.progress{height:9px;background:#e8edf5;border-radius:20px;overflow:hidden}
.progress span{height:100%;display:block;background:linear-gradient(90deg,#3b85f3,#00babc);border-radius:20px;transition:width .25s}
.stats{display:flex;justify-content:space-between;margin-bottom:10px;font-size:12px}
.statrow{padding:10px 0;border-bottom:1px solid #edf2f7}
.statrow:last-child{border:0}
.urgent{border-left:4px solid #e75e72;background:#fff6f7;padding:13px;border-radius:8px;margin:9px 0}
.urgent .tag{font-size:10px;color:#b33145;font-weight:800;letter-spacing:.04em}
.urgent p{font-size:12px;margin:5px 0 0}
.activity{font-size:12px;padding:10px 0;border-bottom:1px solid #eaf0f7}
.activity:last-child{border:0}
.activity time{display:block;color:var(--muted);font-size:10px;margin-top:4px}
.empty{color:var(--muted);text-align:center;padding:34px;font-size:12px}
.steps{display:grid;gap:9px}
.step{display:flex;gap:10px;border:1px solid var(--line);padding:12px;border-radius:10px;background:#fcfdff}
.step .circle{width:25px;height:25px;border-radius:50%;background:#e9f5fb;color:#207ab4;flex-shrink:0;display:grid;place-items:center;font-weight:800;font-size:11px}
.step b{font-size:12px}
.step p{font-size:12px;margin:5px 0;color:#6d7b8e;line-height:1.5}
.notice{border:1px solid #c6e7ed;background:#f0fcff;padding:12px 15px;border-radius:10px;color:#32617a;font-size:12px;line-height:1.6;margin-bottom:15px}
.fileAttached{display:flex;align-items:center;justify-content:space-between;gap:10px;background:#f2f8ff;border:1px solid #cfe2fa;border-radius:8px;padding:8px 11px;margin-top:8px;font-size:12px}
.modalOverlay{position:fixed;inset:0;background:#08162bc7;z-index:30;display:none;align-items:center;justify-content:center;padding:20px}
.modalOverlay.show{display:flex}
.modal{background:white;border-radius:15px;width:780px;max-width:100%;max-height:92vh;overflow:auto;padding:23px;box-shadow:0 20px 70px #0005}
.modal.large{width:1080px}
.modal header{display:flex;justify-content:space-between;align-items:center;border-bottom:1px solid var(--line);padding-bottom:15px;margin-bottom:18px;gap:12px}
.modal h2{margin:0;font-size:18px}
.close{border:0;background:none;font-size:24px;color:#7b8ba2}
.formgrid{display:grid;grid-template-columns:1fr 1fr;gap:13px}
.formgrid label{font-size:11px;font-weight:700;display:block;color:#526179}
.formgrid label input,.formgrid label select,.formgrid label textarea{display:block;width:100%;margin-top:6px}
.formgrid .wide{grid-column:1/-1}
.modalfooter{display:flex;justify-content:flex-end;gap:8px;margin-top:20px;flex-wrap:wrap}
.flash{position:fixed;right:25px;bottom:22px;background:#15395b;color:white;padding:12px 18px;border-radius:10px;z-index:50;display:none;font-size:13px;box-shadow:0 8px 25px #0003}
.highlight{background:linear-gradient(120deg,#102b52,#115779);color:white;padding:25px;border-radius:16px;margin-bottom:18px}
.highlight h2{font-size:23px;margin:0 0 7px}
.highlight p{font-size:12px;color:#c6dceb;max-width:680px;line-height:1.7}
.highlight .btn{margin-top:10px}
.transArea{width:100%;min-height:290px;resize:vertical;font-family:Inter,Segoe UI,Arial,sans-serif;line-height:1.55;font-size:12.5px}
.pdfPreviewFrame{width:100%;height:74vh;border:1px solid var(--line);border-radius:10px;background:#eef2f7}
.footerNote{color:#8793a3;font-size:11px;margin-top:22px;line-height:1.6}
@media(max-width:1100px){
  .sidebar{width:72px;padding:21px 9px}
  .brand{padding:8px 4px}
  .brand b,.brand small,.nav .navtext,.sideFoot{display:none}
  .nav button{padding:11px;justify-content:center}
  .nav .icon{width:auto}
  .main{padding:22px}
  .grid,.gridEqual{grid-template-columns:1fr}
}
@media(max-width:700px){
  .app{display:block}
  .sidebar{position:relative;width:100%;height:auto;padding:9px}
  .brand{display:none}
  .nav{flex-direction:row;overflow:auto}
  .nav button{flex:0 0 auto}
  .main{padding:15px}
  .top{align-items:flex-start;flex-direction:column}
  .kpis{grid-template-columns:repeat(2,minmax(0,1fr));gap:9px}
  .kpi{padding:13px}
  .kpi .n{font-size:25px}
  .formgrid{grid-template-columns:1fr}
  .modal{padding:16px}
}
@media print{
  .sidebar,.actions,.toolbar,.rowactions,.btn,.modalOverlay{display:none!important}
  .main{padding:0}
  .panel,.kpi{box-shadow:none}
}
</style>
</head>
<body>
<div class="app">
  <aside class="sidebar">
    <div class="brand">
      <span class="symbol">✦</span><b>Dirección Técnica</b>
      <small>CENTRO DE CONTROL REGULATORIO</small>
    </div>
    <nav class="nav" id="nav">
      <button data-page="dashboard" class="active"><span class="icon">◫</span><span class="navtext">Panel general</span></button>
      <button data-page="procedimientos"><span class="icon">▤</span><span class="navtext">Control Documental</span></button>
      <button data-page="cronograma"><span class="icon">▦</span><span class="navtext">Cronogramas y Sub-items</span></button>
      <button data-page="inspecciones"><span class="icon">◉</span><span class="navtext">Inspecciones DIGEMID</span></button>
      <button data-page="hallazgos"><span class="icon">⚑</span><span class="navtext">Hallazgos y CAPA</span></button>
      <button data-page="evidencias"><span class="icon">◈</span><span class="navtext">Evidencias y Checklists BPA/BPDT</span></button>
      <button data-page="traduccion"><span class="icon">文</span><span class="navtext">Traducción PDF</span></button>
      <button data-page="configuracion"><span class="icon">⚙</span><span class="navtext">Configuración</span></button>
    </nav>
    <div class="sideFoot">
      Ejecución local en PC v2.5<br>
      Módulo de Evidencias y Checklists BPA/BPDT
    </div>
  </aside>

  <main class="main">
    <div class="top">
      <div>
        <div class="eyebrow">BPA · BPDT · GESTIÓN REGULATORIA</div>
        <h1 id="pageTitle">Evidencias y Checklists BPA/BPDT</h1>
        <div class="subtitle" id="dateCaption"></div>
      </div>
      <div class="actions">
        <button class="btn" onclick="window.print()">⎙ Imprimir panel</button>
        <button class="btn" onclick="exportJSON()">⇩ Respaldo JSON</button>
        <button class="btn primary" onclick="openCreateEvidencia()">＋ Nuevo expediente de evidencia</button>
      </div>
    </div>

    <!-- DASHBOARD -->
    <section class="section" id="dashboard">
      <div class="kpis">
        <div class="kpi"><div class="l">Procedimientos vigentes</div><div class="n" id="kVigentes">0</div><div class="detail" id="kTotalDoc"></div></div>
        <div class="kpi"><div class="l">Actividades próximas (30 días)</div><div class="n" id="kProximas">0</div><div class="detail">Cronograma de DT</div></div>
        <div class="kpi"><div class="l">Alertas y vencimientos</div><div class="n" id="kAlertas">0</div><div class="detail">Documentos y tareas</div></div>
        <div class="kpi"><div class="l">Expedientes de Evidencias</div><div class="n" id="kEvidenciasCount">0</div><div class="detail">BPA y BPDT</div></div>
      </div>
      <div class="grid">
        <div class="panel"><h3>Cumplimiento de cronogramas</h3><div id="progressItems"></div></div>
        <div class="panel"><h3>Atención prioritaria</h3><div id="alertItems"></div></div>
      </div>
      <div class="grid">
        <div class="panel">
          <h3>Próximas actividades y sub-ítems</h3>
          <div class="tablewrap">
            <table class="table">
              <thead><tr><th>Actividad / Sub-ítem</th><th>Vínculo Doc.</th><th>Fecha límite</th><th>Responsable</th><th>Estado</th></tr></thead>
              <tbody id="nextActivities"></tbody>
            </table>
          </div>
        </div>
        <div class="panel"><h3>Movimiento reciente</h3><div id="recentItems"></div></div>
      </div>
    </section>

    <!-- CONTROL DOCUMENTAL -->
    <section class="section" id="procedimientos">
      <div class="sectionTitle">
        <h2>Lista maestra de control documental y POEs regulatorios</h2>
        <button class="btn primary" onclick="openModal('procedimientos')">＋ Agregar documento POE</button>
      </div>
      <div class="subTabs" id="poeSubTabs">
        <button class="subTabBtn active" data-sub="TODOS" onclick="switchPoeSub('TODOS')">📂 Todos los POEs</button>
        <button class="subTabBtn" data-sub="BPA_APERTURA" onclick="switchPoeSub('BPA_APERTURA')">🏢 POEs BPA - Apertura</button>
        <button class="subTabBtn" data-sub="BPA_AMPLIACION" onclick="switchPoeSub('BPA_AMPLIACION')">📈 POEs BPA - Ampliación</button>
        <button class="subTabBtn" data-sub="DT" onclick="switchPoeSub('DT')">📋 POEs Dirección Técnica (DT)</button>
        <button class="subTabBtn" data-sub="BPDT" onclick="switchPoeSub('BPDT')">🚚 POEs BPDT (Transporte/Distribución)</button>
      </div>
      <div class="panel">
        <div class="toolbar">
          <input class="field search" id="searchProcedimientos" placeholder="Buscar código, procedimiento o área...">
          <select class="field" id="filterProcedimientos"><option value="">Todos los estados</option><option>Vigente</option><option>En revisión</option><option>Obsoleto</option></select>
          <button class="btn" onclick="exportCSV('procedimientos')">⇩ Exportar CSV</button>
        </div>
        <div class="tablewrap">
          <table class="table">
            <thead><tr><th>Código</th><th>Documento / POE</th><th>Submódulo</th><th>Área</th><th>Versión</th><th>Vencimiento</th><th>Archivos Adjuntos</th><th>Estado</th><th>Acciones</th></tr></thead>
            <tbody id="rowsProcedimientos"></tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- CRONOGRAMA -->
    <section class="section" id="cronograma">
      <div class="sectionTitle">
        <h2>Cronograma de actividades y sub-ítems vinculados</h2>
        <button class="btn primary" onclick="openModal('cronograma')">＋ Programar actividad principal</button>
      </div>
      <div class="panel">
        <div class="toolbar">
          <input class="field search" id="searchCronograma" placeholder="Buscar actividad, sub-ítem o código doc...">
          <select class="field" id="filterCronograma"><option value="">Todos los estados</option><option>Pendiente</option><option>En proceso</option><option>Completado</option></select>
          <button class="btn" onclick="exportCSV('cronograma')">⇩ Exportar CSV</button>
        </div>
        <div class="tablewrap">
          <table class="table">
            <thead><tr><th>Actividad principal / Sub-ítems (Tareas y Fases)</th><th>Código Doc. Vinculado</th><th>Tipo</th><th>Responsable</th><th>Archivos PDF</th><th>Estado General</th><th>Acciones</th></tr></thead>
            <tbody id="rowsCronograma"></tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- INSPECCIONES -->
    <section class="section" id="inspecciones">
      <div class="highlight">
        <div class="eyebrow" style="color:#58e6dd">PROTOCOLO DE RESPUESTA</div>
        <h2>Inspección inopinada DIGEMID</h2>
        <p>Activa un registro de inspección, adjunta múltiples actas y archivos, asigna responsables y organiza las observaciones.</p>
        <button class="btn primary" onclick="openModal('inspecciones')">＋ Registrar inspección</button>
        <button class="btn" onclick="window.print()">⎙ Imprimir panel</button>
      </div>
      <div class="grid">
        <div class="panel">
          <h3>Lista de actuación inmediata</h3>
          <div class="steps">
            <div class="step"><div class="circle">1</div><div><b>Verificar credenciales y alcance</b><p>Registrar inspectores y autoridad.</p></div></div>
            <div class="step"><div class="circle">2</div><div><b>Notificar a Dirección Técnica</b><p>Designar punto de contacto.</p></div></div>
            <div class="step"><div class="circle">3</div><div><b>Ubicar documentos vigentes</b><p>Consultar lista maestra.</p></div></div>
            <div class="step"><div class="circle">4</div><div><b>Registrar hechos y adjuntar archivos</b><p>Trazabilidad.</p></div></div>
            <div class="step"><div class="circle">5</div><div><b>Dar seguimiento a observaciones</b><p>Crear hallazgos y CAPA.</p></div></div>
          </div>
        </div>
        <div class="panel"><h3>Kit documental</h3><div id="inspectionKit"></div></div>
      </div>
      <div class="panel">
        <h3>Historial de inspecciones</h3>
        <div class="tablewrap">
          <table class="table">
            <thead><tr><th>Fecha</th><th>Tipo / referencia</th><th>Autoridad</th><th>Responsable</th><th>Archivos Adjuntos</th><th>Estado</th><th>Acciones</th></tr></thead>
            <tbody id="rowsInspecciones"></tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- HALLAZGOS Y CAPA -->
    <section class="section" id="hallazgos">
      <div class="sectionTitle">
        <h2>Seguimiento de hallazgos y acciones CAPA</h2>
        <button class="btn primary" onclick="openModal('hallazgos')">＋ Registrar hallazgo</button>
      </div>
      <div class="panel">
        <div class="toolbar">
          <input class="field search" id="searchHallazgos" placeholder="Buscar hallazgo, origen o responsable...">
          <select class="field" id="filterHallazgos"><option value="">Todos los estados</option><option>Abierto</option><option>En proceso</option><option>Cerrado</option></select>
          <button class="btn" onclick="exportCSV('hallazgos')">⇩ Exportar CSV</button>
        </div>
        <div class="tablewrap">
          <table class="table">
            <thead><tr><th>Referencia</th><th>Hallazgo</th><th>Criticidad</th><th>Responsable</th><th>Compromiso</th><th>Sustentos Adjuntos</th><th>Estado</th><th>Acciones</th></tr></thead>
            <tbody id="rowsHallazgos"></tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- MÓDULO DE EVIDENCIAS: CHECKLISTS BPA Y TRAZABILIDAD BPDT -->
    <section class="section active" id="evidencias">
      <div class="sectionTitle">
        <h2>Módulo de Evidencias: Checklists BPA y Trazabilidad BPDT</h2>
        <button class="btn primary" onclick="openCreateEvidencia()">＋ Nuevo expediente de evidencia</button>
      </div>
      
      <div class="notice">
        <b>Gestión Regulatoria de Recepción y Distribución:</b><br>
        • <b>Checklist BPA (Recepción de Importación / Lote):</b> Incluye Acta de Recepción, Commercial Invoice, Packing List, Declaración Aduanera (DAM), Constancia de Percepción, Guía de Transportista, Lectura de Datalogger (si es refrigerado), Análisis Organoléptico y Certificado de Análisis.<br>
        • <b>Trazabilidad BPDT (Distribución y Transporte):</b> Incluye Guía de Remisión (Cargo), Guía de Remisión (Salida), Orden de Compra, Lectura de Datalogger y Hoja de Ruta. Cada ítem permite adjuntar sus respectivos archivos PDF sustentatorios.
      </div>

      <div class="panel">
        <div class="toolbar">
          <input class="field search" id="searchEvidencias" placeholder="Buscar expediente, lote o producto...">
          <button class="btn" onclick="exportCSV('evidencias')">⇩ Exportar CSV</button>
        </div>
        <div class="tablewrap">
          <table class="table">
            <thead><tr><th>Código / Folio</th><th>Expediente / Lote / Producto</th><th>Tipo de Checklist</th><th>Fecha</th><th>Progreso Archivos PDF</th><th>Estado</th><th>Acciones</th></tr></thead>
            <tbody id="rowsEvidencias"></tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- TRADUCCIÓN PDF -->
    <section class="section" id="traduccion">
      <div class="sectionTitle">
        <h2>Módulo de Traducción Técnica de Documentos PDF</h2>
        <div style="display:flex;gap:8px;flex-wrap:wrap">
          <button class="btn" onclick="clearTranslator()">↺ Limpiar mesa</button>
          <button class="btn primary" onclick="saveTranslationRecord()">💾 Guardar en historial</button>
        </div>
      </div>
      <div class="panel" style="margin-bottom:18px">
        <h3>1. Carga de archivo PDF y parámetros</h3>
        <div class="formgrid" style="margin-bottom:14px">
          <label>Código / Referencia<input class="field" id="trCodigo" placeholder="Ej. TRAD-COA-2026-001"></label>
          <label>Nombre del documento<input class="field" id="trNombre" placeholder="Ej. Certificado"></label>
          <label>Categoría regulatoria
            <select class="field" id="trCategoria">
              <option>Certificado de Análisis (CoA)</option>
              <option>Certificado BPM / ISO</option>
              <option>Inserto / Ficha Técnica</option>
              <option>Manual / Instrucciones de Uso (IFU)</option>
              <option>Dossier / Registro Sanitario</option>
              <option>Procedimiento / POE</option>
              <option>Otro</option>
            </select>
          </label>
          <label>Estado de revisión
            <select class="field" id="trEstado">
              <option>En traducción</option>
              <option>Revisado / Vigente</option>
              <option>Pendiente</option>
            </select>
          </label>
          <label>Idioma origen
            <select class="field" id="trSourceLang">
              <option value="en">Inglés (EN)</option>
              <option value="zh-CN">Chino (ZH)</option>
              <option value="pt">Portugués (PT)</option>
              <option value="auto">Detectar (Auto)</option>
            </select>
          </label>
          <label>Idioma destino
            <select class="field" id="trTargetLang">
              <option value="es">Español (ES)</option>
              <option value="en">Inglés (EN)</option>
            </select>
          </label>
        </div>
        <div class="uploadBox" id="trDropZone">
          <p style="margin:0 0 8px;font-weight:700;font-size:13px">📄 Arrastra aquí tu archivo PDF</p>
          <label class="btn primary" style="cursor:pointer">Seleccionar PDF<input type="file" id="trPdfInput" accept="application/pdf,.pdf"></label>
          <div id="trFileInfo" style="margin-top:10px" class="small muted">Ningún archivo cargado.</div>
        </div>
        <div id="trPreviewWrap" style="display:none;margin-top:15px">
          <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px">
            <b class="small">Vista previa PDF</b>
            <button type="button" class="linkBtn" onclick="toggleTrPreview()">Mostrar / Ocultar</button>
          </div>
          <iframe id="trPdfPreview" class="pdfPreviewFrame"></iframe>
        </div>
      </div>
      <div class="panel" style="margin-bottom:18px">
        <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:10px;margin-bottom:12px">
          <h3 style="margin:0">2. Mesa bilingüe de traducción</h3>
          <div style="display:flex;gap:8px;flex-wrap:wrap">
            <button class="btn primary" id="btnRunTranslate" onclick="runTranslation()">⚡ Traducir automáticamente</button>
            <button class="btn" onclick="exportTranslatedDoc()">⎙ Imprimir / PDF</button>
            <button class="btn" onclick="downloadTranslatedTxt()">⇩ Descargar TXT</button>
          </div>
        </div>
        <div id="trProgressWrap" style="display:none;margin-bottom:12px">
          <div class="stats"><span id="trProgressLabel">Traduciendo...</span><b id="trProgressPct">0%</b></div>
          <div class="progress"><span id="trProgressBar" style="width:0%"></span></div>
        </div>
        <div class="gridEqual" style="margin-bottom:0">
          <div>
            <label class="small" style="font-weight:700;display:block;margin-bottom:6px">Texto original (editable)</label>
            <textarea class="field transArea" id="trSourceText" placeholder="Texto original..."></textarea>
          </div>
          <div>
            <label class="small" style="font-weight:700;display:block;margin-bottom:6px">Traducción técnica (editable)</label>
            <textarea class="field transArea" id="trTargetText" placeholder="Traducción..."></textarea>
          </div>
        </div>
      </div>
      <div class="panel">
        <div class="sectionTitle"><h3 style="margin:0">3. Repositorio de traducciones</h3></div>
        <div class="toolbar">
          <input class="field search" id="searchTraduccion" placeholder="Buscar código o documento...">
          <select class="field" id="filterTraduccion"><option value="">Todos los estados</option><option>Pendiente</option><option>En traducción</option><option>Revisado / Vigente</option></select>
          <button class="btn" onclick="exportCSV('traduccion')">⇩ Exportar CSV</button>
        </div>
        <div class="tablewrap">
          <table class="table">
            <thead><tr><th>Código</th><th>Documento</th><th>Categoría</th><th>Idiomas</th><th>Fecha</th><th>Archivos Adjuntos</th><th>Estado</th><th>Acciones</th></tr></thead>
            <tbody id="rowsTraduccion"></tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- CONFIGURACIÓN -->
    <section class="section" id="configuracion">
      <div class="sectionTitle"><h2>Configuración y respaldos en PC</h2></div>
      <div class="grid">
        <div class="panel">
          <h3>Establecimiento y motor de IA opcional</h3>
          <div class="formgrid">
            <label class="wide">Razón social<input class="field" id="empresa"></label>
            <label>Director(a) Técnico(a)<input class="field" id="director"></label>
            <label>Almacén / sede<input class="field" id="sede"></label>
            <label>Anticipación de alertas (días)<input class="field" type="number" min="1" max="365" id="alertDays"></label>
            <label class="wide">Clave API de Google Gemini (Opcional)<input class="field" type="password" id="geminiKey" placeholder="AIzaSy..."></label>
          </div>
          <div style="margin-top:15px"><button class="btn primary" onclick="saveSettings()">Guardar configuración</button></div>
        </div>
        <div class="panel">
          <h3>Almacenamiento local y respaldos</h3>
          <p class="small muted">Ejecución 100% local en PC (IndexedDB). Todos los registros y archivos se respaldan de forma segura.</p>
          <div class="steps">
            <button class="btn" onclick="exportJSON()">⇩ Descargar respaldo rápido (JSON)</button>
            <button class="btn primary" onclick="exportFullBackup()">⇩ Descargar respaldo completo (JSON + Archivos)</button>
            <label class="btn" style="cursor:pointer">⇧ Importar respaldo JSON<input type="file" accept=".json,application/json" style="display:none" id="importFile"></label>
            <button class="btn danger" onclick="resetDemo()">Restablecer datos de demostración</button>
          </div>
        </div>
      </div>
    </section>

    <div class="footerNote">Dirección Técnica · Módulo de Evidencias con Checklists BPA y Trazabilidad BPDT en PC.</div>
  </main>
</div>

<!-- MODAL GENERAL PARA OTROS MÓDULOS -->
<div class="modalOverlay" id="modalOverlay" onclick="if(event.target===this)closeModal()">
  <div class="modal" style="width:860px">
    <header>
      <h2 id="modalTitle">Nuevo registro</h2>
      <button class="close" onclick="closeModal()" aria-label="Cerrar">×</button>
    </header>
    <form id="recordForm">
      <div id="poeSubModuleSelectorWrap" style="margin-bottom:14px;display:none">
        <label style="font-size:11px;font-weight:700;color:var(--navy);display:block;margin-bottom:5px">Submódulo Regulatorio POE *</label>
        <select class="field" id="modalPoeSub" style="font-weight:700;color:var(--blue)">
          <option value="BPA_APERTURA">🏢 POEs BPA - Apertura</option>
          <option value="BPA_AMPLIACION">📈 POEs BPA - Ampliación</option>
          <option value="DT">📋 POEs Dirección Técnica (DT)</option>
          <option value="BPDT">🚚 POEs BPDT (Transporte y Distribución)</option>
        </select>
      </div>

      <div class="formgrid" id="formFields"></div>
      
      <div id="subItemsSection" style="display:none;margin-top:18px;border-top:1px solid var(--line);padding-top:14px">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px">
          <div>
            <b style="font-size:12px;color:var(--navy)">Sub-ítems del cronograma (Fases y fechas límite)</b>
          </div>
          <button type="button" class="btn primary" onclick="addSubItemRow()" style="padding:6px 10px;font-size:11px">＋ Agregar Sub-ítem</button>
        </div>
        <div id="subItemsContainer" style="display:grid;gap:8px;max-height:260px;overflow-y:auto;padding-right:4px"></div>
      </div>

      <div style="margin-top:16px;padding-top:14px;border-top:1px solid var(--line)">
        <label style="font-size:11px;font-weight:700;color:#526179;display:block;margin-bottom:6px">Archivos adjuntos generales (PDF, Word, Excel...)</label>
        <input class="field" type="file" id="modalPdfFiles" multiple style="width:100%">
        <div id="modalCurrentPdfs" style="margin-top:8px"></div>
      </div>

      <div class="modalfooter">
        <button type="button" class="btn" onclick="closeModal()">Cancelar</button>
        <button type="submit" class="btn primary">Guardar registro</button>
      </div>
    </form>
  </div>
</div>

<!-- MODAL ESPECÍFICO PARA EXPEDIENTES DE EVIDENCIAS (CHECKLISTS BPA / BPDT) -->
<div class="modalOverlay" id="evidenciaModalOverlay" onclick="if(event.target===this)closeEvidenciaModal()">
  <div class="modal large" style="width:1100px">
    <header>
      <h2 id="evidenciaModalTitle">Gestión de Expediente de Evidencia (Checklist BPA / BPDT)</h2>
      <button class="close" onclick="closeEvidenciaModal()" aria-label="Cerrar">×</button>
    </header>
    <form id="evidenciaForm" onsubmit="saveEvidenciaRecord(event)">
      <div class="formgrid" style="margin-bottom:16px">
        <label>Código / Folio de Expediente<input class="field" id="evCodigo" required placeholder="Ej. EXP-BPA-2026-001"></label>
        <label>Nombre del Expediente / Lote / Producto<input class="field" id="evNombre" required placeholder="Ej. Importación Paracetamol 500mg Lote L2609"></label>
        <label>Tipo de Checklist Regulatorio
          <select class="field" id="evTipoChecklist" onchange="toggleChecklistTemplate()" style="font-weight:700;color:var(--blue)">
            <option value="BPA_RECEPCION">📦 Checklist BPA (Recepción de Importación / Lote)</option>
            <option value="BPDT_TRAZABILIDAD">🚚 Trazabilidad BPDT (Distribución y Transporte)</option>
          </select>
        </label>
        <label>Fecha del Expediente<input class="field" type="date" id="evFecha" required></label>
        <label class="wide">Observaciones / Notas regulatorias generales<textarea class="field" id="evNotas" rows="2" placeholder="Notas de recepción, temperatura de ingreso o transportista..."></textarea></label>
      </div>

      <div style="border-top:1px solid var(--line);padding-top:14px;margin-bottom:14px">
        <b style="font-size:14px;color:var(--navy)" id="checklistHeadingTitle">Items del Checklist Regulatorio y Carga de Archivos PDF</b>
        <div class="small muted" style="margin-bottom:10px">Marca el estado de cada documento obligatorio y adjunta el archivo PDF correspondiente emitido o verificado por Dirección Técnica.</div>
        
        <div class="checklistContainer" id="checklistItemsContainer"></div>
      </div>

      <div class="modalfooter">
        <button type="button" class="btn" onclick="closeEvidenciaModal()">Cancelar</button>
        <button type="submit" class="btn primary">💾 Guardar Expediente de Evidencia</button>
      </div>
    </form>
  </div>
</div>

<!-- MODAL VISOR DE ARCHIVOS INTEGRADO -->
<div class="modalOverlay" id="pdfModalOverlay" onclick="if(event.target===this)closePdfModal()">
  <div class="modal large">
    <header>
      <h2 id="pdfViewerTitle">Documento adjunto</h2>
      <div style="display:flex;gap:8px;align-items:center">
        <a id="pdfOpenTab" target="_blank" rel="noopener noreferrer" class="btn">↗ Abrir en pestaña</a>
        <a id="pdfDownloadBtn" class="btn primary">⇩ Descargar archivo</a>
        <button class="close" onclick="closePdfModal()" aria-label="Cerrar">×</button>
      </div>
    </header>
    <div id="fileViewerContainer" style="width:100%;height:74vh;background:#eef2f7;border-radius:10px;overflow:auto;display:flex;align-items:center;justify-content:center">
      <iframe id="pdfViewerFrame" style="width:100%;height:100%;border:0;display:none"></iframe>
      <div id="nonPdfPreviewNotice" style="text-align:center;padding:30px;display:none">
        <h3 id="nonPdfTitle" style="margin:0 0 10px;color:var(--navy)">Archivo Word o Excel</h3>
        <p class="muted small" style="margin:0 0 15px">Este formato se descarga directamente a tu PC.</p>
        <a id="nonPdfDownloadLink" class="btn primary">⇩ Descargar y abrir archivo</a>
      </div>
    </div>
  </div>
</div>

<div id="flash" class="flash"></div>

<script>
'use strict';

if(window.pdfjsLib){
  window.pdfjsLib.GlobalWorkerOptions.workerSrc='https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js';
}

/* ==================== INDEXEDDB ==================== */
const DB_NAME='dt_pdf_storage_v7';
const STORE_NAME='files';
function openPdfDB(){
  return new Promise((resolve,reject)=>{
    const req=indexedDB.open(DB_NAME,1);
    req.onupgradeneeded=e=>{
      const db=e.target.result;
      if(!db.objectStoreNames.contains(STORE_NAME)){
        db.createObjectStore(STORE_NAME,{keyPath:'id'});
      }
    };
    req.onsuccess=e=>resolve(e.target.result);
    req.onerror=e=>reject(e.target.error);
  });
}
async function storePdfFile(file){
  const buf=await file.arrayBuffer();
  const rec={
    id:'file_'+Date.now()+'_'+Math.random().toString(36).slice(2,7),
    name:file.name,
    size:file.size,
    type:file.type||'application/octet-stream',
    data:buf,
    savedAt:new Date().toISOString()
  };
  const db=await openPdfDB();
  return new Promise((resolve,reject)=>{
    const tx=db.transaction(STORE_NAME,'readwrite');
    tx.objectStore(STORE_NAME).put(rec);
    tx.oncomplete=()=>resolve({id:rec.id,name:rec.name,size:rec.size,type:rec.type});
    tx.onerror=e=>reject(e.target.error);
  });
}
async function storeRawPdfRecord(rec){
  const db=await openPdfDB();
  return new Promise((resolve,reject)=>{
    const tx=db.transaction(STORE_NAME,'readwrite');
    tx.objectStore(STORE_NAME).put(rec);
    tx.oncomplete=()=>resolve();
    tx.onerror=e=>reject(e.target.error);
  });
}
async function getPdfRecord(id){
  if(!id)return null;
  const db=await openPdfDB();
  return new Promise((resolve,reject)=>{
    const tx=db.transaction(STORE_NAME,'readonly');
    const req=tx.objectStore(STORE_NAME).get(id);
    req.onsuccess=()=>resolve(req.result||null);
    req.onerror=e=>reject(e.target.error);
  });
}
async function getAllPdfRecords(){
  const db=await openPdfDB();
  return new Promise((resolve,reject)=>{
    const tx=db.transaction(STORE_NAME,'readonly');
    const req=tx.objectStore(STORE_NAME).getAll();
    req.onsuccess=()=>resolve(req.result||[]);
    req.onerror=e=>reject(e.target.error);
  });
}

let activePdfUrl=null;
async function viewPdf(fileId){
  try{
    const rec=await getPdfRecord(fileId);
    if(!rec){alert('No se encontró el archivo en la base local.');return;}
    if(activePdfUrl)URL.revokeObjectURL(activePdfUrl);
    const name=(rec.name||'').toLowerCase();
    const isPdf=name.endsWith('.pdf')||rec.type==='application/pdf';
    const blob=new Blob([rec.data],{type:rec.type||'application/octet-stream'});
    activePdfUrl=URL.createObjectURL(blob);
    document.getElementById('pdfViewerTitle').textContent=rec.name||'Documento adjunto';
    const iframe=document.getElementById('pdfViewerFrame');
    const notice=document.getElementById('nonPdfPreviewNotice');
    const dlBtn=document.getElementById('pdfDownloadBtn');
    const nonDlBtn=document.getElementById('nonPdfDownloadLink');
    dlBtn.href=activePdfUrl;dlBtn.download=rec.name||'archivo';
    nonDlBtn.href=activePdfUrl;nonDlBtn.download=rec.name||'archivo';
    if(isPdf){
      iframe.style.display='block';notice.style.display='none';iframe.src=activePdfUrl;
    }else{
      iframe.style.display='none';notice.style.display='block';document.getElementById('nonPdfTitle').textContent=rec.name;
    }
    document.getElementById('pdfModalOverlay').classList.add('show');
  }catch(err){alert('Error al abrir el archivo: '+err.message);}
}
function closePdfModal(){
  document.getElementById('pdfModalOverlay').classList.remove('show');
  document.getElementById('pdfViewerFrame').src='about:blank';
}

/* ==================== ESTADO PRINCIPAL ==================== */
const KEY='dt_dashboard_v6';
const today=()=>new Date().toISOString().slice(0,10);
const relative=(d)=>{const x=new Date();x.setDate(x.getDate()+d);return `${x.getFullYear()}-${String(x.getMonth()+1).padStart(2,'0')}-${String(x.getDate()).padStart(2,'0')}`};

const demo=()=>({
  settings:{empresa:'Droguería de ejemplo',director:'Director Técnico',sede:'Almacén principal',alertDays:30,geminiKey:''},
  procedimientos:[
    {id:'p1',codigo:'PR-BPA-APT-001',nombre:'Recepción de productos para apertura',area:'Almacén',version:'01',fecha:relative(65),estado:'Vigente',enlace:'',pdfs:[],poeSub:'BPA_APERTURA'},
    {id:'p2',codigo:'PR-BPDT-001',nombre:'Distribución y transporte bajo cadena de frío',area:'Distribución',version:'02',fecha:relative(15),estado:'Vigente',enlace:'',pdfs:[],poeSub:'BPDT'}
  ],
  cronograma:[
    {
      id:'c1',
      nombre:'Calificación térmica para habilitación',
      tipo:'Calificación',
      responsable:'Calidad',
      estado:'En proceso',
      notas:'Cronograma anual',
      pdfs:[],
      subItems:[
        {nombre:'Ejecución de mapeo térmico', fecha:relative(15), docCode:'PR-BPDT-001', estado:'En proceso'}
      ]
    }
  ],
  inspecciones:[],
  hallazgos:[],
  evidencias:[
    /* ESTRUCTURA NUEVA PARA EVIDENCIAS CON CHECKLIST */
    {
      id:'ev_demo_1',
      codigo:'EXP-BPA-2026-001',
      nombre:'Importación Amoxicilina 500mg Lote B2604 (Refrigerado)',
      tipoChecklist:'BPA_RECEPCION',
      fecha:today(),
      notas:'Recepción conforme con cadena de frío verificada.',
      estado:'Completo',
      checklistData:{
        'Acta de Recepción':{status:'Conforme',files:[]},
        'Commercial Invoice':{status:'Conforme',files:[]},
        'Packing List':{status:'Conforme',files:[]},
        'Declaración Aduanera de Mercancías (DAM)':{status:'Conforme',files:[]},
        'Constancia de Percepción':{status:'Conforme',files:[]},
        'Guía de Transportista':{status:'Conforme',files:[]},
        'Lectura de Datalogger (Refrigerado)':{status:'Conforme',files:[]},
        'Análisis Organoléptico':{status:'Conforme',files:[]},
        'Certificado de Análisis':{status:'Conforme',files:[]}
      }
    },
    {
      id:'ev_demo_2',
      codigo:'EXP-BPDT-2026-001',
      nombre:'Despacho Guía G001-4582 a Hospital Central',
      tipoChecklist:'BPDT_TRAZABILIDAD',
      fecha:today(),
      notas:'Transporte local con monitoreo térmico.',
      estado:'En proceso',
      checklistData:{
        'Guía de Remisión (Cargo)':{status:'Conforme',files:[]},
        'Guía de Remisión (Salida)':{status:'Conforme',files:[]},
        'Orden de Compra':{status:'Conforme',files:[]},
        'Lectura de Datalogger':{status:'Pendiente',files:[]},
        'Hoja de Ruta':{status:'Conforme',files:[]}
      }
    }
  ],
  traduccion:[],
  log:[]
});

let state;
try{state=JSON.parse(localStorage.getItem(KEY))||demo()}catch(e){state=demo()}
for(const k of ['procedimientos','cronograma','inspecciones','hallazgos','evidencias','traduccion','log']){
  if(!Array.isArray(state[k]))state[k]=[];
}
['procedimientos','cronograma','inspecciones','hallazgos','evidencias','traduccion'].forEach(k=>{
  state[k].forEach(r=>{
    if(!Array.isArray(r.pdfs))r.pdfs=[];
    if(k==='cronograma' && !Array.isArray(r.subItems))r.subItems=[];
    if(k==='procedimientos' && !r.poeSub)r.poeSub='BPA_APERTURA';
    if(k==='evidencias'){
      if(!r.tipoChecklist) r.tipoChecklist='BPA_RECEPCION';
      if(!r.checklistData) r.checklistData={};
    }
  });
});
if(!state.settings)state.settings=demo().settings;

let current='evidencias',currentPoeSub='TODOS',editing=null,editingSection=null;
let trCurrentFile=null,trEditingId=null,trPreviewObjectUrl=null,trExtraPdfs=[];

/* DEFINICIÓN DE PLANTILLAS DE CHECKLIST SOLICITADAS */
const CHECKLIST_TEMPLATES={
  BPA_RECEPCION:[
    'Acta de Recepción',
    'Commercial Invoice',
    'Packing List',
    'Declaración Aduanera de Mercancías (DAM)',
    'Constancia de Percepción',
    'Guía de Transportista',
    'Lectura de Datalogger (Si es refrigerado)',
    'Análisis Organoléptico',
    'Certificado de Análisis'
  ],
  BPDT_TRAZABILIDAD:[
    'Guía de Remisión (Cargo)',
    'Guía de Remisión (Salida)',
    'Orden de Compra',
    'Lectura de Datalogger',
    'Hoja de Ruta'
  ]
};

const titles={
  dashboard:'Panel de Dirección Técnica',
  procedimientos:'Control Documental y Submódulos POE',
  cronograma:'Cronogramas y Sub-ítems',
  inspecciones:'Respuesta ante inspecciones',
  hallazgos:'Hallazgos y acciones CAPA',
  evidencias:'Evidencias y Checklists BPA/BPDT',
  traduccion:'Traducción Técnica de PDF',
  configuracion:'Configuración'
};

const schema={
  procedimientos:[
    ['codigo','Código','text',1],
    ['nombre','Documento / POE','text',1],
    ['area','Área','text',1],
    ['version','Versión','text',1],
    ['fecha','Fecha de revisión / vencimiento','date',1],
    ['estado','Estado','select',1,['Vigente','En revisión','Obsoleto']],
    ['enlace','URL externa opcional (HTTPS)','url',0]
  ],
  cronograma:[
    ['nombre','Actividad Principal / Proyecto','text',1],
    ['tipo','Tipo','select',1,['Auditoría','Capacitación','Documentación','Calificación','Validación','Mantenimiento','Otro']],
    ['responsable','Responsable general','text',1],
    ['estado','Estado general','select',1,['Pendiente','En proceso','Completado']],
    ['notas','Notas / entregable global','textarea',0]
  ],
  inspecciones:[
    ['fecha','Fecha de inspección','date',1],
    ['nombre','Tipo / N.° de acta','text',1],
    ['autoridad','Autoridad / inspectores','text',1],
    ['responsable','Responsable de atención','text',1],
    ['estado','Estado','select',1,['En curso','En seguimiento','Cerrada']],
    ['notas','Hechos y compromisos','textarea',0]
  ],
  hallazgos:[
    ['referencia','Código / acta origen','text',1],
    ['nombre','Descripción del hallazgo','textarea',1],
    ['criticidad','Criticidad','select',1,['Crítico','Mayor','Menor']],
    ['responsable','Responsable','text',1],
    ['fecha','Fecha de compromiso','date',1],
    ['estado','Estado','select',1,['Abierto','En proceso','Cerrado']],
    ['accion','Acción correctiva / causa','textarea',0]
  ],
  traduccion:[
    ['codigo','Código / referencia','text',1],
    ['nombre','Nombre del documento','text',1],
    ['categoria','Categoría','select',1,['Certificado de Análisis (CoA)','Certificado BPM / ISO','Inserto / Ficha Técnica','Manual / Instrucciones de Uso (IFU)','Dossier / Registro Sanitario','Procedimiento / POE','Otro']],
    ['idiomas','Par de idiomas (ej. EN → ES)','text',1],
    ['fecha','Fecha','date',1],
    ['estado','Estado','select',1,['Pendiente','En traducción','Revisado / Vigente']],
    ['textoOrigen','Texto original','textarea',0],
    ['textoTraducido','Texto traducido','textarea',0]
  ]
};

const safe=(s)=>String(s??'').replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
const days=(d)=>d?Math.round((new Date(d+'T12:00:00')-new Date(today()+'T12:00:00'))/86400000):999999;
const fmt=(d)=>d?d.split('-').reverse().join('/'):'—';
const fmtSize=(b)=>!b?'':b<1048576?(b/1024).toFixed(1)+' KB':(b/1048576).toFixed(2)+' MB';

const save=()=>{
  try{localStorage.setItem(KEY,JSON.stringify(state))}
  catch(e){alert('No se pudo guardar en LocalStorage.')}
  render();
};
function note(msg){state.log.unshift({msg,fecha:new Date().toLocaleString('es-PE')});state.log=state.log.slice(0,80)}
function toast(s){const el=document.getElementById('flash');el.textContent=s;el.style.display='block';clearTimeout(window._tTimer);window._tTimer=setTimeout(()=>el.style.display='none',2800)}

function page(id){
  current=id;
  document.querySelectorAll('.section').forEach(x=>x.classList.toggle('active',x.id===id));
  document.querySelectorAll('#nav button').forEach(x=>x.classList.toggle('active',x.dataset.page===id));
  document.getElementById('pageTitle').textContent=titles[id];
  render();
}
document.querySelectorAll('#nav button').forEach(b=>b.onclick=()=>page(b.dataset.page));

function switchPoeSub(sub){
  currentPoeSub=sub;
  document.querySelectorAll('.subTabBtn').forEach(b=>b.classList.toggle('active',b.dataset.sub===sub));
  renderTable('procedimientos');
}

function pill(status,date){
  let c=['Vigente','Completado','Cerrado','Cerrada','Revisado / Vigente','Conforme','Completo'].includes(status)?'ok':
        ['Crítico','Obsoleto'].includes(status)?'bad':
        ['En revisión','En proceso','Mayor','En seguimiento','En traducción','Pendiente'].includes(status)?'warn':'gray';
  if(date&&days(date)<0&&!['Completado','Cerrado','Cerrada','Obsoleto','Revisado / Vigente','Completo'].includes(status))
    return '<span class="pill bad">Vencido · '+safe(status)+'</span>';
  return '<span class="pill '+c+'">'+safe(status)+'</span>';
}

function poeSubBadge(sub){
  const map={
    BPA_APERTURA:{lbl:'BPA - Apertura',bg:'#e6f4ea',color:'#137333'},
    BPA_AMPLIACION:{lbl:'BPA - Ampliación',bg:'#e8f0fe',color:'#1967d2'},
    DT:{lbl:'Dirección Técnica',bg:'#fef7e0',color:'#b06000'},
    BPDT:{lbl:'BPDT (Transporte)',bg:'#fce8e6',color:'#c5221f'}
  };
  const m=map[sub]||{lbl:sub||'General',bg:'#eef1f5',color:'#5f6368'};
  return `<span class="pill" style="background:${m.bg};color:${m.color}">${safe(m.lbl)}</span>`;
}

function validUrl(url){
  if(!url)return null;
  try{const u=new URL(url);return u.protocol==='https:'?u.href:null}catch(e){return null}
}

function pdfsCell(r){
  const pdfs=Array.isArray(r.pdfs)?r.pdfs:[];
  const parts=[];
  pdfs.forEach((p,idx)=>{
    const label=p.name?(p.name.length>18?p.name.slice(0,16)+'…':p.name):`Archivo ${idx+1}`;
    parts.push(`<button type="button" class="fileBadge" title="${safe(p.name||'Ver archivo')}" onclick="viewPdf('${safe(p.id)}')">📄 ${safe(label)}</button>`);
  });
  return parts.length?`<div style="display:flex;gap:5px;align-items:center;flex-wrap:wrap">${parts.join('')}</div>`:'<span class="muted small">Sin adjunto</span>';
}

function cronogramaCell(r){
  const subItems=Array.isArray(r.subItems)?r.subItems:[];
  if(!subItems.length) return `<div class="small muted">Sin sub-ítems.</div>`;
  return `<div class="subItemBox">`+subItems.map(s=>`
    <div class="subItemRow">
      <div style="flex:1"><b>↳ ${safe(s.nombre)}</b> <div class="small muted">Doc: <code>${safe(s.docCode||'—')}</code></div></div>
      <div style="text-align:right"><div class="small">📅 ${fmt(s.fecha)}</div><div>${pill(s.estado,s.fecha)}</div></div>
    </div>
  `).join('')+`</div>`;
}

function renderEvidenciasTable(){
  const rows=state.evidencias||[];
  const dest=document.getElementById('rowsEvidencias');
  if(!dest)return;
  dest.innerHTML=rows.length?rows.map(r=>{
    const checklist=r.checklistData||{};
    const keys=Object.keys(checklist);
    const totalFiles=keys.reduce((acc,k)=>acc+(checklist[k].files?checklist[k].files.length:0),0);
    const tipoLabel=r.tipoChecklist==='BPA_RECEPCION'?'📦 Checklist BPA (Recepción)':'🚚 Trazabilidad BPDT';
    return `<tr>
      <td><b>${safe(r.codigo)}</b></td>
      <td>${safe(r.nombre)}<br><span class="small muted">${safe(r.notas||'')}</span></td>
      <td><span class="pill">${tipoLabel}</span></td>
      <td>${fmt(r.fecha)}</td>
      <td><span class="pill ok">${totalFiles} archivos PDF adjuntos</span></td>
      <td>${pill(r.estado||'En proceso')}</td>
      <td>
        <div class="rowactions">
          <button class="linkBtn teal" onclick="openEditEvidencia('${r.id}')">Editar / Adjuntar</button>
          <button class="linkBtn red" onclick="delEvidencia('${r.id}')">Eliminar</button>
        </div>
      </td>
    </tr>`;
  }).join(''):`<tr><td colspan="7" class="empty">No hay expedientes de evidencia registrados. Haz clic en «＋ Nuevo expediente».</td></tr>`;
}

function renderTable(type){
  if(type==='evidencias'){renderEvidenciasTable();return;}
  const rows=filterList(type);
  const dest=document.getElementById('rows'+type[0].toUpperCase()+type.slice(1));
  if(!dest)return;
  const templates={
    procedimientos:r=>`<td>${safe(r.codigo)}</td><td><b>${safe(r.nombre)}</b></td><td>${poeSubBadge(r.poeSub)}</td><td>${safe(r.area)}</td><td>${safe(r.version)}</td><td>${fmt(r.fecha)}</td><td>${pdfsCell(r)}</td><td>${pill(r.estado,r.fecha)}</td>`,
    cronograma:r=>`<td><b>${safe(r.nombre)}</b><br><span class="small muted">${safe(r.notas||'')}</span>${cronogramaCell(r)}</td><td><span class="muted small">—</span></td><td>${safe(r.tipo)}</td><td>${safe(r.responsable)}</td><td>${pdfsCell(r)}</td><td>${pill(r.estado)}</td>`,
    inspecciones:r=>`<td>${fmt(r.fecha)}</td><td>${safe(r.nombre)}</td><td>${safe(r.autoridad)}</td><td>${safe(r.responsable)}</td><td>${pdfsCell(r)}</td><td>${pill(r.estado)}</td>`,
    hallazgos:r=>`<td>${safe(r.referencia)}</td><td>${safe(r.nombre)}</td><td>${pill(r.criticidad)}</td><td>${safe(r.responsable)}</td><td>${fmt(r.fecha)}</td><td>${pdfsCell(r)}</td><td>${pill(r.estado,r.fecha)}</td>`,
    traduccion:r=>`<td>${safe(r.codigo)}</td><td>${safe(r.nombre)}</td><td>${safe(r.categoria)}</td><td><span class="pill">${safe(r.idiomas||'EN → ES')}</span></td><td>${fmt(r.fecha)}</td><td>${pdfsCell(r)}</td><td>${pill(r.estado)}</td>`
  };
  dest.innerHTML=rows.length?rows.map(r=>`<tr>${templates[type](r)}<td>${actions(type,r.id)}</td></tr>`).join(''):`<tr><td colspan="9" class="empty">No hay registros para mostrar</td></tr>`;
}

function filterList(type){
  const cap=type[0].toUpperCase()+type.slice(1);
  const search=document.getElementById('search'+cap);
  const filter=document.getElementById('filter'+cap);
  let rows=state[type];
  if(type==='procedimientos' && currentPoeSub!=='TODOS'){
    rows=rows.filter(r=>r.poeSub===currentPoeSub);
  }
  return rows.filter(r=>
    (!search||Object.values(r).some(v=>String(v).toLowerCase().includes(search.value.toLowerCase())))&&
    (!filter||!filter.value||r.estado===filter.value)
  );
}

function actions(type,id){
  return `<div class="rowactions"><button class="linkBtn" onclick="openModal('${type}','${id}')">Editar</button><button class="linkBtn red" onclick="delRow('${type}','${id}')">Eliminar</button></div>`;
}

function renderDashboard(){
  const lim=Number(state.settings.alertDays)||30;
  const proc=state.procedimientos,cal=state.cronograma,find=state.hallazgos;
  document.getElementById('kVigentes').textContent=proc.filter(r=>r.estado==='Vigente'&&days(r.fecha)>=0).length;
  const totalFiles=['procedimientos','cronograma','inspecciones','hallazgos','evidencias','traduccion'].reduce((acc,k)=>acc+state[k].reduce((a,r)=>{
    if(k==='evidencias'){
      let sub=0;
      const chk=r.checklistData||{};
      Object.keys(chk).forEach(ck=>sub+=(chk[ck].files?chk[ck].files.length:0));
      return a+sub;
    }
    return a+(Array.isArray(r.pdfs)?r.pdfs.length:0);
  },0),0);
  document.getElementById('kTotalDoc').textContent=`${proc.length} POEs · ${totalFiles} archivos adjuntos`;
  document.getElementById('kEvidenciasCount').textContent=state.evidencias.length;
  
  let proxSubCount=0;
  cal.forEach(c=>{if(Array.isArray(c.subItems))c.subItems.forEach(s=>{if(s.estado!=='Completado'&&days(s.fecha)>=0&&days(s.fecha)<=30)proxSubCount++;});});
  document.getElementById('kProximas').textContent=proxSubCount;

  const alerts=[
    ...proc.filter(r=>r.estado!=='Obsoleto'&&days(r.fecha)<=lim).map(r=>({label:r.codigo+' · '+r.nombre,date:r.fecha,where:'Procedimiento'})),
    ...find.filter(r=>r.estado!=='Cerrado'&&days(r.fecha)<=lim).map(r=>({label:r.nombre,date:r.fecha,where:'CAPA'}))
  ];
  document.getElementById('kAlertas').textContent=alerts.length;

  const types=[['Auditoría','Auditorías'],['Capacitación','Capacitaciones'],['Documentación','Control documental'],['Calificación','Calificaciones'],['Validación','Validaciones'],['Mantenimiento','Mantenimientos']];
  document.getElementById('progressItems').innerHTML=types.map(([typ,name])=>{
    const x=cal.filter(r=>r.tipo===typ);
    let totalSubs=0,compSubs=0;
    x.forEach(item=>{if(Array.isArray(item.subItems)){totalSubs+=item.subItems.length;compSubs+=item.subItems.filter(s=>s.estado==='Completado').length;}});
    const pct=totalSubs?Math.round(compSubs/totalSubs*100):0;
    return `<div class="statrow"><div class="stats"><b>${name}</b><span class="muted">${compSubs}/${totalSubs} sub-ítems · ${pct}%</span></div><div class="progress"><span style="width:${pct}%"></span></div></div>`;
  }).join('');

  document.getElementById('alertItems').innerHTML=alerts.length?alerts.slice(0,5).map(a=>`<div class="urgent"><div class="tag">PRÓXIMO · ${safe(a.where)} · ${fmt(a.date)}</div><p>${safe(a.label)}</p></div>`).join(''):'<p class="small muted">No hay alertas dentro del umbral.</p>';
  document.getElementById('recentItems').innerHTML=state.log.length?state.log.slice(0,5).map(l=>`<div class="activity">${safe(l.msg)}<time>${safe(l.fecha)}</time></div>`).join(''):'<div class="activity">Sistema activo.</div>';
}

function renderKit(){
  const docs=state.procedimientos.filter(p=>(p.pdfs&&p.pdfs.length)||p.enlace).slice(0,8);
  document.getElementById('inspectionKit').innerHTML=docs.length?docs.map(r=>`<div class="statrow" style="display:flex;justify-content:space-between;align-items:center;gap:10px"><div><b style="font-size:12px">${safe(r.nombre)}</b><div class="small muted">${safe(r.codigo)}</div></div><div>${pdfsCell(r)}</div></div>`).join(''):'<p class="small muted">Sin evidencias.</p>';
}

function render(){
  document.getElementById('dateCaption').textContent=`${safe(state.settings.empresa)} · ${new Date().toLocaleDateString('es-PE',{weekday:'long',day:'numeric',month:'long',year:'numeric'})}`;
  renderDashboard();
  ['procedimientos','cronograma','inspecciones','hallazgos','evidencias','traduccion'].forEach(renderTable);
  renderKit();
  if(current==='configuracion'){
    for(const [k,id] of [['empresa','empresa'],['director','director'],['sede','sede'],['alertDays','alertDays'],['geminiKey','geminiKey']]){
      const el=document.getElementById(id);if(el)el.value=state.settings[k]??'';
    }
  }
}

/* ==================== LÓGICA DE EVIDENCIAS Y CHECKLISTS ==================== */
let editingEvidenciaId=null;
let activeChecklistModel={};

function openCreateEvidencia(){
  editingEvidenciaId=null;
  document.getElementById('evCodigo').value='EXP-BPA-'+new Date().getFullYear()+'-'+String(state.evidencias.length+1).padStart(3,'0');
  document.getElementById('evNombre').value='';
  document.getElementById('evTipoChecklist').value='BPA_RECEPCION';
  document.getElementById('evFecha').value=today();
  document.getElementById('evNotas').value='';
  
  initChecklistModel('BPA_RECEPCION');
  renderChecklistBuilder();
  document.getElementById('evidenciaModalOverlay').classList.add('show');
}

async function openEditEvidencia(id){
  editingEvidenciaId=id;
  const r=state.evidencias.find(x=>x.id===id);
  if(!r)return;
  document.getElementById('evCodigo').value=r.codigo||'';
  document.getElementById('evNombre').value=r.nombre||'';
  document.getElementById('evTipoChecklist').value=r.tipoChecklist||'BPA_RECEPCION';
  document.getElementById('evFecha').value=r.fecha||today();
  document.getElementById('evNotas').value=r.notas||'';

  activeChecklistModel=JSON.parse(JSON.stringify(r.checklistData||{}));
  initChecklistModel(r.tipoChecklist||'BPA_RECEPCION', true);
  renderChecklistBuilder();
  document.getElementById('evidenciaModalOverlay').classList.add('show');
}

function closeEvidenciaModal(){
  document.getElementById('evidenciaModalOverlay').classList.remove('show');
}

function initChecklistModel(type, keepExisting=false){
  const templateKeys=CHECKLIST_TEMPLATES[type]||[];
  if(!keepExisting) activeChecklistModel={};
  templateKeys.forEach(k=>{
    if(!activeChecklistModel[k]){
      activeChecklistModel[k]={status:'Conforme',files:[]};
    }
  });
}

function toggleChecklistTemplate(){
  const type=document.getElementById('evTipoChecklist').value;
  initChecklistModel(type, true);
  renderChecklistBuilder();
}

function renderChecklistBuilder(){
  const container=document.getElementById('checklistItemsContainer');
  const type=document.getElementById('evTipoChecklist').value;
  const templateKeys=CHECKLIST_TEMPLATES[type]||[];

  container.innerHTML=templateKeys.map((itemKey, idx)=>{
    const itemData=activeChecklistModel[itemKey]||{status:'Conforme',files:[]};
    const filesArr=itemData.files||[];
    return `
      <div class="checkItemRow">
        <div class="checkItemTop">
          <div><b>${idx+1}. ${safe(itemKey)}</b></div>
          <div style="display:flex;gap:8px;align-items:center">
            <select class="field" style="min-height:32px;padding:4px 8px;font-size:11px" onchange="updateCheckItemStatus('${itemKey}',this.value)">
              <option value="Conforme" ${itemData.status==='Conforme'?'selected':''}>Conforme</option>
              <option value="Pendiente" ${itemData.status==='Pendiente'?'selected':''}>Pendiente</option>
              <option value="No Aplica" ${itemData.status==='No Aplica'?'selected':''}>No Aplica</option>
            </select>
            <label class="btn primary" style="padding:5px 10px;font-size:11px;cursor:pointer;margin:0">
              ＋ Adjuntar PDF
              <input type="file" accept="application/pdf,.pdf" style="display:none" onchange="uploadCheckItemPdf('${itemKey}',this)">
            </label>
          </div>
        </div>
        <div class="checkItemFiles">
          ${filesArr.length?filesArr.map((f,fi)=>`
            <span class="fileAttached" style="margin:0;padding:4px 8px">
              📄 <b>${safe(f.name)}</b> (${fmtSize(f.size)})
              <button type="button" class="linkBtn" onclick="viewPdf('${safe(f.id)}')">Ver</button>
              <button type="button" class="linkBtn red" onclick="removeCheckItemPdf('${itemKey}',${fi})">✕</button>
            </span>
          `).join(''):'<span class="small muted">Sin archivos PDF adjuntos para este ítem.</span>'}
        </div>
      </div>
    `;
  }).join('');
}

function updateCheckItemStatus(itemKey, val){
  if(activeChecklistModel[itemKey]) activeChecklistModel[itemKey].status=val;
}

async function uploadCheckItemPdf(itemKey, inputElem){
  const file=inputElem.files&&inputElem.files[0];
  if(!file)return;
  try{
    const saved=await storePdfFile(file);
    if(!activeChecklistModel[itemKey]) activeChecklistModel[itemKey]={status:'Conforme',files:[]};
    if(!activeChecklistModel[itemKey].files) activeChecklistModel[itemKey].files=[];
    activeChecklistModel[itemKey].files.push(saved);
    renderChecklistBuilder();
    toast('PDF adjuntado correctamente');
  }catch(err){alert('Error al adjuntar PDF: '+err.message);}
  inputElem.value='';
}

function removeCheckItemPdf(itemKey, fileIdx){
  if(activeChecklistModel[itemKey]&&activeChecklistModel[itemKey].files){
    activeChecklistModel[itemKey].files.splice(fileIdx,1);
    renderChecklistBuilder();
  }
}

async function saveEvidenciaRecord(e){
  e.preventDefault();
  const codigo=document.getElementById('evCodigo').value.trim();
  const nombre=document.getElementById('evNombre').value.trim();
  const tipoChecklist=document.getElementById('evTipoChecklist').value;
  const fecha=document.getElementById('evFecha').value;
  const notas=document.getElementById('evNotas').value.trim();

  if(!nombre){alert('Ingresa el nombre del expediente.');return;}

  let allFilesCount=0;
  Object.keys(activeChecklistModel).forEach(k=>{
    if(activeChecklistModel[k].files) allFilesCount+=activeChecklistModel[k].files.length;
  });
  const estado=allFilesCount>0?'Completo':'En proceso';

  if(editingEvidenciaId){
    const idx=state.evidencias.findIndex(r=>r.id===editingEvidenciaId);
    if(idx>=0){
      state.evidencias[idx]={
        ...state.evidencias[idx],
        codigo,nombre,tipoChecklist,fecha,notas,estado,
        checklistData:activeChecklistModel
      };
      note('Expediente de evidencia actualizado: '+codigo);
    }
  }else{
    state.evidencias.unshift({
      id:'ev_'+Date.now(),
      codigo,nombre,tipoChecklist,fecha,notas,estado,
      checklistData:activeChecklistModel
    });
    note('Nuevo expediente de evidencia creado: '+codigo);
  }
  save();
  closeEvidenciaModal();
  toast('Expediente guardado correctamente');
}

async function delEvidencia(id){
  const r=state.evidencias.find(x=>x.id===id);
  if(!r||!confirm('¿Eliminar el expediente de evidencia «'+r.codigo+'»?'))return;
  state.evidencias=state.evidencias.filter(x=>x.id!==id);
  note('Expediente eliminado: '+r.codigo);
  save();
  toast('Expediente eliminado');
}

/* MODAL GENERAL DE OTROS MÓDULOS */
function openModal(type,id){
  editing=id||null;editingSection=type;
  let old=state[type].find(r=>r.id===id)||{};
  document.getElementById('modalTitle').textContent=(id?'Editar: ':'Nuevo: ')+titles[type];
  document.getElementById('formFields').innerHTML=schema[type].map(([key,label,kind,required,opts])=>`<label class="${kind==='textarea'?'wide':''}">${label}${
    kind==='select'?`<select class="field" name="${key}" ${required?'required':''}>${opts.map(o=>`<option value="${safe(o)}" ${old[key]===o?'selected':''}>${safe(o)}</option>`).join('')}</select>`:
    kind==='textarea'?`<textarea class="field" name="${key}" rows="3" ${required?'required':''}>${safe(old[key])}</textarea>`:
    `<input class="field" type="${kind}" name="${key}" value="${safe(old[key]??(kind==='date'?today():''))}" ${required?'required':''}>`
  }</label>`).join('');

  const poeSubWrap=document.getElementById('poeSubModuleSelectorWrap');
  if(type==='procedimientos'){poeSubWrap.style.display='block';document.getElementById('modalPoeSub').value=old.poeSub||'BPA_APERTURA';}
  else{poeSubWrap.style.display='none';}

  const subSec=document.getElementById('subItemsSection');
  if(type==='cronograma'){subSec.style.display='block';window.currentSubItems=old.subItems||[];renderSubItemsContainerModal();}
  else{subSec.style.display='none';}

  document.getElementById('modalPdfFiles').value='';
  document.getElementById('modalOverlay').classList.add('show');
}
function renderSubItemsContainerModal(){
  const container=document.getElementById('subItemsContainer');
  const subs=window.currentSubItems||[];
  if(!subs.length){container.innerHTML='<div class="small muted">Sin sub-ítems.</div>';return;}
  container.innerHTML=subs.map((s,i)=>`
    <div style="background:#f2f7ff;border:1px solid #cce0fc;border-radius:8px;padding:10px;display:grid;grid-template-columns:2fr 1.5fr 1fr 1fr auto;gap:8px;align-items:center">
      <input class="field" type="text" value="${safe(s.nombre)}" oninput="window.currentSubItems[${i}].nombre=this.value" placeholder="Sub-ítem">
      <select class="field" onchange="window.currentSubItems[${i}].docCode=this.value">${getDocumentOptionsHtml(s.docCode)}</select>
      <input class="field" type="date" value="${safe(s.fecha||today())}" oninput="window.currentSubItems[${i}].fecha=this.value">
      <select class="field" onchange="window.currentSubItems[${i}].estado=this.value">
        <option value="Pendiente" ${s.estado==='Pendiente'?'selected':''}>Pendiente</option>
        <option value="En proceso" ${s.estado==='En proceso'?'selected':''}>En proceso</option>
        <option value="Completado" ${s.estado==='Completado'?'selected':''}>Completado</option>
      </select>
      <button type="button" class="linkBtn red" onclick="window.currentSubItems.splice(${i},1);renderSubItemsContainerModal()">✕</button>
    </div>
  `).join('');
}
function addSubItemRow(){if(!window.currentSubItems)window.currentSubItems=[];window.currentSubItems.push({nombre:'',docCode:'',fecha:today(),estado:'Pendiente'});renderSubItemsContainerModal();}
function getDocumentOptionsHtml(selectedCode){
  const procs=state.procedimientos||[];
  let opts=`<option value="">-- Sin doc --</option>`;
  procs.forEach(p=>{const sel=p.codigo===selectedCode?'selected':'';opts+=`<option value="${safe(p.codigo)}" ${sel}>${safe(p.codigo)}</option>`;});
  return opts;
}
function closeModal(){document.getElementById('modalOverlay').classList.remove('show')}

document.getElementById('recordForm').onsubmit=async e=>{
  e.preventDefault();
  const f=new FormData(e.target);const data=Object.fromEntries(f.entries());
  const fileInput=document.getElementById('modalPdfFiles');
  let newPdfs=[];
  if(fileInput.files&&fileInput.files.length){
    for(let i=0;i<fileInput.files.length;i++){const s=await storePdfFile(fileInput.files[i]);newPdfs.push(s);}
  }
  let extra={};
  if(editingSection==='cronograma') extra.subItems=window.currentSubItems||[];
  if(editingSection==='procedimientos') extra.poeSub=document.getElementById('modalPoeSub').value;

  if(editing){
    const i=state[editingSection].findIndex(r=>r.id===editing);
    const prevPdfs=state[editingSection][i].pdfs||[];
    state[editingSection][i]={...state[editingSection][i],...data,...extra,pdfs:[...prevPdfs,...newPdfs]};
  }else{
    state[editingSection].push({id:'r'+Date.now(),...data,...extra,pdfs:newPdfs});
  }
  save();closeModal();toast('Guardado');
};

async function delRow(type,id){
  const r=state[type].find(x=>x.id===id);if(!r||!confirm('¿Eliminar?'))return;
  state[type]=state[type].filter(x=>x.id!==id);save();toast('Eliminado');
}

/* TRADUCCIÓN Y CONFIG */
const trDrop=document.getElementById('trDropZone');const trInput=document.getElementById('trPdfInput');
['dragenter','dragover'].forEach(ev=>trDrop.addEventListener(ev,e=>{e.preventDefault();trDrop.classList.add('drag')}));
['dragleave','drop'].forEach(ev=>trDrop.addEventListener(ev,e=>{e.preventDefault();trDrop.classList.remove('drag')}));
trDrop.addEventListener('drop',e=>{const f=e.dataTransfer.files&&e.dataTransfer.files[0];if(f)handleTrPdfSelected(f);});
trInput.addEventListener('change',e=>{const f=e.target.files&&e.target.files[0];if(f)handleTrPdfSelected(f);});
function toggleTrPreview(){const fr=document.getElementById('trPdfPreview');fr.style.display=fr.style.display==='none'?'block':'none';}
async function handleTrPdfSelected(file){
  if(!file.name.toLowerCase().endsWith('.pdf')&&file.type!=='application/pdf'){alert('PDF requerido.');return;}
  const saved=await storePdfFile(file);trCurrentFile=saved;trExtraPdfs.push(saved);
  document.getElementById('trFileInfo').innerHTML=`✅ <b>${safe(file.name)}</b> listo.`;
  if(trPreviewObjectUrl)URL.revokeObjectURL(trPreviewObjectUrl);
  trPreviewObjectUrl=URL.createObjectURL(file);
  document.getElementById('trPreviewWrap').style.display='block';
  document.getElementById('trPdfPreview').src=trPreviewObjectUrl;
  try{
    const buf=await file.arrayBuffer();const pdf=await window.pdfjsLib.getDocument({data:buf}).promise;
    let pages=[];
    for(let p=1;p<=pdf.numPages;p++){
      const pageObj=await pdf.getPage(p);const content=await pageObj.getTextContent();
      pages.push(`--- [Pág ${p}] ---\n`+content.items.map(i=>i.str).join(' '));
    }
    document.getElementById('trSourceText').value=pages.join('\n\n');
  }catch(e){document.getElementById('trSourceText').value='';}
}
async function runTranslation(){
  const src=document.getElementById('trSourceText').value.trim();
  const sl=document.getElementById('trSourceLang').value;const tl=document.getElementById('trTargetLang').value;
  if(!src){alert('Sin texto.');return;}
  try{
    const res=await fetch(`https://translate.googleapis.com/translate_a/single?client=gtx&sl=${encodeURIComponent(sl)}&tl=${encodeURIComponent(tl)}&dt=t&q=${encodeURIComponent(src)}`);
    const data=await res.json();
    document.getElementById('trTargetText').value=data[0].map(seg=>seg[0]).join('');
    toast('Traducido');
  }catch(e){alert('Error: '+e.message);}
}
async function saveTranslationRecord(){
  const codigo=document.getElementById('trCodigo').value.trim()||('TRAD-'+Date.now().toString().slice(-5));
  const nombre=document.getElementById('trNombre').value.trim();
  const categoria=document.getElementById('trCategoria').value;const estado=document.getElementById('trEstado').value;
  const sl=document.getElementById('trSourceLang').value.toUpperCase();const tl=document.getElementById('trTargetLang').value.toUpperCase();
  const textoOrigen=document.getElementById('trSourceText').value;const textoTraducido=document.getElementById('trTargetText').value;
  if(!nombre){alert('Nombre obligatorio.');return;}
  state.traduccion.unshift({id:'tr_'+Date.now(),codigo,nombre,categoria,estado,idiomas:`${sl} → ${tl}`,fecha:today(),textoOrigen,textoTraducido,pdfs:trExtraPdfs});
  save();toast('Traducción guardada');
}
function clearTranslator(){trCurrentFile=null;trEditingId=null;trExtraPdfs=[];document.getElementById('trPdfInput').value='';document.getElementById('trCodigo').value='';document.getElementById('trNombre').value='';document.getElementById('trSourceText').value='';document.getElementById('trTargetText').value='';document.getElementById('trPreviewWrap').style.display='none';}
function exportTranslatedDoc(){
  const codigo=document.getElementById('trCodigo').value||'S/C';const nombre=document.getElementById('trNombre').value||'Traducción';const text=document.getElementById('trTargetText').value;
  if(!text){alert('Sin texto.');return;}
  const w=window.open('','_blank');
  w.document.write(`<!DOCTYPE html><html lang="es"><head><meta charset="UTF-8"><title>${safe(codigo)}</title><style>body{font-family:Arial;padding:30px;line-height:1.6}</style></head><body><h2>${safe(nombre)}</h2><pre style="white-space:pre-wrap">${safe(text)}</pre><script>window.onload=()=>window.print()<\/script></body></html>`);
  w.document.close();
}
function downloadTranslatedTxt(){download(document.getElementById('trCodigo').value+'.txt',document.getElementById('trTargetText').value,'text/plain');}
function saveSettings(){
  state.settings={empresa:document.getElementById('empresa').value,director:document.getElementById('director').value,sede:document.getElementById('sede').value,alertDays:Number(document.getElementById('alertDays').value)||30,geminiKey:document.getElementById('geminiKey').value.trim()};
  save();toast('Configuración guardada');
}
function download(name,data,type){
  const blob=new Blob([data],{type});const a=document.createElement('a');a.href=URL.createObjectURL(blob);a.download=name;document.body.append(a);a.click();a.remove();
}
function arrayBufferToBase64(buf){const b=new Uint8Array(buf);let bin='';for(let i=0;i<b.byteLength;i+=8192)bin+=String.fromCharCode.apply(null,b.subarray(i,i+8192));return btoa(bin);}
function base64ToArrayBuffer(b64){const bin=atob(b64);const b=new Uint8Array(bin.length);for(let i=0;i<bin.length;i++)b[i]=bin.charCodeAt(i);return b.buffer;}
function exportJSON(){download('Direccion_Tecnica_Respaldo_'+today()+'.json',JSON.stringify(state,null,2),'application/json');toast('Respaldo generado');}
async function exportFullBackup(){
  toast('Empaquetando...');const pdfs=await getAllPdfRecords();
  const encoded=pdfs.map(p=>({id:p.id,name:p.name,size:p.size,type:p.type,savedAt:p.savedAt,base64:arrayBufferToBase64(p.data)}));
  download('Direccion_Tecnica_Respaldo_Completo_'+today()+'.json',JSON.stringify({...state,_embeddedPdfs:encoded}),'application/json');
  toast('Respaldo completo descargado');
}
function exportCSV(type){const rows=state[type];const csv='\ufeff'+rows.map(r=>Object.values(r).join(';')).join('\r\n');download('DT_'+type+'_'+today()+'.csv',csv,'text/csv');toast('CSV exportado');}
document.getElementById('importFile').addEventListener('change',async e=>{
  const file=e.target.files[0];if(!file)return;
  try{
    const obj=JSON.parse(await file.text());
    if(confirm('¿Reemplazar datos?')){
      if(Array.isArray(obj._embeddedPdfs)){
        for(const p of obj._embeddedPdfs)await storeRawPdfRecord({id:p.id,name:p.name,size:p.size,type:p.type,savedAt:p.savedAt,data:base64ToArrayBuffer(p.base64)});
        delete obj._embeddedPdfs;
      }
      state={...obj,traduccion:Array.isArray(obj.traduccion)?obj.traduccion:[],log:Array.isArray(obj.log)?obj.log:[]};
      save();toast('Restaurado correctamente');
    }
  }catch(err){alert('Archivo inválido');}
  e.target.value='';
});
function resetDemo(){if(confirm('¿Restablecer?')){state=demo();save();toast('Demostración restaurada');}}

['Procedimientos','Cronograma','Hallazgos','Evidencias','Traduccion'].forEach(t=>{
  for(const id of ['search'+t,'filter'+t]){
    const x=document.getElementById(id);if(x)x.addEventListener('input',()=>renderTable(t[0].toLowerCase()+t.slice(1)));
  }
});

render();
</script>
</body>
</html>
