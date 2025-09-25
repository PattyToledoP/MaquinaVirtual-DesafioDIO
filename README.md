# MaquinaVirtual-DesafioDIO
Criar uma máquina virtual do Windows no Portal do Azure - Desafio DIO

**Criando a VM pelo Azure Portal — passo a passo detalhado**

**1  - Passo: Login e abrir a tela de criação**\
Acesse o Portal e, na barra de busca no topo, digite "Virtual machines" 
→ clique em Virtual machines → Create → Virtual machine.\
Aba: Basics (Projeto / Instância) — preencha:\
→ Subscription: escolha a subscrição correta.\
→ Resource group: crie novo (windows-teste) ou escolha um existente.\
→ Virtual machine name: ex.: vm-windows-01.\
→ Region: ex.: South Brasil (sua preferência).\
→ Availability options: deixe No infrastructure redundancy required para testes; escolha Availability Zone/Set para produção.
→ Image: selecione uma imagem Windows (ex.: Windows Server 2022 Datacenter).
→ Size (tamanho): escolha conforme necessidade ex: Standard_D2s_v3. (Se estiver em dúvida, o portal oferece o botão Change size com recomendações).
→ Administrator account: coloque um nome de usuário (ex.: winadmin) e uma senha forte (entre 12 e 123 caracteres com complexidade maiúscula, minúscula, número, caractere especial). 
→ Inbound ports: selecione RDP (3389) se quiser acessar via Remote Desktop (por padrão o assistente costuma abrir RDP para Windows; lembre-se de restringir acesso depois)

**Aba: Disks**\
OS disk type: para teste o mais barato absoluto, Standard HDD; Standard SSD é um bom equilíbrio e se precisar de desempenho, escolha Premium SSD.\
Se quiser criptografia adicional, há opções (Azure Disk Encryption), mas é opcional para ambientes de teste.\

**Aba: Networking**\
O portal cria VNet, subnet, NIC, NSG e (opcional) Public IP automaticamente.\
Importante de segurança: se não precisa de acesso via Internet direto, não crie Public IP; ou, se criar, restrinja regras do NSG para permitir RDP apenas do seu IP. Alternativa mais segura: usar Azure Bastion (conexão RDP/SSH via portal sem IP público).\

**Aba: Management**\
Habilite Boot diagnostics (útil pra troubleshooting).\
Auto-shutdown: ative aqui para desligar automaticamente em horário que você escolher — ótima prática para economizar.\

**Aba: Advanced / Tags**\
→ revise conforme necessidade (não obrigatório para teste).\

**Review + Create**\
O Portal vai validar. Se tudo OK, clique Create. A implantação leva alguns minutos\
