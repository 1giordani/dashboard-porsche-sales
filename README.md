# Dashboard interativa de vendas Porsche

Projeto do desafio da DIO **Criando Agentes de Tratamento de Dados**. A página reúne indicadores e gráficos interativos em um único arquivo HTML, publicado com GitHub Pages.

## Acessos

- Dashboard: https://1giordani.github.io/dashboard-porsche-sales/
- Repositório: https://github.com/1giordani/dashboard-porsche-sales

## Evidências visuais

- Visão geral: [porsche-dashboard-1790431641396.jpg](porsche-dashboard-1790431641396.jpg)
- Filtro aplicado para o modelo 911 Dakar: [porsche-filtro-911-dakar-1790431696410.jpg](porsche-filtro-911-dakar-1790431696410.jpg). O recorte retorna 3 vendas e US$ 810.600,00 em receita.

## Perguntas de negócio

1. **Quais modelos concentram o maior valor vendido?** O gráfico ordena os oito modelos de maior receita para apoiar a comparação de portfólio.
2. **Como os clientes pagam pelas compras?** O gráfico compara o número de vendas em cada forma de pagamento e ajuda a entender a composição das transações.
3. **Em quais meses a receita foi maior?** A série mensal usa as datas válidas para identificar variações ao longo do tempo. Datas `INVALID` ficam fora apenas deste gráfico temporal.

Os filtros de modelo, cidade, ano da venda, ano do veículo e pagamento atualizam os gráficos e os indicadores. Os cartões mostram quantidade de vendas, receita total, ticket médio e entregas concluídas.

## Dados e tratamento

Fonte: [planilha sanitizada Porsche do desafio DIO](https://hermes.dio.me/files/assets/8683bed0-cc33-4e06-bca9-04db9c31f9e2.xlsx), com 100 registros.

Para manter a base pública enxuta, o HTML incorpora somente os campos sanitizados usados no painel: data da venda, modelo, ano do veículo, preço, forma de pagamento, cidade e status de entrega. O ano da venda é derivado da data sanitizada. Os preços e anos foram convertidos para tipos numéricos antes de embutir os registros no HTML.

Foram excluídos os campos crus, nomes de clientes, nomes de vendedores e identificadores de venda. Quilometragem e estado também não foram incluídos, pois não são necessários para responder às perguntas escolhidas. A planilha informa **24 datas como `INVALID`**. Essas vendas continuam nos indicadores, receita por modelo e formas de pagamento; somente a série mensal e o filtro de ano da venda dependem de uma data válida. A receita geral na base completa é **US$ 12.827.800,50**.

## Prompt e refinamentos

### Prompt usado

> Crie uma dashboard responsiva em um único arquivo HTML, em português, usando somente os campos sanitizados da planilha de 100 vendas Porsche. Responda a estas perguntas: quais modelos concentram a receita, como os clientes pagam e em quais meses a receita foi maior? Inclua filtros de modelo, cidade, ano da venda, ano do veículo e método de pagamento; cartões com total de vendas, receita, ticket médio e entregas concluídas; e gráficos que atualizem com os filtros. Use um visual premium inspirado na identidade Porsche, com fundo grafite, vermelho de destaque, tipografia legível e layout adaptável a celular. Exclua nomes e identificadores pessoais. Mantenha vendas com data inválida nos totais e explique que elas não aparecem na série temporal. Inclua estados vazios, rótulos acessíveis e nenhum dado inventado.

### Ajustes incorporados

- Mantive a receita e a contagem das vendas sem data válida nos totais, em vez de descartá-las.
- Adicionei um aviso com a quantidade de datas inválidas no recorte atual.
- Limitei o gráfico de modelos aos oito maiores valores para facilitar a leitura.
- Acrescentei filtros combináveis, botão para limpar filtros, estado vazio quando não há resultados e layout responsivo.
- Removi os campos que não respondem às perguntas e que poderiam expor nomes ou identificadores.

## Ferramenta

A dashboard foi construída com ChatGPT nesta conversa. Não foi usado o Canvas nem um agente com skill própria. O HTML, CSS, JavaScript e os dados sanitizados estão no próprio `index.html`; não há bibliotecas externas obrigatórias.

## Como reproduzir

1. Baixe a planilha sanitizada na fonte da DIO.
2. Leia apenas as colunas sanitizadas necessárias às perguntas e descarte nomes, identificadores e colunas cruas antes de publicar.
3. Converta preço e ano do veículo para números. Preserve datas inválidas como ausentes e registre a quantidade excluída de análises por data.
4. Gere ou atualize o array de registros sanitizados embutido em `index.html`.
5. Publique o arquivo na raiz de um repositório público e habilite GitHub Pages para a branch principal, pasta raiz (`/(root)`).

## Estrutura

- `index.html`: dashboard, estilos, lógica dos filtros, gráficos SVG e os dados sanitizados utilizados.
- `README.md`: perguntas, decisões analíticas, tratamento dos dados e instruções de reprodução.
