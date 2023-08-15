# Case 5

A consulta base seria a seguinte:

```
SELECT user_email_id,
    user_id,
    user_email,
    data_cadastramento
FROM user_emails ue
WHERE data_cadastramento >= CURRENT_DATE - INTERVAL '30 days'
ORDER BY data_cadastramento DESC;
```

Na primeira parte, o select, peguei 3 colunas bases da tabela, `user_email_id` que é a chave primária dessa tabela, tendo um caso em que por exemplo cada associado pode ter mais de um e-mail, `user_id` uma chave estrangeira que se relaciona de muitos para um (N:1) com uma tabela dimensional de usuários, onde poderíamos através de um **JOIN** trazer dados pessoais para a análise e `data_cadastramento` para a análise.
A segunda parte é o `FROM user_emails ue` onde estou definindo a tabela que desejo realizar a busca e atribuindo um **ALIAS** a ela, de forma a simplificar um futuro Join.
Em seguida temos o filtro da tabela `WHERE data_cadastramento >= CURRENT_DATE - INTERVAL '31' day` que, no caso pegando o exemplo do Ansi SQL, estaria filtrando de forma dinâmica os últimos 31 dias dado a data atual, aqui pensando que o relatório tem dados **D-1**, que é o mais comum, e que queremos os últimos 30 dias da tabela.
Por fim para manter a ordem da tabela em toda consulta temos `ORDER BY data_cadastramento DESC;` que define que a coluna seja ordenada com base na **data_cadastramento** de forma decrescente.

A depender da tempestividade do envio desse relatório, poderia ser feita uma pipeline mais estruturada utilizando _Apache Airflow_ que com seus conectores poderia conectar no banco, realizar processos de tratamento em Python e enviar email para as pessoas chaves do processo.

Caso fosse uma análise pontual, o mesmo poderia ser exportado diretamente do SGBD (Sistema gerenciador de Banco de Dados) em um formato de consumo rápido, como CSV (Comma Separated Values) ou Excel.
