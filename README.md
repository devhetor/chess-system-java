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
- As peças pretas são representadas pela cor amarela, já que o fundo do terminal é preto.
- Em **Captured pieces** o jogo armazena as peças capturadas.
- O **Turn** exibe o turno (rodada) em que o jogo está.
- **Waiting player** exibe qual é o jogador a jogar a próxima peça.
- **Source** é a origem, ou seja, a peça no qual o jogador irá jogar.
- **Target** é o destino, ou seja, o local no qual o jogador irá mover a peça.
- O jogo possui sistema de **Check** e **CheckMate**
- O jogo possui jogadas especiais do xadrez como: **en passant**, **promotion** e **Roque**.

## Modelo Conceitual
![modelo-conceitual](https://github.com/devhetor/assets/blob/64561f7034522fe592112caed586bdef3d7c4749/Chess-java-assets/imagem/chess-system-design.png)
fonte: Curso Java COMPLETO 2023 Programação Orientada a Objetos + Projetos


## :checkered_flag: Criação do tabuleiro no terminal 
Para a criação do tabuleiro, foi utilizado o conceito de uma matriz 8 x 8. Utilizamos uma função que imprime o tabuleiro de xadrez, incluindo as jogadas possíveis para cada peça. A função recebe como entrada duas matrizes: uma matriz de peças de xadrez (ChessPiece[][]) e uma matriz de valores booleanos (boolean[][]) que indicam se as jogadas são possíveis ou não para cada posição do tabuleiro.

```java
    public static void printBoard(ChessPiece[][] pieces, boolean[][] possibleMoves) {
		for (int i = 0; i < pieces.length; i++) {
			System.out.print((8 - i) + " ");
			for (int j = 0; j < pieces.length; j++) {
				printPiece(pieces[i][j], possibleMoves[i][j]);
			}
			System.out.println();
		}
		System.out.println("  a b c d e f g h");
	}
```
A função começa com um loop externo que percorre as linhas do tabuleiro. Antes de cada linha, é impresso o número da linha (8 - i), para que o tabuleiro seja impresso com a coluna a8 no canto inferior esquerdo e a coluna h1 no canto superior direito, como é comum em tabuleiros de xadrez.

Em seguida, há um loop interno que percorre as colunas do tabuleiro. Para cada posição do tabuleiro, é chamada a função printPiece, que imprime a peça de xadrez na posição (se houver) e se a jogada é possível (possibleMoves[i][j]).

Por fim, é impresso a legenda das colunas, "a b c d e f g h".

Essa função imprime o tabuleiro de xadrez com as jogadas possíveis para cada peça, facilitando a visualização e compreensão da situação da partida.

<h2 align="center">
  
![board](https://github.com/devhetor/assets/blob/64561f7034522fe592112caed586bdef3d7c4749/Chess-java-assets/imagem/board.png)
</h2>

## :chess_pawn: Movimentos possíveis de uma peça
Como cada peça tem maneira diferentes de se mover, deixamos esta função para a própria peça. Para uma torre por exemplo, temos as seguintes opções:

<p align="center">
  
![movimentos-torre](https://github.com/devhetor/assets/blob/64561f7034522fe592112caed586bdef3d7c4749/Chess-java-assets/imagem/movimentos%20possiveis%20torre.png)
fonte: Curso Java COMPLETO 2023 Programação Orientada a Objetos + Projetos
</p>

A torre pode se mover apenas nas casas que estão com o "X"(para os lados enquanto houver casas livres ou capturar a peça adversária), ela não pode se mover para as casas que não estão com o "X" vermelho. Seguindo esssa lógica, podemos fazer a seguinte pergunta: Quais são os movimentos possiveis de uma peça? Utilizamos uma fução que retorna uma matriz de valores booleanos com os movimentos possíveis para essa peça. 

```java
    public abstract boolean[][] possibleMoves();

	public boolean possibleMove(Position position) {
		return possibleMoves()[position.getRow()][position.getColumn()];
	}

	public boolean isThereAnyPossibleMove() {
		boolean[][] mat = possibleMoves();
		for (int i = 0; i < mat.length; i++) {
			for (int j = 0; j < mat.length; j++) {
				if (mat[i][j]) {
					return true;
				}
			}
		}
		return false;
	}
```

A função começa chamando a função possibleMoves, que retorna uma matriz de valores booleanos indicando se a jogada é possível ou não para cada posição do tabuleiro. Essa matriz é armazenada na variável mat. 

Em seguida, há dois loops que percorrem todas as posições da matriz mat. Se for encontrado algum valor true na matriz, significa que existe pelo menos uma jogada possível, então a função retorna true. Se todas as posições da matriz forem false, significa que não há jogadas possíveis, então a função retorna false.
  
## :inbox_tray: Instalação e execução

:warning: Para excução do programa é necessário ter o java instalado na versão 17 [Dowload](https://www.azul.com/downloads/?version=java-17-lts&package=jdk)

1. Faça o dowload do arquivo "Chess-system-java.jar". (clique no arquivo e depois clique em "View raw") 
2. Abra um terminal na pasta do arquivo. (utilize o terminal do Git Bash ou a ultima versão do Windows Power Shell)
3. Digite o codigo ```java -jar Chess-system-java.jar```
4. Bom Jogo!

<h2 align="center">
  
![execucao](https://github.com/devhetor/assets/blob/28a90452e84bcdd17ca84d3bc1ab4db9f0707166/Chess-java-assets/Gifs/execucao.gif)
</h2>

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
