# Dados do COVID-19 por estado brasileiro, no Brasil, por continente, e no mundo.
Durante a quarentena, as aulas têm sido a distância, e eu tive que fazer um trabalho de estatística sobre COVID-19. Como os dados que eu tabulei não são fáceis de encontrar, decido deixá-los aqui.
Eu disponibilizei o meu "trabalho" que pretendi fazê-lo de forma mais profissional e menos "trabalho escolar".
## Plotando os gráficos:
Diponibilizei um arquivo .tex ensinando como eu os faço utilizando os arquivos .dat, também tem a minha jornada de como aprendi a fazer isso no LaTeX. Eu utilizei o TikZ e o pgfplots.
Inclua no seu preâmbulo:
```tex
\usepackage{tikz}
\usepackage{pgfplots}
\usepackage{pgfplotstable}

% Se quiser utilizar as mesmas configurações que eu use também:
\pgfplotsset{width=.8\textwidth,compat=1.9}
```
E então, basciamente:
```tex
\begin{figure}[!h] %Abre o ambiente figura
	\centering % Para centralizar
	\begin{tikzpicture} %Abre o ambiente TikZ
	\begin{axis}[ % Inicializa os eixos
	title = COVID-19 no estado do Amapá, % Um título
	date coordinates in=x, % Datas como coordenadas
	xticklabel style={rotate=90,anchor=near xticklabel}, % Estilo do gráfico
	xticklabel={\day/\month}, % Estilo do gráfico dia/mês
	xlabel={Tempo}, % Descrição eixo x
	xlabel style={yshift=-1pt}, % Estilo da descrição em x
	ylabel=Quantidade de Casos, % Descrição eixo y
	ymin=0, % y mínimo
	ymax=1200, %y máximo
	xmin=2020-03-20, %x mínimo
	xmax=2020-04-30, %x máximo
	ylabel style={yshift=10pt}, % Estilo da descrição em y
	legend style={
	at={(0.5,-0.2)},anchor=north,legend columns=-1,
	}, % Estilo da legenda
	],
	\addplot table [x index=0,y index=1] {DATA-AP.dat}; % Adicionando a curva de  contaminados
	\addlegendentry{Contaminados} % Legenda curva acima
	\addplot table [x index=0,y index=2] {DATA-AP.dat}; % Adicionando a curva de  óbitos
	\addlegendentry{Óbitos} % Legenda curva acima
	\end{axis} % Termina a entrada para os eixos
	\end{tikzpicture} % Fecha o ambiente TikZ 
\end{figure} % Fecha o ambiente figura
```
Gostaria de agradecer e listar como minha fonte o [Ministério da Saúde](https://covid.saude.gov.br/) e a [Johns Hopkins University](https://coronavirus.jhu.edu/map.html) os dados que eu disponibilizo aqui para todos é entre 22/01/2020 e 30/04/2020. Eu utilizei a tabela da Johns Hopkins e separei país por país colocando-o em uma tabela com seu continente. Além de tabelar o Brasil como um todo, que não está disponível no site do Ministério da Saúde. (Ao menos eu não achei).

Possívelmente, eu devo traduzir esse repo para inglês no futuro, mas por enquanto deixarei assim. Desde que esteja para ajudar alguém, já dou a tarefa como cumprida. 
