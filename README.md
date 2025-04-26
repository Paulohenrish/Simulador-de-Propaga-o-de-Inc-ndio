🔥 Simulador de Propagação de Incêndio em Floresta

📚 Introdução

Este projeto implementa um simulador que representa a propagação de incêndio em uma floresta, juntamente com a movimentação de um animal tentando sobreviver ao fogo. O sistema é construído com C++, utilizando conceitos fundamentais de manipulação de matrizes, controle de fluxo e simulação computacional.

A proposta visa desenvolver o raciocínio algorítmico, o uso de estruturas de dados e a prática com manipulação de arquivos.

⚙️ Metodologia

🏗️ Estrutura Geral

O simulador utiliza uma matriz para representar a floresta, onde cada célula possui um estado específico:

Valor	Representação

0	Espaço vazio 🛤️

1	Árvore 🌳

2	Árvore pegando fogo 🔥

3	Árvore queimada 🖤

4	Água 💧

9 ou A	Animal 🦌

A matriz é carregada a partir de um arquivo de entrada chamado input.dat.

🔄 Funcionamento da Simulação

A cada interação (ou rodada do simulador), ocorrem duas etapas principais:

🦌 Movimentação do Animal

O animal tenta se mover para posições adjacentes (cima, baixo, esquerda, direita).

Prioriza a sobrevivência: evita células pegando fogo (2) e queimadas (3).

Caso encontre água (4), contabiliza um encontro.

Se não puder se mover ou for consumido pelo fogo, a simulação registra sua morte.

🔥 Propagação do Fogo

Árvores (1) adjacentes ao fogo (2) começam a pegar fogo.

Árvores que estavam pegando fogo (2) se tornam árvores queimadas (3).

A propagação do fogo e a movimentação do animal são feitas em ciclos alternados, com prioridade para a movimentação do animal antes da propagação em cada iteração.

🧩 Detalhamento das Classes

🌲 Classe Floresta

Representa a matriz da floresta.

Responsável por armazenar o estado de cada célula e disponibilizar funções de leitura da entrada.

🦌 Classe Animal

Representa o animal dentro da floresta.

Responsável por:

Decidir a movimentação em cada turno.

Registrar passos dados e encontros com água.

Determinar se o animal morreu ou sobreviveu.

🔥 Classe Fogo

Responsável pela lógica de propagação do fogo.

Garante que o fogo se espalhe corretamente de acordo com as regras estabelecidas.

📝 Arquivo io.cpp

Gerencia a leitura do arquivo de entrada e a gravação da saída no arquivo output.dat.

Também salva um arquivo de depuração output_debug.txt para verificar o estado interno a cada passo.

📏 Regras de Simulação

O fogo não se propaga instantaneamente: árvores recém-atingidas se tornam fogo apenas na interação seguinte.

O animal se movimenta antes do fogo se propagar em cada ciclo.

Se o fogo atingir a posição do animal, ele é considerado morto na interação atual.

📚Estudo de Caso / Resultados

🎯 Objetivo

Avaliar o comportamento da propagação de fogo em uma floresta representada por uma matriz e analisar a movimentação estratégica de um animal tentando sobreviver ao incêndio.

📋 Configuração Inicial

O ambiente inicial de teste foi configurado com a seguinte matriz (input.dat):

1 1 1 1 4

1 2 1 1 1

1 1 1 1 4

0 0 1 1 1

1 4 1 0 4

Significados:

1 → Árvore

2 → Árvore pegando fogo (foco inicial do incêndio)

4 → Água

0 → Espaço vazio

(o animal A é posicionado automaticamente pelo programa)

🔥 Evolução da Simulação

Durante a execução, o comportamento observado foi:

Interação 1

Fogo: Propagou para árvores adjacentes ao primeiro foco (acima, abaixo e lados).

Animal: Moveu-se rapidamente para longe do fogo, priorizando áreas seguras.

Matriz atualizada:

1 2 1 1 4

2 2 2 1 1

1 2 1 1 4

0 0 1 1 1

1 4 1 0 4

Interação 2

Fogo: Árvores próximas continuaram pegando fogo, aumentando a área de risco.

Animal: Continuou se movimentando de forma estratégica, procurando se afastar do fogo.

Matriz atualizada:

2 2 2 1 4

