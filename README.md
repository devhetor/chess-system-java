<h1 align="center">
  :chess_pawn: Chess System Java :chess_pawn:
</h1>

<p align="center">
  <img alt="GitHub language count" src="https://img.shields.io/github/languages/count/devhetor/chess-system-java?style=for-the-badge">

  <img alt="Repository size" src="https://img.shields.io/github/repo-size/devhetor/chess-system-java?style=for-the-badge">

  <img alt="License" src="https://img.shields.io/github/license/devhetor/chess-system-java?style=for-the-badge">
</p>

<p align="center">
  <a href="#-tecnologias">Tecnologias</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-projeto">Projeto</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#%EF%B8%8F-instalacao">Instalação</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#%EF%B8%8F-imagens">Imagens</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-licença">Licença</a>
</p>

## :hammer_and_wrench: Tecnologias 

Esse projeto foi desenvolvido com as seguintes tecnologias:

- :coffee: Java

## 💻 Projeto
Desenvolvido em linguagem Java, este projeto faz parte do curso *__Java COMPLETO 2020 Programação Orientada a Objetos + Projetos__* da [Udemy](https://www.udemy.com/course/java-curso-completo/). Consiste em um jogo simples de Xadrez, que executa através do terminal. O jogo possui programação defensiva(contra eventuais bugs), tratamentos de erros, jogas especias de xadrez (promoção, roque e en passant) e previsão de movimento das peças.  
Peças: Pawn (Peão), Rook (Torre), Knight (Cavalo), Bishop (Bispo), Queen (Rainha) e King (Rei).
|-|

 A mecânica do jogo é baseada em **linhas** (_1, 2, 3, 4, 5, 6, 7, 8_) e **colunas** (_a, b, c, d, e, f, g, h_), parecido com o jogo batalha naval.
- Para **escolher** uma peça é necessário selecionar _primeiramente_ a **coluna** e logo em seguida (sem espaços) selecionar a **linha**, exemplo: **c2**

- Em **Captured pieces** o jogo armazena as peças capturadas.
- O **Turn** exibe o turno (rodada) em que o jogo está.
- **Waiting player** exibe qual é o jogador a jogar a próxima peça.
- **Source** é a origem, ou seja, a peça no qual o jogador irá jogar.
- **Target** é o destino, ou seja, o local no qual o jogador irá mover a peça.
- O jogo possui sistema de **Check** e **CheckMate**
- O jogo possui jogadas especiais do xadrez como: **en passant**, **promotion** e **Roque**.
  
## :inbox_tray: Instalacao e execução

:warning: Para excução do programa é necessário ter o java instalado na versão 17 [Dowload](https://www.azul.com/downloads/?version=java-17-lts&package=jdk)

1. Faça o dowload do arquivo "Chess-system-java.jar". (clique no arquivo e depois clique em "View raw") 
2. Abra um terminal na pasta do arquivo. (utilize o terminal do Git Bash ou a ultima versão do Windows Power Shell)
3. Digite o codigo ```java -jar Chess-system-java.jar```
4. Bom Jogo!

![execucao](https://github.com/devhetor/assets/blob/28a90452e84bcdd17ca84d3bc1ab4db9f0707166/Chess-java-assets/Gifs/execucao.gif)

## 🖼️ Imagens

| Tela Inicial  | Tratamento de Exceção | Movimentos Possíveis | 
|---|---|---|
| ![tela-inicial](https://github.com/devhetor/assets/blob/60090343fd8d682ce40c32730e3714a953b0a128/Chess-java-assets/imagem/tela%20inicial.png)  | ![tratamento-execao](https://github.com/devhetor/assets/blob/60090343fd8d682ce40c32730e3714a953b0a128/Chess-java-assets/imagem/tratamento%20de%20excecoes.png)  | ![check](https://github.com/devhetor/assets/blob/60090343fd8d682ce40c32730e3714a953b0a128/Chess-java-assets/imagem/movimentos%20possiveis.png)  | 

| Jogada en Passant  | Promotion | 
|---|---|
| ![enPassant moviment](https://github.com/devhetor/assets/blob/60090343fd8d682ce40c32730e3714a953b0a128/Chess-java-assets/imagem/jogada%20en%20passant.png)  | ![promotion](https://github.com/devhetor/assets/blob/60090343fd8d682ce40c32730e3714a953b0a128/Chess-java-assets/imagem/jogada%20promotion.png)  |

## 📝 Licença

Esse projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE.md) para mais detalhes.

## :raised_hands: Agradecimentos

Quero agradeçer ao professor Nelio Alves por disponibilizar este projeto e explicar de maneira clara e objetiva, todas as partes do projeto.
