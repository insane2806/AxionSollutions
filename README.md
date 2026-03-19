<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Axion - Soluções Galaxy Profissional</title>
    <style>
        :root {
            --bg-deep-space: #050509;
            --bg-business: #1A1A1D; /* Cinza Carvão sofisticado */
            --text-main: #FFFFFF;
            --text-desc: #CCCCCC;
            --axion-violet: #7A29CC; /* Roxo Business */
            --axion-gold: #E6B800;   /* Ouro Matte */
            --axion-blue-light: #C7EAFF; /* Azul sutil para realces */
            --glass: rgba(255, 255, 255, 0.03);
            --font-premium: 'Poppins', sans-serif;
            --font-business: 'Outfit', sans-serif;
        }

        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&family=Outfit:wght@300;400;600&display=swap');

        * { margin: 0; padding: 0; box-sizing: border-box; scroll-behavior: smooth; font-family: var(--font-business); }

        body { background-color: var(--bg-deep-space); color: var(--text-main); overflow-x: hidden; }

        /* --- Galaxy Texture --- */
        .galaxy-bg {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background-image: 
                radial-gradient(white, rgba(255,255,255,.15) 1.5px, transparent 2px),
                radial-gradient(white, rgba(255,255,255,.1) 1px, transparent 1px);
            background-size: 550px 550px, 350px 350px;
            z-index: -1;
            opacity: 0.15;
            animation: starsBackground 150s linear infinite;
        }
        @keyframes starsBackground {
            from { background-position: 0 0, 40px 60px; }
            to { background-position: -550px -550px, -310px -290px; }
        }

        /* --- Header & Logo --- */
        header {
            position: fixed;
            top: 0; width: 100%; padding: 25px 60px;
            background: rgba(5, 5, 9, 0.9);
            backdrop-filter: blur(15px);
            display: flex; justify-content: space-between; align-items: center;
            z-index: 1000;
            border-bottom: 1px solid rgba(122, 41, 204, 0.2);
        }

        .logo { font-size: 2.2rem; font-weight: 600; text-transform: uppercase; color: var(--text-main); cursor: pointer; }
        .logo .violet { color: var(--axion-violet); }

        .nav-links { display: flex; list-style: none; gap: 35px; }
        .nav-links a { text-decoration: none; color: var(--text-desc); font-size: 0.95rem; font-weight: 300; transition: 0.3s; text-transform: uppercase; letter-spacing: 1.5px; }
        .nav-links a:hover { color: var(--text-main); text-shadow: 0 0 10px var(--axion-blue-light); }

        /* --- Common Screen Styling --- */
        .screen {
            position: absolute; top: 0; left: 0; width: 100%; min-height: 100vh;
            display: flex; flex-direction: column; align-items: center;
            text-align: center; padding: 120px 40px 60px 40px;
            transition: opacity 1s ease-out, transform 0.8s ease-in-out;
            opacity: 0; transform: translateY(50px); pointer-events: none;
        }

        #hero.screen {
            justify-content: center;
            padding-top: 0;
        }

        .screen.active { opacity: 1; transform: translateY(0); pointer-events: all; }

        .section-title { font-size: 3.2rem; font-weight: 600; font-family: var(--font-premium); margin-bottom: 25px; line-height: 1.1; color: var(--text-main); }
        .section-desc { font-size: 1.15rem; color: var(--text-desc); max-width: 700px; margin-bottom: 50px; font-weight: 300; }

        /* --- Navigation Buttons --- */
        .btn-premium {
            padding: 16px 45px;
            background: transparent;
            border: 2px solid var(--axion-violet);
            color: var(--text-main);
            font-size: 1.1rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.4s;
            text-decoration: none;
            box-shadow: 0 0 10px rgba(122, 41, 204, 0.2);
        }
        .btn-premium:hover { background: var(--axion-violet); box-shadow: 0 0 20px rgba(122, 41, 204, 0.5); transform: translateY(-3px); }

        .btn-back { margin-top: 20px; border-color: var(--axion-gold); color: var(--axion-gold); }
        .btn-back:hover { background: var(--axion-gold); color: #000; box-shadow: 0 0 20px rgba(230, 184, 0, 0.5); }

        /* --- Services Grid --- */
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 40px;
            max-width: 1200px;
            margin: 0 auto;
            opacity: 0;
            transition: opacity 1.5s ease-out 0.5s;
        }
        .screen.active .services-grid { opacity: 1; }

        .service-card {
            background: var(--bg-business);
            padding: 50px 35px;
            border-radius: 10px;
            border: 1px solid rgba(255, 255, 255, 0.03);
            transition: all 0.4s;
            display: flex; flex-direction: column; align-items: flex-start; text-align: left;
            overflow: hidden;
            position: relative;
        }
        .service-card:hover { border-color: var(--axion-violet); transform: scale(1.03); box-shadow: 0 10px 40px rgba(122, 41, 204, 0.2); }
        
        .card-icon { font-size: 2.8rem; margin-bottom: 30px; color: var(--axion-gold); transition: 0.3s; }
        .service-card:hover .card-icon { transform: scale(1.1); color: var(--axion-blue-light); }
        
        .service-card h3 { font-size: 1.6rem; margin-bottom: 20px; font-weight: 600; color: var(--text-main); font-family: var(--font-premium); }
        .service-card p { font-size: 1rem; color: var(--text-desc); font-weight: 300; line-height: 1.7; margin-bottom: 30px; }

        /* --- Indicador de Rolagem (Seta Animada) --- */
        .scroll-indicator {
            margin: 60px 0 30px 0;
            text-align: center;
            animation: bounce 2s infinite;
        }
        
        .scroll-indicator span {
            display: block;
            color: var(--axion-gold);
            font-size: 1.1rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 10px;
        }

        .scroll-indicator .arrow {
            font-size: 2.5rem;
            color: var(--axion-blue-light);
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-15px); }
            60% { transform: translateY(-7px); }
        }

    </style>
