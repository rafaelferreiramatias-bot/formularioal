<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cadastro de Filmes</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 30px;
        }

        input, select, textarea {
            display: block;
            margin-bottom: 10px;
            padding: 5px;
        }

        input[type="radio"] {
            display: inline;
        }

        button {
            padding: 5px 15px;
            cursor: pointer;
        }

        li {
            margin-bottom: 10px;
        }
    </style>
</head>

<body>

    <h1>Cadastro de Filmes</h1>

    <form id="formulario">

        <label for="nome">Nome do filme:</label>
        <input type="text" id="nome" required>

        <label for="genero">Gênero:</label>
        <select id="genero" required>
            <option value="">Selecione um gênero</option>
            <option value="Ação">Ação</option>
            <option value="Comédia">Comédia</option>
            <option value="Terror">Terror</option>
            <option value="Drama">Drama</option>
            <option value="Animação">Animação</option>
            <option value="Ficção científica">Ficção científica</option>
        </select>

        <label for="nota">Nota de avaliação (0 a 10):</label>
        <input
            type="number"
            id="nota"
            min="0"
            max="10"
            step="1"
            required
        >

        <p>Assistiria novamente?</p>

        <div>
            <input
                type="radio"
                id="sim"
                name="assistiria"
                value="Sim"
                required
            >
            <label for="sim">Sim</label>
        </div>

        <div>
            <input
                type="radio"
                id="nao"
                name="assistiria"
                value="Não"
            >
            <label for="nao">Não</label>
        </div>

        <br>

        <button type="submit">Cadastrar filme</button>

    </form>

    <h2>Filmes Cadastrados</h2>

    <ol id="listaFilmes"></ol>

    <script>
        // Array para armazenar os filmes
        let filmes = [];

        const formulario = document.getElementById("formulario");
        const lista = document.getElementById("listaFilmes");

        formulario.addEventListener("submit", function(event) {
            event.preventDefault();

            // Captura os valores do formulário
            let nome = document.getElementById("nome").value;
            let genero = document.getElementById("genero").value;
            let nota = document.getElementById("nota").value;
            let assistiria = document.querySelector(
                'input[name="assistiria"]:checked'
            ).value;

            // Cria o objeto filme
            let filme = {
                nome: nome,
                genero: genero,
                nota: nota,
                assistiria: assistiria
            };

            // Adiciona o filme ao array
            filmes.push(filme);

            // Cria um item na lista
            let item = document.createElement("li");

            item.textContent =
                nome + " — " +
                genero + " — Nota " +
                nota + " — Assistiria novamente: " +
                assistiria;

            // Adiciona o item à lista
            lista.appendChild(item);

            // Mostra o array no console
            console.log(filmes);

            // Limpa o formulário
            formulario.reset();
        });
    </script>

</body>
</html>
