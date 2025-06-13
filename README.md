# Desafio - Criação de Máquina Virtual no Microsoft Azure

Este repositório documenta o desafio proposto no bootcamp "Microsoft 50 Anos - Computação em Nuvem com Azure", com o objetivo de consolidar os conhecimentos práticos sobre máquinas virtuais na plataforma Azure.

## Objetivo

O desafio consiste em criar uma máquina virtual (VM) utilizando o portal da Azure, configurando todos os aspectos relacionados a sistema operacional, autenticação, rede e segurança. O processo também envolve entender como funcionam as opções de disponibilidade e os Acordos de Nível de Serviço (SLA).

## Etapas Realizadas

### 1. Criação do Grupo de Recursos (Resource Group)

No portal da Azure, foi criado um grupo de recursos chamado `rg-bootcamp-geo`. O grupo de recursos serve para organizar e gerenciar todos os serviços utilizados no projeto de forma centralizada.

### 2. Escolha da Imagem do Sistema Operacional

Foi selecionada a imagem "Ubuntu Server 22.04 LTS - x64 Gen2", por ser uma distribuição estável, amplamente utilizada no mercado e compatível com operações via terminal (SSH).

### 3. Seleção da Região

A região escolhida foi "Brazil South". A seleção da região impacta diretamente na latência, disponibilidade e no custo da máquina virtual. Regiões mais próximas do usuário tendem a oferecer melhor desempenho.

### 4. Tamanho da Máquina Virtual

O tamanho selecionado foi `Standard_B1s`, que possui 1 vCPU e 1 GiB de memória RAM. Este tamanho está incluso no plano gratuito da Azure for Students e é ideal para testes e ambientes de laboratório.

### 5. Opções de Disponibilidade

Para este laboratório, foi escolhida a opção "Nenhuma redundância de infraestrutura necessária". 

Entendendo as opções:

- **Nenhuma**: a VM é criada em uma infraestrutura padrão. Se houver falha de hardware, pode haver interrupção temporária.
- **Zonas de disponibilidade**: permitem distribuir os recursos entre zonas físicas separadas dentro da mesma região. Indicadas para sistemas que exigem alta disponibilidade.
- **Conjuntos de disponibilidade (Availability Sets)**: ajudam a garantir que várias VMs não fiquem indisponíveis ao mesmo tempo, usando separação lógica.

### 6. Acordo de Nível de Serviço (SLA)

O SLA (Service Level Agreement) da Azure garante uma taxa de disponibilidade para seus serviços. Por exemplo:

- VMs isoladas sem opções de disponibilidade adicionais possuem SLA inferior (por volta de 95% a 99.5%).
- Quando associadas a zonas de disponibilidade ou conjuntos de disponibilidade, o SLA pode alcançar 99.9% ou superior.

Como a opção de disponibilidade neste caso foi "Nenhuma", não é garantido o mesmo nível de continuidade do serviço em caso de falha de hardware.

### 7. Autenticação por Chave SSH

Foi gerado um novo par de chaves SSH para garantir um acesso seguro à máquina virtual. A chave privada foi baixada e armazenada localmente para uso futuro via terminal.

### 8. Configuração de Rede

Foi configurada a liberação da porta 22 (SSH), permitindo a conexão remota à VM por meio de um terminal.

### 9. Disco de Sistema Operacional

O disco selecionado foi do tipo SSD Premium com 30 GiB de espaço. A opção "Excluir com a VM" foi marcada para evitar cobrança futura quando a VM for excluída.

### 10. Acesso via Terminal

Após a criação da VM, foi possível acessar a máquina utilizando o seguinte comando:

```bash
ssh bootcampgeo@<IP_PUBLICO_DA_VM>
