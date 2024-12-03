# Relatório Geral de Teste de Penetração - Vulnweb

**Matéria:** Ciber Segurança  
**Professor:** Fábio Oliveira  
**Aluno:** Marcos Paulo Roriz  
**RA:** 22007534  

---

## Escopo

O objetivo deste trabalho é analisar vulnerabilidades presentes em sites disponibilizados pelo **Vulnweb**, realizando uma abordagem de teste black-box. Ainda assim, os sites fornecem informações sobre as tecnologias e frameworks utilizados, o que auxilia no reconhecimento e exploração das falhas.

---

## Sites Avaliados

- **testhtml5**  
- **testphp**  
- **testasp**  
- **testaspnet**  
- **rest**  

Esses sites apresentam diferentes tecnologias e propõem cenários variados para análise de segurança.

---

## Fases de Avaliação

### 1. Reconhecimento (Recon)

Durante esta etapa, foram coletadas informações relevantes para mapear os sites e identificar possíveis entradas vulneráveis. As seguintes técnicas foram utilizadas:
- **Google Dorks**: Realizar buscas avançadas, por exemplo, `site:testphp.vulnweb.com +"Index of /admin"`.
- **Ferramentas Online**: Sites como BuiltWith e Whois para obter detalhes das tecnologias e domínios.
- **Ferramentas Automatizadas**: 
  - **dirb**: Para listar diretórios acessíveis.
  - **sqlmap**: Para detectar possíveis vulnerabilidades de SQL Injection.
  - **nmap**: Para descobrir portas abertas e serviços em execução.

### 2. Enumeração

A enumeração foi conduzida para identificar mais detalhes sobre os sistemas. As ferramentas utilizadas foram:
- **Nmap**: Para detectar portas abertas, serviços, e sistemas operacionais.
- **SQLMap**: Para listar bancos de dados, tabelas e outras informações dos SGBDs.
- **DIRB**: Para mapear diretórios expostos.

### 3. Exploração

A exploração focou em vulnerabilidades como **SQL Injection** e **Cross-Site Scripting (XSS)**. Ferramentas utilizadas:
- **SQLMap**: Realizou injeções SQL para extrair informações sensíveis.
- **XSSer** e **BEEF**: Foram usados para explorar cenários de XSS.

### 4. Relatório

Este documento sintetiza todas as etapas realizadas, apresentando metodologias, ferramentas utilizadas, e recomendações com exemplos de códigos seguros.

---

## Relatórios Individuais

Para acessar os detalhes de cada site avaliado, clique nos links abaixo:

- [Relatório: SecurityTweets](Relatorio_SecurityTweets_Vulnweb.md)  
- [Relatório: Acuart](Relatorio_Acuart_Vulnweb.md)  
- [Relatório: Acublog](Relatorio_Acublog_Vulnweb.md)  

---

## Conclusão

Com base nos testes realizados, foi possível identificar como vulnerabilidades simples, como **SQL Injection**, podem comprometer dados críticos de sistemas. A exploração de falhas como **XSS** destacou os riscos de ataques que manipulam o comportamento de navegadores.

### Recomendações:

1. **Validação e Sanitização de Entradas**: Todas as entradas devem ser verificadas para evitar dados maliciosos.
2. **Consultas Parametrizadas**: Uso de consultas seguras para prevenir SQL Injection.
3. **Auditorias de Segurança**: Realizar revisões periódicas para mitigar novas ameaças.

Exemplo de código seguro em Node.js:

```javascript
// Com biblioteca:
const buscarUsuarioPorEmail = async (email) => {
    return await knex('usuarios').where({ email }).first();
};

// Sem biblioteca:
const cadastrarUsuario = async (req, res) => {
    const { nome, email, senha } = req.body;
    const senhaCriptografada = hash(senha);
    await pool.query('INSERT INTO usuarios (nome, email, senha) VALUES ($1, $2, $3)', [nome, email, senhaCriptografada]);
};
```

---

## Referências

- **Livro**: Segurança em Aplicações Web - Conceitos Essenciais  
- **OWASP**: [Cheat Sheet de SQL Injection](https://owasp.org/www-project-cheat-sheets/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html).  

