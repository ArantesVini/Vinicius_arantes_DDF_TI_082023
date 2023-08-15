# Case 1

Como em todo projeto de tecnologia, manter métricas bem definidas e acompanhá-las é uma parte crucial do processo, para satisfação do cliente temos métricas muito utilizadas como o **NPS** (Net promoter Score), taxa de **churn** e **tempo de resposta**.
O primeiro passo é adquirir os dados da ferramentas utilizada, além de todas possuírem uma API que poderia ser integrada em uma pipeline para abastecer um banco relacional em _SQL_ (Structured Query Language), abordarei para o case a ferramenta **Zendesk**, que além da API permite a exportação de relatórios em CSV (_Comma separated values_) o que pode ser útil em análises pontuais.

Para armazenagem seria utilizado um banco relacional, que quanto a modelagem poderia utilizar o _star-schema de Kimball_, sendo então um _Data Warehouse_, tendo o fato que é o atendimento do ticket e possíveis dimensões como a pessoa, local, produto e tempo. Quanto à _SGBD_ (Sistema Gerenciador de Bancos de Dados) utilizaria o **Postgres** que é uma solução simples, prática e open-source que já possuo experiência.
O acompanhamento das métricas seria realizado de duas formas:

- Dashboard utilizando uma ferramenta de Dataviz (Ex. **Power BI**);
- Relatórios gerenciais sintéticos aos _stakeholders_.

Buscando fazer usos dessas métricas acompanhadas seriam abordados analistas onde há possibilidade de melhora de desempenho, produtos que mais geram _tickets_ a serem resolvidos, clientes que mais requerem suporte e com base nisso, tomar ações preventivas e evoluir nossos produtos.
