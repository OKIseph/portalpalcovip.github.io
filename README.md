<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Palco Vip · Futmondo</title>
    <style>
        /* ----- RESET & BASE ----- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Roboto, system-ui, sans-serif;
        }
        body {
            background: #f0f2f5;
            color: #1e1e2f;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        /* ----- HEADER / NAV ----- */
        .navbar {
            background: #0b1a2e;
            color: #fff;
            padding: 0.75rem 2rem;
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: space-between;
            border-bottom: 4px solid #f5c842;
            box-shadow: 0 2px 10px rgba(0,0,0,0.3);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        .navbar .logo {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 1.8rem;
            font-weight: 700;
            letter-spacing: 1px;
        }
        .navbar .logo span {
            color: #f5c842;
        }
        .nav-links {
            display: flex;
            flex-wrap: wrap;
            gap: 0.25rem 1.2rem;
            list-style: none;
            font-weight: 600;
        }
        .nav-links li {
            cursor: pointer;
            padding: 0.4rem 0.2rem;
            border-bottom: 3px solid transparent;
            transition: 0.2s;
            font-size: 1rem;
        }
        .nav-links li:hover,
        .nav-links li.active {
            border-bottom-color: #f5c842;
            color: #f5c842;
        }
        .nav-links li.active {
            color: #f5c842;
        }

        /* ----- MAIN CONTAINER ----- */
        .container {
            max-width: 1300px;
            margin: 2rem auto;
            padding: 0 1.5rem;
            flex: 1;
        }

        /* ----- SECTIONS (tabs) ----- */
        .section {
            display: none;
            animation: fade 0.25s ease;
        }
        .section.active {
            display: block;
        }

        @keyframes fade {
            0% { opacity: 0.3; transform: translateY(8px); }
            100% { opacity: 1; transform: translateY(0); }
        }

        /* ----- CARDS & COMMON ----- */
        .card {
            background: #fff;
            border-radius: 16px;
            padding: 1.8rem 2rem;
            box-shadow: 0 6px 20px rgba(0,0,0,0.06);
            margin-bottom: 2rem;
            border: 1px solid #e9edf2;
        }
        .card-title {
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 1.5rem;
            display: flex;
            align-items: center;
            gap: 0.75rem;
            color: #0b1a2e;
        }
        .card-title i {
            color: #f5c842;
        }
        .badge {
            background: #f5c842;
            color: #0b1a2e;
            padding: 0.2rem 0.8rem;
            border-radius: 30px;
            font-size: 0.75rem;
            font-weight: 700;
            margin-left: 0.5rem;
        }

        /* Resumen cards (inicio) */
        .resumen-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 1rem;
            margin-top: 1rem;
        }
        .resumen-item {
            background: #f5f7fb;
            padding: 1rem;
            border-radius: 12px;
            text-align: center;
        }
        .resumen-icon {
            font-size: 2rem;
        }
        .resumen-valor {
            color: #0b1a2e;
            font-weight: 500;
        }

        /* ----- CLASIFICACIÓN (tabla) ----- */
        .tabla-wrap {
            overflow-x: auto;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.95rem;
        }
        table th {
            background: #0b1a2e;
            color: #fff;
            padding: 0.9rem 0.5rem;
            text-align: left;
        }
        table td {
            padding: 0.7rem 0.5rem;
            border-bottom: 1px solid #eef1f5;
        }
        table tr:hover td {
            background: #f8faff;
        }
        .pos {
            font-weight: 700;
            width: 40px;
            text-align: center;
        }
        .movimiento {
            font-size: 1.2rem;
            text-align: center;
            width: 50px;
        }
        .movimiento.up { color: #2e7d32; }
        .movimiento.down { color: #c62828; }
        .movimiento.same { color: #f9a825; }

        .equipo {
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        .equipo .escudo {
            width: 28px;
            height: 28px;
            background: #ddd;
            border-radius: 50%;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            color: #0b1a2e;
            font-size: 0.7rem;
        }

        /* ----- TORNEOS ----- */
        .torneo-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px,1fr));
            gap: 1.2rem;
        }
        .torneo-item {
            background: #f8fafc;
            border-radius: 14px;
            padding: 1.2rem 1.5rem;
            border-left: 6px solid #f5c842;
            box-shadow: 0 2px 8px rgba(0,0,0,0.03);
        }
        .torneo-item h4 {
            font-size: 1.2rem;
            margin-bottom: 0.4rem;
        }
        .torneo-item p {
            color: #556;
            font-size: 0.9rem;
        }

        /* ----- NOTICIAS ----- */
        .noticia {
            display: flex;
            gap: 1.2rem;
            padding: 1rem 0;
            border-bottom: 1px solid #eef1f5;
        }
        .noticia:last-child {
            border-bottom: none;
        }
        .noticia .fecha {
            color: #888;
            font-size: 0.8rem;
            min-width: 80px;
        }
        .noticia .titulo {
            font-weight: 600;
            font-size: 1.05rem;
        }
        .noticia .resumen {
            color: #445;
            font-size: 0.9rem;
        }

        /* ----- JORNADAS ----- */
        .jornada-selector {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-bottom: 2rem;
        }
        .jornada-btn {
            background: #eef1f5;
            border: none;
            padding: 0.5rem 1.4rem;
            border-radius: 40px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.2s;
            color: #1e1e2f;
        }
        .jornada-btn:hover {
            background: #d5dce6;
        }
        .jornada-btn.active {
            background: #0b1a2e;
            color: #fff;
        }
        .partido {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0.8rem 1rem;
            background: #f8fafc;
            border-radius: 12px;
            margin-bottom: 0.6rem;
            border: 1px solid #e9edf2;
            flex-wrap: wrap;
            gap: 0.5rem;
        }
        .partido .equipos {
            display: flex;
            align-items: center;
            gap: 0.8rem;
            font-weight: 600;
        }
        .partido .resultado {
            font-weight: 700;
            font-size: 1.2rem;
            background: #0b1a2e;
            color: #fff;
            padding: 0.2rem 1rem;
            border-radius: 30px;
        }
        .partido .info {
            color: #667;
            font-size: 0.85rem;
        }

        /* ----- FOOTER ----- */
        .footer {
            background: #0b1a2e;
            color: #aab;
            text-align: center;
            padding: 1.2rem;
            margin-top: 2rem;
            border-top: 3px solid #f5c842;
            font-size: 0.9rem;
        }

        /* ----- RESPONSIVE ----- */
        @media (max-width: 700px) {
            .navbar {
                flex-direction: column;
                align-items: stretch;
                gap: 0.5rem;
                padding: 0.75rem 1rem;
            }
            .nav-links {
                justify-content: center;
                gap: 0.5rem 0.8rem;
                font-size: 0.9rem;
            }
            .card {
                padding: 1.2rem;
            }
            .partido {
                flex-direction: column;
                align-items: stretch;
                text-align: center;
            }
            .partido .equipos {
                justify-content: center;
            }
        }
        @media (max-width: 480px) {
            .nav-links li {
                font-size: 0.8rem;
            }
            .card-title {
                font-size: 1.4rem;
            }
            .movimiento {
                font-size: 1rem;
                width: 40px;
            }
            table {
                font-size: 0.85rem;
            }
        }

        .icon-fut {
            display: inline-block;
            width: 28px;
            text-align: center;
        }
    </style>
</head>
<body>

    <!-- ========== NAVBAR ========== -->
    <header class="navbar">
        <div class="logo">
            <span>⚽</span> Palco <span>Vip</span>
        </div>
        <ul class="nav-links" id="navLinks">
            <li class="active" data-tab="inicio">Inicio</li>
            <li data-tab="clasificacion">Clasificación</li>
            <li data-tab="torneos">Torneos</li>
            <li data-tab="noticias">Noticias</li>
            <li data-tab="jornadas">Jornadas</li>
        </ul>
    </header>

    <!-- ========== MAIN ========== -->
    <main class="container">

        <!-- ===== INICIO ===== -->
        <section id="inicio" class="section active">
            <div class="card">
                <div class="card-title"><i>🏠</i> Bienvenido a Palco Vip</div>
                <p style="font-size:1.1rem; margin-bottom:1rem;">
                    La comunidad de Futmondo donde la pasión por el fútbol se vive cada jornada.
                </p>
                <div class="resumen-cards">
                    <div class="resumen-item">
                        <div class="resumen-icon">🏆</div>
                        <strong>Líder</strong><br />
                        <span class="resumen-valor">Juan Carlos</span>
                    </div>
                    <div class="resumen-item">
                        <div class="resumen-icon">⚡</div>
                        <strong>Próxima jornada</strong><br />
                        <span class="resumen-valor">Jornada 38</span>
                    </div>
                    <div class="resumen-item">
                        <div class="resumen-icon">📰</div>
                        <strong>Noticias</strong><br />
                        <span class="resumen-valor">4 nuevas</span>
                    </div>
                </div>
            </div>
            <div class="card">
                <div class="card-title"><i>📋</i> Últimos resultados</div>
                <p>Resultados de la Jornada 38 disponibles en la sección Jornadas.</p>
            </div>
        </section>

        <!-- ===== CLASIFICACIÓN ===== -->
        <section id="clasificacion" class="section">
            <div class="card">
                <div class="card-title"><i>📊</i> Clasificación <span class="badge">Trofeo VIP 25/26</span></div>
                <div class="tabla-wrap">
                    <table>
                        <thead>
                            <tr>
                                <th>#</th>
                                <th>Mov.</th>
                                <th>Equipo</th>
                                <th>Puntos Totales</th>
                                <th>Créditos</th>
                            </tr>
                        </thead>
                        <tbody id="tablaBody">
                            <!-- JS rellena -->
                        </tbody>
                    </table>
                </div>
            </div>
        </section>

        <!-- ===== TORNEOS ===== -->
        <section id="torneos" class="section">
            <div class="card">
                <div class="card-title"><i>🏅</i> Torneos activos</div>
                <div class="torneo-grid" id="torneosGrid">
                    <!-- JS rellena -->
                </div>
            </div>
        </section>

        <!-- ===== NOTICIAS ===== -->
        <section id="noticias" class="section">
            <div class="card">
                <div class="card-title"><i>📰</i> Noticias de fútbol</div>
                <div id="noticiasList">
                    <!-- JS rellena -->
                </div>
            </div>
        </section>

        <!-- ===== JORNADAS ===== -->
        <section id="jornadas" class="section">
            <div class="card">
                <div class="card-title"><i>📅</i> Jornadas</div>

                <div class="jornada-selector" id="jornadaSelector">
                    <!-- JS rellena botones -->
                </div>

                <div id="jornadaContent">
                    <p style="color:#667;">Selecciona una jornada para ver los partidos.</p>
                </div>
            </div>
        </section>

    </main>

    <!-- ========== FOOTER ========== -->
    <footer class="footer">
        &copy; 2026 Palco Vip · Grupo Futmondo · Hecho con ⚽ y ❤️
    </footer>

    <!-- ========== JAVASCRIPT ========== -->
    <script>
        (function() {
            'use strict';

            // ----- DATOS CON MOVIMIENTO (up, down, same) -----
            const clasificacion = [
                { equipo: 'Juan Carlos', puntosTotales: 3061, creditos: 15, movimiento: 'up' },
                { equipo: 'Rubén', puntosTotales: 3061, creditos: 12, movimiento: 'down' },
                { equipo: 'Manel', puntosTotales: 3061, creditos: 8, movimiento: 'same' },
                { equipo: 'Jotha', puntosTotales: 3061, creditos: 4, movimiento: 'up' },
                { equipo: 'Oscar', puntosTotales: 3061, creditos: 3, movimiento: 'down' },
                { equipo: 'Jose', puntosTotales: 3061, creditos: 2, movimiento: 'same' },
                { equipo: 'Miguel', puntosTotales: 3061, creditos: 1, movimiento: 'up' },
                { equipo: 'Carlos', puntosTotales: 3061, creditos: 0, movimiento: 'down' },
            ];

            const movimientoMap = {
                'up': { icon: '⬆️', class: 'up' },
                'down': { icon: '⬇️', class: 'down' },
                'same': { icon: '➡️', class: 'same' }
            };

            // Torneos (puedes modificarlos)
            const torneos = [
                { nombre: 'Liga Palco Vip', tipo: 'Liga', equipos: 8, estado: 'En curso' },
                { nombre: 'Copa del Rey Vip', tipo: 'Eliminatoria', equipos: 16, estado: 'Cuartos' },
                { nombre: 'Supercopa Palco', tipo: 'Final four', equipos: 4, estado: 'Final' },
                { nombre: 'Torneo de Verano', tipo: 'Amistoso', equipos: 6, estado: 'Próximo' },
            ];

            // Noticias
            const noticias = [
                { fecha: '11/06/2026', titulo: 'Clasificación Trofeo VIP 25/26', resumen: 'Juan Carlos lidera con 3061 puntos y 15 créditos.' },
                { fecha: '10/06/2026', titulo: 'Boletín Jornada 38 25/26', resumen: 'Resultados y resumen de la última jornada.' },
                { fecha: '19/05/2026', titulo: 'Boletín Jornada 37 25/26', resumen: 'Resumen de la jornada 37 con todos los goles.' },
                { fecha: '19/05/2026', titulo: 'Boletín Jornada 36 25/26', resumen: 'Análisis de la jornada 36.' },
            ];

            // Jornadas (ejemplo)
            const jornadas = [
                { numero: 35, partidos: [
                    { local: 'Juan Carlos', visitante: 'Rubén', gl: 2, gv: 1 },
                    { local: 'Manel', visitante: 'Jotha', gl: 1, gv: 1 },
                    { local: 'Oscar', visitante: 'Jose', gl: 3, gv: 0 },
                    { local: 'Miguel', visitante: 'Carlos', gl: 2, gv: 2 },
                ]},
                { numero: 36, partidos: [
                    { local: 'Rubén', visitante: 'Oscar', gl: 1, gv: 2 },
                    { local: 'Jotha', visitante: 'Juan Carlos', gl: 0, gv: 3 },
                    { local: 'Jose', visitante: 'Manel', gl: 1, gv: 1 },
                    { local: 'Carlos', visitante: 'Miguel', gl: 2, gv: 1 },
                ]},
                { numero: 37, partidos: [
                    { local: 'Juan Carlos', visitante: 'Jose', gl: 4, gv: 0 },
                    { local: 'Manel', visitante: 'Carlos', gl: 2, gv: 2 },
                    { local: 'Oscar', visitante: 'Rubén', gl: 1, gv: 1 },
                    { local: 'Miguel', visitante: 'Jotha', gl: 0, gv: 1 },
                ]},
                { numero: 38, partidos: [
                    { local: 'Rubén', visitante: 'Manel', gl: 1, gv: 2 },
                    { local: 'Jotha', visitante: 'Oscar', gl: 1, gv: 1 },
                    { local: 'Jose', visitante: 'Miguel', gl: 3, gv: 1 },
                    { local: 'Carlos', visitante: 'Juan Carlos', gl: 0, gv: 4 },
                ]}
            ];

            // ----- FUNCIONES PARA RENDERIZAR -----

            function renderClasificacion() {
                const tbody = document.getElementById('tablaBody');
                tbody.innerHTML = '';
                clasificacion.forEach((item, index) => {
                    const mov = movimientoMap[item.movimiento] || movimientoMap['same'];
                    const tr = document.createElement('tr');
                    tr.innerHTML = `
                        <td class="pos">${index + 1}</td>
                        <td class="movimiento ${mov.class}">${mov.icon}</td>
                        <td><span class="equipo"><span class="escudo">${item.equipo.charAt(0)}</span> ${item.equipo}</span></td>
                        <td><strong>${item.puntosTotales}</strong></td>
                        <td>${item.creditos}</td>
                    `;
                    tbody.appendChild(tr);
                });
            }

            function renderTorneos() {
                const grid = document.getElementById('torneosGrid');
                grid.innerHTML = '';
                torneos.forEach(t => {
                    const div = document.createElement('div');
                    div.className = 'torneo-item';
                    div.innerHTML = `
                        <h4>${t.nombre}</h4>
                        <p>${t.tipo} · ${t.equipos} equipos</p>
                        <p style="font-weight:600; color:#0b1a2e;">${t.estado}</p>
                    `;
                    grid.appendChild(div);
                });
            }

            function renderNoticias() {
                const list = document.getElementById('noticiasList');
                list.innerHTML = '';
                noticias.forEach(n => {
                    const div = document.createElement('div');
                    div.className = 'noticia';
                    div.innerHTML = `
                        <div class="fecha">${n.fecha}</div>
                        <div>
                            <div class="titulo">${n.titulo}</div>
                            <div class="resumen">${n.resumen}</div>
                        </div>
                    `;
                    list.appendChild(div);
                });
            }

            let jornadaActual = 0;

            function renderJornadas() {
                const selector = document.getElementById('jornadaSelector');
                const content = document.getElementById('jornadaContent');
                selector.innerHTML = '';

                jornadas.forEach((j, idx) => {
                    const btn = document.createElement('button');
                    btn.className = 'jornada-btn' + (idx === jornadaActual ? ' active' : '');
                    btn.textContent = `Jornada ${j.numero}`;
                    btn.dataset.index = idx;
                    btn.addEventListener('click', function() {
                        jornadaActual = parseInt(this.dataset.index);
                        renderJornadas();
                    });
                    selector.appendChild(btn);
                });

                const jornada = jornadas[jornadaActual];
                if (!jornada) {
                    content.innerHTML = '<p style="color:#667;">No hay jornadas disponibles.</p>';
                    return;
                }

                let html = `<h3 style="margin-bottom:1rem;">Jornada ${jornada.numero}</h3>`;
                jornada.partidos.forEach(p => {
                    html += `
                        <div class="partido">
                            <div class="equipos">
                                <span>${p.local}</span>
                                <span style="color:#888;">vs</span>
                                <span>${p.visitante}</span>
                            </div>
                            <div class="resultado">${p.gl} - ${p.gv}</div>
                            <div class="info">${p.info || ''}</div>
                        </div>
                    `;
                });
                content.innerHTML = html;
            }

            // ----- NAVEGACIÓN POR TABS -----
            function initTabs() {
                const links = document.querySelectorAll('#navLinks li');
                const sections = document.querySelectorAll('.section');

                links.forEach(link => {
                    link.addEventListener('click', function() {
                        links.forEach(l => l.classList.remove('active'));
                        this.classList.add('active');

                        const tabId = this.dataset.tab;
                        sections.forEach(sec => sec.classList.remove('active'));
                        const target = document.getElementById(tabId);
                        if (target) target.classList.add('active');
                    });
                });
            }

            // ----- INICIO -----
            function init() {
                renderClasificacion();
                renderTorneos();
                renderNoticias();
                renderJornadas();
                initTabs();
            }

            document.addEventListener('DOMContentLoaded', init);

        })();
    </script>

</body>
</html>
