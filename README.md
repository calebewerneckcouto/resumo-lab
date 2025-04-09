# resumo-lab
# 🚀 Guia de Configuração Azure: Máquina Virtual e Banco de Dados SQL

Este guia descreve os passos essenciais para configurar uma infraestrutura básica no Microsoft Azure, incluindo a criação de uma Máquina Virtual com Windows Server e a instância de um Banco de Dados SQL.

---

## 🖥️ 1. Criando uma Máquina Virtual no Azure

### Etapas:

1. **Acessar o Portal Azure:**  
   https://portal.azure.com

2. **Ir para "Máquinas Virtuais" > "Criar" > "Máquina Virtual".**

3. **Configurações Básicas:**
   - **Assinatura:** Selecione sua assinatura.
   - **Grupo de Recursos:** Crie um novo ou selecione um existente.
   - **Nome da VM:** Ex: `vm-database-windows`.
   - **Região:** Escolha a região mais próxima.
   - **Imagem:** `Windows Server 2019 Datacenter`.
   - **Tamanho:** Selecione o tipo de VM (ex: `Standard B2s`).
   - **Usuário/Admin:** Defina nome de usuário e senha.

4. **Configurações de Disco:**
   - **Disco do SO:** SSD padrão ou premium (recomendado).
   - **Discos adicionais:** Adicione discos conforme necessidade.

5. **Rede:**
   - **Rede Virtual:** Criar nova ou usar existente.
   - **Subnet:** Selecionar ou criar.
   - **IP Público:** Se quiser acesso remoto, mantenha habilitado.
   - **Portas de entrada:** Habilitar RDP (porta 3389) para acesso remoto.

6. **Configuração de Acesso à Internet:**
   - ✅ Se deseja expor para a internet: manter IP público.
   - ❌ Se for uso interno apenas: desmarcar IP público e configurar regras de segurança restritivas.

7. **Revisar e Criar:**  
   - Clique em **"Revisar + Criar"**, e depois em **"Criar"**.

---

## 💽 2. Adicionar Discos à Máquina Virtual

1. Após a VM ser criada, vá até **"Discos"** na página da máquina virtual.
2. Clique em **"Adicionar disco de dados"**.
3. Escolha o tipo (SSD, HDD), tamanho e políticas de desempenho.
4. Salve e aguarde a VM ser atualizada com o novo disco.

---

## 🧠 3. Criando um Banco de Dados SQL no Azure

### Etapas:

1. Vá até **"Banco de Dados SQL" > "Criar"**.

2. **Informações básicas:**
   - **Assinatura / Grupo de Recursos:** Selecione conforme a VM.
   - **Nome do Banco de Dados:** Ex: `db-projeto`.
   - **Servidor:** Clique em **"Criar novo servidor"**.

3. **Criando um Novo Servidor SQL:**
   - Nome: `sqlserver-projeto`.
   - Login do administrador: ex: `adminsql`
   - Senha: definir senha segura.
   - Região: mesma da máquina virtual (para latência mínima).

4. **Camada de Computação:**
   - Escolher tamanho (recomendado: `Basic` ou `Standard` para testes).
   - Configurar armazenamento conforme necessidade.

5. **Configurações de Rede:**
   - Permitir acesso a partir de:
     - ✅ Serviços do Azure.
     - ✅ Meu IP atual (se deseja acessar externamente).
   - Pode optar por restringir completamente o acesso externo.

6. **Revisar + Criar:**  
   Verifique as informações e clique em **"Criar"**.

---

## 🔒 4. Configurar Firewall e Segurança do SQL Server

1. Após o banco ser criado, vá até **"Servidores SQL" > [nome do servidor]**.
2. Acesse **"Firewalls e redes virtuais"**.
3. Adicione endereços IP ou redes que podem acessar o banco.
4. Clique em **"Salvar"**.

---

## 📎 Considerações Finais

- 🔑 **Segurança:** Nunca exponha sua VM ou banco de dados diretamente à internet sem regras específicas de firewall.
- 📦 **Backups:** Configure backups automáticos no SQL Database.
- 🔄 **Escalabilidade:** Você pode escalar recursos da VM e do banco de forma separada conforme a carga.

---

## 📚 Referências Úteis

- [Documentação Azure - Máquinas Virtuais](https://learn.microsoft.com/pt-br/azure/virtual-machines/)
- [Documentação Azure - Banco de Dados SQL](https://learn.microsoft.com/pt-br/azure/azure-sql/database/)
