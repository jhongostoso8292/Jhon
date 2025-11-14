<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IA Particular - Jogos</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 0; padding: 0; background-color: #f4f4f4; color: #333; }
        header { background-color: #ff5722; color: white; padding: 20px; text-align: center; }
        nav { background-color: #333; padding: 10px; text-align: center; }
        nav a { color: white; margin: 0 15px; text-decoration: none; }
        section { padding: 20px; max-width: 1200px; margin: 0 auto; }
        .game-list { display: flex; flex-wrap: wrap; justify-content: space-around; }
        .game-card { background: white; border: 1px solid #ddd; border-radius: 8px; padding: 15px; margin: 10px; width: 300px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); text-align: center; }
        .game-card img { max-width: 100%; height: 150px; object-fit: cover; }
        #game-section { background: white; padding: 20px; border-radius: 8px; margin: 20px 0; }
        footer { background-color: #333; color: white; text-align: center; padding: 10px; }
        form { max-width: 600px; margin: 0 auto; }
        input, textarea { width: 100%; padding: 10px; margin: 10px 0; border: 1px solid #ccc; border-radius: 4px; }
        button { background-color: #ff5722; color: white; padding: 10px; border: none; border-radius: 4px; cursor: pointer; }
        #guess-game { text-align: center; }
    </style>
</head>
<body>
    <header>
        <h1>IA Particular - Jogos</h1>
        <p>Explore o mundo dos jogos com inteligência artificial particular.</p>
    </header>
    
    <nav>
        <a href="#home">Início</a>
        <a href="#games">Jogos Populares</a>
        <a href="#play">Jogue Agora</a>
        <a href="#contact">Contato</a>
    </nav>
    
    <section id="home">
        <h2>Bem-vindo ao IA Particular</h2>
        <p>Este site, gerado por uma IA particular, oferece informações sobre jogos, listas de títulos famosos e até um jogo simples para jogar online!</p>
    </section>
    
    <section id="games">
        <h2>Jogos Populares</h2>
        <div class="game-list">
            <div class="game-card">
                <img src="https://via.placeholder.com/300x150?text=Minecraft" alt="Minecraft">
                <h3>Minecraft</h3>
                <p>Um jogo de construção e aventura onde você cria mundos infinitos.</p>
            </div>
            <div class="game-card">
                <img src="https://via.placeholder.com/300x150?text=Fortnite" alt="Fortnite">
                <h3>Fortnite</h3>
                <p>Batalha real com construção e ação intensa.</p>
            </div>
            <div class="game-card">
                <img src="https://via.placeholder.com/300x150?text=Among+Us" alt="Among Us">
                <h3>Among Us</h3>
                <p>Jogo de dedução social multiplayer.</p>
            </div>
            <div class="game-card">
                <img src="https://via.placeholder.com/300x150?text=The+Legend+of+Zelda" alt="The Legend of Zelda">
                <h3>The Legend of Zelda</h3>
                <p>Aventura épica com exploração e quebra-cabeças.</p>
            </div>
        </div>
    </section>
    
    <section id="play">
        <h2>Jogue Agora: Adivinhe o Número</h2>
        <div id="game-section">
            <p>Adivinhe um número entre 1 e 100. Você tem 10 tentativas!</p>
            <input type="number" id="guess" placeholder="Digite seu palpite">
            <button onclick="checkGuess()">Adivinhar</button>
            <p id="result"></p>
            <p id="attempts">Tentativas restantes: 10</p>
        </div>
    </section>
    
    <section id="contact">
        <h2>Contato</h2>
        <form>
            <label for="name">Nome:</label>
            <input type="text" id="name" name="name" required>
            
            <label for="email">E-mail:</label>
            <input type="email" id="email" name="email" required>
            
            <label for="message">Mensagem:</label>
            <textarea id="message" name="message" rows="5" required></textarea>
            
            <button type="submit">Enviar</button>
        </form>
    </section>
    
    <footer>
        <p>&copy; 2023 IA Particular. Todos os direitos reservados. Site gerado por IA.</p>
    </footer>
    
    <script>
        // Jogo simples: Adivinhe o Número
        let secretNumber = Math.floor(Math.random() * 100) + 1;
        let attempts = 10;
        
        function checkGuess() {
            const guess = parseInt(document.getElementById('guess').value);
            const result = document.getElementById('result');
            const attemptsDisplay = document.getElementById('attempts');
            
            if (isNaN(guess) || guess < 1 || guess > 100) {
                result.textContent = 'Digite um número válido entre 1 e 100!';
                return;
            }
            
            attempts--;
            attemptsDisplay.textContent = `Tentativas restantes: ${attempts}`;
            
            if (guess === secretNumber) {
                result.textContent = 'Parabéns! Você acertou!';
                resetGame();
            } else if (attempts === 0) {
                result.textContent = `Fim de jogo! O número era ${secretNumber}.`;
                resetGame();
            } else if (guess < secretNumber) {
                result.textContent = 'Muito baixo! Tente novamente.';
            } else {
                result.textContent = 'Muito alto! Tente novamente.';
            }
        }
        
        function resetGame() {
            setTimeout(() => {
                secretNumber = Math.floor(Math.random() * 100) + 1;
                attempts = 10;
                document.getElementById('guess').value = '';
                document.getElementById('result').textContent = '';
                document.getElementById('attempts').textContent = 'Tentativas restantes: 10';
            }, 3000);
        }
        
        // Validação do formulário
        document.querySelector('form').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Mensagem enviada! (Simulação - em um site real, isso seria processado no backend)');
        });
    </script>
</body>
</html>
