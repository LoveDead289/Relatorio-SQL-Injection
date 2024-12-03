# Relatório Geral de Teste de Penetração - Vulnweb

**Matéria:** Ciber Segurança  
**Professor:** Fábio Oliveira  
**Aluno:** Marcos Paulo Roriz  
**RA:** 22007534  

---

## Escopo

Este documento apresenta o processo de avaliação de segurança realizado em sites disponibilizados pelo **Vulnweb**, aplicando técnicas de teste black-box com conhecimento prévio das tecnologias utilizadas nos endpoints.

---

## Sites Avaliados

- [Relatório: SecurityTweets](Relatorio_SecurityTweets_Vulnweb.md)  
- [Relatório: Acuart](Relatorio_Acuart_Vulnweb.md)  
- [Relatório: Acublog](Relatorio_Acublog_Vulnweb.md)  

---

## Metodologia

### Fase 1: Reconhecimento

Nesta fase, foram realizadas pesquisas avançadas e uso de ferramentas automatizadas para coletar informações sobre os sites. As ferramentas utilizadas incluem:  
- **Google Dorks**: Pesquisas avançadas, como `site:testphp.vulnweb.com +"Index of /admin"`.  
- **Ferramentas Online**: BuiltWith e Whois para identificar tecnologias e domínios.  
- **Dirb**: Enumeração de diretórios.  
- **Nmap**: Descoberta de serviços e portas abertas.  

### Fase 2: Enumeração

Foi utilizada a ferramenta **Nmap** para mapear detalhes sobre sistemas operacionais, portas abertas e serviços em execução. Em seguida:  
- **SQLMap**: Identificação de bancos de dados e tabelas vulneráveis.  
- **DIRB**: Mapeamento de diretórios acessíveis.

### Fase 3: Exploração

O foco principal foi a exploração de vulnerabilidades de **SQL Injection**. As seguintes ferramentas foram utilizadas:  
- **SQLMap**: Automatizou os ataques de injeção SQL para extrair dados.  
- **XSSer** e **BEEF**: Realizaram testes de Cross-Site Scripting (XSS).  

---

## Conclusão

Os testes demonstram que vulnerabilidades simples, como **SQL Injection**, podem comprometer gravemente a integridade dos sistemas. Reforça-se a importância de práticas seguras de desenvolvimento, como:  
1. Uso de **consultas parametrizadas** para evitar injeções SQL.  
2. **Validação de entradas** no back-end e no front-end.  
3. Realização de **auditorias regulares** de segurança.  

---

## Referências

- **Livro:** Segurança em Aplicações Web - Conceitos Essenciais.  
- **OWASP:** [SQL Injection Prevention Cheat Sheet](https://owasp.org/www-project-cheat-sheets/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html).  
