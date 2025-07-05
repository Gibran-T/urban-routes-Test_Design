
# Urban Routes – Sprint 2: Test Design

Este projeto faz parte do ciclo de testes de regressão do sistema Urban Routes, com foco na **Sprint 2 – Design de Teste Manual** para o formulário de **“Adicionar carteira de motorista”**.

## 🎯 Objetivo
Verificar os critérios de validação e comportamento do campo **Nome**, com base em:
- Classes de equivalência
- Valores-limite
- Caracteres aceitos e rejeitados
- Mensagens de erro e aceitação

---

## 🧪 Classes de Equivalência e Valores Limite

### Campo: Nome / Sobrenome

| Grupo de Verificação     | Nome da Classe                | Limites | Exemplo Válido       | Exemplo de Limite        |
|--------------------------|-------------------------------|---------|------------------------|---------------------------|
| Tamanho válido           | 2 a 14 caracteres              | 7       | Thiagoo               | 2 - Th / 14 - Thiagooooooooo |
| Tamanho inválido maior   | > 14 caracteres                | 15+     | Thiagooooooooooooo    | 15 - Thiagoooooooooo       |
| Tamanho inválido menor   | < 2 caracteres                 | 1       | T                     | Campo vazio / 1 - T        |
| Letras latinas           | A-Z, a-z                      | -       | Deltaalpha            | -                         |
| Letras não latinas       | Não A-Z/a-z                   | -       | 蒂亚戈·纪伯伦             | -                         |
| Espaço no início         | _Nome                         | -       | _Thiagogibran         | -                         |
| Espaço no meio           | Nome_Sobrenome                | -       | Thiago Gibran         | -                         |
| Espaço no fim            | Nome_                         | -       | Thiagogibran_         | -                         |
| Com hífen                | Nome-com-hifen                | -       | Thi-ago               | -                         |
| Campo vazio              | []                            | -       | (sem valor)           | -                         |
| Caracteres especiais     | @, %, $                       | -       | Thi@$%                | -                         |
| Números                  | 123456                        | -       | 1234567               | -                         |

---

### Campo: Data de Nascimento

| Verificação | Limites válidos      | Exemplos válidos       | Exemplos inválidos         |
|-------------|-----------------------|-------------------------|----------------------------|
| Dia         | 01–31                 | 16.06.1990, 28.02.2000  | 00.06.1990, 32.06.1990     |
| Mês         | 01–12                 | 16.01.1990              | 16.00.1990, 16.13.1990     |
| Ano         | 1880–2006             | 16.06.1985              | 16.06.1879, 16.06.2007     |
| Caracteres inválidos | -           | 01.12.2000              | @@.$$, tt.nn.abdc          |

---

## ✅ Casos de Teste

Cada caso segue a estrutura:  
**Pré-condição**: Formulário de adicionar carteira aberto  
**Passos**: Preenchimento do campo e perda de foco  
**Resultado esperado**: Aceitação ou mensagem de erro

| ID     | Nome do Teste                                                           | Valor Testado                | Esperado                                  |
|--------|-------------------------------------------------------------------------|------------------------------|--------------------------------------------|
| t-1    | Aceita nome com 2 caracteres                                            | "Th"                         | Aceita sem erro                            |
| t-2    | Rejeita nome com 1 caractere                                            | "T"                          | Erro: “Inserir o Nome correto”             |
| t-3    | Rejeita nome com mais de 14 caracteres                                  | "Thiagooooooooooooo"         | Erro: “O nome é muito longo”               |
| t-4    | Aceita apenas letras latinas                                            | "Deltaalpha"                 | Aceita sem erro                            |
| t-5    | Rejeita letras não latinas                                              | "蒂亚戈·纪伯伦"              | Exibe mensagem de erro                     |
| t-6    | Rejeita espaço no início                                                | "_Thiagogibran"              | Exibe mensagem de erro                     |
| t-7    | Aceita espaço no meio                                                   | "Thiago Gibran"              | Aceita sem erro                            |
| t-8    | Rejeita espaço no final                                                 | "Thiagogibran_"              | Exibe mensagem de erro                     |
| t-9    | Aceita nomes com hífen                                                  | "Thi-ago"                    | Aceita sem erro                            |
| t-10   | Rejeita campo vazio                                                     | ""                           | Erro: “O campo Nome é obrigatório”         |
| t-11   | Rejeita caracteres especiais                                            | "Thi@$%"                     | Exibe mensagem de erro                     |
| t-12   | Rejeita números                                                         | "1234567"                    | Exibe mensagem de erro                     |

---

## 📌 Observações

- Os testes foram realizados manualmente com base nos requisitos funcionais do formulário Urban Routes.
- Cada teste visa cobrir uma classe de equivalência distinta, com pelo menos um valor limite por grupo.
- Testes podem ser adaptados para **automação futura com Pytest + Selenium**.

---

## 🧠 Autor

**Thiago Gibran**  
QA Engineer | ERP & Logistics | [GitHub/Gibran-T](https://github.com/Gibran-T)
