# Bio-Check

Aplicação web educacional que apresenta gráficos e tabelas de ciclos calculados a partir da data de nascimento e de uma data de referência escolhida pelo usuário.

## Sobre o projeto

O **Bio-Check** foi desenvolvido com HTML, CSS e JavaScript puro. A aplicação calcula curvas senoidais para diferentes categorias, exibe os resultados em um gráfico interativo e gera uma tabela com projeções para os 60 dias seguintes à data de foco.

O nome e a data de nascimento são armazenados localmente no navegador, permitindo que as informações sejam recuperadas no próximo acesso.

> Os resultados são apenas representações matemáticas e educacionais. Não constituem avaliação médica, psicológica, espiritual ou financeira.

## Funcionalidades

- Cadastro de nome e data de nascimento.
- Seleção de uma data de foco.
- Persistência dos dados no `localStorage`.
- Gráfico com janela visual de 30 dias.
- Navegação diária pelos botões anterior e próximo.
- Retorno rápido para a data atual.
- Navegação horizontal pelo gráfico com o mouse.
- Exibição de seis indicadores:
  - físico;
  - emocional;
  - intelectual;
  - espiritual;
  - intuitivo;
  - financeiro.
- Aviso de ponto de instabilidade quando um indicador fica próximo de zero.
- Tabela com projeções para 60 dias.
- Destaque visual das linhas consideradas críticas.
- Layout específico para impressão.
- Impressão do gráfico, dados informados e tabela.

## Tecnologias utilizadas

- HTML5
- CSS3
- JavaScript Vanilla
- Canvas API
- Web Storage API (`localStorage`)
- Media Queries para impressão

## Estrutura do projeto

```text
bio-check/
├── index.html
└── README.md
```

A estrutura da página, os estilos e toda a lógica de cálculo estão concentrados no arquivo `index.html`.

## Como executar

1. Baixe os arquivos do projeto.
2. Abra o arquivo `index.html` em um navegador moderno.
3. Informe o nome e a data de nascimento.
4. Escolha a data de foco desejada.
5. Use os controles para navegar entre os dias.
6. Arraste o gráfico horizontalmente para alterar a data de referência.
7. Clique em **Imprimir** para abrir a janela de impressão do navegador.

Não é necessário instalar pacotes, configurar banco de dados ou executar um processo de compilação.

## Indicadores calculados

A aplicação utiliza curvas senoidais com períodos definidos no JavaScript:

| Indicador | Período utilizado |
|---|---:|
| Físico | 23 dias |
| Emocional | 28 dias |
| Intelectual | 33 dias |
| Espiritual | 53 dias |
| Intuitivo | 38 dias |
| Financeiro | Média dos indicadores intelectual e intuitivo |

Os valores são apresentados como percentuais aproximados entre `-100%` e `100%`.

## Como funciona o cálculo

Para os indicadores principais, o projeto utiliza uma função baseada em seno:

```javascript
Math.sin((2 * Math.PI * diasVividos) / periodo)
```

O total de dias é calculado pela diferença entre a data de referência e a data de nascimento. O indicador financeiro é obtido pela média dos resultados intelectual e intuitivo.

Um ponto é tratado pela interface como instável quando o valor absoluto calculado fica abaixo de `0.1`.

## Gráfico

O gráfico é desenhado em um elemento `canvas` com resolução interna de `1600 × 260`.

A visualização inclui:

- linhas coloridas para cada ciclo principal;
- eixo horizontal central;
- divisões diárias;
- marcador vertical na data de foco;
- intervalo visual de 30 dias;
- suporte a arrastar com o mouse.

## Tabela de projeções

A tabela apresenta 60 linhas a partir da data de referência. Cada linha mostra:

- dia e mês;
- percentual físico;
- percentual emocional;
- percentual intelectual;
- percentual espiritual;
- percentual intuitivo;
- percentual financeiro.

As datas que possuem ao menos um indicador próximo de zero recebem um símbolo de atenção.

## Armazenamento local

O sistema usa as seguintes chaves no `localStorage`:

```text
biocheck_nome
biocheck_nascimento
```

Os dados ficam armazenados somente no navegador e no dispositivo utilizados. Limpar os dados do navegador pode remover essas informações.

## Impressão

O botão **Imprimir** executa `window.print()`. Durante a impressão:

- os controles e o aviso de instabilidade são ocultados;
- o fundo é alterado para branco;
- as cores são ajustadas para maior legibilidade;
- a tabela passa a ser exibida sem limite de altura;
- o gráfico recebe dimensões apropriadas para o documento.

## Personalização

As cores dos indicadores podem ser alteradas nas variáveis CSS:

```css
:root {
  --fisico: #00ff88;
  --emocional: #00d0ff;
  --intelectual: #ffcc00;
  --espiritual: #a200ff;
  --intuitivo: #ff0077;
  --financeiro: #ff8800;
}
```

A quantidade de dias exibida no gráfico pode ser modificada pela constante:

```javascript
const DIAS_VISIVEIS = 30;
```

## Compatibilidade

Use um navegador moderno com suporte a:

- JavaScript;
- Canvas API;
- `localStorage`;
- campos de data do HTML5;
- impressão por CSS.

## Limitações

- A navegação por arraste foi implementada para mouse e não contém eventos específicos de toque.
- Os cálculos não representam diagnóstico científico ou profissional.
- Não há sincronização entre navegadores ou dispositivos.
- A aplicação não possui usuários, autenticação ou banco de dados remoto.
- O conteúdo depende das datas informadas pelo usuário.

---

### Instalação no computador

### No Google Chrome ou Microsoft Edge:

  1. Abra o endereço publicado do projeto.
  2. Aguarde o carregamento completo da página.
  3. Clique no ícone de instalação exibido na barra de endereço ou abra o menu do navegador.
  4. Selecione Instalar aplicativo ou Instalar este site como aplicativo.
  5. Confirme a instalação.

Depois disso, o aplicativo poderá ser aberto pelo menu Iniciar, pela área de trabalho ou pelo gerenciador de aplicativos do sistema.

### Instalação no celular ou tablet

### Em navegadores compatíveis:

1. Abra o endereço do projeto.
2. Acesse o menu do navegador.
3. Selecione Instalar aplicativo ou Adicionar à tela inicial.
4. Confirme o nome e a instalação.

O ícone será adicionado à tela inicial do dispositivo.

**Observações**

A disponibilidade e o nome da opção de instalação podem variar conforme o navegador e o sistema operacional.
Abrir somente o arquivo index.html pelo computador não garante a instalação como PWA.
O projeto deve ser publicado em HTTPS para utilizar os recursos completos de instalação e service worker.
O funcionamento offline depende da configuração do service-worker.js e dos arquivos adicionados ao cache.
Atualizações no projeto podem exigir a atualização da versão do cache do service worker.

---

## Autor

**Alberto de Campos Neto**

## Aviso

> Este projeto é uma demonstração educacional desenvolvida para estudos de HTML, CSS e JavaScript. A empresa mencionada é fictícia e qualquer semelhança com empresas reais é mera coincidência.

Your site is live at https://alcane1959.github.io/Bioritmo/
