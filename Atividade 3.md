## 🔄 Atividade 3 – Flow Designer

Nesta atividade, construímos um fluxo no **Flow Designer** com o objetivo de automatizar as etapas de publicação, as mudanças de estado do Post, 
atualizar informações relacionadas ao Channel, além de disparar notificações quando necessário.  

<img width="1080" height="161" alt="image" src="https://github.com/user-attachments/assets/a9393ec9-6aec-4c93-9fb3-e2b1b25d23e4" />

## Início do Flow

O fluxo é iniciado quando o Post é criado pelo usuário, gerando um **Trigger** do tipo **Created** na tabela **Post**
<img width="1073" height="429" alt="image" src="https://github.com/user-attachments/assets/c3cb707c-5e90-4d26-932f-58bea642b72c" />

## 1 Action
- Quando o campo **Publication date** da tabela Post for preenchido
<img width="1044" height="366" alt="image" src="https://github.com/user-attachments/assets/0c1614d6-e5eb-4ff2-8e8a-eb03a86b58d4" />

## 2 Action
- O campo **State** é atualizado para **Published**
<img width="1029" height="333" alt="image" src="https://github.com/user-attachments/assets/b0902a4c-9a99-4e32-b89c-cad8ba197357" />

## 3 Action
- O campo **Number of Posts** da tabela **Channel** (registro referenciado no campo `Channel`) é incrementado em +1
<img width="1039" height="330" alt="image" src="https://github.com/user-attachments/assets/e1e89247-8abf-4568-a870-4a4dacf0319b" />
> Para realizar o incremento foi utilizado:
> - Função **FX → Add**, ou
> - Script utilizando o objeto `fd_data`.

### 4 Action
- Quando o campo **Total of Clicks** for preenchido
<img width="1027" height="363" alt="image" src="https://github.com/user-attachments/assets/33e13aaf-7303-45bf-bd2b-d5d8e6f8433a" />

### 5 Action
- O campo **State** é atualizado para **Follow-up**
<img width="1038" height="335" alt="image" src="https://github.com/user-attachments/assets/3a7cac3b-7267-41b0-aefa-69a7d3576c3f" />

### 6 Action
- Se, o valor for **menor que 500**
<img width="1033" height="154" alt="image" src="https://github.com/user-attachments/assets/0a242f69-e22a-4efe-9523-2ec325393d79" />

### 7 Then
- Então, um **E-mail** é enviado para o grupo **Social Media - Gestores**
<img width="1039" height="325" alt="image" src="https://github.com/user-attachments/assets/54f32fe5-70f5-4be1-83e4-28f86ee7680d" />

### 8 Send email
- O disparo do e-mail pode ser validado em **System Logs → Emails**
<img width="1046" height="366" alt="image" src="https://github.com/user-attachments/assets/d6070eec-87c2-48b3-b354-150934696a29" />
<img width="966" height="315" alt="image" src="https://github.com/user-attachments/assets/5a958038-acbc-48dc-b4fd-82e4c3acba41" />
<img width="1039" height="228" alt="image" src="https://github.com/user-attachments/assets/f80ba89b-a079-45e0-91fc-e7cf23d732c1" />

### 👉🏼 Gestor recebe o email com a confirmação dos cliques inferior a -500, e encerra o Follow-up.
<img width="1435" height="148" alt="image" src="https://github.com/user-attachments/assets/ee8bbe81-fe15-4f69-817c-0d10c9509f39" />

### 9 Action
- Quando o gestor clicar no campo **End follow-up**, ele será recebido como **true** no flow
<img width="1030" height="367" alt="image" src="https://github.com/user-attachments/assets/19e85a49-6a60-4051-bc5a-7d68c2231fd7" />

### 10 Action
- O campo **State** é atualizado para **Closed**
<img width="1030" height="335" alt="image" src="https://github.com/user-attachments/assets/23cf26fd-c182-40c4-b7b4-cd290a0bcb1d" />

### 🏁 Fim do fluxo!

## ⚙️ Configuração Importante

O fluxo foi configurado para executar como **Run As: System User**  
Essa configuração evita problemas de permissão durante a execução do fluxo.  

## 🧠 Boas Práticas Aplicadas
- Automação baseada em eventos de negócio.
- Atualização de registros relacionados.
- Validação de regras condicionais.
- Execução com privilégios adequados para evitar falhas de acesso.

---

👉🏻 [Clique aqui para voltar ao Readme](https://github.com/DrikaDev/Social-Media-Management/blob/main/README.md)📒