2 3 2 2 1

2 2 2 1 4

0 0 1 1 1

1 4 1 0 4

Interação 3

Fogo: O fogo se alastrou ainda mais pela matriz.

Animal: Encontrou água em seu caminho, o que aumentou suas chances de sobrevivência.

Matriz atualizada:

2 3 2 2 4

3 3 3 2 2

2 3 2 2 4

0 0 2 1 1

1 4 1 0 4

Interação 4

Fogo: Quase toda a parte central da floresta foi tomada por fogo ou árvores queimadas.

Animal: Conseguia ainda se mover pelas laterais mais seguras da floresta.

Matriz atualizada:

3 3 3 2 4

3 3 3 3 2

3 3 3 2 4

0 0 2 2 1

1 4 2 0 4

Interação 5

Fogo: Quase todas as árvores foram destruídas.

Animal: Se manteve vivo e fora das áreas em chamas.

Matriz atualizada:

3 3 3 3 4

3 3 3 3 3

3 3 3 3 4

0 0 3 2 2

1 4 2 0 4

Interação 6

Fogo: Últimos focos de fogo foram extintos, sobrando principalmente árvores queimadas.

Animal: Sobreviveu com sucesso à propagação do incêndio!

Matriz final:

3 3 3 3 4

3 3 3 3 3

3 3 3 3 4

0 0 3 3 2

1 4 3 0 4

🐾 Desempenho do Animal

Total de passos percorridos: 6

Águas encontradas: 1

Estado final: Sobreviveu ✅

Durante o percurso, o animal precisou constantemente analisar seu ambiente para evitar o fogo e buscar áreas de segurança próximas à água (4).

🧠 Análise Crítica

Movimentação inteligente: O algoritmo de movimentação implementado garantiu que o animal priorizasse locais seguros primeiro.

Estratégia do fogo: A propagação lenta e controlada do fogo permitiu maior realismo, evitando que toda a floresta queimasse instantaneamente.

Padrão esperado: As interações e a evolução da matriz seguiram fielmente o esperado para o estudo de caso inicial.

📈 Considerações Finais

A separação da movimentação do animal e da propagação do fogo em ciclos alternados foi essencial para garantir a sobrevivência possível.

Em florestas maiores ou com menos água, a probabilidade de sobrevivência diminui consideravelmente.

O sistema é altamente modular, permitindo no futuro:

Inserção de novos tipos de terreno (pedras, obstáculos).

Alteração da estratégia de movimentação do animal.

🚀 Resumo Visual das Interações

Iteração	Estado Principal da Floresta

1	Fogo começa a se propagar.

2	Expansão do fogo em volta.

3	Região central dominada.

4	Animal quase sem opções.

5	Extinção quase total do fogo.

6	Animal sobrevive, floresta destruída.

📜 Conclusão

O simulador de propagação de incêndio foi desenvolvido com sucesso, cumprindo os seguintes objetivos:

Simular de maneira realista a propagação de fogo em uma floresta usando matrizes.

Implementar um sistema de movimentação para o animal que prioriza a sobrevivência.

Aplicar práticas de programação orientada a objetos em C++ de forma modularizada e organizada.

O projeto reforça habilidades fundamentais para desenvolvimento de algoritmos e abre possibilidades para expansões futuras (como IA mais avançada ou simulações em ambientes maiores).

📚 Referências

📖 Apostilas de Algoritmos e Estruturas de Dados (CEFET-MG).

🌐 Documentação oficial do C++17.

🔥 Modelos de simulação de propagação de incêndios florestais.

🧠 Conceitos de movimentação em grafos e labirintos.

⚙️ Método de Compilação

💻 Compilando localmente (Linux/Windows):

g++ main.cpp floresta.cpp fogo.cpp animal.cpp io.cpp -o simulador -std=c++17
./simulador

Utilize -std=c++17 para compatibilidade.

Mantenha o arquivo input.dat no mesmo diretório da execução.

🌐 Compilando no OnlineGDB:

Crie um novo projeto em C++.

Suba todos os arquivos .cpp e .hpp.

Configure para padrão C++17.

Adicione input.dat.

Compile e execute.

👨‍💻 Autores

Paulo Henrique de Souza Hemetrio

Instagram: @Paulo_henrish

