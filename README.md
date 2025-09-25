<html lang="pt-BR" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Diagnóstico de Segurança Predial - MD Engenharia</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Corporate Safety -->
    <!-- Application Structure Plan: A narrative-driven SPA guiding users through a logical AIDA (Attention, Interest, Desire, Action) funnel. 1) Hook with the core question. 2) Interactive "Risk Explorer" to generate interest and personalize the problem. 3) Solution section with an animated counter to create desire for the thorough, free inspection. 4) A clear form for action. This structure is chosen over a static page to actively engage the user, making the risks feel more tangible and the solution more valuable, ultimately aiming for a higher conversion rate. -->
    <!-- Visualization & Content Choices: 1. Risks (Wear/Tear, Norms): Goal: Inform & Engage -> Viz: Interactive Tabbed Content -> Interaction: User clicks on risk categories (e.g., Electrical) to reveal common issues, making the problem relatable. -> Justification: Breaks down complex info into digestible, user-controlled chunks. -> Method: Vanilla JS. | 2. 50+ Point Check: Goal: Impress & build value -> Viz: Animated number counter + icon grid -> Interaction: Counter animates on scroll. -> Justification: Dynamic effect emphasizes the number's significance more than static text. -> Method: Vanilla JS + IntersectionObserver. All icons are non-SVG Unicode or inline-path characters. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body { font-family: 'Inter', sans-serif; }
        .tab-active { 
            background-color: #f97316; /* orange-500 */
            color: white;
        }
        .tab-inactive {
            background-color: #e2e8f0; /* slate-200 */
            color: #475569; /* slate-600 */
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-700">

    <header class="bg-white/80 backdrop-blur-lg fixed top-0 left-0 right-0 z-50 shadow-sm">
        <div class="container mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16">
                <div class="flex-shrink-0">
                    <a href="#" class="text-2xl font-bold text-slate-800">MD Engenharia</a>
                </div>
                <nav class="hidden md:block">
                    <div class="ml-10 flex items-baseline space-x-4">
                        <a href="#riscos" class="text-slate-600 hover:text-orange-500 px-3 py-2 rounded-md text-sm font-medium transition-colors">Riscos Ocultos</a>
                        <a href="#solucao" class="text-slate-600 hover:text-orange-500 px-3 py-2 rounded-md text-sm font-medium transition-colors">Nossa Solução</a>
                        <a href="#agendar" class="bg-orange-500 text-white hover:bg-orange-600 px-4 py-2 rounded-md text-sm font-bold transition-transform hover:scale-105">Agendar Vistoria Gratuita</a>
                    </div>
                </nav>
                <div class="md:hidden">
                    <a href="#agendar" class="bg-orange-500 text-white hover:bg-orange-600 px-4 py-2 rounded-md text-sm font-bold transition-transform hover:scale-105">Agendar</a>
                </div>
            </div>
        </div>
    </header>

    <main>
        <section class="pt-32 pb-20 bg-white">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8 text-center">
                <h1 class="text-4xl md:text-6xl font-extrabold text-slate-900 leading-tight">
                    O seu estabelecimento é <span class="text-orange-500">realmente</span> seguro?
                </h1>
                <p class="mt-6 max-w-3xl mx-auto text-lg md:text-xl text-slate-600">
                    Um alvará e um projeto aprovado são o ponto de partida, não a garantia final de segurança. Descubra os riscos silenciosos que podem estar presentes agora no seu imóvel.
                </p>
                <a href="#riscos" class="mt-10 inline-block bg-slate-800 text-white font-bold py-3 px-8 rounded-lg text-lg transition-transform hover:scale-105 shadow-lg">
                    Explorar Riscos Comuns
                </a>
            </div>
        </section>

        <section id="riscos" class="py-20 bg-slate-100">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center max-w-3xl mx-auto">
                    <h2 class="text-3xl md:text-4xl font-bold text-slate-900">A Verdadeira Segurança é Contínua</h2>
                    <p class="mt-4 text-lg text-slate-600">
                        O tempo, o uso e as novas regulamentações criam vulnerabilidades que não existiam no projeto original. Interaja com as abas abaixo para entender os pontos críticos que mais exigem atenção.
                    </p>
                </div>

                <div class="mt-12 max-w-4xl mx-auto">
                    <div class="flex flex-wrap justify-center gap-2 md:gap-4 mb-8" id="risk-tabs">
                        <button data-tab="eletrica" class="risk-tab tab-active px-4 py-2 md:px-6 md:py-3 font-semibold rounded-lg transition-colors">Instalações Elétricas & Gás</button>
                        <button data-tab="incendio" class="risk-tab tab-inactive px-4 py-2 md:px-6 md:py-3 font-semibold rounded-lg transition-colors">Combate a Incêndio</button>
                        <button data-tab="estrutura" class="risk-tab tab-inactive px-4 py-2 md:px-6 md:py-3 font-semibold rounded-lg transition-colors">Estrutura e Infiltrações</button>
                        <button data-tab="fuga" class="risk-tab tab-inactive px-4 py-2 md:px-6 md:py-3 font-semibold rounded-lg transition-colors">Sinalização e Rotas de Fuga</button>
                    </div>

                    <div id="risk-content" class="bg-white p-6 sm:p-8 rounded-xl shadow-lg min-h-[20rem]">
                        <div data-content="eletrica" class="risk-pane">
                            <h3 class="font-bold text-2xl text-slate-800 mb-4">Pontos de Atenção: Elétrica e Gás</h3>
                            <ul class="space-y-3 text-slate-600">
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Quadros de energia desatualizados ou sem identificação correta.</li>
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Fiação exposta, ressecada ou com gambiarras.</li>
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Falta de aterramento adequado (SPDA/Para-raios) ou manutenção.</li>
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Vazamentos ou má conservação nas tubulações de gás.</li>
                            </ul>
                        </div>
                        <div data-content="incendio" class="risk-pane hidden">
                             <h3 class="font-bold text-2xl text-slate-800 mb-4">Pontos de Atenção: Combate a Incêndio</h3>
                            <ul class="space-y-3 text-slate-600">
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Extintores de incêndio vencidos, obstruídos ou em locais errados.</li>
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Hidrantes e mangueiras sem teste de pressão ou com vazamentos.</li>
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Alarmes e detectores de fumaça inoperantes ou sem testes periódicos.</li>
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Portas corta-fogo sem a devida vedação ou travadas abertas.</li>
                            </ul>
                        </div>
                        <div data-content="estrutura" class="risk-pane hidden">
                            <h3 class="font-bold text-2xl text-slate-800 mb-4">Pontos de Atenção: Estrutura e Infiltrações</h3>
                             <ul class="space-y-3 text-slate-600">
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Sinais de infiltração, mofo ou umidade em paredes e tetos.</li>
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Fissuras, trincas ou rachaduras em vigas, pilares e lajes.</li>
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Corrosão em armaduras expostas ou em estruturas metálicas.</li>
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Desgaste ou danos em revestimentos, pisos e fachadas.</li>
                            </ul>
                        </div>
                        <div data-content="fuga" class="risk-pane hidden">
                            <h3 class="font-bold text-2xl text-slate-800 mb-4">Pontos de Atenção: Sinalização e Fuga</h3>
                             <ul class="space-y-3 text-slate-600">
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Rotas de fuga obstruídas por móveis, estoque ou lixo.</li>
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Sinalização de emergência (saída, extintores) apagada, danificada ou inexistente.</li>
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Iluminação de emergência que não funciona ou tem baixa autonomia.</li>
                                <li class="flex items-start"><span class="text-orange-500 font-bold mr-3">✔</span>Guarda-corpos e corrimãos frouxos, com altura inadequada ou corroídos.</li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="solucao" class="py-20 bg-white">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                <div class="grid lg:grid-cols-2 gap-12 items-center">
                    <div>
                        <h2 class="text-3xl md:text-4xl font-bold text-slate-900">Nossa Solução: Um Diagnóstico Completo e Gratuito</h2>
                        <p class="mt-4 text-lg text-slate-600">
                            Para garantir sua total tranquilidade, oferecemos uma vistoria técnica completa, sem custo e sem compromisso. Nossa equipe de engenheiros qualificados avalia todos os aspectos vitais da segurança do seu edifício.
                        </p>
                        <div class="mt-8 grid grid-cols-2 gap-6 text-slate-700">
                            <div class="flex items-center"><span class="text-green-500 mr-2">●</span> Acessibilidade</div>
                            <div class="flex items-center"><span class="text-green-500 mr-2">●</span> Estrutura</div>
                            <div class="flex items-center"><span class="text-green-500 mr-2">●</span> Sistema de Incêndio</div>
                            <div class="flex items-center"><span class="text-green-500 mr-2">●</span> Instalações Elétricas</div>
                            <div class="flex items-center"><span class="text-green-500 mr-2">●</span> Rotas de Fuga</div>
                            <div class="flex items-center"><span class="text-green-500 mr-2">●</span> Sistema de Gás</div>
                        </div>
                    </div>
                    <div class="bg-slate-800 text-white p-8 sm:p-12 rounded-2xl shadow-2xl text-center">
                        <p class="text-xl font-semibold text-slate-300">Avaliamos mais de</p>
                        <p id="counter" class="text-7xl md:text-8xl font-extrabold text-orange-400 my-2">0</p>
                        <p class="text-xl font-semibold text-slate-300">pontos críticos de segurança</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="agendar" class="py-20 bg-slate-100">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                 <div class="max-w-2xl mx-auto text-center">
                    <h2 class="text-3xl md:text-4xl font-bold text-slate-900">Proteja seu Patrimônio. Comece Hoje.</h2>
                    <p class="mt-4 text-lg text-slate-600 mb-8">
                        Preencha o formulário e agende sua vistoria gratuita. Nossa equipe entrará em contato em até 24 horas para confirmar o melhor dia e horário para você.
                    </p>
                    <div id="form-wrapper" class="bg-white p-6 sm:p-8 rounded-xl shadow-lg text-left transition-all duration-500">
                        <form id="contactForm">
                            <input type="hidden" name="access_key" value="eb867af9-4fbe-4bdc-940f-df9bdccb9f8e">
                            <div class="grid sm:grid-cols-2 gap-4 mb-4">
                                <div>
                                    <label for="name" class="block text-sm font-bold text-slate-700 mb-1">Nome</label>
                                    <input type="text" id="name" name="name" class="w-full px-3 py-2 border border-slate-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500" required>
                                </div>
                                <div>
                                    <label for="phone" class="block text-sm font-bold text-slate-700 mb-1">Telefone / WhatsApp</label>
                                    <input type="tel" id="phone" name="phone" class="w-full px-3 py-2 border border-slate-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500" required>
                                </div>
                            </div>
                            <div class="mb-4">
                                <label for="company" class="block text-sm font-bold text-slate-700 mb-1">Empresa / Condomínio</label>
                                <input type="text" id="company" name="company" class="w-full px-3 py-2 border border-slate-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500" required>
                            </div>
                             <div class="mb-6">
                                <label for="email" class="block text-sm font-bold text-slate-700 mb-1">E-mail de Contato</label>
                                <input type="email" id="email" name="email" class="w-full px-3 py-2 border border-slate-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500" required>
                            </div>
                            <button type="submit" class="w-full bg-orange-500 hover:bg-orange-600 text-white font-bold py-3 px-4 rounded-lg text-lg transition-transform hover:scale-105">
                                Agendar Minha Vistoria Gratuita
                            </button>
                        </form>
                    </div>
                    <div id="thank-you-message" class="hidden bg-green-100 border-l-4 border-green-500 text-green-700 p-6 rounded-xl shadow-lg text-left">
                        <h4 class="font-bold text-xl mb-2">Obrigado!</h4>
                        <p>Recebemos sua solicitação. Nossa equipe de especialistas entrará em contato em breve para confirmar o melhor dia e horário para a sua vistoria gratuita.</p>
                    </div>
                    <div id="error-message" class="hidden mt-4 bg-red-100 border-l-4 border-red-500 text-red-700 p-4 rounded-lg shadow-lg text-left">
                        <h4 class="font-bold">Ocorreu um erro.</h4>
                        <p>Não foi possível enviar sua solicitação. Por favor, tente novamente ou entre em contato diretamente.</p>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <footer class="bg-slate-900 text-slate-400">
        <div class="container mx-auto px-4 sm:px-6 lg:px-8 py-8 text-center">
            <p>&copy; 2025 MD Engenharia - Segurança Contínua.</p>
            <p class="mt-2 text-sm">davicm00@gmail.com | (61) 99386-2269</p>
        </div>
    </footer>

    <script>
    document.addEventListener('DOMContentLoaded', function () {
        
        const riskTabs = document.querySelectorAll('.risk-tab');
        const riskPanes = document.querySelectorAll('.risk-pane');

        riskTabs.forEach(tab => {
            tab.addEventListener('click', () => {
                riskTabs.forEach(t => {
                    t.classList.remove('tab-active');
                    t.classList.add('tab-inactive');
                });
                tab.classList.add('tab-active');
                tab.classList.remove('tab-inactive');

                const targetContent = tab.getAttribute('data-tab');
                riskPanes.forEach(pane => {
                    if (pane.getAttribute('data-content') === targetContent) {
                        pane.classList.remove('hidden');
                    } else {
                        pane.classList.add('hidden');
                    }
                });
            });
        });

        const counterElement = document.getElementById('counter');
        const targetNumber = 50;
        let animationTriggered = false;

        const animateCounter = () => {
            let currentNumber = 0;
            const increment = targetNumber / 100;
            const interval = setInterval(() => {
                currentNumber += increment;
                if (currentNumber >= targetNumber) {
                    clearInterval(interval);
                    counterElement.innerText = targetNumber;
                } else {
                    counterElement.innerText = Math.ceil(currentNumber);
                }
            }, 20);
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting && !animationTriggered) {
                    animateCounter();
                    animationTriggered = true;
                    observer.unobserve(entry.target);
                }
            });
        }, { threshold: 0.5 });

        if (counterElement) {
             observer.observe(counterElement);
        }

        const form = document.getElementById('contactForm');
        const formWrapper = document.getElementById('form-wrapper');
        const thankYouMessage = document.getElementById('thank-you-message');
        const errorMessage = document.getElementById('error-message');
        const submitButton = form.querySelector('button[type="submit"]');

        form.addEventListener('submit', function (e) {
            e.preventDefault();
            
            // ATENÇÃO: Substitua 'YOUR_ACCESS_KEY_HERE' no campo 'hidden' do formulário.
            // Siga as instruções no arquivo instrucoes_email.md
            const accessKeyInput = form.querySelector('input[name="access_key"]');
            if (accessKeyInput.value === "YOUR_ACCESS_KEY_HERE") {
                errorMessage.querySelector('p').textContent = "A chave de acesso do formulário não foi configurada.";
                errorMessage.classList.remove('hidden');
                return;
            }

            const formData = new FormData(form);
            const object = Object.fromEntries(formData.entries());
            object.subject = `Nova Solicitação de Vistoria - ${object.company || 'Contato Site'}`;
            object.from_name = "Site Vértice Engenharia";
            const json = JSON.stringify(object);

            const originalButtonText = submitButton.innerHTML;
            submitButton.innerHTML = 'Enviando...';
            submitButton.disabled = true;
            errorMessage.classList.add('hidden');

            fetch('https://api.web3forms.com/submit', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                    'Accept': 'application/json'
                },
                body: json
            })
            .then(async (response) => {
                let jsonResponse = await response.json();
                if (response.status == 200) {
                    formWrapper.classList.add('hidden');
                    thankYouMessage.classList.remove('hidden');
                } else {
                    console.error(jsonResponse);
                    errorMessage.querySelector('p').textContent = jsonResponse.message || "Não foi possível enviar sua solicitação. Tente novamente.";
                    errorMessage.classList.remove('hidden');
                    submitButton.innerHTML = originalButtonText;
                    submitButton.disabled = false;
                }
            })
            .catch(error => {
                console.error(error);
                errorMessage.querySelector('p').textContent = "Ocorreu um erro de rede. Verifique sua conexão e tente novamente.";
                errorMessage.classList.remove('hidden');
                submitButton.innerHTML = originalButtonText;
                submitButton.disabled = false;
            });
        });

    });
    </script>
</body>
</html>
