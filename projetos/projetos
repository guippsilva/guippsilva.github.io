projetos/dinamica-populacional.html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simulador de Dinâmica Populacional</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.9.1/chart.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
        }
        
        header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 30px;
            text-align: center;
        }
        
        header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
        }
        
        header p {
            font-size: 1.1em;
            opacity: 0.9;
        }
        
        .content {
            padding: 30px;
        }
        
        .teoria {
            background: #f8f9fa;
            border-left: 4px solid #667eea;
            padding: 20px;
            margin-bottom: 30px;
            border-radius: 5px;
        }
        
        .teoria h2 {
            color: #667eea;
            margin-bottom: 15px;
        }
        
        .formula {
            background: white;
            padding: 15px;
            border-radius: 5px;
            font-family: 'Courier New', monospace;
            margin: 10px 0;
            border: 1px solid #dee2e6;
        }
        
        .controles {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .controle-grupo {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
        }
        
        .controle-grupo label {
            display: block;
            font-weight: bold;
            margin-bottom: 10px;
            color: #495057;
        }
        
        .controle-grupo input[type="range"] {
            width: 100%;
            height: 6px;
            border-radius: 5px;
            background: #dee2e6;
            outline: none;
            -webkit-appearance: none;
        }
        
        .controle-grupo input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: #667eea;
            cursor: pointer;
        }
        
        .controle-grupo input[type="range"]::-moz-range-thumb {
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: #667eea;
            cursor: pointer;
            border: none;
        }
        
        .valor {
            display: inline-block;
            background: #667eea;
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-weight: bold;
            margin-top: 10px;
        }
        
        .botoes {
            display: flex;
            gap: 15px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }
        
        button {
            padding: 12px 30px;
            font-size: 16px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s;
        }
        
        .btn-simular {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }
        
        .btn-simular:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }
        
        .btn-reset {
            background: #6c757d;
            color: white;
        }
        
        .btn-reset:hover {
            background: #5a6268;
        }
        
        .grafico-container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        .info {
            background: #e7f3ff;
            border-left: 4px solid #2196F3;
            padding: 15px;
            margin-top: 20px;
            border-radius: 5px;
        }
        
        .info strong {
            color: #2196F3;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>🦌 Simulador de Dinâmica Populacional</h1>
            <p>Modelo Logístico de Crescimento</p>
        </header>
        
        <div class="content">
            <div class="teoria">
                <h2>📚 Teoria: Modelo Logístico</h2>
                <p>O modelo logístico descreve como uma população cresce quando há recursos limitados.</p>
                
                <div class="formula">
                    dP/dt = r × P × (1 - P/K)
                </div>
                
                <p style="margin-top: 15px;"><strong>Onde:</strong></p>
                <ul style="margin-left: 20px; margin-top: 10px;">
                    <li><strong>P</strong> = população no tempo t</li>
                    <li><strong>r</strong> = taxa de crescimento intrínseca</li>
                    <li><strong>K</strong> = capacidade de suporte (população máxima sustentável)</li>
                </ul>
                
                <p style="margin-top: 15px;">
                    Quando a população é pequena (P << K), o crescimento é aproximadamente exponencial.
                    Quando P se aproxima de K, o crescimento desacelera até estabilizar.
                </p>
            </div>
            
            <div class="controles">
                <div class="controle-grupo">
                    <label>População Inicial (P₀)</label>
                    <input type="range" id="p0" min="10" max="500" value="50" step="10">
                    <div class="valor"><span id="p0-val">50</span> indivíduos</div>
                </div>
                
                <div class="controle-grupo">
                    <label>Taxa de Crescimento (r)</label>
                    <input type="range" id="r" min="0.1" max="2" value="0.5" step="0.1">
                    <div class="valor"><span id="r-val">0.5</span></div>
                </div>
                
                <div class="controle-grupo">
                    <label>Capacidade de Suporte (K)</label>
                    <input type="range" id="k" min="100" max="1000" value="500" step="50">
                    <div class="valor"><span id="k-val">500</span> indivíduos</div>
                </div>
                
                <div class="controle-grupo">
                    <label>Tempo de Simulação</label>
                    <input type="range" id="tempo" min="10" max="100" value="50" step="5">
                    <div class="valor"><span id="tempo-val">50</span> unidades</div>
                </div>
            </div>
            
            <div class="botoes">
                <button class="btn-simular" onclick="simular()">▶ Executar Simulação</button>
                <button class="btn-reset" onclick="reset()">↻ Resetar</button>
            </div>
            
            <div class="grafico-container">
                <canvas id="grafico"></canvas>
            </div>
            
            <div class="info">
                <strong>💡 Experimente:</strong> Aumente o valor de <strong>r</strong> acima de 2.0 e observe o comportamento caótico da população!
                Com valores altos de r, pequenas mudanças nas condições iniciais causam grandes diferenças no resultado.
            </div>
        </div>
    </div>
    
    <script>
        let chart = null;
        
        // Atualizar valores exibidos
        document.getElementById('p0').addEventListener('input', (e) => {
            document.getElementById('p0-val').textContent = e.target.value;
        });
        
        document.getElementById('r').addEventListener('input', (e) => {
            document.getElementById('r-val').textContent = e.target.value;
        });
        
        document.getElementById('k').addEventListener('input', (e) => {
            document.getElementById('k-val').textContent = e.target.value;
        });
        
        document.getElementById('tempo').addEventListener('input', (e) => {
            document.getElementById('tempo-val').textContent = e.target.value;
        });
        
        function modeloLogistico(P, r, K) {
            return r * P * (1 - P / K);
        }
        
        function simular() {
            // Pegar parâmetros
            const P0 = parseFloat(document.getElementById('p0').value);
            const r = parseFloat(document.getElementById('r').value);
            const K = parseFloat(document.getElementById('k').value);
            const tempoMax = parseInt(document.getElementById('tempo').value);
            
            // Método de Euler para resolver a EDO
            const dt = 0.1;
            const passos = Math.floor(tempoMax / dt);
            
            let tempo = [0];
            let populacao = [P0];
            let P = P0;
            
            for (let i = 1; i <= passos; i++) {
                const dP = modeloLogistico(P, r, K) * dt;
                P = Math.max(0, P + dP); // Evita população negativa
                
                if (i % 10 === 0) { // Salvar a cada 1 unidade de tempo
                    tempo.push(i * dt);
                    populacao.push(P);
                }
            }
            
            // Plotar gráfico
            plotarGrafico(tempo, populacao, K);
        }
        
        function plotarGrafico(tempo, populacao, K) {
            const ctx = document.getElementById('grafico').getContext('2d');
            
            if (chart) {
                chart.destroy();
            }
            
            chart = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: tempo,
                    datasets: [{
                        label: 'População',
                        data: populacao,
                        borderColor: '#667eea',
                        backgroundColor: 'rgba(102, 126, 234, 0.1)',
                        borderWidth: 3,
                        tension: 0.4,
                        fill: true
                    }, {
                        label: 'Capacidade de Suporte (K)',
                        data: Array(tempo.length).fill(K),
                        borderColor: '#e74c3c',
                        borderWidth: 2,
                        borderDash: [10, 5],
                        pointRadius: 0,
                        fill: false
                    }]
                },
                options: {
                    responsive: true,
                    plugins: {
                        legend: {
                            display: true,
                            position: 'top',
                        },
                        title: {
                            display: true,
                            text: 'Evolução da População ao Longo do Tempo',
                            font: {
                                size: 18
                            }
                        }
                    },
                    scales: {
                        x: {
                            title: {
                                display: true,
                                text: 'Tempo',
                                font: {
                                    size: 14
                                }
                            }
                        },
                        y: {
                            title: {
                                display: true,
                                text: 'População',
                                font: {
                                    size: 14
                                }
                            },
                            beginAtZero: true
                        }
                    }
                }
            });
        }
        
        function reset() {
            document.getElementById('p0').value = 50;
            document.getElementById('r').value = 0.5;
            document.getElementById('k').value = 500;
            document.getElementById('tempo').value = 50;
            
            document.getElementById('p0-val').textContent = '50';
            document.getElementById('r-val').textContent = '0.5';
            document.getElementById('k-val').textContent = '500';
            document.getElementById('tempo-val').textContent = '50';
            
            if (chart) {
                chart.destroy();
                chart = null;
            }
        }
        
        // Simular automaticamente ao carregar
        window.addEventListener('load', () => {
            simular();
        });
    </script>
