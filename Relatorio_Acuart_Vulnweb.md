# Relatório: Acuart


### **Informações do Site**

- **URL:** [http://testphp.vulnweb.com](http://testphp.vulnweb.com)  
- **Tecnologias:** Apache, PHP, MySQL

---

### **Vulnerabilidade Identificada**

> **SQL Injection encontrado no parâmetro artist.**  

---

### **Etapas do Teste**

#### **1. Reconhecimento**

Inicialmente, realizamos o mapeamento dos endpoints disponíveis no site utilizando ferramentas como o **Nmap** para identificar serviços e tecnologias.  

#### **2. Teste Manual**

Durante o teste manual, aplicamos o seguinte payload:

```sql
' UNION SELECT null, version(), user()
```

O objetivo era avaliar se o sistema validava ou sanitizava as entradas do usuário. O resultado demonstrou que a aplicação estava vulnerável.

#### **3. Teste Automatizado**

Para explorar mais profundamente a vulnerabilidade, utilizamos o **SQLMap** com o seguinte comando:

```bash
sqlmap -u "http://testphp.vulnweb.com/artists.php?artist=1" --dbs
```

Esse comando automatizou a exploração e retornou informações detalhadas sobre o banco de dados da aplicação.

---

### **Resultados Obtidos**

- **Impacto:** A vulnerabilidade permite acesso não autorizado ao banco de dados.  
- **Dados Expostos:** Estruturas do banco de dados, versões do sistema e outros dados sensíveis.  

---

### **Recomendações**

Para corrigir as vulnerabilidades identificadas, recomendamos as seguintes ações:  
1. Implementar consultas parametrizadas (*Prepared Statements*).  
2. Validar e sanitizar todas as entradas do usuário, tanto no front-end quanto no back-end.  
3. Configurar firewalls de aplicação web (**WAF**) para monitorar e bloquear ataques automatizados.  
4. Realizar auditorias regulares de segurança para identificar e corrigir novas vulnerabilidades.

---

## Relatório: Acublog

### **Informações do Site**

- **URL:** [http://testaspnet.vulnweb.com](http://testaspnet.vulnweb.com)  
- **Tecnologias:** IIS, ASP.NET, Microsoft SQL Server

---

### **Vulnerabilidade Identificada**

> **Sistema de login vulnerável a SQL Injection.**  

---

### **Etapas do Teste**

#### **1. Reconhecimento**

Inicialmente, realizamos o mapeamento dos endpoints disponíveis no site utilizando ferramentas como o **Nmap** para identificar serviços e tecnologias.  

#### **2. Teste Manual**

Durante o teste manual, aplicamos o seguinte payload:

```sql
' OR '1'='1
```

O objetivo era avaliar se o sistema validava ou sanitizava as entradas do usuário. O resultado demonstrou que a aplicação estava vulnerável.

#### **3. Teste Automatizado**

Para explorar mais profundamente a vulnerabilidade, utilizamos o **SQLMap** com o seguinte comando:

```bash
sqlmap -u "http://testaspnet.vulnweb.com/login" --data="username=admin&password=test" --dbs
```

Esse comando automatizou a exploração e retornou informações detalhadas sobre o banco de dados da aplicação.

---

### **Resultados Obtidos**

- **Impacto:** A vulnerabilidade permite acesso não autorizado ao banco de dados.  
- **Dados Expostos:** Estruturas do banco de dados, versões do sistema e outros dados sensíveis.  

---

### **Recomendações**

Para corrigir as vulnerabilidades identificadas, recomendamos as seguintes ações:  
1. Implementar consultas parametrizadas (*Prepared Statements*).  
2. Validar e sanitizar todas as entradas do usuário, tanto no front-end quanto no back-end.  
3. Configurar firewalls de aplicação web (**WAF**) para monitorar e bloquear ataques automatizados.  
4. Realizar auditorias regulares de segurança para identificar e corrigir novas vulnerabilidades.

---

