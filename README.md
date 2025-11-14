<!doctype html>
<html lang="pt-BR">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sistema de Controle de Vendas</title>
  <script src="/_sdk/data_sdk.js"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <style>
        body {
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            margin: 0;
            padding: 0;
            background: #f8fafc;
            color: #334155;
            line-height: 1.5;
        }
        
        /* Reset and base styles */
        * { box-sizing: border-box; }
        
        /* Utility classes */
        .container { max-width: 1200px; margin: 0 auto; padding: 0 1rem; }
        .flex { display: flex; }
        .flex-col { flex-direction: column; }
        .items-center { align-items: center; }
        .justify-between { justify-content: space-between; }
        .justify-center { justify-content: center; }
        .gap-4 { gap: 1rem; }
        .gap-6 { gap: 1.5rem; }
        .hidden { display: none; }
        .text-center { text-align: center; }
        .font-bold { font-weight: 700; }
        .font-medium { font-weight: 500; }
        .text-sm { font-size: 0.875rem; }
        .text-lg { font-size: 1.125rem; }
        .text-xl { font-size: 1.25rem; }
        .text-2xl { font-size: 1.5rem; }
        .text-3xl { font-size: 1.875rem; }
        .mb-4 { margin-bottom: 1rem; }
        .mb-6 { margin-bottom: 1.5rem; }
        .mb-8 { margin-bottom: 2rem; }
        .mt-1 { margin-top: 0.25rem; }
        .mt-2 { margin-top: 0.5rem; }
        .p-4 { padding: 1rem; }
        .p-6 { padding: 1.5rem; }
        .px-3 { padding-left: 0.75rem; padding-right: 0.75rem; }
        .px-4 { padding-left: 1rem; padding-right: 1rem; }
        .px-6 { padding-left: 1.5rem; padding-right: 1.5rem; }
        .py-2 { padding-top: 0.5rem; padding-bottom: 0.5rem; }
        .py-3 { padding-top: 0.75rem; padding-bottom: 0.75rem; }
        .py-4 { padding-top: 1rem; padding-bottom: 1rem; }
        .py-6 { padding-top: 1.5rem; padding-bottom: 1.5rem; }
        .py-12 { padding-top: 3rem; padding-bottom: 3rem; }
        .w-full { width: 100%; }
        .min-h-screen { min-height: 100%; }
        .rounded { border-radius: 0.375rem; }
        .rounded-lg { border-radius: 0.5rem; }
        .shadow { box-shadow: 0 1px 3px rgba(0,0,0,0.1); }
        .border { border: 1px solid #e2e8f0; }
        .border-b { border-bottom: 1px solid #e2e8f0; }
        
        /* Colors */
        .bg-white { background-color: white; }
        .bg-gray-50 { background-color: #f8fafc; }
        .bg-blue-600 { background-color: #2563eb; }
        .bg-blue-700 { background-color: #1d4ed8; }
        .bg-green-600 { background-color: #16a34a; }
        .bg-green-700 { background-color: #15803d; }
        .bg-red-600 { background-color: #dc2626; }
        .bg-orange-600 { background-color: #ea580c; }
        .bg-purple-600 { background-color: #9333ea; }
        .text-white { color: white; }
        .text-gray-600 { color: #64748b; }
        .text-gray-700 { color: #374151; }
        .text-gray-900 { color: #111827; }
        .text-blue-600 { color: #2563eb; }
        .text-green-600 { color: #16a34a; }
        .text-red-600 { color: #dc2626; }
        .text-orange-600 { color: #ea580c; }
        .text-purple-600 { color: #9333ea; }
        
        /* Components */
        .card {
            background: white;
            border-radius: 0.5rem;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
            border: 1px solid #e2e8f0;
        }
        
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            padding: 0.5rem 1rem;
            border-radius: 0.375rem;
            font-weight: 500;
            font-size: 0.875rem;
            border: none;
            cursor: pointer;
            transition: all 0.2s;
            text-decoration: none;
        }
        
        .btn:hover { opacity: 0.9; }
        .btn:disabled { opacity: 0.5; cursor: not-allowed; }
        
        .btn-primary { background: #2563eb; color: white; }
        .btn-success { background: #16a34a; color: white; }
        .btn-danger { background: #dc2626; color: white; }
        .btn-secondary { background: #64748b; color: white; }
        
        .form-input {
            width: 100%;
            padding: 0.5rem 0.75rem;
            border: 1px solid #d1d5db;
            border-radius: 0.375rem;
            font-size: 0.875rem;
            transition: border-color 0.2s;
        }
        
        .form-input:focus {
            outline: none;
            border-color: #2563eb;
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
        }
        
        .metric-card {
            background: white;
            padding: 1.5rem;
            border-radius: 0.5rem;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
            border: 1px solid #e2e8f0;
            transition: transform 0.2s;
        }
        
        .metric-card:hover {
            transform: translateY(-2px);
        }
        
        .table {
            width: 100%;
            border-collapse: collapse;
            background: white;
        }
        
        .table th,
        .table td {
            padding: 0.75rem;
            text-align: left;
            border-bottom: 1px solid #e2e8f0;
        }
        
        .table th {
            background: #f8fafc;
            font-weight: 600;
            font-size: 0.75rem;
            text-transform: uppercase;
            color: #64748b;
        }
        
        .header {
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 25%, #0f3460 50%, #533483 75%, #e94560 100%);
            border-bottom: 3px solid #e94560;
            padding: 0;
            position: relative;
            overflow: hidden;
        }
        
        .header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grid" width="10" height="10" patternUnits="userSpaceOnUse"><path d="M 10 0 L 0 0 0 10" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="0.5"/></pattern></defs><rect width="100" height="100" fill="url(%23grid)"/></svg>');
            opacity: 0.3;
        }
        
        .header::after {
            content: '';
            position: absolute;
            top: -50%;
            right: -10%;
            width: 200px;
            height: 200px;
            background: radial-gradient(circle, rgba(233, 69, 96, 0.2) 0%, transparent 70%);
            border-radius: 50%;
            animation: pulse 4s ease-in-out infinite;
        }
        
        @keyframes pulse {
            0%, 100% { transform: scale(1); opacity: 0.2; }
            50% { transform: scale(1.1); opacity: 0.4; }
        }
        
        .header-content {
            position: relative;
            z-index: 2;
            padding: 1.5rem 0;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .header-title {
            display: flex;
            align-items: center;
            gap: 1rem;
        }
        
        .header-icon {
            width: 48px;
            height: 48px;
            background: linear-gradient(45deg, #e94560, #ff6b6b);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 15px rgba(233, 69, 96, 0.3);
            position: relative;
        }
        
        .header-icon::before {
            content: '⚔️';
            font-size: 24px;
            filter: drop-shadow(0 2px 4px rgba(0,0,0,0.3));
        }
        
        .header-text h1 {
            color: white;
            font-size: 1.75rem;
            font-weight: 800;
            margin: 0;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
            letter-spacing: -0.025em;
        }
        
        .header-subtitle {
            color: rgba(255,255,255,0.8);
            font-size: 0.875rem;
            margin: 0;
            font-weight: 500;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }
        
        .header-user {
            display: flex;
            align-items: center;
            gap: 1rem;
            background: rgba(255,255,255,0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255,255,255,0.2);
            border-radius: 12px;
            padding: 0.75rem 1rem;
        }
        
        .user-avatar {
            width: 40px;
            height: 40px;
            background: linear-gradient(45deg, #533483, #e94560);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            font-size: 1.1rem;
            box-shadow: 0 2px 8px rgba(0,0,0,0.2);
        }
        
        .user-info {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
        }
        
        .user-name {
            color: white;
            font-weight: 600;
            font-size: 0.95rem;
            margin: 0;
        }
        
        .user-role {
            color: rgba(255,255,255,0.7);
            font-size: 0.75rem;
            margin: 0;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }
        
        .header-logout {
            background: linear-gradient(45deg, #dc2626, #ef4444);
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 8px;
            font-weight: 600;
            font-size: 0.875rem;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 2px 8px rgba(220, 38, 38, 0.3);
        }
        
        .header-logout:hover {
            transform: translateY(-1px);
            box-shadow: 0 4px 12px rgba(220, 38, 38, 0.4);
        }
        
        .battle-stats {
            position: absolute;
            top: 0;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(0,0,0,0.3);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255,255,255,0.1);
            border-radius: 0 0 12px 12px;
            padding: 0.5rem 1.5rem;
            display: flex;
            gap: 2rem;
            font-size: 0.75rem;
            color: rgba(255,255,255,0.9);
        }
        
        .battle-stat {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .battle-stat-icon {
            font-size: 1rem;
        }
        
        .battle-stat-value {
            font-weight: bold;
            color: #e94560;
        }
        
        /* Steel texture overlay */
        .steel-texture {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: 
                radial-gradient(circle at 20% 80%, rgba(255,255,255,0.1) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(255,255,255,0.1) 0%, transparent 50%),
                linear-gradient(45deg, transparent 30%, rgba(255,255,255,0.05) 50%, transparent 70%);
            pointer-events: none;
        }
        
        /* Responsive adjustments */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 1rem;
                padding: 1rem 0;
            }
            
            .header-title {
                flex-direction: column;
                text-align: center;
                gap: 0.5rem;
            }
            
            .header-text h1 {
                font-size: 1.5rem;
            }
            
            .header-user {
                width: 100%;
                justify-content: center;
            }
            
            .battle-stats {
                position: relative;
                left: auto;
                transform: none;
                border-radius: 8px;
                margin-top: 0.5rem;
            }
        }
        
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.5);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1000;
        }
        
        .modal-content {
            background: white;
            border-radius: 0.5rem;
            padding: 1.5rem;
            max-width: 500px;
            width: 90%;
            max-height: 90vh;
            overflow-y: auto;
        }
        
        .grid {
            display: grid;
            gap: 1rem;
        }
        
        .grid-2 { grid-template-columns: repeat(2, 1fr); }
        .grid-3 { grid-template-columns: repeat(3, 1fr); }
        .grid-4 { grid-template-columns: repeat(4, 1fr); }
        .grid-5 { grid-template-columns: repeat(5, 1fr); }
        
        .status-badge {
            display: inline-flex;
            align-items: center;
            padding: 0.25rem 0.5rem;
            border-radius: 9999px;
            font-size: 0.75rem;
            font-weight: 500;
        }
        
        .status-hot { background: #fef2f2; color: #dc2626; }
        .status-warm { background: #fffbeb; color: #d97706; }
        .status-cold { background: #eff6ff; color: #2563eb; }
        .status-no-return { background: #f3f4f6; color: #6b7280; }
        .status-lost { background: #fef2f2; color: #991b1b; }
        
        .loading {
            opacity: 0.6;
            pointer-events: none;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .container { padding: 0 0.5rem; }
            .grid-2, .grid-3, .grid-4, .grid-5 { grid-template-columns: 1fr; }
            .text-3xl { font-size: 1.5rem; }
            .text-2xl { font-size: 1.25rem; }
            .p-6 { padding: 1rem; }
            .px-6 { padding-left: 1rem; padding-right: 1rem; }
            .py-12 { padding-top: 2rem; padding-bottom: 2rem; }
            
            .table {
                font-size: 0.75rem;
            }
            
            .table th,
            .table td {
                padding: 0.5rem 0.25rem;
            }
            
            .modal-content {
                margin: 1rem;
                width: calc(100% - 2rem);
            }
            
            .btn {
                width: 100%;
                margin-bottom: 0.5rem;
            }
            
            .flex {
                flex-direction: column;
                gap: 0.5rem;
            }
        }
        
        /* Scrollbar */
        .overflow-x-auto {
            overflow-x: auto;
            -webkit-overflow-scrolling: touch;
        }
        
        .overflow-x-auto::-webkit-scrollbar {
            height: 6px;
        }
        
        .overflow-x-auto::-webkit-scrollbar-track {
            background: #f1f5f9;
        }
        
        .overflow-x-auto::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 3px;
        }
    </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="https://cdn.tailwindcss.com" type="text/javascript"></script>
 </head>
 <body class="min-h-full bg-gray-50">
  <div id="app" class="min-h-screen"><!-- Login Screen -->
   <div id="loginScreen" class="min-h-screen flex items-center justify-center py-12 relative overflow-hidden" style="background: linear-gradient(135deg, #1e293b 0%, #334155 25%, #475569 50%, #64748b 75%, #94a3b8 100%);"><!-- Animated Background Elements -->
    <div class="absolute inset-0 overflow-hidden">
     <div class="absolute -top-40 -right-40 w-80 h-80 bg-gradient-to-br from-blue-400/15 to-indigo-400/15 rounded-full blur-3xl animate-pulse"></div>
     <div class="absolute -bottom-40 -left-40 w-80 h-80 bg-gradient-to-tr from-slate-400/15 to-blue-400/15 rounded-full blur-3xl animate-pulse" style="animation-delay: 1s;"></div>
     <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-96 h-96 bg-gradient-to-r from-indigo-400/10 to-blue-400/10 rounded-full blur-3xl animate-pulse" style="animation-delay: 2s;"></div>
    </div><!-- Subtle Grid Pattern -->
    <div class="absolute inset-0" style="background-image: url('data:image/svg+xml,<svg xmlns=\" http: www.w3.org 2000 svg\ viewbox="\&quot;0" 0 100 100\>
     <defs>
      <pattern id="\&quot;grid\&quot;" width="\&quot;20\&quot;" height="\&quot;20\&quot;" patternunits="\&quot;userSpaceOnUse\&quot;">
       <path d="\&quot;M" 20 0 l 20\ fill="\&quot;none\&quot;" stroke="\&quot;rgba(255,255,255,0.05)\&quot;" stroke-width="\&quot;1\&quot;/"></path>
      </pattern>
     </defs><rect width="\&quot;100\&quot;" height="\&quot;100\&quot;" fill="\&quot;url(%23grid)\&quot;/">
      '); opacity: 0.4;"&gt;
     </rect>
    </div>
    <div class="w-full relative z-10" style="max-width: 450px;"><!-- War Banner -->
     <div class="text-center mb-8 relative">
      <div id="companyLogoContainer" class="inline-flex items-center justify-center w-20 h-20 mb-4 rounded-full bg-gradient-to-br from-blue-500 to-indigo-500 shadow-xl"><img id="companyLogoImg" src="" alt="Logo da Empresa" class="w-16 h-16 object-contain rounded-full hidden" onerror="this.style.display='none'; document.getElementById('defaultLogoIcon').style.display='block';"> <span id="defaultLogoIcon" class="text-4xl filter drop-shadow-lg">🏆</span>
      </div>
      <h1 id="companyName" class="text-4xl font-bold text-white mb-2 tracking-tight" style="text-shadow: 2px 2px 8px rgba(0,0,0,0.3);">JORNADA DO SUCESSO</h1>
      <div class="bg-gradient-to-r from-transparent via-white/20 to-transparent h-px w-32 mx-auto mb-4"></div><!-- Dynamic Motivational Cloud -->
      <div id="motivationalPhrase" class="relative bg-white/95 backdrop-blur-sm border border-blue-200/30 rounded-full px-8 py-6 mb-4 shadow-xl" style="border-radius: 50px 50px 50px 10px;"><!-- Cloud decorative elements -->
       <div class="absolute -top-2 -right-2 w-6 h-6 bg-white/80 rounded-full"></div>
       <div class="absolute -top-1 -right-6 w-4 h-4 bg-white/60 rounded-full"></div>
       <div class="absolute -top-3 -left-3 w-5 h-5 bg-white/70 rounded-full"></div>
       <p class="text-slate-700 font-bold text-lg leading-tight text-center" id="phraseText">✨ O sucesso é construído dia após dia</p>
       <p class="text-slate-500 text-sm mt-2 text-center font-medium" id="phraseSubtext">Cada esforço de hoje é um tijolo no seu futuro</p>
      </div><!-- Success Stats -->
      <div class="flex justify-center space-x-6 text-white/80 text-sm">
       <div class="text-center">
        <div class="text-blue-300 font-bold">
         🎯
        </div>
        <div>
         FOCO
        </div>
       </div>
       <div class="text-center">
        <div class="text-indigo-300 font-bold">
         💪
        </div>
        <div>
         DEDICAÇÃO
        </div>
       </div>
       <div class="text-center">
        <div class="text-slate-300 font-bold">
         🌟
        </div>
        <div>
         EXCELÊNCIA
        </div>
       </div>
      </div>
     </div><!-- Login Card -->
     <div class="bg-white/10 backdrop-blur-lg border border-white/20 rounded-2xl p-8 shadow-2xl">
      <div class="text-center mb-6">
       <h2 class="text-xl font-bold text-white mb-2">ACESSO AO CAMPO DE BATALHA</h2>
       <div class="bg-gradient-to-r from-transparent via-white/30 to-transparent h-px w-24 mx-auto"></div>
      </div>
      <form id="loginForm" class="gap-6 flex-col flex">
       <div><label for="loginName" class="block text-sm font-bold text-white/90 mb-2 uppercase tracking-wide">🏷️ Nome do Guerreiro</label> <input id="loginName" type="text" required class="w-full px-4 py-3 bg-white/20 backdrop-blur-sm border border-white/30 rounded-lg text-white placeholder-white/60 focus:outline-none focus:ring-2 focus:ring-orange-500 focus:border-transparent transition-all duration-300" placeholder="Digite seu nome de guerra">
       </div>
       <div><label for="loginPassword" class="block text-sm font-bold text-white/90 mb-2 uppercase tracking-wide">🔐 Código de Acesso</label> <input id="loginPassword" type="password" required class="w-full px-4 py-3 bg-white/20 backdrop-blur-sm border border-white/30 rounded-lg text-white placeholder-white/60 focus:outline-none focus:ring-2 focus:ring-orange-500 focus:border-transparent transition-all duration-300" placeholder="Sua senha secreta">
       </div><!-- Success Button --> <button type="submit" id="loginBtn" class="w-full py-4 bg-gradient-to-r from-blue-600 to-indigo-600 hover:from-blue-700 hover:to-indigo-700 text-white font-bold text-lg rounded-lg shadow-xl transform hover:scale-105 transition-all duration-300 border-2 border-white/20"> <span class="flex items-center justify-center"> <span class="mr-2">🚀</span> INICIAR JORNADA DE SUCESSO <span class="ml-2">🚀</span> </span> </button>
      </form>
     </div><!-- Footer Inspiration -->
     <div class="text-center mt-6">
      <p class="text-white/70 text-sm font-medium italic">"O sucesso é a soma de pequenos esforços repetidos dia após dia"</p>
     </div>
    </div>
   </div><!-- Admin Dashboard -->
   <div id="adminDashboard" class="hidden min-h-screen">
    <header class="header">
     <div class="steel-texture"></div>
     <div class="battle-stats">
      <div class="battle-stat"><span class="battle-stat-icon">🎯</span> <span>Meta: <span class="battle-stat-value" id="headerGoal">0</span></span>
      </div>
      <div class="battle-stat"><span class="battle-stat-icon">💰</span> <span>Vendas: <span class="battle-stat-value" id="headerSales">0</span></span>
      </div>
      <div class="battle-stat"><span class="battle-stat-icon">⚡</span> <span>Taxa: <span class="battle-stat-value" id="headerRate">0%</span></span>
      </div>
     </div>
     <div class="container">
      <div class="header-content">
       <div class="header-title">
        <div class="header-icon"></div>
        <div class="header-text">
         <h1 id="adminTitle">Painel Administrativo</h1>
         <p class="header-subtitle">Guerra de Vendas • Aço &amp; Tecnologia</p>
        </div>
       </div>
       <div class="header-user">
        <div class="user-avatar" id="adminAvatar">
         A
        </div>
        <div class="user-info">
         <p class="user-name" id="adminUserName">Admin</p>
         <p class="user-role">Comandante</p>
        </div><button id="adminLogoutBtn" class="header-logout">Sair</button>
       </div>
      </div>
     </div>
    </header>
    <main class="container py-6"><!-- Daily Leads Control -->
     <div class="card mb-8" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white;">
      <div class="p-6">
       <div class="flex items-center justify-between mb-6">
        <div>
         <h2 class="text-2xl font-bold text-white">⚡ Controle de Leads - HOJE</h2>
         <p class="text-blue-100" id="todayDate">Carregando data...</p>
        </div>
        <div class="text-4xl">
         🎯
        </div>
       </div>
       <div class="grid grid-5 gap-6">
        <div class="bg-white bg-opacity-20 backdrop-blur-sm rounded-lg p-4 text-center">
         <div class="text-3xl mb-2">
          📥
         </div>
         <p class="text-sm text-blue-100">Leads Entrada</p>
         <p id="todayLeadsIn" class="text-2xl font-bold">0</p>
        </div>
        <div class="bg-white bg-opacity-20 backdrop-blur-sm rounded-lg p-4 text-center">
         <div class="text-3xl mb-2">
          💵
         </div>
         <p class="text-sm text-blue-100">Orçamento Total</p>
         <p id="todayBudgetTotal" class="text-xl font-bold">R$ 0,00</p>
        </div>
        <div class="bg-white bg-opacity-20 backdrop-blur-sm rounded-lg p-4 text-center">
         <div class="text-3xl mb-2">
          🛒
         </div>
         <p class="text-sm text-blue-100">Compraram Hoje</p>
         <p id="todaySales" class="text-2xl font-bold text-green-300">0</p>
        </div>
        <div class="bg-white bg-opacity-20 backdrop-blur-sm rounded-lg p-4 text-center">
         <div class="text-3xl mb-2">
          💰
         </div>
         <p class="text-sm text-blue-100">Valor Fechamento</p>
         <p id="todayRevenue" class="text-xl font-bold text-green-300">R$ 0,00</p>
        </div>
        <div class="bg-white bg-opacity-20 backdrop-blur-sm rounded-lg p-4 text-center">
         <div class="text-3xl mb-2">
          ⚡
         </div>
         <p class="text-sm text-blue-100">Taxa Conversão</p>
         <p id="todayConversionRate" class="text-xl font-bold text-yellow-300">0%</p>
        </div>
       </div>
      </div>
     </div><!-- Metrics Overview -->
     <div class="grid grid-4 mb-8">
      <div class="metric-card">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-sm text-gray-600">Total de Contatos</p>
         <p id="totalContacts" class="text-2xl font-bold text-gray-900">0</p>
         <p class="text-xs text-gray-500 mt-1">Este mês: <span id="monthlyContacts">0</span></p>
        </div>
        <div class="text-2xl">
         📞
        </div>
       </div>
      </div>
      <div class="metric-card">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-sm text-gray-600">Vendas Convertidas</p>
         <p id="totalSales" class="text-2xl font-bold text-green-600">0</p>
         <p class="text-xs text-gray-500 mt-1">Este mês: <span id="monthlySales">0</span></p>
        </div>
        <div class="text-2xl">
         💰
        </div>
       </div>
      </div>
      <div class="metric-card">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-sm text-gray-600">Taxa de Conversão</p>
         <p id="conversionRate" class="text-2xl font-bold text-purple-600">0%</p>
         <p class="text-xs text-gray-500 mt-1">Este mês: <span id="monthlyConversionRate">0%</span></p>
        </div>
        <div class="text-2xl">
         📊
        </div>
       </div>
      </div>
      <div class="metric-card">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-sm text-gray-600">Receita Total</p>
         <p id="totalRevenue" class="text-2xl font-bold text-orange-600">R$ 0,00</p>
         <p class="text-xs text-gray-500 mt-1">Este mês: <span id="monthlyRevenue">R$ 0,00</span></p>
        </div>
        <div class="text-2xl">
         💼
        </div>
       </div>
      </div>
     </div><!-- Management Controls -->
     <div class="grid grid-3 gap-6 mb-8"><!-- Monthly Goals Management -->
      <div class="card">
       <div class="p-4 border-b flex justify-between items-center">
        <h2 class="text-lg font-bold text-gray-900">Metas Mensais</h2><button id="setGoalsBtn" class="btn btn-primary">Definir Metas</button>
       </div>
       <div class="p-4">
        <div class="grid grid-3 gap-4 text-center">
         <div>
          <p class="text-sm text-gray-600">Meta Geral</p>
          <p id="generalGoal" class="text-xl font-bold text-blue-600">0</p>
         </div>
         <div>
          <p class="text-sm text-gray-600">Realizadas</p>
          <p id="currentSales" class="text-xl font-bold text-green-600">0</p>
         </div>
         <div>
          <p class="text-sm text-gray-600">Progresso</p>
          <p id="generalProgress" class="text-xl font-bold text-purple-600">0%</p>
         </div>
        </div>
       </div>
      </div><!-- Users Management -->
      <div class="card">
       <div class="p-4 border-b flex justify-between items-center">
        <h2 class="text-lg font-bold text-gray-900">Usuários do Sistema</h2><button id="addUserBtn" class="btn btn-success">Adicionar Usuário</button>
       </div>
       <div class="p-4">
        <div class="grid grid-3 gap-4 text-center mb-4">
         <div>
          <p class="text-sm text-gray-600">Administradores</p>
          <p id="totalAdmins" class="text-xl font-bold text-red-600">0</p>
         </div>
         <div>
          <p class="text-sm text-gray-600">Vendedores</p>
          <p id="totalSellers" class="text-xl font-bold text-blue-600">0</p>
         </div>
         <div>
          <p class="text-sm text-gray-600">Assistentes</p>
          <p id="totalAssistants" class="text-xl font-bold text-green-600">0</p>
         </div>
        </div>
        <div class="overflow-x-auto">
         <table class="table">
          <thead>
           <tr>
            <th>Nome</th>
            <th>Tipo</th>
            <th>Status</th>
            <th>Cadastrado em</th>
            <th>Ações</th>
           </tr>
          </thead>
          <tbody id="usersTable">
          </tbody>
         </table>
        </div>
       </div>
      </div><!-- Store and Commission Management -->
      <div class="card">
       <div class="p-4 border-b">
        <h2 class="text-lg font-bold text-gray-900 mb-4">Configurações</h2>
        <div class="flex gap-2"><button id="manageStoresBtn" class="btn btn-success">Lojas</button> <button id="manageCampaignsBtn" class="btn bg-orange-600 text-white">Campanhas</button> <button id="setCommissionBtn" class="btn bg-purple-600 text-white">Comissão</button>
        </div>
       </div>
       <div class="p-4">
        <div class="grid grid-3 gap-4 text-center">
         <div>
          <p class="text-sm text-gray-600">Comissão</p>
          <p id="currentCommission" class="text-xl font-bold text-purple-600">1.0%</p>
         </div>
         <div>
          <p class="text-sm text-gray-600">Lojas</p>
          <p id="totalStores" class="text-xl font-bold text-green-600">0</p>
         </div>
         <div>
          <p class="text-sm text-gray-600">Campanhas</p>
          <p id="totalCampaigns" class="text-xl font-bold text-orange-600">0</p>
         </div>
        </div>
       </div>
      </div>
     </div><!-- Sellers Performance -->
     <div class="card mb-8">
      <div class="p-4 border-b">
       <h2 class="text-lg font-bold text-gray-900">Desempenho dos Vendedores</h2>
       <p class="text-sm text-gray-600 mt-1">Dados do mês atual e histórico geral</p>
      </div>
      <div class="overflow-x-auto">
       <table class="table">
        <thead>
         <tr>
          <th>Vendedor</th>
          <th>Meta Individual</th>
          <th>Contatos (Mês)</th>
          <th>Vendas (Mês)</th>
          <th>Progresso Meta</th>
          <th>Conversão (Mês)</th>
          <th>Receita (Mês)</th>
          <th>Total Geral</th>
         </tr>
        </thead>
        <tbody id="sellersTable">
        </tbody>
       </table>
      </div>
     </div><!-- Campaign Performance Report -->
     <div class="card mb-8">
      <div class="p-4 border-b">
       <h2 class="text-lg font-bold text-gray-900">Performance das Campanhas</h2>
      </div>
      <div class="p-4">
       <div class="grid grid-4 gap-4 mb-6">
        <div class="p-4 rounded" style="background: #eff6ff;">
         <p class="text-sm font-medium text-blue-600">Total Investido</p>
         <p id="totalInvested" class="text-xl font-bold text-blue-900">R$ 0,00</p>
        </div>
        <div class="p-4 rounded" style="background: #f0fdf4;">
         <p class="text-sm font-medium text-green-600">Receita Total</p>
         <p id="totalRevenue" class="text-xl font-bold text-green-900">R$ 0,00</p>
        </div>
        <div class="p-4 rounded" style="background: #faf5ff;">
         <p class="text-sm font-medium text-purple-600">ROI Geral</p>
         <p id="overallROI" class="text-xl font-bold text-purple-900">0%</p>
        </div>
        <div class="p-4 rounded" style="background: #fff7ed;">
         <p class="text-sm font-medium text-orange-600">Custo por Lead</p>
         <p id="avgCostPerLead" class="text-xl font-bold text-orange-900">R$ 0,00</p>
        </div>
       </div>
       <div class="overflow-x-auto">
        <table class="table">
         <thead>
          <tr>
           <th>Campanha</th>
           <th>Período</th>
           <th>Investimento</th>
           <th>Leads</th>
           <th>Vendas</th>
           <th>Receita</th>
           <th>ROI</th>
           <th>Custo/Lead</th>
           <th>Taxa Conv.</th>
          </tr>
         </thead>
         <tbody id="campaignPerformanceTable">
         </tbody>
        </table>
       </div>
      </div>
     </div><!-- Assistant Ranking -->
     <div class="card mb-8">
      <div class="p-4 border-b">
       <h2 class="text-lg font-bold text-gray-900">Ranking dos Assistentes de Vendas</h2>
       <p class="text-sm text-gray-600 mt-1">Performance baseada em leads distribuídos e conversões</p>
      </div>
      <div class="overflow-x-auto">
       <table class="table">
        <thead>
         <tr>
          <th>Posição</th>
          <th>Assistente</th>
          <th>Meta Mensal</th>
          <th>Leads Distribuídos</th>
          <th>Vendas Convertidas</th>
          <th>Taxa de Conversão</th>
          <th>Receita Gerada</th>
          <th>Score Performance</th>
         </tr>
        </thead>
        <tbody id="assistantRankingTable">
        </tbody>
       </table>
      </div>
     </div><!-- Overdue Reminders Alert -->
     <div class="card mb-8">
      <div class="p-4 border-b bg-red-50">
       <h2 class="text-lg font-bold text-red-800">🚨 Lembretes em Atraso - Ação Necessária</h2>
       <p class="text-sm text-red-600 mt-1">Vendedores com lembretes não concluídos estão bloqueados para novos leads</p>
      </div>
      <div class="overflow-x-auto">
       <table class="table">
        <thead>
         <tr>
          <th>Vendedor</th>
          <th>Cliente</th>
          <th>Tipo de Ação</th>
          <th>Data Programada</th>
          <th>Dias em Atraso</th>
          <th>Status Bloqueio</th>
          <th>Ações</th>
         </tr>
        </thead>
        <tbody id="overdueRemindersTable">
        </tbody>
       </table>
      </div>
     </div><!-- Store Performance Report -->
     <div class="card mb-8">
      <div class="p-4 border-b">
       <h2 class="text-lg font-bold text-gray-900">📊 Performance das Lojas</h2>
       <p class="text-sm text-gray-600 mt-1">Análise de faturamento e leads por loja</p>
      </div>
      <div class="p-4">
       <div class="grid grid-4 gap-4 mb-6">
        <div class="p-4 rounded" style="background: #eff6ff;">
         <p class="text-sm font-medium text-blue-600">Total de Lojas</p>
         <p id="totalActiveStores" class="text-xl font-bold text-blue-900">0</p>
        </div>
        <div class="p-4 rounded" style="background: #f0fdf4;">
         <p class="text-sm font-medium text-green-600">Melhor Performance</p>
         <p id="bestPerformingStore" class="text-xl font-bold text-green-900">-</p>
        </div>
        <div class="p-4 rounded" style="background: #faf5ff;">
         <p class="text-sm font-medium text-purple-600">Faturamento Total</p>
         <p id="totalStoreRevenue" class="text-xl font-bold text-purple-900">R$ 0,00</p>
        </div>
        <div class="p-4 rounded" style="background: #fff7ed;">
         <p class="text-sm font-medium text-orange-600">Ticket Médio</p>
         <p id="averageTicketAllStores" class="text-xl font-bold text-orange-900">R$ 0,00</p>
        </div>
       </div>
       <div class="overflow-x-auto">
        <table class="table">
         <thead>
          <tr>
           <th>Loja</th>
           <th>Tipo</th>
           <th>Leads Recebidos</th>
           <th>Vendas Pagas</th>
           <th>Taxa Conversão</th>
           <th>Faturamento</th>
           <th>Ticket Médio</th>
           <th>Performance</th>
          </tr>
         </thead>
         <tbody id="storePerformanceTable">
         </tbody>
        </table>
       </div>
      </div>
     </div><!-- Recent Sales -->
     <div class="card">
      <div class="p-4 border-b">
       <h2 class="text-lg font-bold text-gray-900">Vendas Recentes</h2>
      </div>
      <div class="overflow-x-auto">
       <table class="table">
        <thead>
         <tr>
          <th>Data</th>
          <th>Vendedor</th>
          <th>Cliente</th>
          <th>Produto</th>
          <th>Valor</th>
          <th>Loja</th>
          <th>Campanha</th>
         </tr>
        </thead>
        <tbody id="recentSalesTable">
        </tbody>
       </table>
      </div>
     </div>
    </main>
   </div><!-- Seller Dashboard -->
   <div id="sellerDashboard" class="hidden min-h-screen">
    <header class="header">
     <div class="steel-texture"></div>
     <div class="battle-stats">
      <div class="battle-stat"><span class="battle-stat-icon">🎯</span> <span>Meta: <span class="battle-stat-value" id="sellerHeaderGoal">0</span></span>
      </div>
      <div class="battle-stat"><span class="battle-stat-icon">💰</span> <span>Vendas: <span class="battle-stat-value" id="sellerHeaderSales">0</span></span>
      </div>
      <div class="battle-stat"><span class="battle-stat-icon">⚡</span> <span>Taxa: <span class="battle-stat-value" id="sellerHeaderRate">0%</span></span>
      </div>
     </div>
     <div class="container">
      <div class="header-content">
       <div class="header-title">
        <div class="header-icon"></div>
        <div class="header-text">
         <h1 id="sellerTitle">Meu Desempenho</h1>
         <p class="header-subtitle">Guerreiro de Vendas • Aço &amp; Tecnologia</p>
        </div>
       </div>
       <div class="header-user">
        <div class="user-avatar" id="sellerAvatar">
         V
        </div>
        <div class="user-info">
         <p class="user-name" id="sellerUserName">Vendedor</p>
         <p class="user-role">Guerreiro</p>
        </div><button id="sellerLogoutBtn" class="header-logout">Sair</button>
       </div>
      </div>
     </div>
    </header>
    <main class="container py-6"><!-- Personal Metrics -->
     <div class="grid grid-4 mb-8">
      <div class="metric-card">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-sm text-gray-600">Meus Contatos</p>
         <p id="myContacts" class="text-2xl font-bold text-blue-600">0</p>
        </div>
        <div class="text-2xl">
         📞
        </div>
       </div>
      </div>
      <div class="metric-card">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-sm text-gray-600">Minhas Vendas</p>
         <p id="mySales" class="text-2xl font-bold text-green-600">0</p>
        </div>
        <div class="text-2xl">
         💰
        </div>
       </div>
      </div>
      <div class="metric-card">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-sm text-gray-600">Minha Conversão</p>
         <p id="myConversionRate" class="text-2xl font-bold text-purple-600">0%</p>
        </div>
        <div class="text-2xl">
         📊
        </div>
       </div>
      </div>
      <div class="metric-card">
       <div class="flex items-center justify-between">
        <div>
         <p class="text-sm text-gray-600">Meta do Mês</p>
         <p id="monthlyGoal" class="text-2xl font-bold text-orange-600">Não definida</p>
         <p id="sellerProgress" class="text-sm text-gray-500 mt-1">0% concluído</p>
        </div>
        <div class="text-2xl">
         🎯
        </div>
       </div>
      </div>
     </div><!-- Add New Contact -->
     <div class="card mb-8">
      <div class="p-4 border-b">
       <h2 class="text-lg font-bold text-gray-900">Adicionar Novo Contato</h2>
      </div>
      <div class="p-4">
       <form id="contactForm" class="grid grid-2 gap-4">
        <div><label for="contactName" class="block text-sm font-medium text-gray-700 mb-1">Nome do Cliente</label> <input id="contactName" type="text" required class="form-input">
        </div>
        <div><label for="contactEmail" class="block text-sm font-medium text-gray-700 mb-1">Email (opcional)</label> <input id="contactEmail" type="email" class="form-input">
        </div>
        <div><label for="contactPhone" class="block text-sm font-medium text-gray-700 mb-1">Telefone</label> <input id="contactPhone" type="tel" required class="form-input">
        </div>
        <div><label for="contactProduct" class="block text-sm font-medium text-gray-700 mb-1">Produto de Interesse</label> <input id="contactProduct" type="text" required class="form-input">
        </div>
        <div><label for="clientStatus" class="block text-sm font-medium text-gray-700 mb-1">Status do Cliente</label> <select id="clientStatus" required class="form-input"> <option value="">Selecione o status...</option> <option value="novo">🆕 Novo - Cliente recém cadastrado</option> <option value="em_andamento">⏳ Em Andamento - Cliente sendo trabalhado</option> <option value="quente">🔥 Quente - Cliente muito interessado</option> <option value="morno">🟡 Morno - Cliente com interesse moderado</option> <option value="frio">❄️ Frio - Cliente com pouco interesse</option> <option value="sem_retorno">📵 Sem Retorno - Cliente não responde</option> <option value="venda_perdida">❌ Venda Perdida - Cliente desistiu</option> </select>
        </div>
        <div><label for="contactStore" class="block text-sm font-medium text-gray-700 mb-1">Loja de Interesse (opcional)</label> <select id="contactStore" class="form-input"> <option value="">Selecione a loja...</option> </select>
        </div>
        <div><label for="contactCampaign" class="block text-sm font-medium text-gray-700 mb-1">Campanha de Marketing</label> <select id="contactCampaign" class="form-input"> <option value="">Selecione a campanha...</option> </select>
        </div>
        <div><label for="budgetValue" class="block text-sm font-medium text-gray-700 mb-1">Valor do Orçamento (R$)</label> <input id="budgetValue" type="number" step="0.01" min="0" class="form-input">
        </div>
        <div style="grid-column: 1 / -1;"><label for="contactNotes" class="block text-sm font-medium text-gray-700 mb-1">Observações</label> <textarea id="contactNotes" rows="3" class="form-input"></textarea>
        </div>
        <div style="grid-column: 1 / -1;"><button type="submit" id="addContactBtn" class="btn btn-primary">Adicionar Contato</button>
        </div>
       </form>
      </div>
     </div><!-- Active Reminders -->
     <div class="card mb-8">
      <div class="p-4 border-b bg-blue-50">
       <h2 class="text-lg font-bold text-blue-800">⏰ Meus Lembretes Ativos</h2>
       <p class="text-sm text-blue-600 mt-1">Lembretes programados que precisam da sua atenção</p>
      </div>
      <div class="overflow-x-auto">
       <table class="table">
        <thead>
         <tr>
          <th>Cliente</th>
          <th>Tipo de Ação</th>
          <th>Data Programada</th>
          <th>Status</th>
          <th>Observações</th>
          <th>Ações</th>
         </tr>
        </thead>
        <tbody id="myRemindersTable">
        </tbody>
       </table>
      </div>
     </div><!-- My Contacts -->
     <div class="card">
      <div class="p-4 border-b">
       <h2 class="text-lg font-bold text-gray-900">Meus Contatos</h2>
      </div>
      <div class="overflow-x-auto">
       <table class="table">
        <thead>
         <tr>
          <th>Cliente</th>
          <th>Contato</th>
          <th>Produto</th>
          <th>Status Cliente</th>
          <th>Status Venda</th>
          <th>Último Contato</th>
          <th>Ações</th>
         </tr>
        </thead>
        <tbody id="myContactsTable">
        </tbody>
       </table>
      </div>
     </div>
    </main>
   </div><!-- Assistant Dashboard -->
   <div id="assistantDashboard" class="hidden min-h-full">
    <header class="header">
     <div class="steel-texture"></div>
     <div class="battle-stats">
      <div class="battle-stat"><span class="battle-stat-icon">📤</span> <span>Leads: <span class="battle-stat-value" id="assistantHeaderLeads">0</span></span>
      </div>
      <div class="battle-stat"><span class="battle-stat-icon">💰</span> <span>Conversões: <span class="battle-stat-value" id="assistantHeaderConversions">0</span></span>
      </div>
      <div class="battle-stat"><span class="battle-stat-icon">🏆</span> <span>Ranking: <span class="battle-stat-value" id="assistantHeaderRanking">#1</span></span>
      </div>
     </div>
     <div class="container">
      <div class="header-content">
       <div class="header-title">
        <div class="header-icon"></div>
        <div class="header-text">
         <h1>Assistente de Vendas</h1>
         <p class="header-subtitle">Estrategista • Aço &amp; Tecnologia</p>
        </div>
       </div>
       <div class="header-user">
        <div class="user-avatar" id="assistantAvatar">
         S
        </div>
        <div class="user-info">
         <p class="user-name" id="assistantUserName">Assistente</p>
         <p class="user-role">Estrategista</p>
        </div><button id="assistantLogoutBtn" class="header-logout">Sair</button>
       </div>
      </div>
     </div>
    </header>
    <main class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8"><!-- Assistant Metrics -->
     <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-5 gap-6 mb-8">
      <div class="metric-card bg-white p-6 rounded-lg shadow">
       <div class="flex items-center">
        <div class="flex-1">
         <p class="text-sm font-medium text-gray-600">Leads Distribuídos</p>
         <p id="distributedLeads" class="text-2xl font-bold text-blue-600">0</p>
         <p class="text-xs text-gray-500 mt-1">Este mês</p>
        </div>
        <div class="w-12 h-12 bg-blue-100 rounded-lg flex items-center justify-center"><span class="text-blue-600 text-xl">📤</span>
        </div>
       </div>
      </div>
      <div class="metric-card bg-white p-6 rounded-lg shadow">
       <div class="flex items-center">
        <div class="flex-1">
         <p class="text-sm font-medium text-gray-600">Vendas Convertidas</p>
         <p id="assistantConversions" class="text-2xl font-bold text-green-600">0</p>
         <p class="text-xs text-gray-500 mt-1">Dos meus leads</p>
        </div>
        <div class="w-12 h-12 bg-green-100 rounded-lg flex items-center justify-center"><span class="text-green-600 text-xl">💰</span>
        </div>
       </div>
      </div>
      <div class="metric-card bg-white p-6 rounded-lg shadow">
       <div class="flex items-center">
        <div class="flex-1">
         <p class="text-sm font-medium text-gray-600">Taxa Conversão</p>
         <p id="assistantConversionRate" class="text-2xl font-bold text-purple-600">0%</p>
         <p class="text-xs text-gray-500 mt-1">Performance</p>
        </div>
        <div class="w-12 h-12 bg-purple-100 rounded-lg flex items-center justify-center"><span class="text-purple-600 text-xl">📊</span>
        </div>
       </div>
      </div>
      <div class="metric-card bg-white p-6 rounded-lg shadow">
       <div class="flex items-center">
        <div class="flex-1">
         <p class="text-sm font-medium text-gray-600">Meta do Mês</p>
         <p id="assistantGoal" class="text-2xl font-bold text-orange-600">0</p>
         <p id="assistantProgress" class="text-xs text-gray-500 mt-1">0% concluído</p>
        </div>
        <div class="w-12 h-12 bg-orange-100 rounded-lg flex items-center justify-center"><span class="text-orange-600 text-xl">🎯</span>
        </div>
       </div>
      </div>
      <div class="metric-card bg-white p-6 rounded-lg shadow">
       <div class="flex items-center">
        <div class="flex-1">
         <p class="text-sm font-medium text-gray-600">Ranking</p>
         <p id="assistantRanking" class="text-2xl font-bold text-indigo-600">#1</p>
         <p class="text-xs text-gray-500 mt-1">Entre assistentes</p>
        </div>
        <div class="w-12 h-12 bg-indigo-100 rounded-lg flex items-center justify-center"><span class="text-indigo-600 text-xl">🏆</span>
        </div>
       </div>
      </div>
     </div><!-- Follow-up and Remarketing Section -->
     <div class="grid grid-cols-1 lg:grid-cols-2 gap-6 mb-8"><!-- Follow-up Actions -->
      <div class="bg-white rounded-lg shadow">
       <div class="px-6 py-4 border-b border-gray-200">
        <h2 class="text-lg font-semibold text-gray-900">Follow-up de Leads</h2>
        <p class="text-sm text-gray-600">Acompanhe e estimule conversões</p>
       </div>
       <div class="p-6">
        <div class="grid grid-cols-3 gap-4 mb-6">
         <div class="text-center p-4 bg-yellow-50 rounded-lg">
          <p class="text-sm font-medium text-yellow-600">Leads Pendentes</p>
          <p id="pendingLeads" class="text-xl font-bold text-yellow-800">0</p>
         </div>
         <div class="text-center p-4 bg-blue-50 rounded-lg">
          <p class="text-sm font-medium text-blue-600">Em Follow-up</p>
          <p id="followupLeads" class="text-xl font-bold text-blue-800">0</p>
         </div>
         <div class="text-center p-4 bg-red-50 rounded-lg">
          <p class="text-sm font-medium text-red-600">Sem Retorno</p>
          <p id="noResponseLeads" class="text-xl font-bold text-red-800">0</p>
         </div>
        </div>
        <div class="space-y-3"><button id="viewPendingLeadsBtn" class="w-full bg-yellow-600 hover:bg-yellow-700 text-white px-4 py-2 rounded-md font-medium"> 📋 Ver Leads Pendentes </button> <button id="sendRemarketingBtn" class="w-full bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-md font-medium"> 📢 Enviar Remarketing </button> <button id="contactSellersBtn" class="w-full bg-green-600 hover:bg-green-700 text-white px-4 py-2 rounded-md font-medium"> 📞 Contatar Vendedores </button>
        </div>
       </div>
      </div><!-- Performance Insights -->
      <div class="bg-white rounded-lg shadow">
       <div class="px-6 py-4 border-b border-gray-200">
        <h2 class="text-lg font-semibold text-gray-900">Insights de Performance</h2>
        <p class="text-sm text-gray-600">Análise dos seus leads</p>
       </div>
       <div class="p-6">
        <div class="space-y-4">
         <div class="flex justify-between items-center p-3 bg-gray-50 rounded-lg"><span class="text-sm font-medium text-gray-700">Melhor Vendedor</span> <span id="bestSeller" class="text-sm font-bold text-green-600">-</span>
         </div>
         <div class="flex justify-between items-center p-3 bg-gray-50 rounded-lg"><span class="text-sm font-medium text-gray-700">Campanha Top</span> <span id="topCampaign" class="text-sm font-bold text-blue-600">-</span>
         </div>
         <div class="flex justify-between items-center p-3 bg-gray-50 rounded-lg"><span class="text-sm font-medium text-gray-700">Tempo Médio Conversão</span> <span id="avgConversionTime" class="text-sm font-bold text-purple-600">-</span>
         </div>
         <div class="flex justify-between items-center p-3 bg-gray-50 rounded-lg"><span class="text-sm font-medium text-gray-700">Receita Gerada</span> <span id="assistantRevenue" class="text-sm font-bold text-orange-600">R$ 0,00</span>
         </div>
        </div>
       </div>
      </div>
     </div><!-- Add New Lead -->
     <div class="bg-white rounded-lg shadow mb-8">
      <div class="px-6 py-4 border-b border-gray-200">
       <h2 class="text-lg font-semibold text-gray-900">Adicionar Novo Lead</h2>
      </div>
      <div class="p-6">
       <form id="leadForm" class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div><label for="leadName" class="block text-sm font-medium text-gray-700">Nome do Cliente</label> <input id="leadName" type="text" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
        </div>
        <div><label for="leadEmail" class="block text-sm font-medium text-gray-700">Email (opcional)</label> <input id="leadEmail" type="email" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
        </div>
        <div><label for="leadPhone" class="block text-sm font-medium text-gray-700">Telefone</label> <input id="leadPhone" type="tel" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
        </div>
        <div><label for="leadProduct" class="block text-sm font-medium text-gray-700">Produto de Interesse</label> <input id="leadProduct" type="text" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
        </div>
        <div><label for="assignToSeller" class="block text-sm font-medium text-gray-700">Atribuir ao Vendedor</label> <select id="assignToSeller" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione o vendedor...</option> </select>
        </div>
        <div><label for="leadStore" class="block text-sm font-medium text-gray-700">Loja de Interesse (opcional)</label> <select id="leadStore" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione a loja...</option> </select>
        </div>
        <div><label for="leadCampaign" class="block text-sm font-medium text-gray-700">Campanha de Marketing</label> <select id="leadCampaign" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione a campanha...</option> </select>
        </div>
        <div><label for="leadBudgetValue" class="block text-sm font-medium text-gray-700">Valor do Orçamento (R$)</label> <input id="leadBudgetValue" type="number" step="0.01" min="0" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
        </div>
        <div class="md:col-span-2"><label for="leadNotes" class="block text-sm font-medium text-gray-700">Observações do Lead</label> <textarea id="leadNotes" rows="3" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"></textarea>
        </div>
        <div class="md:col-span-2"><button type="submit" id="addLeadBtn" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-md font-medium"> Adicionar Lead e Atribuir </button>
        </div>
       </form>
      </div>
     </div><!-- Lost Sales Review Section -->
     <div class="bg-white rounded-lg shadow mb-8">
      <div class="px-6 py-4 border-b border-gray-200">
       <h2 class="text-lg font-semibold text-gray-900">🚨 Vendas Perdidas - Revisão Obrigatória</h2>
       <p class="text-sm text-gray-600">Vendas perdidas que precisam da sua confirmação</p>
      </div>
      <div class="overflow-x-auto">
       <table class="min-w-full divide-y divide-gray-200">
        <thead class="bg-red-50">
         <tr>
          <th class="px-6 py-3 text-left text-xs font-medium text-red-600 uppercase tracking-wider">Cliente</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-red-600 uppercase tracking-wider">Vendedor</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-red-600 uppercase tracking-wider">Motivo</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-red-600 uppercase tracking-wider">Data</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-red-600 uppercase tracking-wider">Status</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-red-600 uppercase tracking-wider">Ações</th>
         </tr>
        </thead>
        <tbody id="lostSalesTable" class="bg-white divide-y divide-gray-200">
        </tbody>
       </table>
      </div>
     </div><!-- Seller Reminders Monitoring -->
     <div class="bg-white rounded-lg shadow mb-8">
      <div class="px-6 py-4 border-b border-gray-200">
       <h2 class="text-lg font-semibold text-gray-900">⏰ Lembretes dos Meus Vendedores</h2>
       <p class="text-sm text-gray-600">Acompanhe os lembretes dos leads que você distribuiu</p>
      </div>
      <div class="overflow-x-auto">
       <table class="min-w-full divide-y divide-gray-200">
        <thead class="bg-gray-50">
         <tr>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Vendedor</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Cliente</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Tipo de Ação</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Data Programada</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Status</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Observações</th>
         </tr>
        </thead>
        <tbody id="sellerRemindersTable" class="bg-white divide-y divide-gray-200">
        </tbody>
       </table>
      </div>
     </div><!-- My Leads Management -->
     <div class="bg-white rounded-lg shadow mb-8">
      <div class="px-6 py-4 border-b border-gray-200">
       <h2 class="text-lg font-semibold text-gray-900">Meus Leads Distribuídos</h2>
       <p class="text-sm text-gray-600">Acompanhe o status dos leads que você distribuiu</p>
      </div>
      <div class="overflow-x-auto">
       <table class="min-w-full divide-y divide-gray-200">
        <thead class="bg-gray-50">
         <tr>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Cliente</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Vendedor</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Produto</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Status Cliente</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Status Venda</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Último Contato</th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Ações</th>
         </tr>
        </thead>
        <tbody id="assistantLeadsTable" class="bg-white divide-y divide-gray-200">
        </tbody>
       </table>
      </div>
     </div>
    </main>
   </div><!-- Goals Modal -->
   <div id="goalsModal" class="hidden modal">
    <div class="modal-content">
     <h3 class="text-lg font-bold text-gray-900 mb-4">Definir Metas Mensais</h3>
     <form id="goalsForm" class="flex-col flex gap-4">
      <div><label for="generalGoalInput" class="block text-sm font-medium text-gray-700 mb-1">Meta Geral de Vendas</label> <input id="generalGoalInput" type="number" min="1" required class="form-input">
      </div>
      <div><label for="individualGoalInput" class="block text-sm font-medium text-gray-700 mb-1">Meta Individual por Vendedor</label> <input id="individualGoalInput" type="number" min="1" required class="form-input">
      </div>
      <div class="flex gap-3"><button type="button" id="cancelGoalsBtn" class="btn btn-secondary">Cancelar</button> <button type="submit" id="confirmGoalsBtn" class="btn btn-primary">Salvar Metas</button>
      </div>
     </form>
    </div>
   </div><!-- Stores Management Modal -->
   <div id="storesModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-10 mx-auto p-5 border w-full max-w-2xl shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">Gerenciar Lojas</h3><!-- Add Store Form -->
      <div class="mb-6 p-4 bg-gray-50 rounded-lg">
       <h4 class="text-md font-medium text-gray-800 mb-3">Adicionar Nova Loja</h4>
       <form id="addStoreForm" class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div><label for="storeName" class="block text-sm font-medium text-gray-700">Nome da Loja</label> <input id="storeName" type="text" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
        </div>
        <div><label for="storeType" class="block text-sm font-medium text-gray-700">Tipo</label> <select id="storeType" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione...</option> <option value="matriz">Matriz</option> <option value="filial">Filial</option> </select>
        </div>
        <div class="md:col-span-2"><label for="storeAddress" class="block text-sm font-medium text-gray-700">Endereço</label> <input id="storeAddress" type="text" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
        </div>
        <div class="md:col-span-2"><button type="submit" id="addStoreBtn" class="bg-green-600 hover:bg-green-700 text-white px-4 py-2 rounded-md font-medium"> Adicionar Loja </button>
        </div>
       </form>
      </div><!-- Stores List -->
      <div class="mb-4">
       <h4 class="text-md font-medium text-gray-800 mb-3">Lojas Cadastradas</h4>
       <div class="overflow-x-auto">
        <table class="min-w-full divide-y divide-gray-200">
         <thead class="bg-gray-50">
          <tr>
           <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Nome</th>
           <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Tipo</th>
           <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Endereço</th>
           <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Ações</th>
          </tr>
         </thead>
         <tbody id="storesTableBody" class="bg-white divide-y divide-gray-200">
         </tbody>
        </table>
       </div>
      </div>
      <div class="flex justify-end"><button id="closeStoresBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Fechar </button>
      </div>
     </div>
    </div>
   </div><!-- Campaigns Management Modal -->
   <div id="campaignsModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-10 mx-auto p-5 border w-full max-w-6xl shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">🚀 Gerenciar Campanhas e Anúncios de Marketing</h3><!-- Add Campaign Form -->
      <div class="mb-6 p-4 bg-gray-50 rounded-lg">
       <h4 class="text-md font-medium text-gray-800 mb-3">Adicionar Nova Campanha</h4>
       <form id="addCampaignForm" class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div><label for="campaignName" class="block text-sm font-medium text-gray-700">Nome da Campanha</label> <input id="campaignName" type="text" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
        </div>
        <div><label for="campaignType" class="block text-sm font-medium text-gray-700">Tipo</label> <select id="campaignType" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione...</option> <option value="google_ads">Google Ads</option> <option value="facebook_ads">Facebook Ads</option> <option value="instagram_ads">Instagram Ads</option> <option value="whatsapp">WhatsApp</option> <option value="email">Email Marketing</option> <option value="indicacao">Indicação</option> <option value="site">Site/Landing Page</option> <option value="contato_direto">Contato Direto</option> <option value="trafego_vendedor">Tráfego do Vendedor</option> <option value="outros">Outros</option> </select>
        </div>
        <div><label for="campaignStartDate" class="block text-sm font-medium text-gray-700">Data de Início</label> <input id="campaignStartDate" type="date" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
        </div>
        <div><label for="campaignEndDate" class="block text-sm font-medium text-gray-700">Data de Fim (opcional)</label> <input id="campaignEndDate" type="date" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
        </div>
        <div><label for="campaignGoal" class="block text-sm font-medium text-gray-700">Meta de Leads</label> <input id="campaignGoal" type="number" min="1" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
        </div>
        <div class="md:col-span-2"><label for="campaignDescription" class="block text-sm font-medium text-gray-700">Descrição</label> <textarea id="campaignDescription" rows="2" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"></textarea>
        </div>
        <div class="md:col-span-2"><button type="submit" id="addCampaignBtn" class="bg-orange-600 hover:bg-orange-700 text-white px-4 py-2 rounded-md font-medium"> Adicionar Campanha </button>
        </div>
       </form>
      </div><!-- Campaigns List with Ads Management -->
      <div class="mb-4">
       <h4 class="text-md font-medium text-gray-800 mb-3">📊 Campanhas e Performance dos Anúncios</h4>
       <div id="campaignsAccordion" class="space-y-4"><!-- Campaigns will be populated here -->
       </div>
      </div>
      <div class="flex justify-end"><button id="closeCampaignsBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Fechar </button>
      </div>
     </div>
    </div>
   </div><!-- Add Ad Modal -->
   <div id="addAdModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-20 mx-auto p-5 border w-full max-w-md shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">📢 Adicionar Novo Anúncio</h3>
      <form id="addAdForm" class="space-y-4">
       <div><label for="adName" class="block text-sm font-medium text-gray-700">Nome do Anúncio</label> <input id="adName" type="text" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="Ex: Anúncio Aço Inox - Público 25-45">
       </div>
       <div><label for="adType" class="block text-sm font-medium text-gray-700">Tipo de Anúncio</label> <select id="adType" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione...</option> <option value="imagem">Imagem</option> <option value="video">Vídeo</option> <option value="carrossel">Carrossel</option> <option value="colecao">Coleção</option> <option value="texto">Texto</option> <option value="stories">Stories</option> <option value="reels">Reels</option> </select>
       </div>
       <div><label for="adAudience" class="block text-sm font-medium text-gray-700">Público-Alvo</label> <input id="adAudience" type="text" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="Ex: Homens 30-50, Construção Civil">
       </div>
       <div><label for="adDailyBudget" class="block text-sm font-medium text-gray-700">Orçamento Diário (R$)</label> <input id="adDailyBudget" type="number" step="0.01" min="1" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
       </div>
       <div><label for="adStartDate" class="block text-sm font-medium text-gray-700">Data de Início</label> <input id="adStartDate" type="date" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
       </div>
       <div><label for="adEndDate" class="block text-sm font-medium text-gray-700">Data de Fim (opcional)</label> <input id="adEndDate" type="date" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
       </div>
       <div><label for="adDescription" class="block text-sm font-medium text-gray-700">Descrição/Texto do Anúncio</label> <textarea id="adDescription" rows="3" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="Descreva o anúncio, copy, call-to-action..."></textarea>
       </div>
       <div class="flex justify-end space-x-3"><button type="button" id="cancelAddAdBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Cancelar </button> <button type="submit" id="confirmAddAdBtn" class="px-4 py-2 bg-blue-600 text-white rounded-md hover:bg-blue-700"> Adicionar Anúncio </button>
       </div>
      </form>
     </div>
    </div>
   </div><!-- Update Ad Budget Modal -->
   <div id="updateAdBudgetModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-20 mx-auto p-5 border w-full max-w-md shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">💰 Atualizar Orçamento do Anúncio</h3>
      <form id="updateAdBudgetForm" class="space-y-4">
       <div><label for="newDailyBudget" class="block text-sm font-medium text-gray-700">Novo Orçamento Diário (R$)</label> <input id="newDailyBudget" type="number" step="0.01" min="1" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
       </div>
       <div><label for="budgetChangeReason" class="block text-sm font-medium text-gray-700">Motivo da Alteração</label> <select id="budgetChangeReason" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione...</option> <option value="escalar">🚀 Escalar - Anúncio performando bem</option> <option value="reduzir">📉 Reduzir - Performance baixa</option> <option value="testar">🧪 Testar - Novo orçamento</option> <option value="pausar">⏸️ Pausar - Orçamento R$ 0,00</option> <option value="ajuste">⚙️ Ajuste estratégico</option> </select>
       </div>
       <div><label for="budgetNotes" class="block text-sm font-medium text-gray-700">Observações</label> <textarea id="budgetNotes" rows="2" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="Detalhes sobre a mudança..."></textarea>
       </div>
       <div class="flex justify-end space-x-3"><button type="button" id="cancelUpdateBudgetBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Cancelar </button> <button type="submit" id="confirmUpdateBudgetBtn" class="px-4 py-2 bg-green-600 text-white rounded-md hover:bg-green-700"> Atualizar Orçamento </button>
       </div>
      </form>
     </div>
    </div>
   </div><!-- Add User Modal -->
   <div id="addUserModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-20 mx-auto p-5 border w-full max-w-md shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">Cadastrar Novo Usuário</h3>
      <form id="addUserForm" class="space-y-4">
       <div><label for="newUserName" class="block text-sm font-medium text-gray-700">Nome Completo</label> <input id="newUserName" type="text" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
       </div>
       <div><label for="newUserEmail" class="block text-sm font-medium text-gray-700">Email (opcional)</label> <input id="newUserEmail" type="email" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
       </div>
       <div><label for="newUserPassword" class="block text-sm font-medium text-gray-700">Senha</label> <input id="newUserPassword" type="password" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
       </div>
       <div><label for="newUserRole" class="block text-sm font-medium text-gray-700">Tipo de Usuário</label> <select id="newUserRole" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione...</option> <option value="admin">Administrador</option> <option value="seller">Vendedor</option> <option value="assistant">Assistente de Vendas</option> </select>
       </div>
       <div class="flex justify-end space-x-3"><button type="button" id="cancelAddUserBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Cancelar </button> <button type="submit" id="confirmAddUserBtn" class="px-4 py-2 bg-green-600 text-white rounded-md hover:bg-green-700"> Cadastrar Usuário </button>
       </div>
      </form>
     </div>
    </div>
   </div><!-- Commission Modal -->
   <div id="commissionModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-20 mx-auto p-5 border w-96 shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">Configurar Taxa de Comissão</h3>
      <form id="commissionForm">
       <div class="mb-4"><label for="commissionRateInput" class="block text-sm font-medium text-gray-700">Taxa de Comissão (%)</label> <input id="commissionRateInput" type="number" step="0.1" min="0" max="100" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
        <p class="text-xs text-gray-500 mt-1">Exemplo: 1.5 para 1,5% de comissão</p>
       </div>
       <div class="flex justify-end space-x-3"><button type="button" id="cancelCommissionBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Cancelar </button> <button type="submit" id="confirmCommissionBtn" class="px-4 py-2 bg-purple-600 text-white rounded-md hover:bg-purple-700"> Salvar Taxa </button>
       </div>
      </form>
     </div>
    </div>
   </div><!-- Update Status Modal -->
   <div id="updateStatusModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-20 mx-auto p-5 border w-96 shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">Atualizar Status do Cliente</h3>
      <form id="updateStatusForm">
       <div class="mb-4"><label for="newClientStatus" class="block text-sm font-medium text-gray-700">Novo Status</label> <select id="newClientStatus" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione o status...</option> <option value="novo">🆕 Novo - Cliente recém cadastrado</option> <option value="em_andamento">⏳ Em Andamento - Cliente sendo trabalhado</option> <option value="quente">🔥 Quente - Cliente muito interessado</option> <option value="morno">🟡 Morno - Cliente com interesse moderado</option> <option value="frio">❄️ Frio - Cliente com pouco interesse</option> <option value="sem_retorno">📵 Sem Retorno - Cliente não responde</option> <option value="venda_perdida" data-requires-justification="true">❌ Venda Perdida - Cliente desistiu</option> </select>
       </div>
       <div class="mb-4"><label for="statusNotes" class="block text-sm font-medium text-gray-700">Observações do Contato</label> <textarea id="statusNotes" rows="3" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"></textarea>
       </div>
       <div class="flex justify-end space-x-3"><button type="button" id="cancelStatusBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Cancelar </button> <button type="submit" id="confirmStatusBtn" class="px-4 py-2 bg-blue-600 text-white rounded-md hover:bg-blue-700"> Atualizar Status </button>
       </div>
      </form>
     </div>
    </div>
   </div><!-- Set Reminder Modal -->
   <div id="setReminderModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-20 mx-auto p-5 border w-full max-w-md shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">⏰ Definir Lembrete de Contato</h3>
      <form id="setReminderForm" class="space-y-4">
       <div><label for="reminderDate" class="block text-sm font-medium text-gray-700">Data e Hora do Lembrete *</label> <input id="reminderDate" type="datetime-local" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
        <p class="text-xs text-gray-500 mt-1">O lembrete aparecerá 24h antes desta data</p>
       </div>
       <div><label for="reminderType" class="block text-sm font-medium text-gray-700">Tipo de Ação *</label> <select id="reminderType" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione...</option> <option value="fechar_venda">💰 Fechar Venda</option> <option value="followup">📞 Follow-up</option> <option value="apresentacao">📊 Apresentação</option> <option value="negociacao">🤝 Negociação</option> <option value="visita_tecnica">🔧 Visita Técnica</option> <option value="envio_proposta">📋 Envio de Proposta</option> <option value="outros">📝 Outros</option> </select>
       </div>
       <div><label for="reminderNotes" class="block text-sm font-medium text-gray-700">Observações do Lembrete *</label> <textarea id="reminderNotes" rows="3" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="Ex: Entrar em contato para fechar a venda do produto X. Cliente demonstrou interesse e pediu para ligar nesta data..."></textarea>
       </div>
       <div class="bg-yellow-50 border border-yellow-200 rounded-lg p-3">
        <div class="flex">
         <div class="flex-shrink-0"><span class="text-yellow-600">⚠️</span>
         </div>
         <div class="ml-3">
          <p class="text-sm text-yellow-800"><strong>Importante:</strong> Se você não marcar este lembrete como concluído até a data programada, ficará bloqueado para receber novos leads do estrategista.</p>
         </div>
        </div>
       </div>
       <div class="flex justify-end space-x-3"><button type="button" id="cancelReminderBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Cancelar </button> <button type="submit" id="confirmReminderBtn" class="px-4 py-2 bg-blue-600 text-white rounded-md hover:bg-blue-700"> Criar Lembrete </button>
       </div>
      </form>
     </div>
    </div>
   </div><!-- Complete Reminder Modal -->
   <div id="completeReminderModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-20 mx-auto p-5 border w-full max-w-md shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">✅ Marcar Lembrete como Concluído</h3>
      <div id="reminderDetailsContent" class="mb-4"><!-- Content will be populated dynamically -->
      </div>
      <form id="completeReminderForm" class="space-y-4">
       <div><label for="completionNotes" class="block text-sm font-medium text-gray-700">Resultado da Ação *</label> <textarea id="completionNotes" rows="4" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="Descreva o que aconteceu no contato: cliente respondeu, venda fechada, reagendamento necessário, etc..."></textarea>
       </div>
       <div><label for="actionResult" class="block text-sm font-medium text-gray-700">Status da Ação</label> <select id="actionResult" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione...</option> <option value="sucesso">✅ Sucesso - Ação realizada com êxito</option> <option value="reagendar">📅 Reagendar - Precisa de novo contato</option> <option value="sem_sucesso">❌ Sem Sucesso - Cliente não respondeu/desinteressado</option> </select>
       </div>
       <div class="flex justify-end space-x-3"><button type="button" id="cancelCompleteReminderBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Cancelar </button> <button type="submit" id="confirmCompleteReminderBtn" class="px-4 py-2 bg-green-600 text-white rounded-md hover:bg-green-700"> Marcar como Concluído </button>
       </div>
      </form>
     </div>
    </div>
   </div><!-- Convert Sale Modal -->
   <div id="convertModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-20 mx-auto p-5 border w-96 shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">Converter em Venda</h3>
      <form id="convertForm">
       <div class="mb-4"><label for="saleValue" class="block text-sm font-medium text-gray-700">Valor da Venda (R$)</label> <input id="saleValue" type="number" step="0.01" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
       </div>
       <div class="mb-4"><label for="saleStore" class="block text-sm font-medium text-gray-700">Loja onde foi pago</label> <select id="saleStore" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione a loja...</option> </select>
       </div>
       <div class="mb-4"><label for="orderNumber" class="block text-sm font-medium text-gray-700">Número do Pedido</label> <input id="orderNumber" type="text" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="Ex: PED-2024-001">
       </div>
       <div class="mb-4"><label for="saleNotes" class="block text-sm font-medium text-gray-700">Observações da Venda</label> <textarea id="saleNotes" rows="3" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"></textarea>
       </div>
       <div class="flex justify-end space-x-3"><button type="button" id="cancelConvertBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Cancelar </button> <button type="submit" id="confirmConvertBtn" class="px-4 py-2 bg-green-600 text-white rounded-md hover:bg-green-700"> Confirmar Venda </button>
       </div>
      </form>
     </div>
    </div>
   </div><!-- Pending Leads Modal -->
   <div id="pendingLeadsModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-10 mx-auto p-5 border w-full max-w-4xl shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">Leads Pendentes de Follow-up</h3>
      <div class="overflow-x-auto">
       <table class="min-w-full divide-y divide-gray-200">
        <thead class="bg-gray-50">
         <tr>
          <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Cliente</th>
          <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Vendedor</th>
          <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Produto</th>
          <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Status</th>
          <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Último Contato</th>
          <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Ações</th>
         </tr>
        </thead>
        <tbody id="pendingLeadsTableBody" class="bg-white divide-y divide-gray-200">
        </tbody>
       </table>
      </div>
      <div class="flex justify-end mt-4"><button id="closePendingLeadsBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Fechar </button>
      </div>
     </div>
    </div>
   </div><!-- Remarketing Modal -->
   <div id="remarketingModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-20 mx-auto p-5 border w-full max-w-md shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">Enviar Remarketing</h3>
      <form id="remarketingForm">
       <div class="mb-4"><label for="remarketingType" class="block text-sm font-medium text-gray-700">Tipo de Remarketing</label> <select id="remarketingType" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione o tipo...</option> <option value="whatsapp">WhatsApp</option> <option value="email">Email</option> <option value="sms">SMS</option> <option value="ligacao">Ligação</option> </select>
       </div>
       <div class="mb-4"><label for="remarketingMessage" class="block text-sm font-medium text-gray-700">Mensagem</label> <textarea id="remarketingMessage" rows="4" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="Digite a mensagem de remarketing..."></textarea>
       </div>
       <div class="mb-4"><label for="targetLeads" class="block text-sm font-medium text-gray-700">Público Alvo</label> <select id="targetLeads" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione o público...</option> <option value="sem_retorno">Leads sem retorno</option> <option value="frios">Leads frios</option> <option value="mornos">Leads mornos</option> <option value="todos_pendentes">Todos os pendentes</option> </select>
       </div>
       <div class="flex justify-end space-x-3"><button type="button" id="cancelRemarketingBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Cancelar </button> <button type="submit" id="confirmRemarketingBtn" class="px-4 py-2 bg-blue-600 text-white rounded-md hover:bg-blue-700"> Enviar Remarketing </button>
       </div>
      </form>
     </div>
    </div>
   </div><!-- Contact Sellers Modal -->
   <div id="contactSellersModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-20 mx-auto p-5 border w-full max-w-md shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">Contatar Vendedores</h3>
      <form id="contactSellersForm">
       <div class="mb-4"><label for="contactMethod" class="block text-sm font-medium text-gray-700">Método de Contato</label> <select id="contactMethod" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione o método...</option> <option value="whatsapp">WhatsApp</option> <option value="email">Email</option> <option value="ligacao">Ligação</option> <option value="reuniao">Reunião</option> </select>
       </div>
       <div class="mb-4"><label for="contactMessage" class="block text-sm font-medium text-gray-700">Mensagem/Assunto</label> <textarea id="contactMessage" rows="4" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="Digite a mensagem para os vendedores..."></textarea>
       </div>
       <div class="mb-4"><label for="targetSellers" class="block text-sm font-medium text-gray-700">Vendedores</label> <select id="targetSellers" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione...</option> <option value="baixa_performance">Vendedores com baixa performance</option> <option value="leads_pendentes">Vendedores com leads pendentes</option> <option value="todos">Todos os vendedores</option> </select>
       </div>
       <div class="flex justify-end space-x-3"><button type="button" id="cancelContactSellersBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Cancelar </button> <button type="submit" id="confirmContactSellersBtn" class="px-4 py-2 bg-green-600 text-white rounded-md hover:bg-green-700"> Enviar Contato </button>
       </div>
      </form>
     </div>
    </div>
   </div><!-- Return Contact Modal -->
   <div id="returnContactModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-20 mx-auto p-5 border w-full max-w-md shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">Devolver Contato ao Estrategista</h3>
      <form id="returnContactForm">
       <div class="mb-4"><label for="returnReason" class="block text-sm font-medium text-gray-700">Motivo da Devolução *</label> <select id="returnReason" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione o motivo...</option> <option value="cliente_nao_responde">Cliente não responde</option> <option value="numero_incorreto">Número incorreto/inexistente</option> <option value="cliente_desinteressado">Cliente totalmente desinteressado</option> <option value="fora_perfil">Cliente fora do perfil</option> <option value="informacoes_incorretas">Informações do lead incorretas</option> <option value="cliente_ja_comprou">Cliente já comprou em outro lugar</option> <option value="outros">Outros motivos</option> </select>
       </div>
       <div class="mb-4"><label for="returnDetails" class="block text-sm font-medium text-gray-700">Detalhes do Motivo *</label> <textarea id="returnDetails" rows="4" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="Descreva detalhadamente o motivo da devolução..."></textarea>
       </div>
       <div class="mb-4"><label for="returnAttempts" class="block text-sm font-medium text-gray-700">Tentativas de Contato Realizadas</label> <input id="returnAttempts" type="number" min="0" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="Quantas vezes tentou contato?">
       </div>
       <div class="flex justify-end space-x-3"><button type="button" id="cancelReturnContactBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Cancelar </button> <button type="submit" id="confirmReturnContactBtn" class="px-4 py-2 bg-orange-600 text-white rounded-md hover:bg-orange-700"> Devolver Contato </button>
       </div>
      </form>
     </div>
    </div>
   </div><!-- Lost Sale Reason Modal -->
   <div id="lostSaleModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-20 mx-auto p-5 border w-full max-w-md shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">Justificar Venda Perdida</h3>
      <form id="lostSaleForm">
       <div class="mb-4"><label for="lostSaleReason" class="block text-sm font-medium text-gray-700">Motivo da Perda *</label> <select id="lostSaleReason" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione o motivo...</option> <option value="preco_alto">Preço muito alto</option> <option value="concorrencia">Comprou da concorrência</option> <option value="prazo_entrega">Prazo de entrega inadequado</option> <option value="condicoes_pagamento">Condições de pagamento</option> <option value="qualidade_produto">Dúvidas sobre qualidade</option> <option value="atendimento">Problemas no atendimento</option> <option value="mudou_ideia">Cliente mudou de ideia</option> <option value="orcamento_insuficiente">Orçamento insuficiente</option> <option value="outros">Outros motivos</option> </select>
       </div>
       <div class="mb-4"><label for="lostSaleDetails" class="block text-sm font-medium text-gray-700">Detalhes da Perda *</label> <textarea id="lostSaleDetails" rows="4" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="Descreva detalhadamente o que aconteceu..."></textarea>
       </div>
       <div class="mb-4"><label for="competitorInfo" class="block text-sm font-medium text-gray-700">Informações da Concorrência (se aplicável)</label> <textarea id="competitorInfo" rows="2" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="Preço, condições, empresa..."></textarea>
       </div>
       <div class="flex justify-end space-x-3"><button type="button" id="cancelLostSaleBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Cancelar </button> <button type="submit" id="confirmLostSaleBtn" class="px-4 py-2 bg-red-600 text-white rounded-md hover:bg-red-700"> Confirmar Perda </button>
       </div>
      </form>
     </div>
    </div>
   </div><!-- Assistant Lost Sale Review Modal -->
   <div id="assistantLostSaleModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-10 mx-auto p-5 border w-full max-w-2xl shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">Revisar Venda Perdida</h3>
      <div id="lostSaleReviewContent" class="mb-6"><!-- Content will be populated dynamically -->
      </div>
      <form id="assistantLostSaleForm">
       <div class="mb-4"><label for="assistantContactMethod" class="block text-sm font-medium text-gray-700">Método de Contato com Cliente</label> <select id="assistantContactMethod" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione...</option> <option value="whatsapp">WhatsApp</option> <option value="ligacao">Ligação</option> <option value="email">Email</option> <option value="nao_conseguiu_contato">Não conseguiu contato</option> </select>
       </div>
       <div class="mb-4"><label for="clientConfirmation" class="block text-sm font-medium text-gray-700">Confirmação do Cliente</label> <select id="clientConfirmation" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione...</option> <option value="confirmou_motivo">Cliente confirmou o motivo</option> <option value="motivo_diferente">Cliente informou motivo diferente</option> <option value="cliente_interessado">Cliente ainda tem interesse</option> <option value="nao_respondeu">Cliente não respondeu</option> </select>
       </div>
       <div class="mb-4"><label for="assistantReport" class="block text-sm font-medium text-gray-700">Relatório da Revisão *</label> <textarea id="assistantReport" rows="5" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="Descreva o que aconteceu no contato com o cliente, se confirmou o motivo da perda, e suas conclusões..."></textarea>
       </div>
       <div class="mb-4"><label for="assistantRecommendation" class="block text-sm font-medium text-gray-700">Recomendações</label> <textarea id="assistantRecommendation" rows="3" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500" placeholder="Recomendações para melhorar o processo de vendas..."></textarea>
       </div>
       <div class="flex justify-end space-x-3"><button type="button" id="cancelAssistantLostSaleBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Cancelar </button> <button type="submit" id="confirmAssistantLostSaleBtn" class="px-4 py-2 bg-blue-600 text-white rounded-md hover:bg-blue-700"> Finalizar Revisão </button>
       </div>
      </form>
     </div>
    </div>
   </div><!-- Edit Store Modal -->
   <div id="editStoreModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-20 mx-auto p-5 border w-full max-w-md shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">Editar Loja</h3>
      <form id="editStoreForm" class="space-y-4">
       <div><label for="editStoreName" class="block text-sm font-medium text-gray-700">Nome da Loja</label> <input id="editStoreName" type="text" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
       </div>
       <div><label for="editStoreType" class="block text-sm font-medium text-gray-700">Tipo</label> <select id="editStoreType" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione...</option> <option value="matriz">Matriz</option> <option value="filial">Filial</option> </select>
       </div>
       <div><label for="editStoreAddress" class="block text-sm font-medium text-gray-700">Endereço</label> <input id="editStoreAddress" type="text" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
       </div>
       <div class="flex justify-end space-x-3"><button type="button" id="cancelEditStoreBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Cancelar </button> <button type="submit" id="confirmEditStoreBtn" class="px-4 py-2 bg-blue-600 text-white rounded-md hover:bg-blue-700"> Salvar Alterações </button>
       </div>
      </form>
     </div>
    </div>
   </div><!-- Edit User Modal -->
   <div id="editUserModal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full z-50">
    <div class="relative top-20 mx-auto p-5 border w-full max-w-md shadow-lg rounded-md bg-white">
     <div class="mt-3">
      <h3 class="text-lg font-medium text-gray-900 mb-4">Editar Usuário</h3>
      <form id="editUserForm" class="space-y-4">
       <div><label for="editUserName" class="block text-sm font-medium text-gray-700">Nome Completo</label> <input id="editUserName" type="text" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
       </div>
       <div><label for="editUserEmail" class="block text-sm font-medium text-gray-700">Email (opcional)</label> <input id="editUserEmail" type="email" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
       </div>
       <div><label for="editUserPassword" class="block text-sm font-medium text-gray-700">Nova Senha (deixe em branco para manter a atual)</label> <input id="editUserPassword" type="password" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500">
       </div>
       <div><label for="editUserRole" class="block text-sm font-medium text-gray-700">Tipo de Usuário</label> <select id="editUserRole" required class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500"> <option value="">Selecione...</option> <option value="admin">Administrador</option> <option value="seller">Vendedor</option> <option value="assistant">Assistente de Vendas</option> </select>
       </div>
       <div class="flex justify-end space-x-3"><button type="button" id="cancelEditUserBtn" class="px-4 py-2 text-gray-600 border border-gray-300 rounded-md hover:bg-gray-50"> Cancelar </button> <button type="submit" id="confirmEditUserBtn" class="px-4 py-2 bg-blue-600 text-white rounded-md hover:bg-blue-700"> Salvar Alterações </button>
       </div>
      </form>
     </div>
    </div>
   </div>
  </div>
  <script>
        // Global variables
        let currentUser = null;
        let allData = [];
        let currentContactToConvert = null;
        let currentContactToUpdate = null;
        let currentContactToReturn = null;
        let currentContactForLostSale = null;
        let currentLostSaleToReview = null;
        let currentCampaignForAd = null;
        let currentAdToUpdate = null;
        let currentContactForReminder = null;
        let currentReminderToComplete = null;
        let currentStoreToEdit = null;

        // Default configuration
        const defaultConfig = {
            company_name: "Sistema de Vendas Aço",
            company_logo: "",
            admin_title: "Painel Administrativo", 
            seller_title: "Meu Desempenho",
            primary_color: "#2563eb",
            secondary_color: "#ffffff",
            commission_rate: 1.0
        };

        // Data handler for SDK
        const dataHandler = {
            onDataChanged(data) {
                allData = data;
                updateUI();
                
                // Create default admin if needed (only on first data load)
                if (data.length === 0) {
                    createDefaultAdmin();
                }
            }
        };

        // Initialize SDKs
        async function initializeApp() {
            try {
                // Initialize Data SDK
                if (window.dataSdk) {
                    const result = await window.dataSdk.init(dataHandler);
                    if (!result.isOk) {
                        console.error("Failed to initialize data SDK");
                    }
                }

                // Initialize Element SDK
                if (window.elementSdk) {
                    await window.elementSdk.init({
                        defaultConfig,
                        onConfigChange: async (config) => {
                            document.getElementById('companyName').textContent = config.company_name || defaultConfig.company_name;
                            document.getElementById('adminTitle').textContent = config.admin_title || defaultConfig.admin_title;
                            document.getElementById('sellerTitle').textContent = config.seller_title || defaultConfig.seller_title;
                            
                            // Update company logo
                            const logoUrl = config.company_logo || defaultConfig.company_logo;
                            const logoImg = document.getElementById('companyLogoImg');
                            const defaultIcon = document.getElementById('defaultLogoIcon');
                            
                            if (logoUrl && logoUrl.trim()) {
                                logoImg.src = logoUrl;
                                logoImg.style.display = 'block';
                                logoImg.classList.remove('hidden');
                                defaultIcon.style.display = 'none';
                            } else {
                                logoImg.style.display = 'none';
                                logoImg.classList.add('hidden');
                                defaultIcon.style.display = 'block';
                            }
                            
                            // Apply colors
                            const primaryColor = config.primary_color || defaultConfig.primary_color;
                            const secondaryColor = config.secondary_color || defaultConfig.secondary_color;
                            
                            document.documentElement.style.setProperty('--primary-color', primaryColor);
                            document.documentElement.style.setProperty('--secondary-color', secondaryColor);
                        },
                        mapToCapabilities: (config) => ({
                            recolorables: [
                                {
                                    get: () => config.primary_color || defaultConfig.primary_color,
                                    set: (value) => {
                                        if (window.elementSdk) {
                                            window.elementSdk.setConfig({ primary_color: value });
                                        }
                                    }
                                },
                                {
                                    get: () => config.secondary_color || defaultConfig.secondary_color,
                                    set: (value) => {
                                        if (window.elementSdk) {
                                            window.elementSdk.setConfig({ secondary_color: value });
                                        }
                                    }
                                }
                            ],
                            borderables: [],
                            fontEditable: undefined,
                            fontSizeable: undefined
                        }),
                        mapToEditPanelValues: (config) => new Map([
                            ["company_name", config.company_name || defaultConfig.company_name],
                            ["company_logo", config.company_logo || defaultConfig.company_logo],
                            ["admin_title", config.admin_title || defaultConfig.admin_title],
                            ["seller_title", config.seller_title || defaultConfig.seller_title]
                        ])
                    });
                }

                // Setup event listeners
                setupEventListeners();
                
                // Initialize UI with default values
                updateInitialUI();
                
            } catch (error) {
                console.error("Error initializing app:", error);
                // Continue with basic functionality even if SDKs fail
                setupEventListeners();
                updateInitialUI();
            }
        }

        // Initialize app when page loads
        document.addEventListener('DOMContentLoaded', initializeApp);

        // Motivational phrases system
        const motivationalPhrases = [
            {
                main: "✨ O sucesso é construído dia após dia",
                sub: "Cada esforço de hoje é um tijolo no seu futuro"
            },
            {
                main: "🌟 Persistência é o caminho da realização",
                sub: "Grandes conquistas nascem de pequenos passos diários"
            },
            {
                main: "🎯 Foque no progresso, não na perfeição",
                sub: "Cada dia melhor que ontem é uma vitória"
            },
            {
                main: "💎 Seu potencial se revela no esforço constante",
                sub: "A excelência é um hábito, não um acidente"
            },
            {
                main: "🚀 Sonhos se tornam realidade com dedicação",
                sub: "O trabalho árduo de hoje é o sucesso de amanhã"
            },
            {
                main: "🌱 Crescimento acontece fora da zona de conforto",
                sub: "Desafios são oportunidades disfarçadas"
            },
            {
                main: "⭐ Acredite no poder da sua determinação",
                sub: "Você é mais forte do que imagina"
            },
            {
                main: "🏆 Vencedores são feitos de disciplina diária",
                sub: "Consistência é a mãe de todas as conquistas"
            },
            {
                main: "💪 Sua jornada é única e valiosa",
                sub: "Cada passo te aproxima dos seus objetivos"
            },
            {
                main: "🌈 Oportunidades surgem para quem se prepara",
                sub: "O sucesso encontra quem nunca para de tentar"
            },
            {
                main: "🔥 Paixão pelo que faz move montanhas",
                sub: "Amor pelo trabalho transforma esforço em prazer"
            },
            {
                main: "⚡ Energia positiva atrai resultados positivos",
                sub: "Sua atitude determina sua altitude"
            },
            {
                main: "🎪 Transforme desafios em trampolins",
                sub: "Obstáculos são degraus para o próximo nível"
            },
            {
                main: "🌟 Seja a mudança que quer ver no mundo",
                sub: "Liderança começa com o exemplo pessoal"
            },
            {
                main: "💫 O futuro pertence aos que acreditam",
                sub: "Fé em si mesmo é o primeiro passo para o sucesso"
            }
        ];

        // Function to set random motivational phrase
        function setRandomMotivationalPhrase() {
            const randomIndex = Math.floor(Math.random() * motivationalPhrases.length);
            const phrase = motivationalPhrases[randomIndex];
            
            document.getElementById('phraseText').textContent = phrase.main;
            document.getElementById('phraseSubtext').textContent = phrase.sub;
        }

        // Set random phrase on page load
        document.addEventListener('DOMContentLoaded', () => {
            setRandomMotivationalPhrase();
            initializeApp();
        });

        // Create default admin user on first load
        async function createDefaultAdmin() {
            // This function is now handled by ensureAdminExists in login
            return;
        }

        // Update initial UI with default values
        function updateInitialUI() {
            document.getElementById('companyName').textContent = defaultConfig.company_name;
            document.getElementById('adminTitle').textContent = defaultConfig.admin_title;
            document.getElementById('sellerTitle').textContent = defaultConfig.seller_title;
            
            // Update company logo
            const logoUrl = defaultConfig.company_logo;
            const logoImg = document.getElementById('companyLogoImg');
            const defaultIcon = document.getElementById('defaultLogoIcon');
            
            if (logoUrl && logoUrl.trim()) {
                logoImg.src = logoUrl;
                logoImg.style.display = 'block';
                logoImg.classList.remove('hidden');
                defaultIcon.style.display = 'none';
            } else {
                logoImg.style.display = 'none';
                logoImg.classList.add('hidden');
                defaultIcon.style.display = 'block';
            }
            
            // Populate selects with empty options initially
            updateStoreSelects();
            updateCampaignSelects();
            updateSellerSelects();
        }

        // Setup event listeners
        function setupEventListeners() {
            // Login form
            document.getElementById('loginForm').addEventListener('submit', handleLogin);
            

            
            // Logout buttons
            document.getElementById('adminLogoutBtn').addEventListener('click', logout);
            document.getElementById('sellerLogoutBtn').addEventListener('click', logout);
            document.getElementById('assistantLogoutBtn').addEventListener('click', logout);
            
            // Contact form
            document.getElementById('contactForm').addEventListener('submit', handleAddContact);
            
            // Convert modal
            document.getElementById('cancelConvertBtn').addEventListener('click', closeConvertModal);
            document.getElementById('convertForm').addEventListener('submit', handleConvertSale);
            
            // Update status modal
            document.getElementById('cancelStatusBtn').addEventListener('click', closeUpdateStatusModal);
            document.getElementById('updateStatusForm').addEventListener('submit', handleUpdateStatus);
            
            // Goals modal
            document.getElementById('setGoalsBtn').addEventListener('click', showGoalsModal);
            document.getElementById('cancelGoalsBtn').addEventListener('click', closeGoalsModal);
            document.getElementById('goalsForm').addEventListener('submit', handleSetGoals);
            
            // Stores modal
            document.getElementById('manageStoresBtn').addEventListener('click', showStoresModal);
            document.getElementById('closeStoresBtn').addEventListener('click', closeStoresModal);
            document.getElementById('addStoreForm').addEventListener('submit', handleAddStore);
            
            // Campaigns modal
            document.getElementById('manageCampaignsBtn').addEventListener('click', showCampaignsModal);
            document.getElementById('closeCampaignsBtn').addEventListener('click', closeCampaignsModal);
            document.getElementById('addCampaignForm').addEventListener('submit', handleAddCampaign);
            
            // Ads modal
            document.getElementById('cancelAddAdBtn').addEventListener('click', closeAddAdModal);
            document.getElementById('addAdForm').addEventListener('submit', handleAddAd);
            
            // Update ad budget modal
            document.getElementById('cancelUpdateBudgetBtn').addEventListener('click', closeUpdateAdBudgetModal);
            document.getElementById('updateAdBudgetForm').addEventListener('submit', handleUpdateAdBudget);
            
            // Commission modal
            document.getElementById('setCommissionBtn').addEventListener('click', showCommissionModal);
            document.getElementById('cancelCommissionBtn').addEventListener('click', closeCommissionModal);
            document.getElementById('commissionForm').addEventListener('submit', handleSetCommission);
            
            // User management modal
            document.getElementById('addUserBtn').addEventListener('click', showAddUserModal);
            document.getElementById('cancelAddUserBtn').addEventListener('click', closeAddUserModal);
            document.getElementById('addUserForm').addEventListener('submit', handleAddUser);
            
            // Edit store modal
            document.getElementById('cancelEditStoreBtn').addEventListener('click', closeEditStoreModal);
            document.getElementById('editStoreForm').addEventListener('submit', handleEditStore);
            
            // Edit user modal
            document.getElementById('cancelEditUserBtn').addEventListener('click', closeEditUserModal);
            document.getElementById('editUserForm').addEventListener('submit', handleEditUser);
            
            // Assistant functionality
            document.getElementById('leadForm').addEventListener('submit', handleAddLead);
            
            // Assistant follow-up functionality
            document.getElementById('viewPendingLeadsBtn').addEventListener('click', showPendingLeadsModal);
            document.getElementById('sendRemarketingBtn').addEventListener('click', showRemarketingModal);
            document.getElementById('contactSellersBtn').addEventListener('click', showContactSellersModal);
            
            // Modal close buttons
            document.getElementById('closePendingLeadsBtn').addEventListener('click', closePendingLeadsModal);
            document.getElementById('cancelRemarketingBtn').addEventListener('click', closeRemarketingModal);
            document.getElementById('cancelContactSellersBtn').addEventListener('click', closeContactSellersModal);
            
            // Modal forms
            document.getElementById('remarketingForm').addEventListener('submit', handleRemarketing);
            document.getElementById('contactSellersForm').addEventListener('submit', handleContactSellers);
            
            // Return contact modal
            document.getElementById('cancelReturnContactBtn').addEventListener('click', closeReturnContactModal);
            document.getElementById('returnContactForm').addEventListener('submit', handleReturnContact);
            
            // Lost sale modal
            document.getElementById('cancelLostSaleBtn').addEventListener('click', closeLostSaleModal);
            document.getElementById('lostSaleForm').addEventListener('submit', handleLostSale);
            
            // Assistant lost sale review modal
            document.getElementById('cancelAssistantLostSaleBtn').addEventListener('click', closeAssistantLostSaleModal);
            document.getElementById('assistantLostSaleForm').addEventListener('submit', handleAssistantLostSaleReview);
            
            // Reminder modals
            document.getElementById('cancelReminderBtn').addEventListener('click', closeSetReminderModal);
            document.getElementById('setReminderForm').addEventListener('submit', handleSetReminder);
            document.getElementById('cancelCompleteReminderBtn').addEventListener('click', closeCompleteReminderModal);
            document.getElementById('completeReminderForm').addEventListener('submit', handleCompleteReminder);
        }

        // Utility functions
        function generateId() {
            return Date.now().toString(36) + Math.random().toString(36).substr(2);
        }

        function showMessage(message, type = 'info') {
            // Create toast message
            const toast = document.createElement('div');
            toast.className = `fixed top-4 right-4 z-50 px-4 py-2 rounded-md text-white font-medium ${
                type === 'success' ? 'bg-green-600' : 
                type === 'error' ? 'bg-red-600' : 
                'bg-blue-600'
            }`;
            toast.textContent = message;
            
            document.body.appendChild(toast);
            
            // Remove after 3 seconds
            setTimeout(() => {
                if (toast.parentNode) {
                    toast.parentNode.removeChild(toast);
                }
            }, 3000);
        }

        // Authentication functions
        async function handleLogin(e) {
            e.preventDefault();
            const name = document.getElementById('loginName').value.trim();
            const password = document.getElementById('loginPassword').value;
            
            const loginBtn = document.getElementById('loginBtn');
            loginBtn.classList.add('loading');
            loginBtn.textContent = 'Entrando...';
            
            // Ensure admin user exists first
            await ensureAdminExists();
            
            // Wait a moment to ensure data is loaded
            await new Promise(resolve => setTimeout(resolve, 300));
            
            const users = allData.filter(item => item.type === 'user' && item.active);
            console.log('Available users:', users.map(u => ({ name: u.name, role: u.role, id: u.id })));
            
            const user = users.find(u => u.name === name && u.password === password);
            
            if (user) {
                currentUser = user;
                console.log('Logged in user:', currentUser);
                showMessage(`Bem-vindo, ${user.name}!`, 'success');
                showDashboard(user.role);
                document.getElementById('loginForm').reset();
            } else {
                showMessage(`Login inválido. Credenciais: mau/admin123 ou geo/geo123`, 'error');
            }
            
            loginBtn.classList.remove('loading');
            loginBtn.textContent = 'Entrar';
        }

        // Ensure admin user exists
        async function ensureAdminExists() {
            if (!window.dataSdk) return;
            
            const users = allData.filter(item => item.type === 'user');
            const adminExists = users.find(u => u.name === 'mau' && u.role === 'admin');
            
            if (!adminExists) {
                const defaultAdmin = {
                    id: generateId(),
                    type: 'user',
                    name: 'mau',
                    email: 'admin@sistema.com',
                    password: 'admin123',
                    role: 'admin',
                    active: true,
                    createdAt: new Date().toISOString()
                };
                
                await window.dataSdk.create(defaultAdmin);
            }
            
            // Ensure Geo user exists
            const geoExists = users.find(u => u.name === 'geo' && u.role === 'seller');
            if (!geoExists) {
                const geoUser = {
                    id: generateId(),
                    type: 'user',
                    name: 'geo',
                    email: 'geo@sistema.com',
                    password: 'geo123',
                    role: 'seller',
                    active: true,
                    createdAt: new Date().toISOString()
                };
                
                await window.dataSdk.create(geoUser);
            }
        }



        function logout() {
            currentUser = null;
            // Hide all dashboards first
            document.getElementById('adminDashboard').classList.add('hidden');
            document.getElementById('sellerDashboard').classList.add('hidden');
            document.getElementById('assistantDashboard').classList.add('hidden');
            // Show login screen
            document.getElementById('loginScreen').classList.remove('hidden');
        }

        function showDashboard(role) {
            // Hide all screens first
            document.getElementById('loginScreen').classList.add('hidden');
            document.getElementById('adminDashboard').classList.add('hidden');
            document.getElementById('sellerDashboard').classList.add('hidden');
            document.getElementById('assistantDashboard').classList.add('hidden');
            
            // Show the correct dashboard
            if (role === 'admin') {
                document.getElementById('adminDashboard').classList.remove('hidden');
                document.getElementById('adminUserName').textContent = currentUser.name;
                document.getElementById('adminAvatar').textContent = currentUser.name.charAt(0).toUpperCase();
                updateStoreSelects();
                updateCampaignSelects();
            } else if (role === 'assistant') {
                document.getElementById('assistantDashboard').classList.remove('hidden');
                document.getElementById('assistantUserName').textContent = currentUser.name;
                document.getElementById('assistantAvatar').textContent = currentUser.name.charAt(0).toUpperCase();
                updateSellerSelects();
                updateStoreSelects();
                updateCampaignSelects();
            } else {
                document.getElementById('sellerDashboard').classList.remove('hidden');
                document.getElementById('sellerUserName').textContent = currentUser.name;
                document.getElementById('sellerAvatar').textContent = currentUser.name.charAt(0).toUpperCase();
                updateStoreSelects();
                updateCampaignSelects();
            }
        }

        // Update store selects
        function updateStoreSelects() {
            const stores = allData.filter(item => item.type === 'store' && item.active);
            const storeSelects = [
                document.getElementById('contactStore'),
                document.getElementById('leadStore'),
                document.getElementById('saleStore')
            ];
            
            storeSelects.forEach(select => {
                if (select) {
                    select.innerHTML = '<option value="">Selecione a loja...</option>';
                    stores.forEach(store => {
                        const option = document.createElement('option');
                        option.value = store.id;
                        option.textContent = `${store.name} (${store.storeType})`;
                        select.appendChild(option);
                    });
                }
            });
        }

        // Update campaign selects
        function updateCampaignSelects() {
            const campaigns = allData.filter(item => item.type === 'campaign' && item.active);
            const campaignSelects = [
                document.getElementById('contactCampaign'),
                document.getElementById('leadCampaign')
            ];
            
            campaignSelects.forEach(select => {
                if (select) {
                    select.innerHTML = '<option value="">Selecione a campanha...</option>';
                    campaigns.forEach(campaign => {
                        const option = document.createElement('option');
                        option.value = campaign.id;
                        option.textContent = `${campaign.name} (${campaign.campaignType})`;
                        select.appendChild(option);
                    });
                }
            });
        }

        // Update seller selects for assistant
        function updateSellerSelects() {
            const sellers = allData.filter(item => item.type === 'user' && item.role === 'seller' && item.active);
            const sellerSelect = document.getElementById('assignToSeller');
            
            if (sellerSelect) {
                sellerSelect.innerHTML = '<option value="">Selecione o vendedor...</option>';
                
                sellers.forEach(seller => {
                    const option = document.createElement('option');
                    option.value = seller.id;
                    option.textContent = seller.name;
                    sellerSelect.appendChild(option);
                });
            }
        }

        // Contact management
        async function handleAddContact(e) {
            e.preventDefault();
            
            const addBtn = document.getElementById('addContactBtn');
            addBtn.classList.add('loading');
            addBtn.textContent = 'Adicionando...';
            
            const phone = document.getElementById('contactPhone').value.replace(/\D/g, '');
            
            // Check if phone already exists
            const existingContact = allData.find(item => 
                item.type === 'contact' && 
                item.contactPhone.replace(/\D/g, '') === phone
            );
            
            if (existingContact) {
                showMessage('Este número de telefone já está cadastrado no sistema!', 'error');
                addBtn.classList.remove('loading');
                addBtn.textContent = 'Adicionar Contato';
                return;
            }
            
            const newContact = {
                id: generateId(),
                type: 'contact',
                sellerId: currentUser.id,
                contactName: document.getElementById('contactName').value,
                contactEmail: document.getElementById('contactEmail').value || '',
                contactPhone: document.getElementById('contactPhone').value,
                product: document.getElementById('contactProduct').value,
                notes: document.getElementById('contactNotes').value,
                status: 'contato',
                clientStatus: document.getElementById('clientStatus').value,
                storeId: document.getElementById('contactStore').value || null,
                campaignId: document.getElementById('contactCampaign').value || null,
                budgetValue: parseFloat(document.getElementById('budgetValue').value) || 0,
                value: 0,
                createdAt: new Date().toISOString(),
                convertedAt: null,
                lastContactDate: new Date().toISOString()
            };
            
            if (window.dataSdk) {
                const result = await window.dataSdk.create(newContact);
                if (result.isOk) {
                    showMessage('Contato adicionado com sucesso!', 'success');
                    document.getElementById('contactForm').reset();
                } else {
                    showMessage('Erro ao adicionar contato', 'error');
                }
            }
            
            addBtn.classList.remove('loading');
            addBtn.textContent = 'Adicionar Contato';
        }

        // Assistant Lead Management
        async function handleAddLead(e) {
            e.preventDefault();
            
            const addBtn = document.getElementById('addLeadBtn');
            addBtn.classList.add('loading');
            addBtn.textContent = 'Adicionando...';
            
            const phone = document.getElementById('leadPhone').value.replace(/\D/g, '');
            
            // Check if phone already exists
            const existingContact = allData.find(item => 
                item.type === 'contact' && 
                item.contactPhone.replace(/\D/g, '') === phone
            );
            
            if (existingContact) {
                showMessage('Este número de telefone já está cadastrado no sistema!', 'error');
                addBtn.classList.remove('loading');
                addBtn.textContent = 'Adicionar Lead e Atribuir';
                return;
            }
            
            const newLead = {
                id: generateId(),
                type: 'contact',
                sellerId: document.getElementById('assignToSeller').value,
                assignedBy: currentUser.id,
                contactName: document.getElementById('leadName').value,
                contactEmail: document.getElementById('leadEmail').value || '',
                contactPhone: document.getElementById('leadPhone').value,
                product: document.getElementById('leadProduct').value,
                storeId: document.getElementById('leadStore').value || null,
                campaignId: document.getElementById('leadCampaign').value || null,
                budgetValue: parseFloat(document.getElementById('leadBudgetValue').value) || 0,
                notes: document.getElementById('leadNotes').value,
                status: 'contato',
                clientStatus: 'morno',
                value: 0,
                createdAt: new Date().toISOString(),
                convertedAt: null,
                lastContactDate: new Date().toISOString()
            };
            
            if (window.dataSdk) {
                const result = await window.dataSdk.create(newLead);
                if (result.isOk) {
                    showMessage('Lead adicionado e atribuído com sucesso!', 'success');
                    document.getElementById('leadForm').reset();
                } else {
                    showMessage('Erro ao adicionar lead', 'error');
                }
            }
            
            addBtn.classList.remove('loading');
            addBtn.textContent = 'Adicionar Lead e Atribuir';
        }

        // Modal functions
        function showGoalsModal() {
            document.getElementById('goalsModal').classList.remove('hidden');
        }

        function closeGoalsModal() {
            document.getElementById('goalsModal').classList.add('hidden');
            document.getElementById('goalsForm').reset();
        }

        function showStoresModal() {
            updateStoresTable();
            document.getElementById('storesModal').classList.remove('hidden');
        }

        function closeStoresModal() {
            document.getElementById('storesModal').classList.add('hidden');
            document.getElementById('addStoreForm').reset();
        }

        function showCommissionModal() {
            const currentRate = defaultConfig.commission_rate;
            document.getElementById('commissionRateInput').value = currentRate;
            document.getElementById('commissionModal').classList.remove('hidden');
        }

        function showCampaignsModal() {
            updateCampaignsAccordion();
            document.getElementById('campaignsModal').classList.remove('hidden');
        }

        function closeCampaignsModal() {
            document.getElementById('campaignsModal').classList.add('hidden');
            document.getElementById('addCampaignForm').reset();
        }

        function showAddAdModal(campaignId) {
            currentCampaignForAd = campaignId;
            document.getElementById('addAdModal').classList.remove('hidden');
        }

        function closeAddAdModal() {
            currentCampaignForAd = null;
            document.getElementById('addAdModal').classList.add('hidden');
            document.getElementById('addAdForm').reset();
        }

        function showUpdateAdBudgetModal(adId) {
            currentAdToUpdate = adId;
            const ad = allData.find(item => item.id === adId);
            if (ad) {
                document.getElementById('newDailyBudget').value = ad.dailyBudget;
            }
            document.getElementById('updateAdBudgetModal').classList.remove('hidden');
        }

        function closeUpdateAdBudgetModal() {
            currentAdToUpdate = null;
            document.getElementById('updateAdBudgetModal').classList.add('hidden');
            document.getElementById('updateAdBudgetForm').reset();
        }

        function closeCommissionModal() {
            document.getElementById('commissionModal').classList.add('hidden');
            document.getElementById('commissionForm').reset();
        }

        function showAddUserModal() {
            document.getElementById('addUserModal').classList.remove('hidden');
        }

        function closeAddUserModal() {
            document.getElementById('addUserModal').classList.add('hidden');
            document.getElementById('addUserForm').reset();
        }

        let currentUserToEdit = null;

        function showEditUserModal(userId) {
            const user = allData.find(item => item.id === userId);
            if (!user) return;
            
            currentUserToEdit = user;
            
            // Populate form with current user data
            document.getElementById('editUserName').value = user.name;
            document.getElementById('editUserEmail').value = user.email || '';
            document.getElementById('editUserPassword').value = '';
            document.getElementById('editUserRole').value = user.role;
            
            document.getElementById('editUserModal').classList.remove('hidden');
        }

        function showEditStoreModal(storeId) {
            const store = allData.find(item => item.id === storeId);
            if (!store) return;
            
            currentStoreToEdit = store;
            
            // Populate form with current store data
            document.getElementById('editStoreName').value = store.name;
            document.getElementById('editStoreType').value = store.storeType;
            document.getElementById('editStoreAddress').value = store.address;
            
            document.getElementById('editStoreModal').classList.remove('hidden');
        }

        function closeEditStoreModal() {
            currentStoreToEdit = null;
            document.getElementById('editStoreModal').classList.add('hidden');
            document.getElementById('editStoreForm').reset();
        }

        function closeEditUserModal() {
            currentUserToEdit = null;
            document.getElementById('editUserModal').classList.add('hidden');
            document.getElementById('editUserForm').reset();
        }

        function showConvertModal(contactId) {
            currentContactToConvert = contactId;
            updateStoreSelects();
            document.getElementById('convertModal').classList.remove('hidden');
        }

        function closeConvertModal() {
            currentContactToConvert = null;
            document.getElementById('convertModal').classList.add('hidden');
            document.getElementById('convertForm').reset();
        }

        function showUpdateStatusModal(contactId) {
            currentContactToUpdate = contactId;
            const contact = allData.find(item => item.id === contactId);
            if (contact) {
                document.getElementById('newClientStatus').value = contact.clientStatus;
            }
            document.getElementById('updateStatusModal').classList.remove('hidden');
        }

        function closeUpdateStatusModal() {
            currentContactToUpdate = null;
            document.getElementById('updateStatusModal').classList.add('hidden');
            document.getElementById('updateStatusForm').reset();
        }

        // Handle functions
        async function handleSetGoals(e) {
            e.preventDefault();
            
            const confirmBtn = document.getElementById('confirmGoalsBtn');
            confirmBtn.classList.add('loading');
            confirmBtn.textContent = 'Salvando...';
            
            const generalGoal = parseInt(document.getElementById('generalGoalInput').value);
            const individualGoal = parseInt(document.getElementById('individualGoalInput').value);
            
            const newGoal = {
                id: generateId(),
                type: 'goal',
                generalGoal: generalGoal,
                individualGoal: individualGoal,
                month: new Date().getMonth(),
                year: new Date().getFullYear(),
                createdAt: new Date().toISOString()
            };
            
            if (window.dataSdk) {
                const result = await window.dataSdk.create(newGoal);
                if (result.isOk) {
                    showMessage('Metas definidas com sucesso!', 'success');
                    closeGoalsModal();
                } else {
                    showMessage('Erro ao definir metas', 'error');
                }
            }
            
            confirmBtn.classList.remove('loading');
            confirmBtn.textContent = 'Salvar Metas';
        }

        async function handleAddStore(e) {
            e.preventDefault();
            
            const addBtn = document.getElementById('addStoreBtn');
            addBtn.classList.add('loading');
            addBtn.textContent = 'Adicionando...';
            
            const newStore = {
                id: generateId(),
                type: 'store',
                name: document.getElementById('storeName').value,
                storeType: document.getElementById('storeType').value,
                address: document.getElementById('storeAddress').value,
                active: true,
                createdAt: new Date().toISOString()
            };
            
            if (window.dataSdk) {
                const result = await window.dataSdk.create(newStore);
                if (result.isOk) {
                    showMessage('Loja adicionada com sucesso!', 'success');
                    document.getElementById('addStoreForm').reset();
                    updateStoresTable();
                    updateStoreSelects();
                } else {
                    showMessage('Erro ao adicionar loja', 'error');
                }
            }
            
            addBtn.classList.remove('loading');
            addBtn.textContent = 'Adicionar Loja';
        }

        async function handleAddCampaign(e) {
            e.preventDefault();
            
            const addBtn = document.getElementById('addCampaignBtn');
            addBtn.classList.add('loading');
            addBtn.textContent = 'Adicionando...';
            
            const newCampaign = {
                id: generateId(),
                type: 'campaign',
                name: document.getElementById('campaignName').value,
                campaignType: document.getElementById('campaignType').value,
                description: document.getElementById('campaignDescription').value || '',
                startDate: document.getElementById('campaignStartDate').value,
                endDate: document.getElementById('campaignEndDate').value || null,
                leadGoal: parseInt(document.getElementById('campaignGoal').value) || 0,
                active: true,
                createdAt: new Date().toISOString()
            };
            
            if (window.dataSdk) {
                const result = await window.dataSdk.create(newCampaign);
                if (result.isOk) {
                    showMessage('Campanha adicionada com sucesso!', 'success');
                    document.getElementById('addCampaignForm').reset();
                    updateCampaignsAccordion();
                    updateCampaignSelects();
                } else {
                    showMessage('Erro ao adicionar campanha', 'error');
                }
            }
            
            addBtn.classList.remove('loading');
            addBtn.textContent = 'Adicionar Campanha';
        }

        async function handleAddAd(e) {
            e.preventDefault();
            
            if (!currentCampaignForAd) return;
            
            const addBtn = document.getElementById('confirmAddAdBtn');
            addBtn.classList.add('loading');
            addBtn.textContent = 'Adicionando...';
            
            const newAd = {
                id: generateId(),
                type: 'ad',
                campaignId: currentCampaignForAd,
                adName: document.getElementById('adName').value,
                adType: document.getElementById('adType').value,
                adAudience: document.getElementById('adAudience').value,
                dailyBudget: parseFloat(document.getElementById('adDailyBudget').value),
                startDate: document.getElementById('adStartDate').value,
                endDate: document.getElementById('adEndDate').value || null,
                description: document.getElementById('adDescription').value || '',
                totalSpent: 0,
                impressions: 0,
                clicks: 0,
                ctr: 0,
                cpc: 0,
                cpl: 0,
                budgetHistory: JSON.stringify([{
                    date: new Date().toISOString(),
                    budget: parseFloat(document.getElementById('adDailyBudget').value),
                    reason: 'Criação do anúncio',
                    notes: 'Anúncio criado com orçamento inicial'
                }]),
                active: true,
                createdAt: new Date().toISOString()
            };
            
            if (window.dataSdk) {
                const result = await window.dataSdk.create(newAd);
                if (result.isOk) {
                    showMessage('Anúncio adicionado com sucesso!', 'success');
                    closeAddAdModal();
                    updateCampaignsAccordion();
                } else {
                    showMessage('Erro ao adicionar anúncio', 'error');
                }
            }
            
            addBtn.classList.remove('loading');
            addBtn.textContent = 'Adicionar Anúncio';
        }

        async function handleUpdateAdBudget(e) {
            e.preventDefault();
            
            if (!currentAdToUpdate) return;
            
            const confirmBtn = document.getElementById('confirmUpdateBudgetBtn');
            confirmBtn.classList.add('loading');
            confirmBtn.textContent = 'Atualizando...';
            
            const ad = allData.find(item => item.id === currentAdToUpdate);
            if (ad) {
                const newBudget = parseFloat(document.getElementById('newDailyBudget').value);
                const reason = document.getElementById('budgetChangeReason').value;
                const notes = document.getElementById('budgetNotes').value;
                
                // Update budget history
                let budgetHistory = [];
                try {
                    budgetHistory = JSON.parse(ad.budgetHistory || '[]');
                } catch (e) {
                    budgetHistory = [];
                }
                
                budgetHistory.push({
                    date: new Date().toISOString(),
                    oldBudget: ad.dailyBudget,
                    newBudget: newBudget,
                    reason: reason,
                    notes: notes || ''
                });
                
                const updatedAd = {
                    ...ad,
                    dailyBudget: newBudget,
                    budgetHistory: JSON.stringify(budgetHistory),
                    active: newBudget > 0 // Pause ad if budget is 0
                };
                
                if (window.dataSdk) {
                    const result = await window.dataSdk.update(updatedAd);
                    if (result.isOk) {
                        const actionText = newBudget > ad.dailyBudget ? 'escalado' : 
                                         newBudget === 0 ? 'pausado' : 'reduzido';
                        showMessage(`Orçamento do anúncio ${actionText} com sucesso!`, 'success');
                        closeUpdateAdBudgetModal();
                        updateCampaignsAccordion();
                    } else {
                        showMessage('Erro ao atualizar orçamento', 'error');
                    }
                }
            }
            
            confirmBtn.classList.remove('loading');
            confirmBtn.textContent = 'Atualizar Orçamento';
        }

        async function handleSetCommission(e) {
            e.preventDefault();
            
            const confirmBtn = document.getElementById('confirmCommissionBtn');
            confirmBtn.classList.add('loading');
            confirmBtn.textContent = 'Salvando...';
            
            const newRate = parseFloat(document.getElementById('commissionRateInput').value);
            
            // Update default config
            defaultConfig.commission_rate = newRate;
            
            // Update Element SDK config if available
            if (window.elementSdk) {
                await window.elementSdk.setConfig({ commission_rate: newRate });
            }
            
            showMessage('Taxa de comissão atualizada com sucesso!', 'success');
            closeCommissionModal();
            
            confirmBtn.classList.remove('loading');
            confirmBtn.textContent = 'Salvar Taxa';
        }

        async function handleAddUser(e) {
            e.preventDefault();
            
            const confirmBtn = document.getElementById('confirmAddUserBtn');
            confirmBtn.classList.add('loading');
            confirmBtn.textContent = 'Cadastrando...';
            
            const name = document.getElementById('newUserName').value;
            const email = document.getElementById('newUserEmail').value;
            const password = document.getElementById('newUserPassword').value;
            const role = document.getElementById('newUserRole').value;
            
            // Check if name already exists
            const users = allData.filter(item => item.type === 'user');
            if (users.find(u => u.name === name)) {
                showMessage('Nome já cadastrado no sistema', 'error');
                confirmBtn.classList.remove('loading');
                confirmBtn.textContent = 'Cadastrar Usuário';
                return;
            }
            
            const newUser = {
                id: generateId(),
                type: 'user',
                name,
                email: email || '',
                password,
                role,
                active: true,
                createdAt: new Date().toISOString()
            };
            
            if (window.dataSdk) {
                const result = await window.dataSdk.create(newUser);
                if (result.isOk) {
                    showMessage('Usuário cadastrado com sucesso!', 'success');
                    closeAddUserModal();
                } else {
                    showMessage('Erro ao cadastrar usuário', 'error');
                }
            }
            
            confirmBtn.classList.remove('loading');
            confirmBtn.textContent = 'Cadastrar Usuário';
        }

        async function handleEditStore(e) {
            e.preventDefault();
            
            if (!currentStoreToEdit) return;
            
            const confirmBtn = document.getElementById('confirmEditStoreBtn');
            confirmBtn.classList.add('loading');
            confirmBtn.textContent = 'Salvando...';
            
            const name = document.getElementById('editStoreName').value;
            const storeType = document.getElementById('editStoreType').value;
            const address = document.getElementById('editStoreAddress').value;
            
            // Check if name already exists (excluding current store)
            const stores = allData.filter(item => item.type === 'store' && item.id !== currentStoreToEdit.id && item.active);
            if (stores.find(s => s.name === name)) {
                showMessage('Nome da loja já cadastrado no sistema', 'error');
                confirmBtn.classList.remove('loading');
                confirmBtn.textContent = 'Salvar Alterações';
                return;
            }
            
            // Prepare updated store data
            const updatedStore = {
                ...currentStoreToEdit,
                name,
                storeType,
                address
            };
            
            if (window.dataSdk) {
                const result = await window.dataSdk.update(updatedStore);
                if (result.isOk) {
                    showMessage('Loja atualizada com sucesso!', 'success');
                    closeEditStoreModal();
                    updateStoresTable();
                    updateStoreSelects();
                } else {
                    showMessage('Erro ao atualizar loja', 'error');
                }
            }
            
            confirmBtn.classList.remove('loading');
            confirmBtn.textContent = 'Salvar Alterações';
        }

        async function handleEditUser(e) {
            e.preventDefault();
            
            if (!currentUserToEdit) return;
            
            const confirmBtn = document.getElementById('confirmEditUserBtn');
            confirmBtn.classList.add('loading');
            confirmBtn.textContent = 'Salvando...';
            
            const name = document.getElementById('editUserName').value;
            const email = document.getElementById('editUserEmail').value;
            const password = document.getElementById('editUserPassword').value;
            const role = document.getElementById('editUserRole').value;
            
            // Check if name already exists (excluding current user)
            const users = allData.filter(item => item.type === 'user' && item.id !== currentUserToEdit.id);
            if (users.find(u => u.name === name)) {
                showMessage('Nome já cadastrado no sistema', 'error');
                confirmBtn.classList.remove('loading');
                confirmBtn.textContent = 'Salvar Alterações';
                return;
            }
            
            // Prepare updated user data
            const updatedUser = {
                ...currentUserToEdit,
                name,
                email: email || '',
                role
            };
            
            // Only update password if a new one was provided
            if (password.trim()) {
                updatedUser.password = password;
            }
            
            if (window.dataSdk) {
                const result = await window.dataSdk.update(updatedUser);
                if (result.isOk) {
                    showMessage('Usuário atualizado com sucesso!', 'success');
                    closeEditUserModal();
                    
                    // If editing current user, update current user data
                    if (currentUserToEdit.id === currentUser.id) {
                        currentUser = updatedUser;
                        // Update displayed name if needed
                        if (currentUser.role === 'admin') {
                            document.getElementById('adminUserName').textContent = currentUser.name;
                        } else if (currentUser.role === 'assistant') {
                            document.getElementById('assistantUserName').textContent = currentUser.name;
                        } else {
                            document.getElementById('sellerUserName').textContent = currentUser.name;
                        }
                    }
                } else {
                    showMessage('Erro ao atualizar usuário', 'error');
                }
            }
            
            confirmBtn.classList.remove('loading');
            confirmBtn.textContent = 'Salvar Alterações';
        }

        async function handleUpdateStatus(e) {
            e.preventDefault();
            
            if (!currentContactToUpdate) return;
            
            const newStatus = document.getElementById('newClientStatus').value;
            
            // Check if it's a lost sale that requires justification
            if (newStatus === 'venda_perdida') {
                closeUpdateStatusModal();
                showLostSaleModal(currentContactToUpdate);
                return;
            }
            
            const confirmBtn = document.getElementById('confirmStatusBtn');
            confirmBtn.classList.add('loading');
            confirmBtn.textContent = 'Atualizando...';
            
            const contact = allData.find(item => item.id === currentContactToUpdate);
            if (contact) {
                const statusNotes = document.getElementById('statusNotes').value;
                
                const updatedContact = {
                    ...contact,
                    clientStatus: newStatus,
                    lastContactDate: new Date().toISOString(),
                    notes: statusNotes ? `${contact.notes}\n\n${new Date().toLocaleDateString('pt-BR')}: ${statusNotes}` : contact.notes
                };
                
                if (window.dataSdk) {
                    const result = await window.dataSdk.update(updatedContact);
                    if (result.isOk) {
                        showMessage('Status do cliente atualizado com sucesso!', 'success');
                        closeUpdateStatusModal();
                    } else {
                        showMessage('Erro ao atualizar status do cliente', 'error');
                    }
                }
            }
            
            confirmBtn.classList.remove('loading');
            confirmBtn.textContent = 'Atualizar Status';
        }

        async function handleConvertSale(e) {
            e.preventDefault();
            
            if (!currentContactToConvert) return;
            
            const confirmBtn = document.getElementById('confirmConvertBtn');
            confirmBtn.classList.add('loading');
            confirmBtn.textContent = 'Convertendo...';
            
            const contact = allData.find(item => item.id === currentContactToConvert);
            if (contact) {
                const updatedContact = {
                    ...contact,
                    status: 'vendido',
                    value: parseFloat(document.getElementById('saleValue').value),
                    storeId: document.getElementById('saleStore').value,
                    orderNumber: document.getElementById('orderNumber').value,
                    notes: document.getElementById('saleNotes').value || contact.notes,
                    convertedAt: new Date().toISOString()
                };
                
                if (window.dataSdk) {
                    const result = await window.dataSdk.update(updatedContact);
                    if (result.isOk) {
                        showMessage('Venda convertida com sucesso!', 'success');
                        closeConvertModal();
                    } else {
                        showMessage('Erro ao converter venda', 'error');
                    }
                }
            }
            
            confirmBtn.classList.remove('loading');
            confirmBtn.textContent = 'Confirmar Venda';
        }

        // Assistant Modal Functions
        function showPendingLeadsModal() {
            updatePendingLeadsTable();
            document.getElementById('pendingLeadsModal').classList.remove('hidden');
        }

        function closePendingLeadsModal() {
            document.getElementById('pendingLeadsModal').classList.add('hidden');
        }

        function showRemarketingModal() {
            document.getElementById('remarketingModal').classList.remove('hidden');
        }

        function closeRemarketingModal() {
            document.getElementById('remarketingModal').classList.add('hidden');
            document.getElementById('remarketingForm').reset();
        }

        function showContactSellersModal() {
            document.getElementById('contactSellersModal').classList.remove('hidden');
        }

        function closeContactSellersModal() {
            document.getElementById('contactSellersModal').classList.add('hidden');
            document.getElementById('contactSellersForm').reset();
        }

        function showReturnContactModal(contactId) {
            currentContactToReturn = contactId;
            document.getElementById('returnContactModal').classList.remove('hidden');
        }

        function closeReturnContactModal() {
            currentContactToReturn = null;
            document.getElementById('returnContactModal').classList.add('hidden');
            document.getElementById('returnContactForm').reset();
        }

        function showLostSaleModal(contactId) {
            currentContactForLostSale = contactId;
            document.getElementById('lostSaleModal').classList.remove('hidden');
        }

        function closeLostSaleModal() {
            currentContactForLostSale = null;
            document.getElementById('lostSaleModal').classList.add('hidden');
            document.getElementById('lostSaleForm').reset();
        }

        function showAssistantLostSaleModal(lostSaleId) {
            currentLostSaleToReview = lostSaleId;
            
            // Populate review content
            const lostSale = allData.find(item => item.id === lostSaleId);
            const contact = allData.find(item => item.id === lostSale.contactId);
            const seller = allData.find(item => item.id === contact.sellerId);
            
            const reviewContent = document.getElementById('lostSaleReviewContent');
            reviewContent.innerHTML = `
                <div class="bg-red-50 border border-red-200 rounded-lg p-4">
                    <h4 class="font-semibold text-red-800 mb-2">Informações da Venda Perdida</h4>
                    <div class="grid grid-cols-2 gap-4 text-sm">
                        <div><strong>Cliente:</strong> ${contact.contactName}</div>
                        <div><strong>Telefone:</strong> ${contact.contactPhone}</div>
                        <div><strong>Vendedor:</strong> ${seller ? seller.name : 'N/A'}</div>
                        <div><strong>Produto:</strong> ${contact.product}</div>
                        <div><strong>Motivo:</strong> ${lostSale.lostSaleReason}</div>
                        <div><strong>Data:</strong> ${new Date(lostSale.createdAt).toLocaleDateString('pt-BR')}</div>
                    </div>
                    <div class="mt-3">
                        <strong>Detalhes:</strong>
                        <p class="text-gray-700 mt-1">${lostSale.lostSaleDetails}</p>
                    </div>
                    ${lostSale.competitorInfo ? `
                        <div class="mt-3">
                            <strong>Informações da Concorrência:</strong>
                            <p class="text-gray-700 mt-1">${lostSale.competitorInfo}</p>
                        </div>
                    ` : ''}
                </div>
            `;
            
            document.getElementById('assistantLostSaleModal').classList.remove('hidden');
        }

        function closeAssistantLostSaleModal() {
            currentLostSaleToReview = null;
            document.getElementById('assistantLostSaleModal').classList.add('hidden');
            document.getElementById('assistantLostSaleForm').reset();
        }

        function showSetReminderModal(contactId) {
            currentContactForReminder = contactId;
            
            // Set minimum date to tomorrow
            const tomorrow = new Date();
            tomorrow.setDate(tomorrow.getDate() + 1);
            const minDateTime = tomorrow.toISOString().slice(0, 16);
            document.getElementById('reminderDate').min = minDateTime;
            
            document.getElementById('setReminderModal').classList.remove('hidden');
        }

        function closeSetReminderModal() {
            currentContactForReminder = null;
            document.getElementById('setReminderModal').classList.add('hidden');
            document.getElementById('setReminderForm').reset();
        }

        function showCompleteReminderModal(reminderId) {
            currentReminderToComplete = reminderId;
            
            // Populate reminder details
            const reminder = allData.find(item => item.id === reminderId);
            const contact = allData.find(item => item.id === reminder.contactId);
            
            if (reminder && contact) {
                let reminderTypeText = '';
                switch(reminder.reminderType) {
                    case 'fechar_venda': reminderTypeText = '💰 Fechar Venda'; break;
                    case 'followup': reminderTypeText = '📞 Follow-up'; break;
                    case 'apresentacao': reminderTypeText = '📊 Apresentação'; break;
                    case 'negociacao': reminderTypeText = '🤝 Negociação'; break;
                    case 'visita_tecnica': reminderTypeText = '🔧 Visita Técnica'; break;
                    case 'envio_proposta': reminderTypeText = '📋 Envio de Proposta'; break;
                    default: reminderTypeText = '📝 Outros';
                }
                
                const reminderDate = new Date(reminder.reminderDate).toLocaleString('pt-BR');
                
                document.getElementById('reminderDetailsContent').innerHTML = `
                    <div class="bg-blue-50 border border-blue-200 rounded-lg p-4">
                        <h4 class="font-semibold text-blue-800 mb-2">Detalhes do Lembrete</h4>
                        <div class="grid grid-cols-1 gap-2 text-sm">
                            <div><strong>Cliente:</strong> ${contact.contactName}</div>
                            <div><strong>Produto:</strong> ${contact.product}</div>
                            <div><strong>Tipo de Ação:</strong> ${reminderTypeText}</div>
                            <div><strong>Data Programada:</strong> ${reminderDate}</div>
                            <div><strong>Observações:</strong> ${reminder.reminderNotes}</div>
                        </div>
                    </div>
                `;
            }
            
            document.getElementById('completeReminderModal').classList.remove('hidden');
        }

        function closeCompleteReminderModal() {
            currentReminderToComplete = null;
            document.getElementById('completeReminderModal').classList.add('hidden');
            document.getElementById('completeReminderForm').reset();
        }

        function updatePendingLeadsTable() {
            const contacts = allData.filter(item => item.type === 'contact' && item.assignedBy === currentUser.id);
            const users = allData.filter(item => item.type === 'user' && item.active);
            const sellers = users.filter(user => user.role === 'seller');
            
            const now = new Date();
            const threeDaysAgo = new Date(now.getTime() - (3 * 24 * 60 * 60 * 1000));
            
            const pendingLeads = contacts.filter(contact => 
                contact.status === 'contato' && 
                contact.clientStatus !== 'venda_perdida' &&
                new Date(contact.lastContactDate) < threeDaysAgo
            );
            
            const tbody = document.getElementById('pendingLeadsTableBody');
            tbody.innerHTML = '';
            
            pendingLeads.forEach(contact => {
                const seller = sellers.find(s => s.id === contact.sellerId);
                const lastContactDate = contact.lastContactDate ? 
                    new Date(contact.lastContactDate).toLocaleDateString('pt-BR') : 
                    'Nunca';
                
                let clientStatusIcon = '';
                let clientStatusClass = '';
                let clientStatusText = '';
                
                switch(contact.clientStatus) {
                    case 'novo':
                        clientStatusIcon = '🆕';
                        clientStatusClass = 'text-green-600 bg-green-100';
                        clientStatusText = 'Novo';
                        break;
                    case 'em_andamento':
                        clientStatusIcon = '⏳';
                        clientStatusClass = 'text-blue-600 bg-blue-100';
                        clientStatusText = 'Em Andamento';
                        break;
                    case 'quente':
                        clientStatusIcon = '🔥';
                        clientStatusClass = 'text-red-600 bg-red-100';
                        clientStatusText = 'Quente';
                        break;
                    case 'morno':
                        clientStatusIcon = '🟡';
                        clientStatusClass = 'text-yellow-600 bg-yellow-100';
                        clientStatusText = 'Morno';
                        break;
                    case 'frio':
                        clientStatusIcon = '❄️';
                        clientStatusClass = 'text-blue-600 bg-blue-100';
                        clientStatusText = 'Frio';
                        break;
                    case 'sem_retorno':
                        clientStatusIcon = '📵';
                        clientStatusClass = 'text-gray-600 bg-gray-100';
                        clientStatusText = 'Sem Retorno';
                        break;
                    default:
                        clientStatusIcon = '❓';
                        clientStatusClass = 'text-gray-600 bg-gray-100';
                        clientStatusText = 'Indefinido';
                }
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td class="px-4 py-2 text-sm font-medium text-gray-900">${contact.contactName}</td>
                    <td class="px-4 py-2 text-sm text-gray-500">${seller ? seller.name : 'N/A'}</td>
                    <td class="px-4 py-2 text-sm text-gray-500">${contact.product}</td>
                    <td class="px-4 py-2 text-sm">
                        <span class="inline-flex items-center px-2 py-1 text-xs font-semibold rounded-full ${clientStatusClass}">
                            ${clientStatusIcon} ${clientStatusText}
                        </span>
                    </td>
                    <td class="px-4 py-2 text-sm text-gray-500">${lastContactDate}</td>
                    <td class="px-4 py-2 text-sm font-medium">
                        <button onclick="sendFollowupReminder('${contact.id}')" class="text-blue-600 hover:text-blue-900">
                            Enviar Lembrete
                        </button>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        async function handleRemarketing(e) {
            e.preventDefault();
            
            const confirmBtn = document.getElementById('confirmRemarketingBtn');
            confirmBtn.classList.add('loading');
            confirmBtn.textContent = 'Enviando...';
            
            const remarketingType = document.getElementById('remarketingType').value;
            const message = document.getElementById('remarketingMessage').value;
            const targetLeads = document.getElementById('targetLeads').value;
            
            // Create remarketing record
            const remarketingRecord = {
                id: generateId(),
                type: 'remarketing',
                assistantId: currentUser.id,
                remarketingType,
                message,
                targetLeads,
                createdAt: new Date().toISOString()
            };
            
            if (window.dataSdk) {
                const result = await window.dataSdk.create(remarketingRecord);
                if (result.isOk) {
                    showMessage('Remarketing enviado com sucesso!', 'success');
                    closeRemarketingModal();
                } else {
                    showMessage('Erro ao enviar remarketing', 'error');
                }
            }
            
            confirmBtn.classList.remove('loading');
            confirmBtn.textContent = 'Enviar Remarketing';
        }

        async function handleContactSellers(e) {
            e.preventDefault();
            
            const confirmBtn = document.getElementById('confirmContactSellersBtn');
            confirmBtn.classList.add('loading');
            confirmBtn.textContent = 'Enviando...';
            
            const contactMethod = document.getElementById('contactMethod').value;
            const message = document.getElementById('contactMessage').value;
            const targetSellers = document.getElementById('targetSellers').value;
            
            // Create contact record
            const contactRecord = {
                id: generateId(),
                type: 'seller_contact',
                assistantId: currentUser.id,
                contactMethod,
                message,
                targetSellers,
                createdAt: new Date().toISOString()
            };
            
            if (window.dataSdk) {
                const result = await window.dataSdk.create(contactRecord);
                if (result.isOk) {
                    showMessage('Contato enviado aos vendedores com sucesso!', 'success');
                    closeContactSellersModal();
                } else {
                    showMessage('Erro ao enviar contato', 'error');
                }
            }
            
            confirmBtn.classList.remove('loading');
            confirmBtn.textContent = 'Enviar Contato';
        }

        async function sendFollowupReminder(contactId) {
            const contact = allData.find(item => item.id === contactId);
            if (!contact) return;
            
            // Create follow-up reminder record
            const reminderRecord = {
                id: generateId(),
                type: 'followup_reminder',
                assistantId: currentUser.id,
                contactId: contactId,
                sellerId: contact.sellerId,
                message: `Follow-up necessário para o cliente ${contact.contactName} - Produto: ${contact.product}`,
                createdAt: new Date().toISOString()
            };
            
            if (window.dataSdk) {
                const result = await window.dataSdk.create(reminderRecord);
                if (result.isOk) {
                    showMessage('Lembrete de follow-up enviado ao vendedor!', 'success');
                } else {
                    showMessage('Erro ao enviar lembrete', 'error');
                }
            }
        }

        async function handleReturnContact(e) {
            e.preventDefault();
            
            if (!currentContactToReturn) return;
            
            const confirmBtn = document.getElementById('confirmReturnContactBtn');
            confirmBtn.classList.add('loading');
            confirmBtn.textContent = 'Devolvendo...';
            
            const contact = allData.find(item => item.id === currentContactToReturn);
            if (contact) {
                const returnReason = document.getElementById('returnReason').value;
                const returnDetails = document.getElementById('returnDetails').value;
                const returnAttempts = document.getElementById('returnAttempts').value;
                
                // Create return record
                const returnRecord = {
                    id: generateId(),
                    type: 'contact_return',
                    contactId: currentContactToReturn,
                    sellerId: contact.sellerId,
                    assistantId: contact.assignedBy,
                    returnReason,
                    returnDetails,
                    returnAttempts: parseInt(returnAttempts) || 0,
                    createdAt: new Date().toISOString()
                };
                
                // Update contact status
                const updatedContact = {
                    ...contact,
                    clientStatus: 'devolvido',
                    status: 'devolvido',
                    lastContactDate: new Date().toISOString(),
                    notes: `${contact.notes}\n\n${new Date().toLocaleDateString('pt-BR')}: DEVOLVIDO - ${returnReason} - ${returnDetails}`
                };
                
                if (window.dataSdk) {
                    const returnResult = await window.dataSdk.create(returnRecord);
                    const updateResult = await window.dataSdk.update(updatedContact);
                    
                    if (returnResult.isOk && updateResult.isOk) {
                        showMessage('Contato devolvido ao estrategista com sucesso!', 'success');
                        closeReturnContactModal();
                    } else {
                        showMessage('Erro ao devolver contato', 'error');
                    }
                }
            }
            
            confirmBtn.classList.remove('loading');
            confirmBtn.textContent = 'Devolver Contato';
        }

        async function handleLostSale(e) {
            e.preventDefault();
            
            if (!currentContactForLostSale) return;
            
            const confirmBtn = document.getElementById('confirmLostSaleBtn');
            confirmBtn.classList.add('loading');
            confirmBtn.textContent = 'Processando...';
            
            const contact = allData.find(item => item.id === currentContactForLostSale);
            if (contact) {
                const lostSaleReason = document.getElementById('lostSaleReason').value;
                const lostSaleDetails = document.getElementById('lostSaleDetails').value;
                const competitorInfo = document.getElementById('competitorInfo').value;
                
                // Create lost sale record
                const lostSaleRecord = {
                    id: generateId(),
                    type: 'lost_sale',
                    contactId: currentContactForLostSale,
                    sellerId: contact.sellerId,
                    assistantId: contact.assignedBy,
                    lostSaleReason,
                    lostSaleDetails,
                    competitorInfo,
                    needsReview: true,
                    reviewedAt: null,
                    createdAt: new Date().toISOString()
                };
                
                // Update contact status
                const updatedContact = {
                    ...contact,
                    clientStatus: 'venda_perdida',
                    lastContactDate: new Date().toISOString(),
                    notes: `${contact.notes}\n\n${new Date().toLocaleDateString('pt-BR')}: VENDA PERDIDA - ${lostSaleReason} - ${lostSaleDetails}`
                };
                
                if (window.dataSdk) {
                    const lostSaleResult = await window.dataSdk.create(lostSaleRecord);
                    const updateResult = await window.dataSdk.update(updatedContact);
                    
                    if (lostSaleResult.isOk && updateResult.isOk) {
                        showMessage('Venda perdida registrada. O estrategista será notificado para revisão.', 'success');
                        closeLostSaleModal();
                    } else {
                        showMessage('Erro ao registrar venda perdida', 'error');
                    }
                }
            }
            
            confirmBtn.classList.remove('loading');
            confirmBtn.textContent = 'Confirmar Perda';
        }

        async function handleAssistantLostSaleReview(e) {
            e.preventDefault();
            
            if (!currentLostSaleToReview) return;
            
            const confirmBtn = document.getElementById('confirmAssistantLostSaleBtn');
            confirmBtn.classList.add('loading');
            confirmBtn.textContent = 'Finalizando...';
            
            const lostSale = allData.find(item => item.id === currentLostSaleToReview);
            if (lostSale) {
                const assistantContactMethod = document.getElementById('assistantContactMethod').value;
                const clientConfirmation = document.getElementById('clientConfirmation').value;
                const assistantReport = document.getElementById('assistantReport').value;
                const assistantRecommendation = document.getElementById('assistantRecommendation').value;
                
                // Update lost sale record with review
                const updatedLostSale = {
                    ...lostSale,
                    needsReview: false,
                    reviewedAt: new Date().toISOString(),
                    assistantContactMethod,
                    clientConfirmation,
                    assistantReport,
                    assistantRecommendation
                };
                
                if (window.dataSdk) {
                    const result = await window.dataSdk.update(updatedLostSale);
                    if (result.isOk) {
                        showMessage('Revisão da venda perdida finalizada com sucesso!', 'success');
                        closeAssistantLostSaleModal();
                    } else {
                        showMessage('Erro ao finalizar revisão', 'error');
                    }
                }
            }
            
            confirmBtn.classList.remove('loading');
            confirmBtn.textContent = 'Finalizar Revisão';
        }

        async function handleSetReminder(e) {
            e.preventDefault();
            
            if (!currentContactForReminder) return;
            
            const confirmBtn = document.getElementById('confirmReminderBtn');
            confirmBtn.classList.add('loading');
            confirmBtn.textContent = 'Criando...';
            
            const contact = allData.find(item => item.id === currentContactForReminder);
            if (contact) {
                const reminderDate = document.getElementById('reminderDate').value;
                const reminderType = document.getElementById('reminderType').value;
                const reminderNotes = document.getElementById('reminderNotes').value;
                
                // Create reminder record
                const newReminder = {
                    id: generateId(),
                    type: 'reminder',
                    contactId: currentContactForReminder,
                    sellerId: contact.sellerId,
                    assistantId: contact.assignedBy,
                    reminderDate: new Date(reminderDate).toISOString(),
                    reminderType,
                    reminderNotes,
                    reminderCompleted: false,
                    completedAt: null,
                    completionNotes: null,
                    actionResult: null,
                    createdAt: new Date().toISOString()
                };
                
                if (window.dataSdk) {
                    const result = await window.dataSdk.create(newReminder);
                    if (result.isOk) {
                        showMessage('Lembrete criado com sucesso!', 'success');
                        closeSetReminderModal();
                    } else {
                        showMessage('Erro ao criar lembrete', 'error');
                    }
                }
            }
            
            confirmBtn.classList.remove('loading');
            confirmBtn.textContent = 'Criar Lembrete';
        }

        async function handleCompleteReminder(e) {
            e.preventDefault();
            
            if (!currentReminderToComplete) return;
            
            const confirmBtn = document.getElementById('confirmCompleteReminderBtn');
            confirmBtn.classList.add('loading');
            confirmBtn.textContent = 'Concluindo...';
            
            const reminder = allData.find(item => item.id === currentReminderToComplete);
            if (reminder) {
                const completionNotes = document.getElementById('completionNotes').value;
                const actionResult = document.getElementById('actionResult').value;
                
                // Update reminder as completed
                const updatedReminder = {
                    ...reminder,
                    reminderCompleted: true,
                    completedAt: new Date().toISOString(),
                    completionNotes,
                    actionResult
                };
                
                // Check if seller was blocked and unblock them
                const seller = allData.find(item => item.id === reminder.sellerId && item.type === 'user');
                if (seller && seller.blockedFromReceiving) {
                    const updatedSeller = {
                        ...seller,
                        blockedFromReceiving: false,
                        blockReason: null
                    };
                    
                    if (window.dataSdk) {
                        await window.dataSdk.update(updatedSeller);
                    }
                }
                
                if (window.dataSdk) {
                    const result = await window.dataSdk.update(updatedReminder);
                    if (result.isOk) {
                        showMessage('Lembrete marcado como concluído! Você foi desbloqueado para receber novos leads.', 'success');
                        closeCompleteReminderModal();
                    } else {
                        showMessage('Erro ao concluir lembrete', 'error');
                    }
                }
            }
            
            confirmBtn.classList.remove('loading');
            confirmBtn.textContent = 'Marcar como Concluído';
        }

        function updateStoresTable() {
            const stores = allData.filter(item => item.type === 'store' && item.active);
            const tbody = document.getElementById('storesTableBody');
            tbody.innerHTML = '';
            
            stores.forEach(store => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td class="px-4 py-2 text-sm text-gray-900">${store.name}</td>
                    <td class="px-4 py-2 text-sm text-gray-500">${store.storeType}</td>
                    <td class="px-4 py-2 text-sm text-gray-500">${store.address}</td>
                    <td class="px-4 py-2 text-sm font-medium">
                        <button onclick="showEditStoreModal('${store.id}')" class="text-blue-600 hover:text-blue-900 mr-2">
                            Editar
                        </button>
                        <button onclick="deleteStore('${store.id}')" class="text-red-600 hover:text-red-900">
                            Excluir
                        </button>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function updateCampaignsAccordion() {
            const campaigns = allData.filter(item => item.type === 'campaign' && item.active);
            const contacts = allData.filter(item => item.type === 'contact');
            const ads = allData.filter(item => item.type === 'ad');
            const accordion = document.getElementById('campaignsAccordion');
            accordion.innerHTML = '';
            
            campaigns.forEach(campaign => {
                const campaignContacts = contacts.filter(c => c.campaignId === campaign.id);
                const campaignSales = campaignContacts.filter(c => c.status === 'vendido');
                const campaignAds = ads.filter(a => a.campaignId === campaign.id && a.active);
                
                const conversionRate = campaignContacts.length > 0 ? ((campaignSales.length / campaignContacts.length) * 100).toFixed(1) : 0;
                const revenue = campaignSales.reduce((sum, sale) => sum + (sale.value || 0), 0);
                const totalAdSpend = campaignAds.reduce((sum, ad) => sum + (ad.totalSpent || 0), 0);
                const totalDailyBudget = campaignAds.reduce((sum, ad) => sum + (ad.dailyBudget || 0), 0);
                const roi = totalAdSpend > 0 ? (((revenue - totalAdSpend) / totalAdSpend) * 100).toFixed(1) : 0;
                
                const campaignCard = document.createElement('div');
                campaignCard.className = 'border border-gray-200 rounded-lg overflow-hidden';
                campaignCard.innerHTML = `
                    <div class="bg-gradient-to-r from-blue-50 to-indigo-50 px-6 py-4 cursor-pointer" onclick="toggleCampaignAccordion('${campaign.id}')">
                        <div class="flex items-center justify-between">
                            <div class="flex items-center space-x-4">
                                <div class="flex-shrink-0">
                                    <div class="w-10 h-10 bg-blue-600 rounded-lg flex items-center justify-center">
                                        <span class="text-white font-bold text-sm">📊</span>
                                    </div>
                                </div>
                                <div>
                                    <h3 class="text-lg font-semibold text-gray-900">${campaign.name}</h3>
                                    <p class="text-sm text-gray-600">${campaign.campaignType} • ${campaignAds.length} anúncios ativos</p>
                                </div>
                            </div>
                            <div class="flex items-center space-x-6">
                                <div class="text-center">
                                    <p class="text-sm text-gray-500">Leads</p>
                                    <p class="text-lg font-bold text-blue-600">${campaignContacts.length}</p>
                                </div>
                                <div class="text-center">
                                    <p class="text-sm text-gray-500">Vendas</p>
                                    <p class="text-lg font-bold text-green-600">${campaignSales.length}</p>
                                </div>
                                <div class="text-center">
                                    <p class="text-sm text-gray-500">ROI</p>
                                    <p class="text-lg font-bold ${roi >= 0 ? 'text-green-600' : 'text-red-600'}">${roi}%</p>
                                </div>
                                <div class="text-center">
                                    <p class="text-sm text-gray-500">Orçamento/dia</p>
                                    <p class="text-lg font-bold text-purple-600">R$ ${totalDailyBudget.toLocaleString('pt-BR', {minimumFractionDigits: 2})}</p>
                                </div>
                                <div class="flex space-x-2">
                                    <button onclick="event.stopPropagation(); showAddAdModal('${campaign.id}')" class="bg-blue-600 hover:bg-blue-700 text-white px-3 py-1 rounded text-sm font-medium">
                                        + Anúncio
                                    </button>
                                    <button onclick="event.stopPropagation(); deleteCampaign('${campaign.id}')" class="bg-red-600 hover:bg-red-700 text-white px-3 py-1 rounded text-sm font-medium">
                                        Excluir
                                    </button>
                                </div>
                                <div class="text-gray-400">
                                    <span id="chevron-${campaign.id}">▼</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div id="content-${campaign.id}" class="hidden bg-white">
                        <div class="px-6 py-4">
                            <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                                <!-- Campaign Summary -->
                                <div class="bg-gray-50 rounded-lg p-4">
                                    <h4 class="font-semibold text-gray-800 mb-3">📈 Resumo da Campanha</h4>
                                    <div class="grid grid-cols-2 gap-4 text-sm">
                                        <div>
                                            <span class="text-gray-600">Taxa Conversão:</span>
                                            <span class="font-semibold text-purple-600 ml-2">${conversionRate}%</span>
                                        </div>
                                        <div>
                                            <span class="text-gray-600">Receita Total:</span>
                                            <span class="font-semibold text-green-600 ml-2">R$ ${revenue.toLocaleString('pt-BR', {minimumFractionDigits: 2})}</span>
                                        </div>
                                        <div>
                                            <span class="text-gray-600">Gasto Total:</span>
                                            <span class="font-semibold text-red-600 ml-2">R$ ${totalAdSpend.toLocaleString('pt-BR', {minimumFractionDigits: 2})}</span>
                                        </div>
                                        <div>
                                            <span class="text-gray-600">Período:</span>
                                            <span class="font-semibold text-gray-800 ml-2">${new Date(campaign.startDate).toLocaleDateString('pt-BR')} - ${campaign.endDate ? new Date(campaign.endDate).toLocaleDateString('pt-BR') : 'Ativa'}</span>
                                        </div>
                                    </div>
                                </div>
                                
                                <!-- Top Performing Ad -->
                                <div class="bg-green-50 rounded-lg p-4">
                                    <h4 class="font-semibold text-gray-800 mb-3">🏆 Melhor Anúncio</h4>
                                    ${campaignAds.length > 0 ? (() => {
                                        const bestAd = campaignAds.reduce((best, ad) => {
                                            const adContacts = contacts.filter(c => c.adId === ad.id);
                                            const adSales = adContacts.filter(c => c.status === 'vendido');
                                            const adConversionRate = adContacts.length > 0 ? (adSales.length / adContacts.length) : 0;
                                            const bestContacts = contacts.filter(c => c.adId === best.id);
                                            const bestSales = bestContacts.filter(c => c.status === 'vendido');
                                            const bestConversionRate = bestContacts.length > 0 ? (bestSales.length / bestContacts.length) : 0;
                                            return adConversionRate > bestConversionRate ? ad : best;
                                        });
                                        const bestAdContacts = contacts.filter(c => c.adId === bestAd.id);
                                        const bestAdSales = bestAdContacts.filter(c => c.status === 'vendido');
                                        const bestAdConversionRate = bestAdContacts.length > 0 ? ((bestAdSales.length / bestAdContacts.length) * 100).toFixed(1) : 0;
                                        return `
                                            <div class="text-sm">
                                                <p class="font-semibold text-green-800">${bestAd.adName}</p>
                                                <p class="text-gray-600">Conversão: ${bestAdConversionRate}% • Orçamento: R$ ${bestAd.dailyBudget.toLocaleString('pt-BR', {minimumFractionDigits: 2})}/dia</p>
                                            </div>
                                        `;
                                    })() : '<p class="text-gray-500 text-sm">Nenhum anúncio cadastrado</p>'}
                                </div>
                            </div>
                            
                            <!-- Ads Table -->
                            <div class="mt-6">
                                <div class="flex items-center justify-between mb-4">
                                    <h4 class="font-semibold text-gray-800">🎯 Anúncios da Campanha</h4>
                                    <button onclick="showAddAdModal('${campaign.id}')" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-md text-sm font-medium">
                                        + Novo Anúncio
                                    </button>
                                </div>
                                <div class="overflow-x-auto">
                                    <table class="min-w-full divide-y divide-gray-200">
                                        <thead class="bg-gray-50">
                                            <tr>
                                                <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Anúncio</th>
                                                <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Tipo</th>
                                                <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Público</th>
                                                <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Orçamento/dia</th>
                                                <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Leads</th>
                                                <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Vendas</th>
                                                <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Taxa Conv.</th>
                                                <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">CPL</th>
                                                <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Status</th>
                                                <th class="px-4 py-2 text-left text-xs font-medium text-gray-500 uppercase">Ações</th>
                                            </tr>
                                        </thead>
                                        <tbody id="ads-${campaign.id}" class="bg-white divide-y divide-gray-200">
                                            ${campaignAds.map(ad => {
                                                const adContacts = contacts.filter(c => c.adId === ad.id);
                                                const adSales = adContacts.filter(c => c.status === 'vendido');
                                                const adConversionRate = adContacts.length > 0 ? ((adSales.length / adContacts.length) * 100).toFixed(1) : 0;
                                                const cpl = adContacts.length > 0 && ad.totalSpent > 0 ? (ad.totalSpent / adContacts.length).toFixed(2) : 0;
                                                
                                                let statusBadge = '';
                                                let statusClass = '';
                                                if (!ad.active || ad.dailyBudget === 0) {
                                                    statusBadge = '⏸️ Pausado';
                                                    statusClass = 'bg-gray-100 text-gray-800';
                                                } else if (adConversionRate >= 5) {
                                                    statusBadge = '🚀 Excelente';
                                                    statusClass = 'bg-green-100 text-green-800';
                                                } else if (adConversionRate >= 2) {
                                                    statusBadge = '✅ Bom';
                                                    statusClass = 'bg-blue-100 text-blue-800';
                                                } else if (adContacts.length >= 10) {
                                                    statusBadge = '⚠️ Baixa Conv.';
                                                    statusClass = 'bg-yellow-100 text-yellow-800';
                                                } else {
                                                    statusBadge = '🧪 Testando';
                                                    statusClass = 'bg-purple-100 text-purple-800';
                                                }
                                                
                                                return `
                                                    <tr>
                                                        <td class="px-4 py-3 text-sm">
                                                            <div class="font-medium text-gray-900">${ad.adName}</div>
                                                            <div class="text-xs text-gray-500">${ad.adAudience}</div>
                                                        </td>
                                                        <td class="px-4 py-3 text-sm text-gray-500">${ad.adType}</td>
                                                        <td class="px-4 py-3 text-sm text-gray-500 max-w-32 truncate">${ad.adAudience}</td>
                                                        <td class="px-4 py-3 text-sm">
                                                            <div class="font-semibold ${ad.dailyBudget > 0 ? 'text-green-600' : 'text-gray-500'}">
                                                                R$ ${ad.dailyBudget.toLocaleString('pt-BR', {minimumFractionDigits: 2})}
                                                            </div>
                                                        </td>
                                                        <td class="px-4 py-3 text-sm text-center">
                                                            <span class="font-semibold text-blue-600">${adContacts.length}</span>
                                                        </td>
                                                        <td class="px-4 py-3 text-sm text-center">
                                                            <span class="font-semibold text-green-600">${adSales.length}</span>
                                                        </td>
                                                        <td class="px-4 py-3 text-sm text-center">
                                                            <span class="font-semibold ${adConversionRate >= 5 ? 'text-green-600' : adConversionRate >= 2 ? 'text-blue-600' : 'text-yellow-600'}">${adConversionRate}%</span>
                                                        </td>
                                                        <td class="px-4 py-3 text-sm text-center">
                                                            <span class="text-gray-600">R$ ${parseFloat(cpl).toLocaleString('pt-BR', {minimumFractionDigits: 2})}</span>
                                                        </td>
                                                        <td class="px-4 py-3 text-sm">
                                                            <span class="inline-flex items-center px-2 py-1 text-xs font-semibold rounded-full ${statusClass}">
                                                                ${statusBadge}
                                                            </span>
                                                        </td>
                                                        <td class="px-4 py-3 text-sm">
                                                            <div class="flex space-x-2">
                                                                <button onclick="showUpdateAdBudgetModal('${ad.id}')" class="text-blue-600 hover:text-blue-900 text-xs font-medium">
                                                                    ${ad.dailyBudget === 0 ? 'Reativar' : adConversionRate >= 5 ? 'Escalar' : adConversionRate < 2 && adContacts.length >= 10 ? 'Reduzir' : 'Ajustar'}
                                                                </button>
                                                                <button onclick="deleteAd('${ad.id}')" class="text-red-600 hover:text-red-900 text-xs font-medium">
                                                                    Excluir
                                                                </button>
                                                            </div>
                                                        </td>
                                                    </tr>
                                                `;
                                            }).join('')}
                                        </tbody>
                                    </table>
                                </div>
                                ${campaignAds.length === 0 ? `
                                    <div class="text-center py-8">
                                        <div class="text-gray-400 text-4xl mb-4">📢</div>
                                        <p class="text-gray-500 mb-4">Nenhum anúncio cadastrado nesta campanha</p>
                                        <button onclick="showAddAdModal('${campaign.id}')" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-md font-medium">
                                            Criar Primeiro Anúncio
                                        </button>
                                    </div>
                                ` : ''}
                            </div>
                        </div>
                    </div>
                `;
                accordion.appendChild(campaignCard);
            });
            
            if (campaigns.length === 0) {
                accordion.innerHTML = `
                    <div class="text-center py-12">
                        <div class="text-gray-400 text-6xl mb-4">🚀</div>
                        <h3 class="text-lg font-medium text-gray-900 mb-2">Nenhuma campanha cadastrada</h3>
                        <p class="text-gray-500 mb-6">Crie sua primeira campanha de marketing para começar a gerenciar seus anúncios</p>
                    </div>
                `;
            }
        }

        function toggleCampaignAccordion(campaignId) {
            const content = document.getElementById(`content-${campaignId}`);
            const chevron = document.getElementById(`chevron-${campaignId}`);
            
            if (content.classList.contains('hidden')) {
                content.classList.remove('hidden');
                chevron.textContent = '▲';
            } else {
                content.classList.add('hidden');
                chevron.textContent = '▼';
            }
        }

        async function deleteAd(adId) {
            const ad = allData.find(item => item.id === adId);
            if (ad) {
                const updatedAd = { ...ad, active: false };
                
                if (window.dataSdk) {
                    const result = await window.dataSdk.update(updatedAd);
                    if (result.isOk) {
                        showMessage('Anúncio excluído com sucesso!', 'success');
                        updateCampaignsAccordion();
                    } else {
                        showMessage('Erro ao excluir anúncio', 'error');
                    }
                }
            }
        }

        async function deleteStore(storeId) {
            const store = allData.find(item => item.id === storeId);
            if (store) {
                const updatedStore = { ...store, active: false };
                
                if (window.dataSdk) {
                    const result = await window.dataSdk.update(updatedStore);
                    if (result.isOk) {
                        showMessage('Loja excluída com sucesso!', 'success');
                        updateStoresTable();
                        updateStoreSelects();
                    } else {
                        showMessage('Erro ao excluir loja', 'error');
                    }
                }
            }
        }

        async function deleteCampaign(campaignId) {
            const campaign = allData.find(item => item.id === campaignId);
            if (campaign) {
                const updatedCampaign = { ...campaign, active: false };
                
                if (window.dataSdk) {
                    const result = await window.dataSdk.update(updatedCampaign);
                    if (result.isOk) {
                        showMessage('Campanha excluída com sucesso!', 'success');
                        updateCampaignsAccordion();
                        updateCampaignSelects();
                    } else {
                        showMessage('Erro ao excluir campanha', 'error');
                    }
                }
            }
        }

        // UI Update functions
        function updateUI() {
            if (!currentUser) return;
            
            if (currentUser.role === 'admin') {
                updateAdminDashboard();
            } else if (currentUser.role === 'assistant') {
                updateAssistantDashboard();
            } else {
                updateSellerDashboard();
            }
        }

        function updateAdminDashboard() {
            const contacts = allData.filter(item => item.type === 'contact');
            const sales = contacts.filter(contact => contact.status === 'vendido');
            const users = allData.filter(item => item.type === 'user' && item.active);
            const sellers = users.filter(user => user.role === 'seller');
            
            // Calculate daily data (TODAY)
            const today = new Date();
            const todayStart = new Date(today.getFullYear(), today.getMonth(), today.getDate());
            const todayEnd = new Date(today.getFullYear(), today.getMonth(), today.getDate() + 1);
            
            const todayContacts = contacts.filter(contact => {
                const contactDate = new Date(contact.createdAt);
                return contactDate >= todayStart && contactDate < todayEnd;
            });
            
            const todaySales = sales.filter(sale => {
                const saleDate = new Date(sale.convertedAt);
                return saleDate >= todayStart && saleDate < todayEnd;
            });
            
            // Update today's date display
            document.getElementById('todayDate').textContent = today.toLocaleDateString('pt-BR', {
                weekday: 'long',
                year: 'numeric',
                month: 'long',
                day: 'numeric'
            });
            
            // Update daily metrics
            document.getElementById('todayLeadsIn').textContent = todayContacts.length;
            
            const todayBudgetTotal = todayContacts.reduce((sum, contact) => sum + (contact.budgetValue || 0), 0);
            document.getElementById('todayBudgetTotal').textContent = `R$ ${todayBudgetTotal.toLocaleString('pt-BR', {minimumFractionDigits: 2})}`;
            
            document.getElementById('todaySales').textContent = todaySales.length;
            
            const todayRevenue = todaySales.reduce((sum, sale) => sum + (sale.value || 0), 0);
            document.getElementById('todayRevenue').textContent = `R$ ${todayRevenue.toLocaleString('pt-BR', {minimumFractionDigits: 2})}`;
            
            const todayConversionRate = todayContacts.length > 0 ? ((todaySales.length / todayContacts.length) * 100).toFixed(1) : 0;
            document.getElementById('todayConversionRate').textContent = `${todayConversionRate}%`;
            
            // Calculate monthly data
            const currentMonth = new Date().getMonth();
            const currentYear = new Date().getFullYear();
            
            const monthlyContacts = contacts.filter(contact => {
                const contactDate = new Date(contact.createdAt);
                return contactDate.getMonth() === currentMonth && contactDate.getFullYear() === currentYear;
            });
            
            const monthlySales = sales.filter(sale => {
                const saleDate = new Date(sale.convertedAt);
                return saleDate.getMonth() === currentMonth && saleDate.getFullYear() === currentYear;
            });
            
            // Update header battle stats
            const goals = allData.filter(item => item.type === 'goal');
            const currentGoal = goals.find(goal => {
                const goalDate = new Date(goal.createdAt);
                return goalDate.getMonth() === currentMonth && goalDate.getFullYear() === currentYear;
            });
            
            document.getElementById('headerGoal').textContent = currentGoal ? currentGoal.generalGoal : 0;
            document.getElementById('headerSales').textContent = monthlySales.length;
            
            const monthlyConversionRate = monthlyContacts.length > 0 ? ((monthlySales.length / monthlyContacts.length) * 100).toFixed(1) : 0;
            document.getElementById('headerRate').textContent = monthlyConversionRate + '%';
            
            // Update main metrics
            document.getElementById('totalContacts').textContent = contacts.length;
            document.getElementById('monthlyContacts').textContent = monthlyContacts.length;
            
            document.getElementById('totalSales').textContent = sales.length;
            document.getElementById('monthlySales').textContent = monthlySales.length;
            
            const conversionRate = contacts.length > 0 ? ((sales.length / contacts.length) * 100).toFixed(1) : 0;
            document.getElementById('conversionRate').textContent = conversionRate + '%';
            document.getElementById('monthlyConversionRate').textContent = monthlyConversionRate + '%';
            
            const totalRevenue = sales.reduce((sum, sale) => sum + (sale.value || 0), 0);
            const monthlyRevenue = monthlySales.reduce((sum, sale) => sum + (sale.value || 0), 0);
            document.getElementById('totalRevenue').textContent = `R$ ${totalRevenue.toLocaleString('pt-BR', {minimumFractionDigits: 2})}`;
            document.getElementById('monthlyRevenue').textContent = `R$ ${monthlyRevenue.toLocaleString('pt-BR', {minimumFractionDigits: 2})}`;
            
            // Update user counts
            updateUserCounts(users);
            
            // Update goals
            updateAdminGoals();
            
            // Update commission display
            updateAdminCommissionDisplay();
            
            // Update campaign performance report
            updateCampaignPerformanceReport();
            
            // Update sellers table with monthly data
            updateSellersTable(sellers, contacts, sales, monthlyContacts, monthlySales);
            
            // Update overdue reminders table
            updateOverdueRemindersTable();
            
            // Update store performance report
            updateStorePerformanceReport();
            
            // Update recent sales
            updateRecentSalesTable(sales, users);
            
            // Update assistant ranking
            updateAssistantRankingTable();
        }

        function updateCampaignPerformanceReport() {
            const campaigns = allData.filter(item => item.type === 'campaign' && item.active);
            const contacts = allData.filter(item => item.type === 'contact');
            
            let totalInvestment = 0;
            let totalRevenue = 0;
            let totalLeads = 0;
            
            // Calculate overall metrics
            campaigns.forEach(campaign => {
                const campaignContacts = contacts.filter(c => c.campaignId === campaign.id);
                const campaignSales = campaignContacts.filter(c => c.status === 'vendido');
                const revenue = campaignSales.reduce((sum, sale) => sum + (sale.value || 0), 0);
                
                totalInvestment += campaign.investment || 0;
                totalRevenue += revenue;
                totalLeads += campaignContacts.length;
            });
            
            const overallROI = totalInvestment > 0 ? (((totalRevenue - totalInvestment) / totalInvestment) * 100).toFixed(1) : 0;
            const avgCostPerLead = totalLeads > 0 ? (totalInvestment / totalLeads).toFixed(2) : 0;
            
            // Update summary cards
            document.getElementById('totalInvested').textContent = `R$ ${totalInvestment.toLocaleString('pt-BR', {minimumFractionDigits: 2})}`;
            document.getElementById('totalRevenue').textContent = `R$ ${totalRevenue.toLocaleString('pt-BR', {minimumFractionDigits: 2})}`;
            document.getElementById('overallROI').textContent = `${overallROI}%`;
            document.getElementById('avgCostPerLead').textContent = `R$ ${parseFloat(avgCostPerLead).toLocaleString('pt-BR', {minimumFractionDigits: 2})}`;
            
            // Update performance table
            const tbody = document.getElementById('campaignPerformanceTable');
            tbody.innerHTML = '';
            
            campaigns.forEach(campaign => {
                const campaignContacts = contacts.filter(c => c.campaignId === campaign.id);
                const campaignSales = campaignContacts.filter(c => c.status === 'vendido');
                const revenue = campaignSales.reduce((sum, sale) => sum + (sale.value || 0), 0);
                const investment = campaign.investment || 0;
                const roi = investment > 0 ? (((revenue - investment) / investment) * 100).toFixed(1) : 0;
                const costPerLead = campaignContacts.length > 0 ? (investment / campaignContacts.length).toFixed(2) : 0;
                const conversionRate = campaignContacts.length > 0 ? ((campaignSales.length / campaignContacts.length) * 100).toFixed(1) : 0;
                
                const startDate = campaign.startDate ? new Date(campaign.startDate).toLocaleDateString('pt-BR') : 'N/A';
                const endDate = campaign.endDate ? new Date(campaign.endDate).toLocaleDateString('pt-BR') : 'Ativa';
                const period = `${startDate} - ${endDate}`;
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td class="px-4 py-3 text-sm font-medium text-gray-900">${campaign.name}</td>
                    <td class="px-4 py-3 text-sm text-gray-500">${period}</td>
                    <td class="px-4 py-3 text-sm text-gray-500">R$ ${investment.toLocaleString('pt-BR', {minimumFractionDigits: 2})}</td>
                    <td class="px-4 py-3 text-sm text-gray-500">${campaignContacts.length}</td>
                    <td class="px-4 py-3 text-sm text-gray-500">${campaignSales.length}</td>
                    <td class="px-4 py-3 text-sm text-gray-500">R$ ${revenue.toLocaleString('pt-BR', {minimumFractionDigits: 2})}</td>
                    <td class="px-4 py-3 text-sm font-medium ${roi >= 0 ? 'text-green-600' : 'text-red-600'}">${roi}%</td>
                    <td class="px-4 py-3 text-sm text-gray-500">R$ ${parseFloat(costPerLead).toLocaleString('pt-BR', {minimumFractionDigits: 2})}</td>
                    <td class="px-4 py-3 text-sm text-gray-500">${conversionRate}%</td>
                `;
                tbody.appendChild(row);
            });
        }

        function updateSellerDashboard() {
            // Debug: Log current user and all data
            console.log('Current User ID:', currentUser.id);
            console.log('All contacts:', allData.filter(item => item.type === 'contact'));
            
            const myContacts = allData.filter(item => {
                return item.type === 'contact' && 
                       item.sellerId && 
                       item.sellerId === currentUser.id;
            });
            
            console.log('My contacts found:', myContacts);
            
            const mySales = myContacts.filter(contact => contact.status === 'vendido');
            
            const currentMonth = new Date().getMonth();
            const currentYear = new Date().getFullYear();
            
            const currentMonthContacts = myContacts.filter(contact => {
                const contactDate = new Date(contact.createdAt);
                return contactDate.getMonth() === currentMonth && contactDate.getFullYear() === currentYear;
            });
            
            const currentMonthSales = mySales.filter(sale => {
                if (!sale.convertedAt) return false;
                const saleDate = new Date(sale.convertedAt);
                return saleDate.getMonth() === currentMonth && saleDate.getFullYear() === currentYear;
            });
            
            // Update header battle stats
            const goals = allData.filter(item => item.type === 'goal');
            const currentGoal = goals.find(goal => {
                const goalDate = new Date(goal.createdAt);
                return goalDate.getMonth() === currentMonth && goalDate.getFullYear() === currentYear;
            });
            
            document.getElementById('sellerHeaderGoal').textContent = currentGoal ? currentGoal.individualGoal : 0;
            document.getElementById('sellerHeaderSales').textContent = currentMonthSales.length;
            
            const currentConversionRate = currentMonthContacts.length > 0 ? ((currentMonthSales.length / currentMonthContacts.length) * 100).toFixed(1) : 0;
            document.getElementById('sellerHeaderRate').textContent = currentConversionRate + '%';
            
            // Update metrics
            document.getElementById('myContacts').textContent = currentMonthContacts.length;
            document.getElementById('mySales').textContent = currentMonthSales.length;
            document.getElementById('myConversionRate').textContent = currentConversionRate + '%';
            
            // Update goal progress
            updateGoalProgress(currentMonthSales.length);
            
            // Update reminders table
            updateMyRemindersTable();
            
            // Update contacts table
            updateMyContactsTable(myContacts);
        }

        function updateAssistantDashboard() {
            const contacts = allData.filter(item => item.type === 'contact' && item.assignedBy === currentUser.id);
            const users = allData.filter(item => item.type === 'user' && item.active);
            const sellers = users.filter(user => user.role === 'seller');
            const campaigns = allData.filter(item => item.type === 'campaign' && item.active);
            
            // Calculate monthly data
            const currentMonth = new Date().getMonth();
            const currentYear = new Date().getFullYear();
            
            const monthlyContacts = contacts.filter(contact => {
                const contactDate = new Date(contact.createdAt);
                return contactDate.getMonth() === currentMonth && contactDate.getFullYear() === currentYear;
            });
            
            const conversions = contacts.filter(contact => contact.status === 'vendido');
            const monthlyConversions = conversions.filter(conversion => {
                const conversionDate = new Date(conversion.convertedAt);
                return conversionDate.getMonth() === currentMonth && conversionDate.getFullYear() === currentYear;
            });
            
            // Update header battle stats
            document.getElementById('assistantHeaderLeads').textContent = monthlyContacts.length;
            document.getElementById('assistantHeaderConversions').textContent = monthlyConversions.length;
            
            // Calculate ranking for header
            const assistants = allData.filter(item => item.type === 'user' && item.role === 'assistant' && item.active);
            const assistantPerformance = assistants.map(assistant => {
                const assistantContacts = allData.filter(item => 
                    item.type === 'contact' && 
                    item.assignedBy === assistant.id
                );
                
                const assistantMonthlyContacts = assistantContacts.filter(contact => {
                    const contactDate = new Date(contact.createdAt);
                    return contactDate.getMonth() === currentMonth && contactDate.getFullYear() === currentYear;
                });
                
                const assistantConversions = assistantContacts.filter(contact => contact.status === 'vendido');
                const assistantMonthlyConversions = assistantConversions.filter(conversion => {
                    const conversionDate = new Date(conversion.convertedAt);
                    return conversionDate.getMonth() === currentMonth && conversionDate.getFullYear() === currentYear;
                });
                
                const conversionRate = assistantMonthlyContacts.length > 0 ? (assistantMonthlyConversions.length / assistantMonthlyContacts.length) : 0;
                const revenue = assistantConversions.reduce((sum, sale) => sum + (sale.value || 0), 0);
                
                const score = (assistantMonthlyContacts.length * 0.4) + (conversionRate * 100 * 0.4) + (revenue / 1000 * 0.2);
                
                return { assistant, score };
            });
            
            assistantPerformance.sort((a, b) => b.score - a.score);
            const currentUserRanking = assistantPerformance.findIndex(perf => perf.assistant.id === currentUser.id) + 1;
            document.getElementById('assistantHeaderRanking').textContent = `#${currentUserRanking}`;
            
            // Update main metrics
            document.getElementById('distributedLeads').textContent = monthlyContacts.length;
            document.getElementById('assistantConversions').textContent = monthlyConversions.length;
            
            // Calculate conversion rate
            const conversionRate = monthlyContacts.length > 0 ? ((monthlyConversions.length / monthlyContacts.length) * 100).toFixed(1) : 0;
            document.getElementById('assistantConversionRate').textContent = conversionRate + '%';
            
            // Update goal progress
            updateAssistantGoalProgress(monthlyConversions.length);
            
            // Update ranking
            updateAssistantRanking();
            
            // Update follow-up metrics
            updateFollowupMetrics(contacts);
            
            // Update performance insights
            updatePerformanceInsights(contacts, sellers, campaigns);
            
            // Update seller reminders table
            updateSellerRemindersTable();
            
            // Update leads table
            updateAssistantLeadsTable(contacts, sellers);
            
            // Update lost sales table
            updateLostSalesTable();
        }

        function updateAssistantGoalProgress(currentConversions) {
            const goals = allData.filter(item => item.type === 'goal');
            const currentGoal = goals.find(goal => {
                const goalDate = new Date(goal.createdAt);
                const currentDate = new Date();
                return goalDate.getMonth() === currentDate.getMonth() && goalDate.getFullYear() === currentDate.getFullYear();
            });
            
            if (currentGoal) {
                // Assistants have a goal of 50% of individual seller goal for conversions
                const assistantGoal = Math.ceil(currentGoal.individualGoal * 0.5);
                document.getElementById('assistantGoal').textContent = assistantGoal;
                
                const progress = assistantGoal > 0 ? ((currentConversions / assistantGoal) * 100).toFixed(1) : 0;
                document.getElementById('assistantProgress').textContent = `${progress}% concluído`;
            } else {
                document.getElementById('assistantGoal').textContent = 'Não definida';
                document.getElementById('assistantProgress').textContent = '0% concluído';
            }
        }

        function updateAssistantRanking() {
            const assistants = allData.filter(item => item.type === 'user' && item.role === 'assistant' && item.active);
            const currentMonth = new Date().getMonth();
            const currentYear = new Date().getFullYear();
            
            // Calculate performance score for each assistant
            const assistantPerformance = assistants.map(assistant => {
                const assistantContacts = allData.filter(item => 
                    item.type === 'contact' && 
                    item.assignedBy === assistant.id
                );
                
                const monthlyContacts = assistantContacts.filter(contact => {
                    const contactDate = new Date(contact.createdAt);
                    return contactDate.getMonth() === currentMonth && contactDate.getFullYear() === currentYear;
                });
                
                const conversions = assistantContacts.filter(contact => contact.status === 'vendido');
                const monthlyConversions = conversions.filter(conversion => {
                    const conversionDate = new Date(conversion.convertedAt);
                    return conversionDate.getMonth() === currentMonth && conversionDate.getFullYear() === currentYear;
                });
                
                const conversionRate = monthlyContacts.length > 0 ? (monthlyConversions.length / monthlyContacts.length) : 0;
                const revenue = conversions.reduce((sum, sale) => sum + (sale.value || 0), 0);
                
                // Performance score: leads distributed (40%) + conversion rate (40%) + revenue (20%)
                const score = (monthlyContacts.length * 0.4) + (conversionRate * 100 * 0.4) + (revenue / 1000 * 0.2);
                
                return {
                    assistant,
                    monthlyContacts: monthlyContacts.length,
                    monthlyConversions: monthlyConversions.length,
                    conversionRate,
                    revenue,
                    score
                };
            });
            
            // Sort by performance score
            assistantPerformance.sort((a, b) => b.score - a.score);
            
            // Find current user ranking
            const currentUserRanking = assistantPerformance.findIndex(perf => perf.assistant.id === currentUser.id) + 1;
            document.getElementById('assistantRanking').textContent = `#${currentUserRanking}`;
        }

        function updateFollowupMetrics(contacts) {
            const now = new Date();
            const threeDaysAgo = new Date(now.getTime() - (3 * 24 * 60 * 60 * 1000));
            const sevenDaysAgo = new Date(now.getTime() - (7 * 24 * 60 * 60 * 1000));
            
            const pendingLeads = contacts.filter(contact => 
                contact.status === 'contato' && 
                contact.clientStatus !== 'venda_perdida' &&
                new Date(contact.lastContactDate) < threeDaysAgo
            );
            
            const followupLeads = contacts.filter(contact => 
                contact.status === 'contato' && 
                contact.clientStatus === 'morno' &&
                new Date(contact.lastContactDate) >= threeDaysAgo
            );
            
            const noResponseLeads = contacts.filter(contact => 
                contact.clientStatus === 'sem_retorno' ||
                (contact.status === 'contato' && new Date(contact.lastContactDate) < sevenDaysAgo)
            );
            
            document.getElementById('pendingLeads').textContent = pendingLeads.length;
            document.getElementById('followupLeads').textContent = followupLeads.length;
            document.getElementById('noResponseLeads').textContent = noResponseLeads.length;
        }

        function updatePerformanceInsights(contacts, sellers, campaigns) {
            // Find best performing seller from assistant's leads
            const sellerPerformance = sellers.map(seller => {
                const sellerContacts = contacts.filter(c => c.sellerId === seller.id);
                const sellerSales = sellerContacts.filter(c => c.status === 'vendido');
                const conversionRate = sellerContacts.length > 0 ? (sellerSales.length / sellerContacts.length) : 0;
                
                return { seller, conversionRate, sales: sellerSales.length };
            }).filter(perf => perf.sales > 0);
            
            sellerPerformance.sort((a, b) => b.conversionRate - a.conversionRate);
            
            if (sellerPerformance.length > 0) {
                document.getElementById('bestSeller').textContent = `${sellerPerformance[0].seller.name} (${(sellerPerformance[0].conversionRate * 100).toFixed(1)}%)`;
            } else {
                document.getElementById('bestSeller').textContent = 'Nenhum ainda';
            }
            
            // Find top campaign
            const campaignPerformance = campaigns.map(campaign => {
                const campaignContacts = contacts.filter(c => c.campaignId === campaign.id);
                const campaignSales = campaignContacts.filter(c => c.status === 'vendido');
                
                return { campaign, leads: campaignContacts.length, sales: campaignSales.length };
            }).filter(perf => perf.leads > 0);
            
            campaignPerformance.sort((a, b) => b.sales - a.sales);
            
            if (campaignPerformance.length > 0) {
                document.getElementById('topCampaign').textContent = `${campaignPerformance[0].campaign.name} (${campaignPerformance[0].sales} vendas)`;
            } else {
                document.getElementById('topCampaign').textContent = 'Nenhuma ainda';
            }
            
            // Calculate average conversion time
            const conversions = contacts.filter(c => c.status === 'vendido' && c.convertedAt);
            if (conversions.length > 0) {
                const avgTime = conversions.reduce((sum, conversion) => {
                    const created = new Date(conversion.createdAt);
                    const converted = new Date(conversion.convertedAt);
                    const days = Math.floor((converted - created) / (1000 * 60 * 60 * 24));
                    return sum + days;
                }, 0) / conversions.length;
                
                document.getElementById('avgConversionTime').textContent = `${Math.round(avgTime)} dias`;
            } else {
                document.getElementById('avgConversionTime').textContent = 'N/A';
            }
            
            // Calculate revenue generated
            const revenue = contacts.filter(c => c.status === 'vendido').reduce((sum, sale) => sum + (sale.value || 0), 0);
            document.getElementById('assistantRevenue').textContent = `R$ ${revenue.toLocaleString('pt-BR', {minimumFractionDigits: 2})}`;
        }

        function updateAssistantLeadsTable(contacts, sellers) {
            const tbody = document.getElementById('assistantLeadsTable');
            tbody.innerHTML = '';
            
            // Sort contacts by creation date (newest first)
            const sortedContacts = contacts.sort((a, b) => new Date(b.createdAt) - new Date(a.createdAt));
            
            sortedContacts.forEach(contact => {
                const seller = sellers.find(s => s.id === contact.sellerId);
                const lastContactDate = contact.lastContactDate ? 
                    new Date(contact.lastContactDate).toLocaleDateString('pt-BR') : 
                    'Nunca';
                
                let clientStatusIcon = '';
                let clientStatusClass = '';
                let clientStatusText = '';
                
                switch(contact.clientStatus) {
                    case 'novo':
                        clientStatusIcon = '🆕';
                        clientStatusClass = 'text-green-600 bg-green-100';
                        clientStatusText = 'Novo';
                        break;
                    case 'em_andamento':
                        clientStatusIcon = '⏳';
                        clientStatusClass = 'text-blue-600 bg-blue-100';
                        clientStatusText = 'Em Andamento';
                        break;
                    case 'quente':
                        clientStatusIcon = '🔥';
                        clientStatusClass = 'text-red-600 bg-red-100';
                        clientStatusText = 'Quente';
                        break;
                    case 'morno':
                        clientStatusIcon = '🟡';
                        clientStatusClass = 'text-yellow-600 bg-yellow-100';
                        clientStatusText = 'Morno';
                        break;
                    case 'frio':
                        clientStatusIcon = '❄️';
                        clientStatusClass = 'text-blue-600 bg-blue-100';
                        clientStatusText = 'Frio';
                        break;
                    case 'sem_retorno':
                        clientStatusIcon = '📵';
                        clientStatusClass = 'text-gray-600 bg-gray-100';
                        clientStatusText = 'Sem Retorno';
                        break;
                    case 'venda_perdida':
                        clientStatusIcon = '❌';
                        clientStatusClass = 'text-red-800 bg-red-200';
                        clientStatusText = 'Venda Perdida';
                        break;
                    default:
                        clientStatusIcon = '❓';
                        clientStatusClass = 'text-gray-600 bg-gray-100';
                        clientStatusText = 'Indefinido';
                }
                
                const statusClass = contact.status === 'vendido' ? 'text-green-600' : 'text-yellow-600';
                const statusText = contact.status === 'vendido' ? 'Vendido' : 'Contato';
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${contact.contactName}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${seller ? seller.name : 'N/A'}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${contact.product}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm">
                        <span class="inline-flex items-center px-2 py-1 text-xs font-semibold rounded-full ${clientStatusClass}">
                            ${clientStatusIcon} ${clientStatusText}
                        </span>
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium ${statusClass}">${statusText}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${lastContactDate}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium">
                        ${contact.status !== 'vendido' ? 
                            `<button onclick="sendFollowupReminder('${contact.id}')" class="text-blue-600 hover:text-blue-900 mr-2">Follow-up</button>` :
                            `<div class="text-green-600 font-semibold">R$ ${(contact.value || 0).toLocaleString('pt-BR', {minimumFractionDigits: 2})}</div>`
                        }
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function updateGoalProgress(currentSales) {
            const goals = allData.filter(item => item.type === 'goal');
            const currentGoal = goals.find(goal => {
                const goalDate = new Date(goal.createdAt);
                const currentDate = new Date();
                return goalDate.getMonth() === currentDate.getMonth() && goalDate.getFullYear() === currentDate.getFullYear();
            });
            
            if (currentGoal) {
                // Exibir a meta individual definida pelo administrador
                document.getElementById('monthlyGoal').textContent = `${currentGoal.individualGoal} vendas`;
                
                // Calcular progresso baseado na meta individual
                const progress = currentGoal.individualGoal > 0 ? ((currentSales / currentGoal.individualGoal) * 100).toFixed(1) : 0;
                
                // Atualizar indicador de progresso se existir
                const progressElement = document.getElementById('sellerProgress');
                if (progressElement) {
                    progressElement.textContent = `${progress}% concluído`;
                }
            } else {
                document.getElementById('monthlyGoal').textContent = 'Não definida';
                const progressElement = document.getElementById('sellerProgress');
                if (progressElement) {
                    progressElement.textContent = '0% concluído';
                }
            }
        }

        function updateAdminGoals() {
            const goals = allData.filter(item => item.type === 'goal');
            const currentGoal = goals.find(goal => {
                const goalDate = new Date(goal.createdAt);
                const currentDate = new Date();
                return goalDate.getMonth() === currentDate.getMonth() && goalDate.getFullYear() === currentDate.getFullYear();
            });
            
            if (currentGoal) {
                document.getElementById('generalGoal').textContent = currentGoal.generalGoal;
                
                // Calculate current sales for the month
                const currentMonth = new Date().getMonth();
                const currentYear = new Date().getFullYear();
                const currentMonthSales = allData.filter(item => {
                    if (item.type !== 'contact' || item.status !== 'vendido') return false;
                    const saleDate = new Date(item.convertedAt);
                    return saleDate.getMonth() === currentMonth && saleDate.getFullYear() === currentYear;
                });
                
                document.getElementById('currentSales').textContent = currentMonthSales.length;
                
                const progress = currentGoal.generalGoal > 0 ? ((currentMonthSales.length / currentGoal.generalGoal) * 100).toFixed(1) : 0;
                document.getElementById('generalProgress').textContent = `${progress}%`;
            } else {
                document.getElementById('generalGoal').textContent = 'Não definida';
                document.getElementById('currentSales').textContent = '0';
                document.getElementById('generalProgress').textContent = '0%';
            }
        }

        function updateUserCounts(users) {
            const admins = users.filter(user => user.role === 'admin');
            const sellers = users.filter(user => user.role === 'seller');
            const assistants = users.filter(user => user.role === 'assistant');
            
            document.getElementById('totalAdmins').textContent = admins.length;
            document.getElementById('totalSellers').textContent = sellers.length;
            document.getElementById('totalAssistants').textContent = assistants.length;
            
            // Update users table
            updateUsersTable(users);
        }

        function updateUsersTable(users) {
            const tbody = document.getElementById('usersTable');
            tbody.innerHTML = '';
            
            users.forEach(user => {
                const createdDate = new Date(user.createdAt).toLocaleDateString('pt-BR');
                let roleText = '';
                let roleClass = '';
                
                switch(user.role) {
                    case 'admin':
                        roleText = 'Administrador';
                        roleClass = 'text-red-600 bg-red-100';
                        break;
                    case 'seller':
                        roleText = 'Vendedor';
                        roleClass = 'text-blue-600 bg-blue-100';
                        break;
                    case 'assistant':
                        roleText = 'Assistente';
                        roleClass = 'text-green-600 bg-green-100';
                        break;
                }
                
                const statusClass = user.active ? 'text-green-600 bg-green-100' : 'text-red-600 bg-red-100';
                const statusText = user.active ? 'Ativo' : 'Inativo';
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td class="px-4 py-3 text-sm font-medium text-gray-900">${user.name}</td>
                    <td class="px-4 py-3 text-sm">
                        <span class="inline-flex items-center px-2 py-1 text-xs font-semibold rounded-full ${roleClass}">
                            ${roleText}
                        </span>
                    </td>
                    <td class="px-4 py-3 text-sm">
                        <span class="inline-flex items-center px-2 py-1 text-xs font-semibold rounded-full ${statusClass}">
                            ${statusText}
                        </span>
                    </td>
                    <td class="px-4 py-3 text-sm text-gray-500">${createdDate}</td>
                    <td class="px-4 py-3 text-sm font-medium">
                        <button onclick="showEditUserModal('${user.id}')" class="text-blue-600 hover:text-blue-900 mr-2">Editar</button>
                        ${user.active ? 
                            `<button onclick="deactivateUser('${user.id}')" class="text-red-600 hover:text-red-900">Desativar</button>` :
                            `<button onclick="activateUser('${user.id}')" class="text-green-600 hover:text-green-900">Ativar</button>`
                        }
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        async function deactivateUser(userId) {
            const user = allData.find(item => item.id === userId);
            if (user && user.id !== currentUser.id) {
                const updatedUser = { ...user, active: false };
                
                if (window.dataSdk) {
                    const result = await window.dataSdk.update(updatedUser);
                    if (result.isOk) {
                        showMessage('Usuário desativado com sucesso!', 'success');
                    } else {
                        showMessage('Erro ao desativar usuário', 'error');
                    }
                }
            } else if (user.id === currentUser.id) {
                showMessage('Você não pode desativar sua própria conta', 'error');
            }
        }

        async function activateUser(userId) {
            const user = allData.find(item => item.id === userId);
            if (user) {
                const updatedUser = { ...user, active: true };
                
                if (window.dataSdk) {
                    const result = await window.dataSdk.update(updatedUser);
                    if (result.isOk) {
                        showMessage('Usuário ativado com sucesso!', 'success');
                    } else {
                        showMessage('Erro ao ativar usuário', 'error');
                    }
                }
            }
        }

        function updateAdminCommissionDisplay() {
            const rate = defaultConfig.commission_rate;
            const stores = allData.filter(item => item.type === 'store' && item.active);
            const campaigns = allData.filter(item => item.type === 'campaign' && item.active);
            
            document.getElementById('currentCommission').textContent = `${rate}%`;
            document.getElementById('totalStores').textContent = stores.length;
            document.getElementById('totalCampaigns').textContent = campaigns.length;
        }

        function updateSellersTable(sellers, contacts, sales, monthlyContacts, monthlySales) {
            const tbody = document.getElementById('sellersTable');
            tbody.innerHTML = '';
            
            // Get current goal
            const goals = allData.filter(item => item.type === 'goal');
            const currentGoal = goals.find(goal => {
                const goalDate = new Date(goal.createdAt);
                const currentDate = new Date();
                return goalDate.getMonth() === currentDate.getMonth() && goalDate.getFullYear() === currentDate.getFullYear();
            });
            
            const currentMonth = new Date().getMonth();
            const currentYear = new Date().getFullYear();
            
            sellers.forEach(seller => {
                // Debug: Log seller data
                console.log(`Processing seller: ${seller.name} (ID: ${seller.id})`);
                
                // Monthly data - ensure proper filtering
                const sellerMonthlyContacts = monthlyContacts.filter(c => {
                    const match = c.sellerId && c.sellerId === seller.id;
                    if (match) console.log(`Found monthly contact for ${seller.name}:`, c);
                    return match;
                });
                
                const sellerMonthlySales = monthlySales.filter(s => {
                    const match = s.sellerId && s.sellerId === seller.id;
                    if (match) console.log(`Found monthly sale for ${seller.name}:`, s);
                    return match;
                });
                
                const monthlyConversionRate = sellerMonthlyContacts.length > 0 ? ((sellerMonthlySales.length / sellerMonthlyContacts.length) * 100).toFixed(1) : 0;
                const monthlyRevenue = sellerMonthlySales.reduce((sum, sale) => sum + (sale.value || 0), 0);
                
                // Total data - ensure proper filtering
                const sellerTotalContacts = contacts.filter(c => c.sellerId && c.sellerId === seller.id);
                const sellerTotalSales = sales.filter(s => s.sellerId && s.sellerId === seller.id);
                const totalRevenue = sellerTotalSales.reduce((sum, sale) => sum + (sale.value || 0), 0);
                
                console.log(`${seller.name} stats - Monthly: ${sellerMonthlyContacts.length} contacts, ${sellerMonthlySales.length} sales | Total: ${sellerTotalContacts.length} contacts, ${sellerTotalSales.length} sales`);
                
                // Goal progress
                const individualGoal = currentGoal ? currentGoal.individualGoal : 0;
                const goalProgress = individualGoal > 0 ? ((sellerMonthlySales.length / individualGoal) * 100).toFixed(1) : 0;
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td class="px-4 py-3 text-sm font-medium text-gray-900">${seller.name}</td>
                    <td class="px-4 py-3 text-sm text-center">
                        <span class="text-blue-600 font-semibold">${individualGoal}</span>
                        <div class="text-xs text-gray-500">vendas</div>
                    </td>
                    <td class="px-4 py-3 text-sm text-center text-gray-600">${sellerMonthlyContacts.length}</td>
                    <td class="px-4 py-3 text-sm text-center">
                        <span class="font-semibold text-green-600">${sellerMonthlySales.length}</span>
                    </td>
                    <td class="px-4 py-3 text-sm text-center">
                        <div class="flex items-center justify-center">
                            <div class="w-16 bg-gray-200 rounded-full h-2 mr-2">
                                <div class="bg-blue-600 h-2 rounded-full" style="width: ${Math.min(goalProgress, 100)}%"></div>
                            </div>
                            <span class="text-xs font-medium ${goalProgress >= 100 ? 'text-green-600' : 'text-gray-600'}">${goalProgress}%</span>
                        </div>
                    </td>
                    <td class="px-4 py-3 text-sm text-center text-purple-600">${monthlyConversionRate}%</td>
                    <td class="px-4 py-3 text-sm text-center">
                        <span class="font-semibold text-green-600">R$ ${monthlyRevenue.toLocaleString('pt-BR', {minimumFractionDigits: 2})}</span>
                    </td>
                    <td class="px-4 py-3 text-sm text-center">
                        <div class="text-xs text-gray-500">${sellerTotalSales.length} vendas</div>
                        <div class="text-xs text-gray-400">R$ ${totalRevenue.toLocaleString('pt-BR', {minimumFractionDigits: 2})}</div>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function updateStorePerformanceReport() {
            const stores = allData.filter(item => item.type === 'store' && item.active);
            const contacts = allData.filter(item => item.type === 'contact');
            const sales = contacts.filter(contact => contact.status === 'vendido' && contact.storeId);
            
            // Calculate overall metrics
            let totalRevenue = 0;
            let totalSales = 0;
            let bestStore = null;
            let bestPerformance = 0;
            
            // Update summary cards
            document.getElementById('totalActiveStores').textContent = stores.length;
            
            const storePerformanceData = stores.map(store => {
                // Get all contacts that showed interest in this store
                const storeContacts = contacts.filter(c => c.storeId === store.id);
                
                // Get sales that were actually paid at this store
                const storeSales = sales.filter(s => s.storeId === store.id);
                
                const storeRevenue = storeSales.reduce((sum, sale) => sum + (sale.value || 0), 0);
                const conversionRate = storeContacts.length > 0 ? (storeSales.length / storeContacts.length) : 0;
                const averageTicket = storeSales.length > 0 ? (storeRevenue / storeSales.length) : 0;
                
                // Performance score: conversion rate (60%) + average ticket relative to overall (40%)
                const performanceScore = (conversionRate * 60) + ((averageTicket / 1000) * 40);
                
                totalRevenue += storeRevenue;
                totalSales += storeSales.length;
                
                if (performanceScore > bestPerformance) {
                    bestPerformance = performanceScore;
                    bestStore = store;
                }
                
                return {
                    store,
                    contacts: storeContacts.length,
                    sales: storeSales.length,
                    revenue: storeRevenue,
                    conversionRate,
                    averageTicket,
                    performanceScore
                };
            });
            
            // Update summary metrics
            document.getElementById('bestPerformingStore').textContent = bestStore ? bestStore.name : '-';
            document.getElementById('totalStoreRevenue').textContent = `R$ ${totalRevenue.toLocaleString('pt-BR', {minimumFractionDigits: 2})}`;
            
            const overallAverageTicket = totalSales > 0 ? (totalRevenue / totalSales) : 0;
            document.getElementById('averageTicketAllStores').textContent = `R$ ${overallAverageTicket.toLocaleString('pt-BR', {minimumFractionDigits: 2})}`;
            
            // Update performance table
            const tbody = document.getElementById('storePerformanceTable');
            tbody.innerHTML = '';
            
            // Sort by performance score
            storePerformanceData.sort((a, b) => b.performanceScore - a.performanceScore);
            
            storePerformanceData.forEach((data, index) => {
                const position = index + 1;
                let performanceIcon = '';
                let performanceClass = '';
                
                if (position === 1) {
                    performanceIcon = '🥇';
                    performanceClass = 'text-yellow-600 font-bold';
                } else if (position === 2) {
                    performanceIcon = '🥈';
                    performanceClass = 'text-gray-500 font-bold';
                } else if (position === 3) {
                    performanceIcon = '🥉';
                    performanceClass = 'text-orange-600 font-bold';
                } else if (data.performanceScore >= 50) {
                    performanceIcon = '✅';
                    performanceClass = 'text-green-600';
                } else if (data.performanceScore >= 25) {
                    performanceIcon = '⚠️';
                    performanceClass = 'text-yellow-600';
                } else {
                    performanceIcon = '🚨';
                    performanceClass = 'text-red-600';
                }
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td class="px-4 py-3 text-sm font-medium text-gray-900">
                        <div class="font-semibold">${data.store.name}</div>
                        <div class="text-xs text-gray-500">${data.store.address}</div>
                    </td>
                    <td class="px-4 py-3 text-sm text-gray-500">
                        <span class="inline-flex items-center px-2 py-1 text-xs font-semibold rounded-full ${data.store.storeType === 'matriz' ? 'bg-blue-100 text-blue-800' : 'bg-green-100 text-green-800'}">
                            ${data.store.storeType === 'matriz' ? '🏢 Matriz' : '🏪 Filial'}
                        </span>
                    </td>
                    <td class="px-4 py-3 text-sm text-center text-blue-600 font-semibold">${data.contacts}</td>
                    <td class="px-4 py-3 text-sm text-center text-green-600 font-semibold">${data.sales}</td>
                    <td class="px-4 py-3 text-sm text-center text-purple-600">${(data.conversionRate * 100).toFixed(1)}%</td>
                    <td class="px-4 py-3 text-sm text-center text-green-600 font-semibold">R$ ${data.revenue.toLocaleString('pt-BR', {minimumFractionDigits: 2})}</td>
                    <td class="px-4 py-3 text-sm text-center text-orange-600">R$ ${data.averageTicket.toLocaleString('pt-BR', {minimumFractionDigits: 2})}</td>
                    <td class="px-4 py-3 text-sm text-center">
                        <div class="flex items-center justify-center">
                            <span class="${performanceClass} text-lg mr-2">${performanceIcon}</span>
                            <div class="text-xs">
                                <div class="font-semibold">#${position}</div>
                                <div class="text-gray-500">${data.performanceScore.toFixed(1)} pts</div>
                            </div>
                        </div>
                    </td>
                `;
                tbody.appendChild(row);
            });
            
            if (stores.length === 0) {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td colspan="8" class="px-4 py-8 text-center text-gray-500">
                        <div class="text-4xl mb-2">🏪</div>
                        <div class="font-medium">Nenhuma loja cadastrada</div>
                        <div class="text-xs text-gray-400 mt-1">Cadastre lojas para acompanhar a performance</div>
                    </td>
                `;
                tbody.appendChild(row);
            }
        }

        function updateRecentSalesTable(sales, sellers) {
            const tbody = document.getElementById('recentSalesTable');
            tbody.innerHTML = '';
            
            const campaigns = allData.filter(item => item.type === 'campaign' && item.active);
            const stores = allData.filter(item => item.type === 'store' && item.active);
            
            const recentSales = sales
                .sort((a, b) => new Date(b.convertedAt) - new Date(a.convertedAt))
                .slice(0, 10);
            
            recentSales.forEach(sale => {
                const seller = sellers.find(s => s.id === sale.sellerId);
                const campaign = campaigns.find(c => c.id === sale.campaignId);
                const store = stores.find(s => s.id === sale.storeId);
                const date = new Date(sale.convertedAt).toLocaleDateString('pt-BR');
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${date}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${seller ? seller.name : 'N/A'}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${sale.contactName}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${sale.product}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">R$ ${(sale.value || 0).toLocaleString('pt-BR', {minimumFractionDigits: 2})}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${store ? store.name : 'N/A'}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${campaign ? campaign.name : 'Direto'}</td>
                `;
                tbody.appendChild(row);
            });
        }

        function updateMyContactsTable(contacts) {
            const tbody = document.getElementById('myContactsTable');
            tbody.innerHTML = '';
            
            // Debug: Log contacts being processed
            console.log('Updating my contacts table with:', contacts);
            
            // Sort contacts by creation date (newest first)
            const sortedContacts = contacts.sort((a, b) => new Date(b.createdAt) - new Date(a.createdAt));
            
            sortedContacts.forEach(contact => {
                const row = document.createElement('tr');
                const statusClass = contact.status === 'vendido' ? 'text-green-600' : 'text-yellow-600';
                const statusText = contact.status === 'vendido' ? 'Vendido' : 'Contato';
                
                let clientStatusIcon = '';
                let clientStatusClass = '';
                let clientStatusText = '';
                
                switch(contact.clientStatus) {
                    case 'novo':
                        clientStatusIcon = '🆕';
                        clientStatusClass = 'text-green-600 bg-green-100';
                        clientStatusText = 'Novo';
                        break;
                    case 'em_andamento':
                        clientStatusIcon = '⏳';
                        clientStatusClass = 'text-blue-600 bg-blue-100';
                        clientStatusText = 'Em Andamento';
                        break;
                    case 'quente':
                        clientStatusIcon = '🔥';
                        clientStatusClass = 'text-red-600 bg-red-100';
                        clientStatusText = 'Quente';
                        break;
                    case 'morno':
                        clientStatusIcon = '🟡';
                        clientStatusClass = 'text-yellow-600 bg-yellow-100';
                        clientStatusText = 'Morno';
                        break;
                    case 'frio':
                        clientStatusIcon = '❄️';
                        clientStatusClass = 'text-blue-600 bg-blue-100';
                        clientStatusText = 'Frio';
                        break;
                    case 'sem_retorno':
                        clientStatusIcon = '📵';
                        clientStatusClass = 'text-gray-600 bg-gray-100';
                        clientStatusText = 'Sem Retorno';
                        break;
                    case 'venda_perdida':
                        clientStatusIcon = '❌';
                        clientStatusClass = 'text-red-800 bg-red-200';
                        clientStatusText = 'Venda Perdida';
                        break;
                    default:
                        clientStatusIcon = '❓';
                        clientStatusClass = 'text-gray-600 bg-gray-100';
                        clientStatusText = 'Indefinido';
                }
                
                const lastContactDate = contact.lastContactDate ? 
                    new Date(contact.lastContactDate).toLocaleDateString('pt-BR') : 
                    'Nunca';
                
                row.innerHTML = `
                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${contact.contactName}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                        <div>
                            <a href="https://wa.me/55${contact.contactPhone.replace(/\D/g, '')}" target="_blank" rel="noopener noreferrer" class="text-green-600 hover:text-green-800 font-medium">
                                📱 ${contact.contactPhone}
                            </a>
                        </div>
                        ${contact.contactEmail ? `<div class="text-xs text-gray-400">${contact.contactEmail}</div>` : ''}
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${contact.product}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm">
                        <span class="inline-flex items-center px-2 py-1 text-xs font-semibold rounded-full ${clientStatusClass}">
                            ${clientStatusIcon} ${clientStatusText}
                        </span>
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium ${statusClass}">${statusText}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${lastContactDate}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium">
                        ${contact.status !== 'vendido' && contact.status !== 'devolvido' ? 
                            `<div class="flex flex-col space-y-1">
                                <div class="flex space-x-2">
                                    <button onclick="showUpdateStatusModal('${contact.id}')" class="text-blue-600 hover:text-blue-900 text-xs">Atualizar</button>
                                    <button onclick="showConvertModal('${contact.id}')" class="text-green-600 hover:text-green-900 text-xs">Vender</button>
                                    <button onclick="showSetReminderModal('${contact.id}')" class="text-purple-600 hover:text-purple-900 text-xs">⏰ Lembrete</button>
                                </div>
                                ${contact.assignedBy ? `<button onclick="showReturnContactModal('${contact.id}')" class="text-orange-600 hover:text-orange-900 text-xs">Devolver</button>` : ''}
                             </div>` :
                            contact.status === 'vendido' ?
                            `<div class="text-green-600">
                                <div class="font-semibold">R$ ${(contact.value || 0).toLocaleString('pt-BR', {minimumFractionDigits: 2})}</div>
                                ${contact.orderNumber ? `<div class="text-xs text-gray-500">Pedido: ${contact.orderNumber}</div>` : ''}
                             </div>` :
                            `<div class="text-orange-600 font-semibold">Devolvido</div>`
                        }
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function updateLostSalesTable() {
            const lostSales = allData.filter(item => 
                item.type === 'lost_sale' && 
                item.assistantId === currentUser.id && 
                item.needsReview
            );
            
            const contacts = allData.filter(item => item.type === 'contact');
            const users = allData.filter(item => item.type === 'user' && item.active);
            const sellers = users.filter(user => user.role === 'seller');
            
            const tbody = document.getElementById('lostSalesTable');
            tbody.innerHTML = '';
            
            lostSales.forEach(lostSale => {
                const contact = contacts.find(c => c.id === lostSale.contactId);
                const seller = sellers.find(s => s.id === lostSale.sellerId);
                
                if (!contact) return;
                
                const date = new Date(lostSale.createdAt).toLocaleDateString('pt-BR');
                
                let reasonText = '';
                switch(lostSale.lostSaleReason) {
                    case 'preco_alto': reasonText = 'Preço alto'; break;
                    case 'concorrencia': reasonText = 'Concorrência'; break;
                    case 'prazo_entrega': reasonText = 'Prazo entrega'; break;
                    case 'condicoes_pagamento': reasonText = 'Condições pagamento'; break;
                    case 'qualidade_produto': reasonText = 'Dúvidas qualidade'; break;
                    case 'atendimento': reasonText = 'Problemas atendimento'; break;
                    case 'mudou_ideia': reasonText = 'Mudou de ideia'; break;
                    case 'orcamento_insuficiente': reasonText = 'Orçamento insuficiente'; break;
                    default: reasonText = 'Outros motivos';
                }
                
                const row = document.createElement('tr');
                row.className = 'bg-red-50';
                row.innerHTML = `
                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">
                        <div>${contact.contactName}</div>
                        <div class="text-xs text-gray-500">${contact.contactPhone}</div>
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${seller ? seller.name : 'N/A'}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                        <div class="font-medium">${reasonText}</div>
                        <div class="text-xs text-gray-400">${contact.product}</div>
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${date}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm">
                        <span class="inline-flex items-center px-2 py-1 text-xs font-semibold rounded-full bg-red-100 text-red-800">
                            🚨 Aguardando Revisão
                        </span>
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium">
                        <button onclick="showAssistantLostSaleModal('${lostSale.id}')" class="bg-red-600 hover:bg-red-700 text-white px-3 py-1 rounded text-xs font-medium">
                            Revisar Agora
                        </button>
                    </td>
                `;
                tbody.appendChild(row);
            });
            
            // Show notification if there are pending reviews
            if (lostSales.length > 0) {
                const notification = document.createElement('div');
                notification.className = 'fixed top-4 right-4 z-50 bg-red-600 text-white px-4 py-2 rounded-md font-medium';
                notification.textContent = `${lostSales.length} venda(s) perdida(s) aguardando sua revisão!`;
                document.body.appendChild(notification);
                
                setTimeout(() => {
                    if (notification.parentNode) {
                        notification.parentNode.removeChild(notification);
                    }
                }, 5000);
            }
        }

        function updateAssistantRankingTable() {
            const assistants = allData.filter(item => item.type === 'user' && item.role === 'assistant' && item.active);
            const currentMonth = new Date().getMonth();
            const currentYear = new Date().getFullYear();
            
            // Calculate performance for each assistant
            const assistantPerformance = assistants.map(assistant => {
                const assistantContacts = allData.filter(item => 
                    item.type === 'contact' && 
                    item.assignedBy === assistant.id
                );
                
                const monthlyContacts = assistantContacts.filter(contact => {
                    const contactDate = new Date(contact.createdAt);
                    return contactDate.getMonth() === currentMonth && contactDate.getFullYear() === currentYear;
                });
                
                const conversions = assistantContacts.filter(contact => contact.status === 'vendido');
                const monthlyConversions = conversions.filter(conversion => {
                    const conversionDate = new Date(conversion.convertedAt);
                    return conversionDate.getMonth() === currentMonth && conversionDate.getFullYear() === currentYear;
                });
                
                const conversionRate = monthlyContacts.length > 0 ? (monthlyConversions.length / monthlyContacts.length) : 0;
                const revenue = conversions.reduce((sum, sale) => sum + (sale.value || 0), 0);
                
                // Performance score: leads distributed (40%) + conversion rate (40%) + revenue (20%)
                const score = (monthlyContacts.length * 0.4) + (conversionRate * 100 * 0.4) + (revenue / 1000 * 0.2);
                
                // Get goal for assistant
                const goals = allData.filter(item => item.type === 'goal');
                const currentGoal = goals.find(goal => {
                    const goalDate = new Date(goal.createdAt);
                    return goalDate.getMonth() === currentMonth && goalDate.getFullYear() === currentYear;
                });
                
                const assistantGoal = currentGoal ? Math.ceil(currentGoal.individualGoal * 0.5) : 0;
                
                return {
                    assistant,
                    monthlyContacts: monthlyContacts.length,
                    monthlyConversions: monthlyConversions.length,
                    conversionRate,
                    revenue,
                    score,
                    goal: assistantGoal
                };
            });
            
            // Sort by performance score
            assistantPerformance.sort((a, b) => b.score - a.score);
            
            const tbody = document.getElementById('assistantRankingTable');
            tbody.innerHTML = '';
            
            assistantPerformance.forEach((perf, index) => {
                const position = index + 1;
                const progressGoal = perf.goal > 0 ? ((perf.monthlyConversions / perf.goal) * 100).toFixed(1) : 0;
                
                let positionIcon = '';
                let positionClass = '';
                
                switch(position) {
                    case 1:
                        positionIcon = '🥇';
                        positionClass = 'text-yellow-600 font-bold';
                        break;
                    case 2:
                        positionIcon = '🥈';
                        positionClass = 'text-gray-500 font-bold';
                        break;
                    case 3:
                        positionIcon = '🥉';
                        positionClass = 'text-orange-600 font-bold';
                        break;
                    default:
                        positionIcon = `#${position}`;
                        positionClass = 'text-gray-700';
                }
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td class="px-4 py-3 text-sm font-medium ${positionClass}">
                        ${positionIcon}
                    </td>
                    <td class="px-4 py-3 text-sm font-medium text-gray-900">${perf.assistant.name}</td>
                    <td class="px-4 py-3 text-sm text-center">
                        <span class="text-orange-600 font-semibold">${perf.goal}</span>
                        <div class="text-xs text-gray-500">conversões</div>
                    </td>
                    <td class="px-4 py-3 text-sm text-center text-blue-600 font-semibold">${perf.monthlyContacts}</td>
                    <td class="px-4 py-3 text-sm text-center text-green-600 font-semibold">${perf.monthlyConversions}</td>
                    <td class="px-4 py-3 text-sm text-center text-purple-600">${(perf.conversionRate * 100).toFixed(1)}%</td>
                    <td class="px-4 py-3 text-sm text-center text-green-600">R$ ${perf.revenue.toLocaleString('pt-BR', {minimumFractionDigits: 2})}</td>
                    <td class="px-4 py-3 text-sm text-center">
                        <div class="flex items-center justify-center">
                            <div class="w-16 bg-gray-200 rounded-full h-2 mr-2">
                                <div class="bg-indigo-600 h-2 rounded-full" style="width: ${Math.min(perf.score, 100)}%"></div>
                            </div>
                            <span class="text-xs font-medium text-indigo-600">${perf.score.toFixed(1)}</span>
                        </div>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function updateMyRemindersTable() {
            const reminders = allData.filter(item => 
                item.type === 'reminder' && 
                item.sellerId === currentUser.id
            );
            
            const contacts = allData.filter(item => item.type === 'contact');
            const tbody = document.getElementById('myRemindersTable');
            tbody.innerHTML = '';
            
            const now = new Date();
            const twentyFourHoursFromNow = new Date(now.getTime() + (24 * 60 * 60 * 1000));
            
            // Check for overdue reminders and block seller if needed
            checkAndBlockSellerForOverdueReminders();
            
            reminders.forEach(reminder => {
                const contact = contacts.find(c => c.id === reminder.contactId);
                if (!contact) return;
                
                const reminderDate = new Date(reminder.reminderDate);
                const isActive = reminderDate <= twentyFourHoursFromNow && !reminder.reminderCompleted;
                const isOverdue = reminderDate < now && !reminder.reminderCompleted;
                
                // Only show active or recently completed reminders
                if (!isActive && reminder.reminderCompleted && 
                    new Date(reminder.completedAt) < new Date(now.getTime() - (7 * 24 * 60 * 60 * 1000))) {
                    return;
                }
                
                let reminderTypeText = '';
                switch(reminder.reminderType) {
                    case 'fechar_venda': reminderTypeText = '💰 Fechar Venda'; break;
                    case 'followup': reminderTypeText = '📞 Follow-up'; break;
                    case 'apresentacao': reminderTypeText = '📊 Apresentação'; break;
                    case 'negociacao': reminderTypeText = '🤝 Negociação'; break;
                    case 'visita_tecnica': reminderTypeText = '🔧 Visita Técnica'; break;
                    case 'envio_proposta': reminderTypeText = '📋 Envio de Proposta'; break;
                    default: reminderTypeText = '📝 Outros';
                }
                
                let statusBadge = '';
                let statusClass = '';
                
                if (reminder.reminderCompleted) {
                    statusBadge = '✅ Concluído';
                    statusClass = 'bg-green-100 text-green-800';
                } else if (isOverdue) {
                    statusBadge = '🚨 Em Atraso';
                    statusClass = 'bg-red-100 text-red-800';
                } else if (isActive) {
                    statusBadge = '⏰ Ativo';
                    statusClass = 'bg-yellow-100 text-yellow-800';
                } else {
                    statusBadge = '⏳ Aguardando';
                    statusClass = 'bg-blue-100 text-blue-800';
                }
                
                const row = document.createElement('tr');
                row.className = isOverdue ? 'bg-red-50' : '';
                row.innerHTML = `
                    <td class="px-4 py-3 text-sm font-medium text-gray-900">
                        <div>${contact.contactName}</div>
                        <div class="text-xs text-gray-500">${contact.product}</div>
                    </td>
                    <td class="px-4 py-3 text-sm text-gray-500">${reminderTypeText}</td>
                    <td class="px-4 py-3 text-sm text-gray-500">
                        <div class="font-medium">${reminderDate.toLocaleDateString('pt-BR')}</div>
                        <div class="text-xs text-gray-400">${reminderDate.toLocaleTimeString('pt-BR', {hour: '2-digit', minute: '2-digit'})}</div>
                    </td>
                    <td class="px-4 py-3 text-sm">
                        <span class="inline-flex items-center px-2 py-1 text-xs font-semibold rounded-full ${statusClass}">
                            ${statusBadge}
                        </span>
                    </td>
                    <td class="px-4 py-3 text-sm text-gray-500 max-w-48 truncate">${reminder.reminderNotes}</td>
                    <td class="px-4 py-3 text-sm font-medium">
                        ${!reminder.reminderCompleted && isActive ? 
                            `<button onclick="showCompleteReminderModal('${reminder.id}')" class="bg-green-600 hover:bg-green-700 text-white px-3 py-1 rounded text-xs font-medium">
                                Marcar Concluído
                            </button>` :
                            reminder.reminderCompleted ?
                            `<div class="text-green-600 text-xs">
                                <div>Concluído em:</div>
                                <div>${new Date(reminder.completedAt).toLocaleDateString('pt-BR')}</div>
                            </div>` :
                            `<div class="text-gray-400 text-xs">Aguardando data</div>`
                        }
                    </td>
                `;
                tbody.appendChild(row);
            });
            
            if (reminders.length === 0) {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td colspan="6" class="px-4 py-8 text-center text-gray-500">
                        <div class="text-4xl mb-2">⏰</div>
                        <div>Nenhum lembrete criado ainda</div>
                        <div class="text-xs text-gray-400 mt-1">Use o botão "⏰ Lembrete" nos seus contatos para criar lembretes</div>
                    </td>
                `;
                tbody.appendChild(row);
            }
        }

        function updateOverdueRemindersTable() {
            const reminders = allData.filter(item => item.type === 'reminder');
            const contacts = allData.filter(item => item.type === 'contact');
            const users = allData.filter(item => item.type === 'user' && item.active);
            const sellers = users.filter(user => user.role === 'seller');
            
            const tbody = document.getElementById('overdueRemindersTable');
            tbody.innerHTML = '';
            
            const now = new Date();
            
            const overdueReminders = reminders.filter(reminder => {
                const reminderDate = new Date(reminder.reminderDate);
                return reminderDate < now && !reminder.reminderCompleted;
            });
            
            overdueReminders.forEach(reminder => {
                const contact = contacts.find(c => c.id === reminder.contactId);
                const seller = sellers.find(s => s.id === reminder.sellerId);
                
                if (!contact || !seller) return;
                
                const reminderDate = new Date(reminder.reminderDate);
                const daysOverdue = Math.floor((now - reminderDate) / (1000 * 60 * 60 * 24));
                
                let reminderTypeText = '';
                switch(reminder.reminderType) {
                    case 'fechar_venda': reminderTypeText = '💰 Fechar Venda'; break;
                    case 'followup': reminderTypeText = '📞 Follow-up'; break;
                    case 'apresentacao': reminderTypeText = '📊 Apresentação'; break;
                    case 'negociacao': reminderTypeText = '🤝 Negociação'; break;
                    case 'visita_tecnica': reminderTypeText = '🔧 Visita Técnica'; break;
                    case 'envio_proposta': reminderTypeText = '📋 Envio de Proposta'; break;
                    default: reminderTypeText = '📝 Outros';
                }
                
                const isBlocked = seller.blockedFromReceiving;
                
                const row = document.createElement('tr');
                row.className = 'bg-red-50';
                row.innerHTML = `
                    <td class="px-4 py-3 text-sm font-medium text-gray-900">
                        <div class="font-semibold">${seller.name}</div>
                        <div class="text-xs text-gray-500">${seller.email || 'Sem email'}</div>
                    </td>
                    <td class="px-4 py-3 text-sm text-gray-500">
                        <div class="font-medium">${contact.contactName}</div>
                        <div class="text-xs text-gray-400">${contact.product}</div>
                    </td>
                    <td class="px-4 py-3 text-sm text-gray-500">${reminderTypeText}</td>
                    <td class="px-4 py-3 text-sm text-gray-500">
                        <div class="font-medium">${reminderDate.toLocaleDateString('pt-BR')}</div>
                        <div class="text-xs text-gray-400">${reminderDate.toLocaleTimeString('pt-BR', {hour: '2-digit', minute: '2-digit'})}</div>
                    </td>
                    <td class="px-4 py-3 text-sm text-center">
                        <span class="inline-flex items-center px-2 py-1 text-xs font-semibold rounded-full bg-red-100 text-red-800">
                            ${daysOverdue} dia${daysOverdue !== 1 ? 's' : ''}
                        </span>
                    </td>
                    <td class="px-4 py-3 text-sm text-center">
                        <span class="inline-flex items-center px-2 py-1 text-xs font-semibold rounded-full ${isBlocked ? 'bg-red-100 text-red-800' : 'bg-yellow-100 text-yellow-800'}">
                            ${isBlocked ? '🚫 Bloqueado' : '⚠️ Pendente'}
                        </span>
                    </td>
                    <td class="px-4 py-3 text-sm font-medium">
                        <button onclick="contactSellerAboutReminder('${seller.id}', '${reminder.id}')" class="bg-blue-600 hover:bg-blue-700 text-white px-3 py-1 rounded text-xs font-medium mr-2">
                            Contatar
                        </button>
                        ${isBlocked ? 
                            `<button onclick="unblockSeller('${seller.id}')" class="bg-green-600 hover:bg-green-700 text-white px-3 py-1 rounded text-xs font-medium">
                                Desbloquear
                            </button>` : ''
                        }
                    </td>
                `;
                tbody.appendChild(row);
            });
            
            if (overdueReminders.length === 0) {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td colspan="7" class="px-4 py-8 text-center text-gray-500">
                        <div class="text-4xl mb-2">✅</div>
                        <div class="font-medium">Nenhum lembrete em atraso</div>
                        <div class="text-xs text-gray-400 mt-1">Todos os vendedores estão em dia com seus lembretes</div>
                    </td>
                `;
                tbody.appendChild(row);
            }
        }

        function updateSellerRemindersTable() {
            const reminders = allData.filter(item => 
                item.type === 'reminder' && 
                item.assistantId === currentUser.id
            );
            
            const contacts = allData.filter(item => item.type === 'contact');
            const users = allData.filter(item => item.type === 'user' && item.active);
            const sellers = users.filter(user => user.role === 'seller');
            
            const tbody = document.getElementById('sellerRemindersTable');
            tbody.innerHTML = '';
            
            const now = new Date();
            const twentyFourHoursFromNow = new Date(now.getTime() + (24 * 60 * 60 * 1000));
            
            // Show active and recent reminders
            const relevantReminders = reminders.filter(reminder => {
                const reminderDate = new Date(reminder.reminderDate);
                return reminderDate <= twentyFourHoursFromNow || 
                       (reminder.reminderCompleted && new Date(reminder.completedAt) > new Date(now.getTime() - (7 * 24 * 60 * 60 * 1000)));
            });
            
            relevantReminders.forEach(reminder => {
                const contact = contacts.find(c => c.id === reminder.contactId);
                const seller = sellers.find(s => s.id === reminder.sellerId);
                
                if (!contact || !seller) return;
                
                const reminderDate = new Date(reminder.reminderDate);
                const isOverdue = reminderDate < now && !reminder.reminderCompleted;
                
                let reminderTypeText = '';
                switch(reminder.reminderType) {
                    case 'fechar_venda': reminderTypeText = '💰 Fechar Venda'; break;
                    case 'followup': reminderTypeText = '📞 Follow-up'; break;
                    case 'apresentacao': reminderTypeText = '📊 Apresentação'; break;
                    case 'negociacao': reminderTypeText = '🤝 Negociação'; break;
                    case 'visita_tecnica': reminderTypeText = '🔧 Visita Técnica'; break;
                    case 'envio_proposta': reminderTypeText = '📋 Envio de Proposta'; break;
                    default: reminderTypeText = '📝 Outros';
                }
                
                let statusBadge = '';
                let statusClass = '';
                
                if (reminder.reminderCompleted) {
                    statusBadge = '✅ Concluído';
                    statusClass = 'bg-green-100 text-green-800';
                } else if (isOverdue) {
                    statusBadge = '🚨 Em Atraso';
                    statusClass = 'bg-red-100 text-red-800';
                } else {
                    statusBadge = '⏰ Ativo';
                    statusClass = 'bg-yellow-100 text-yellow-800';
                }
                
                const row = document.createElement('tr');
                row.className = isOverdue ? 'bg-red-50' : '';
                row.innerHTML = `
                    <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">
                        <div class="font-semibold">${seller.name}</div>
                        ${seller.blockedFromReceiving ? '<div class="text-xs text-red-600">🚫 Bloqueado</div>' : ''}
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                        <div class="font-medium">${contact.contactName}</div>
                        <div class="text-xs text-gray-400">${contact.product}</div>
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${reminderTypeText}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                        <div class="font-medium">${reminderDate.toLocaleDateString('pt-BR')}</div>
                        <div class="text-xs text-gray-400">${reminderDate.toLocaleTimeString('pt-BR', {hour: '2-digit', minute: '2-digit'})}</div>
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap text-sm">
                        <span class="inline-flex items-center px-2 py-1 text-xs font-semibold rounded-full ${statusClass}">
                            ${statusBadge}
                        </span>
                    </td>
                    <td class="px-6 py-4 text-sm text-gray-500 max-w-48 truncate">${reminder.reminderNotes}</td>
                `;
                tbody.appendChild(row);
            });
            
            if (relevantReminders.length === 0) {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td colspan="6" class="px-6 py-8 text-center text-gray-500">
                        <div class="text-4xl mb-2">⏰</div>
                        <div>Nenhum lembrete ativo dos seus vendedores</div>
                        <div class="text-xs text-gray-400 mt-1">Os lembretes aparecerão aqui quando os vendedores criarem</div>
                    </td>
                `;
                tbody.appendChild(row);
            }
        }

        async function checkAndBlockSellerForOverdueReminders() {
            const reminders = allData.filter(item => 
                item.type === 'reminder' && 
                item.sellerId === currentUser.id
            );
            
            const now = new Date();
            const overdueReminders = reminders.filter(reminder => {
                const reminderDate = new Date(reminder.reminderDate);
                return reminderDate < now && !reminder.reminderCompleted;
            });
            
            if (overdueReminders.length > 0) {
                const seller = allData.find(item => item.id === currentUser.id && item.type === 'user');
                if (seller && !seller.blockedFromReceiving) {
                    const updatedSeller = {
                        ...seller,
                        blockedFromReceiving: true,
                        blockReason: `Lembretes em atraso: ${overdueReminders.length}`
                    };
                    
                    if (window.dataSdk) {
                        await window.dataSdk.update(updatedSeller);
                        showMessage('⚠️ Você foi bloqueado para receber novos leads devido a lembretes em atraso. Complete seus lembretes para ser desbloqueado.', 'error');
                    }
                }
            }
        }

        async function contactSellerAboutReminder(sellerId, reminderId) {
            // Create a contact record for admin action
            const contactRecord = {
                id: generateId(),
                type: 'admin_contact',
                adminId: currentUser.id,
                sellerId: sellerId,
                reminderId: reminderId,
                message: 'Contato sobre lembrete em atraso',
                createdAt: new Date().toISOString()
            };
            
            if (window.dataSdk) {
                const result = await window.dataSdk.create(contactRecord);
                if (result.isOk) {
                    showMessage('Contato registrado! Vendedor será notificado sobre o lembrete em atraso.', 'success');
                } else {
                    showMessage('Erro ao registrar contato', 'error');
                }
            }
        }

        async function unblockSeller(sellerId) {
            const seller = allData.find(item => item.id === sellerId && item.type === 'user');
            if (seller) {
                const updatedSeller = {
                    ...seller,
                    blockedFromReceiving: false,
                    blockReason: null
                };
                
                if (window.dataSdk) {
                    const result = await window.dataSdk.update(updatedSeller);
                    if (result.isOk) {
                        showMessage('Vendedor desbloqueado com sucesso!', 'success');
                    } else {
                        showMessage('Erro ao desbloquear vendedor', 'error');
                    }
                }
            }
        }
    </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'99e2f0352534f62c',t:'MTc2MzA4NTg2OC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