</body>
</html>

projetos/algebra-linear.html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Visualizador de Álgebra Linear</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
        }
        
        header {
            text-align: center;
            margin-bottom: 40px;
        }
        
        h1 {
            font-size: 2.5em;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 10px;
        }
        
        .status {
            background: #fff3cd;
            border-left: 4px solid #ffc107;
            padding: 20px;
            border-radius: 5px;
            margin: 20px 0;
        }
        
        .topicos {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }
        
        .topico {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }
        
        .topico h3 {
            margin-bottom: 10px;
        }
        
        .topico p {
            opacity: 0.9;
            font-size: 0.95em;
        }
        
        .canvas-container {
            background: #f8f9fa;
            padding: 30px;
            border-radius: 10px;
            margin-top: 30px;
            text-align: center;
        }
        
        canvas {
            border: 2px solid #dee2e6;
            background: white;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>📊 Visualizador de Álgebra Linear</h1>
            <p style="font-size: 1.2em; color: #6c757d;">Algoritmos Numéricos Explicados Visualmente</p>
        </header>
        
        <div class="status">
            <h3>🚧 Projeto em Desenvolvimento</h3>
            <p>Este projeto está sendo construído gradualmente. Pretendo implementar visualizações interativas de algoritmos fundamentais de álgebra linear numérica.</p>
        </div>
        
        <h2 style="margin: 30px 0 20px 0;">📚 Algoritmos Planejados:</h2>
        
        <div class="topicos">
            <div class="topico">
                <h3>🔄 Decomposição QR</h3>
                <p>Visualização passo a passo do processo de Gram-Schmidt e sua interpretação geométrica.</p>
            </div>
            
            <div class="topico">
                <h3>✨ SVD (Singular Value Decomposition)</h3>
                <p>Como matrizes transformam o espaço e o papel dos valores singulares.</p>
            </div>
            
            <div class="topico">
                <h3>🎯 Método das Potências</h3>
                <p>Encontrando autovalores dominantes de forma iterativa.</p>
            </div>
            
            <div class="topico">
                <h3>🔍 Eliminação Gaussiana</h3>
                <p>Resolvendo sistemas lineares com visualização matricial.</p>
            </div>
        </div>
        
        <div class="canvas-container">
            <h3 style="margin-bottom: 20px; color: #495057;">Área de Visualização</h3>
            <canvas id="canvas" width="600" height="400"></canvas>
            <p style="margin-top: 20px; color: #6c757d;">
                <em>Em breve: transformações lineares animadas, vetores próprios, e mais!</em>
            </p>
        </div>
        
        <div style="background: #e7f3ff; padding: 20px; border-radius: 10px; margin-top: 30px; border-left: 4px solid #2196F3;">
            <h3 style="color: #2196F3; margin-bottom: 10px;">💡 Objetivo do Projeto</h3>
            <p style="color: #495057;">
                Criar visualizações que ajudem a entender <strong>geometricamente</strong> o que esses algoritmos fazem,
                não apenas como executá-los algebricamente. A álgebra linear fica muito mais intuitiva quando vemos
                as transformações acontecendo no espaço!
            </p>
        </div>
    </div>
    
    <script>
        // Placeholder para futuras visualizações
        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');
        
        // Desenhar grid de fundo
        ctx.strokeStyle = '#e0e0e0';
        ctx.lineWidth = 1;
        
        for (let i = 0; i <= 600; i += 50) {
            ctx.beginPath();
            ctx.moveTo(i, 0);
            ctx.lineTo(i, 400);
            ctx.stroke();
        }
        
        for (let i = 0; i <= 400; i += 50) {
            ctx.beginPath();
            ctx.moveTo(0, i);
            ctx.lineTo(600, i);
            ctx.stroke();
        }
        
        // Texto placeholder
        ctx.fillStyle = '#6c757d';
        ctx.font = '20px Arial';
        ctx.textAlign = 'center';
        ctx.fillText('Visualizações em breve...', 300, 200);
    </script>
</body>
</html>

projetos/fractais.html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Explorador de Fractais e Caos</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #FA8BFF 0%, #2BD2FF 52%, #2BFF88 90%);
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
        }
        
        header {
            text-align: center;
            margin-bottom: 40px;
        }
        
        h1 {
            font-size: 2.5em;
            background: linear-gradient(135deg, #FA8BFF 0%, #2BD2FF 52%, #2BFF88 90%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 10px;
        }
        
        .status {
            background: #d4edda;
            border-left: 4px solid #28a745;
            padding: 20px;
            border-radius: 5px;
            margin: 20px 0;
            color: #155724;
        }
        
        .canvas-container {
            background: #000;
            padding: 20px;
            border-radius: 15px;
            margin: 30px 0;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
        }
        
        canvas {
            display: block;
            margin: 0 auto;
            border-radius: 5px;
        }
        
        .controles {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }
        
        .controle {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 10px;
        }
        
        .controle label {
            display: block;
            font-weight: bold;
            margin-bottom: 8px;
            color: #495057;
        }
        
        button {
            background: linear-gradient(135deg, #FA8BFF 0%, #2BD2FF 100%);
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 8px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.2s;
        }
        
        button:hover {
            transform: translateY(-2px);
        }
        
        .info {
            background: #e7f3ff;
            padding: 20px;
            border-radius: 10px;
            border-left: 4px solid #2196F3;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>🌀 Explorador de Fractais & Caos</h1>
            <p style="font-size: 1.2em; color: #6c757d;">Beleza Matemática em Padrões Infinitos</p>
        </header>
        
        <div class="status">
            <h3>✅ Projeto Parcialmente Implementado</h3>
            <p>Versão básica do fractal de Mandelbrot funcionando! Mais fractais e interatividade virão em breve.</p>
        </div>
        
        <div class="canvas-container">
            <canvas id="canvas" width="800" height="600"></canvas>
        </div>
        
        <div class="controles">
            <div class="controle">
                <label>Iterações Máximas</label>
                <input type="range" id="iteracoes" min="20" max="200" value="50" style="width: 100%">
                <div style="text-align: center; margin-top: 5px; font-weight: bold;" id="iter-val">50</div>
            </div>
            
            <div class="controle" style="grid-column: span 2;">
                <button onclick="desenharMandelbrot()">🔄 Redesenhar</button>
            </div>
        </div>
        
        <div class="info">
            <h3 style="color: #2196F3; margin-bottom: 15px;">📐 Sobre o Conjunto de Mandelbrot</h3>
            <p style="margin-bottom: 10px;">
                O conjunto de Mandelbrot é definido pela iteração: <strong>z<sub>n+1</sub> = z<sub>n</sub>² + c</strong>
            </p>
            <p style="margin-bottom: 10px;">
                Para cada ponto c no plano complexo, iteramos começando com z₀ = 0. Se a sequência permanece limitada, 
                c pertence ao conjunto (colorido de preto). Caso contrário, colorimos baseado em quantas iterações 
                foram necessárias para divergir.
            </p>
            <p style="color: #6c757d; font-style: italic;">
                💡 Dica: Aumente as iterações para ver mais detalhes nas bordas do fractal!
            </p>
        </div>
        
        <div style="margin-top: 30px; padding: 20px; background: #fff3cd; border-radius: 10px; border-left: 4px solid #ffc107;">
            <h3 style="color: #856404; margin-bottom: 10px;">🚧 Próximas Funcionalidades</h3>
            <ul style="margin-left: 20px; color: #856404;">
                <li>Zoom interativo com mouse</li>
                <li>Conjunto de Julia</li>
                <li>Atratores estranhos (Lorenz, etc)</li>
                <li>Esquemas de cores personalizáveis</li>
            </ul>
        </div>
    </div>
    
    <script>
        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');
        const width = canvas.width;
        const height = canvas.height;
        
        document.getElementById('iteracoes').addEventListener('input', (e) => {
            document.getElementById('iter-val').textContent = e.target.value;
        });
        
        function mandelbrot(cx, cy, maxIter) {
            let x = 0, y = 0;
            let iter = 0;
            
            while (x*x + y*y <= 4 && iter < maxIter) {
                let xtemp = x*x - y*y + cx;
                y = 2*x*y + cy;
                x = xtemp;
                iter++;
            }
            
            return iter;
        }
        
        function desenharMandelbrot() {
            const maxIter = parseInt(document.getElementById('iteracoes').value);
            const imageData = ctx.createImageData(width, height);
            
            // Limites do plano complexo
            const xMin = -2.5, xMax = 1;
            const yMin = -1.25, yMax = 1.25;
            
            for (let py = 0; py < height; py++) {
                for (let px = 0; px < width; px++) {
                    // Mapear pixel para coordenada complexa
                    const cx = xMin + (px / width) * (xMax - xMin);
                    const cy = yMin + (py / height) * (yMax - yMin);
                    
                    const iter = mandelbrot(cx, cy, maxIter);
                    
                    const index = (py * width + px) * 4;
                    
                    if (iter === maxIter) {
                        // Dentro do conjunto - preto
                        imageData.data[index] = 0;
                        imageData.data[index + 1] = 0;
                        imageData.data[index + 2] = 0;
                    } else {
                        // Fora do conjunto - colorir baseado nas iterações
                        const ratio = iter / maxIter;
                        imageData.data[index] = Math.floor(255 * ratio);
                        imageData.data[index + 1] = Math.floor(255 * Math.sqrt(ratio));
                        imageData.data[index + 2] = Math.floor(255 * (1 - ratio));
                    }
                    imageData.data[index + 3] = 255; // Alpha
                }
            }
            
            ctx.putImageData(imageData, 0, 0);
        }
        
        // Desenhar ao carregar
        window.addEventListener('load', desenharMandelbrot);
    </script>
</body>
</html>

