## 🔐 Atividade 2 - Segurança e acessos

Nesta etapa, implementamos controles de acesso baseados em perfil, utilizando Roles, Groups e ACLs na aplicação **Social Media Management**.

## 1 - Criação de Roles

Foram criadas duas roles customizadas para a aplicação: `social_manager` e `social_analyst`:  

<img width="1083" height="223" alt="image" src="https://github.com/user-attachments/assets/e44083b3-1172-4495-a361-d7a0a3c37748" />
<img width="470" height="237" alt="image" src="https://github.com/user-attachments/assets/296e9e4d-1869-4174-a14e-04c5b5a193b0" /> e <img width="472" height="238" alt="image" src="https://github.com/user-attachments/assets/0ecc37b8-db14-46e3-bea3-cb9a775556c6" />

## 2 - Criação de Grupos e Associação de Roles

Foram criados dois grupos `Social Media - Gestores` e `Social Media - Analistas`:  
<img width="1432" height="176" alt="image" src="https://github.com/user-attachments/assets/4d9f7531-a261-4df4-866e-c807ab74ade3" />

Atribuímos ao grupo **Social Media - Gestores** a role `social_manager` e adicionamos alguns usuários:  
<img width="1422" height="527" alt="image" src="https://github.com/user-attachments/assets/9b96bd9f-a8d8-4259-82b1-d969fe637e20" />   

E, atribuímos ao grupo **Social Media - Analistas** a role `social_analyst` e adicionamos alguns usuários:  
<img width="1422" height="524" alt="image" src="https://github.com/user-attachments/assets/99dab51d-4e67-45ae-aa9d-20f8d5e06ea5" />

## 3 - Configuração de Permissões (CRUD)

O controle de acesso (CRUD) foi configurado conforme a matriz definida no desafio.  

<img width="547" height="238" alt="image" src="https://github.com/user-attachments/assets/9c82c937-bf1a-412f-9801-6fee74da777e" />  

- **Manager**: Usuários com permissão total para visualizar, criar e atualizar canais e posts.  
<img width="788" height="602" alt="image" src="https://github.com/user-attachments/assets/03ddeefc-093a-419c-8a5e-c7a964e2f22e" />

- **Analyst**: Usuários com permissão para apenas para visualizar canais, e criar e atualizar posts.  
<img width="789" height="606" alt="image" src="https://github.com/user-attachments/assets/1bd687db-c15e-4a65-b1fe-4fe1897cabc4" />  

#### **Em System Security - Access Control**, foram incluídas as roles de acordo com a exigência de cada operação:  

**Na tabela Channel:**  
<img width="1407" height="405" alt="image" src="https://github.com/user-attachments/assets/17190ad0-23bc-4832-8845-b9c32e117bac" />

**Na tabela Post:**  
<img width="1401" height="348" alt="image" src="https://github.com/user-attachments/assets/e75365e9-c549-4032-872f-e413dad084a4" />

### ⚠️ **Observação importante:**  
Como a tabela **Post** estende a tabela **Task**, algumas restrições de acesso podem ocorrer devido às ACLs herdadas da tabela pai.  
> Os campos **work notes** e **additional comments** são herdados da tabela **TASK**!  

Por esse motivo, foi necessário criar ou ajustar ACLs na tabela **Post** para permitir a manipulação / autorização de escrita dos seguintes campos:  
`Short description`, `Work notes - (read & write)` e `Additional comments`  

<img width="1430" height="399" alt="image" src="https://github.com/user-attachments/assets/cae55cc1-9f16-4a1b-9c68-a2cbc117a355" />

Em **System Security / Access Control (ACL)** - com **Elevate role**, clica em **New**.
- Exemplo: `Short description - (write)`
<img width="1415" height="461" alt="image" src="https://github.com/user-attachments/assets/0cfcd001-e9f7-4d7a-b872-c976a1b70bb1" />

Fazer o mesmo com os outros campos.

E logo abaixo, incluimos as Roles:
<img width="1102" height="336" alt="image" src="https://github.com/user-attachments/assets/5d9e39e3-09fb-491c-86f8-caa20a44866e" />

🎉 **Resultado**
<img width="1440" height="784" alt="image" src="https://github.com/user-attachments/assets/fe785a31-44f6-4d97-a465-f14ed77a8c30" />

## 4 - Restrição de Acesso ao Application Menu e Modules

Em **System Definition/ Application Menus** definimos as permissões que foram refletidas na navegação da aplicação, garantindo que:
- Apenas usuários autorizados visualizem os módulos correspondentes.
- O acesso ao menu respeite as roles atribuídas.
<img width="1423" height="604" alt="image" src="https://github.com/user-attachments/assets/d4de02ad-89f7-4228-9318-c66b2ab90868" />

Assim, ao impersonarmos um **manager**, vemos que tem acesso ao CRUD completo conforme solicitado na atividade:  
<img width="304" height="287" alt="image" src="https://github.com/user-attachments/assets/4a67a6cb-7a99-4281-a82c-4ae415a13b37" />

E, ao impersonarmos um **analista**, vemos que tem acesso a quase tudo: ele pode criar e listar posts, pode listar Channel, porém, não pode criar um Channel.  
<img width="314" height="260" alt="image" src="https://github.com/user-attachments/assets/8903a961-fb95-48b2-9048-57b8b73c9a9f" />

## ⚠️ Boas Práticas Aplicadas

- Remoção de roles desnecessárias criadas anteriormente.
- Evitar excesso de ACLs sem necessidade.
- Manutenção de uma estrutura de segurança limpa e organizada.

A segurança foi configurada de forma enxuta, respeitando o "princípio do menor privilégio".

---

👉🏻 [Clique aqui para voltar ao Readme](https://github.com/DrikaDev/Social-Media-Management/blob/main/README.md)📒