</head>
<body>

    <div class="galaxy-bg"></div>

    <header>
        <div class="logo" onclick="toggleScreen('hero')">AX<span class="violet">I</span>ON</div>
        <ul class="nav-links">
            <li><a href="#" onclick="toggleScreen('hero')">Home</a></li>
            <li><a href="#" onclick="toggleScreen('services')">Serviços</a></li>
        </ul>
    </header>

    <section id="hero" class="screen active">
        <h1 class="section-title">Inovação Estratégica <br> para o seu Universo Digital</h1>
        <p class="section-desc">A Axion é a sua parceira estratégica para soluções tecnológicas e criativas avançadas. Transformamos desafios em resultados impecáveis.</p>
        <button class="btn-premium" onclick="toggleScreen('services')">Conhecer Serviços</button>
    </section>

    <section id="services" class="screen">
        <h1 class="section-title">Nossa Constelação de Soluções</h1>
        <p class="section-desc">Diagnóstico preciso e criação inovadora. Explore nossos serviços essenciais de tecnologia.</p>
        
        <div class="services-grid">
            
            <div class="service-card group-header" style="grid-column: 1 / -1; background: none; border: none; padding: 0 0 20px 0; border-bottom: 1px solid rgba(230,184,0, 0.3); margin-bottom: 30px;">
                <h3 style="color: var(--axion-gold); font-size: 1.2rem; text-transform: uppercase; letter-spacing: 2px;">Soluções Hardware & Mobile</h3>
            </div>

            <div class="service-card">
                <div class="card-icon">🛠️</div>
                <h3>Assistência Técnica</h3>
                <p>Diagnóstico preciso e reparo de hardware para computadores, notebooks e infraestrutura de TI.</p>
            </div>

            <div class="service-card">
                <div class="card-icon">🚀</div>
                <h3>Montagem de Computadores</h3>
                <p>Montamos o PC ideal para a sua necessidade (Gamer, Trabalho, Edição ou Estudos) com foco em performance.</p>
            </div>

            <div class="service-card">
                <div class="card-icon">💡</div>
                <h3>Auxílio para Compras</h3>
                <p>Consultoria especializada para você comprar o melhor notebook, PC ou peça sem gastar dinheiro à toa.</p>
            </div>

            <div class="service-card">
                <div class="card-icon">🔓</div>
                <h3>Desbloqueio de Celulares</h3>
                <p>Recuperação segura de acesso, desbloqueio de rede e soluções avançadas para dispositivos móveis.</p>
            </div>

            <div class="service-card group-header" style="grid-column: 1 / -1; background: none; border: none; padding: 40px 0 20px 0; border-bottom: 1px solid rgba(122, 41, 204, 0.3); margin-bottom: 30px;">
                <h3 style="color: var(--axion-violet); font-size: 1.2rem; text-transform: uppercase; letter-spacing: 2px;">Soluções de Criatividade Digital</h3>
            </div>

            <div class="service-card">
                <div class="card-icon">🌐</div>
                <h3>Desenvolvimento Web</h3>
                <p>Criação de plataformas online impecáveis, otimizadas para performance e focadas na experiência do usuário.</p>
            </div>

            <div class="service-card">
                <div class="card-icon">🎨</div>
                <h3>Design Gráfico</h3>
                <p>Identidade visual e conceitos criativos que capturam a essência da sua marca e a destacam no mercado.</p>
            </div>

            <div class="service-card">
                <div class="card-icon">🖼️</div>
                <h3>Restauração de Fotos</h3>
                <p>Revitalização profissional de memórias, reparando danos e aprimorando a nitidez de fotografias históricas.</p>
            </div>

        </div>

        <button class="btn-premium btn-back" onclick="toggleScreen('hero')">Voltar para Home</button>
    </section>

    <script>
        function toggleScreen(screenId) {
            document.querySelector('.screen.active').classList.remove('active');
            
            setTimeout(() => {
                const nextScreen = document.getElementById(screenId);
                nextScreen.classList.add('active');
                window.scrollTo(0,0); 
            }, 300);
        }
    </script>
</body>
</html>
