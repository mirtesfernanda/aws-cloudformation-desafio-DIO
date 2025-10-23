# 🏗️ Implementando sua Primeira Stack com AWS CloudFormation

## 📘 Descrição do Projeto
Este projeto faz parte do laboratório da **DIO (Digital Innovation One)**, no qual foi implementada a **primeira stack utilizando o AWS CloudFormation**.  
O objetivo foi aprender a **automatizar a criação de recursos na nuvem** (infraestrutura como código) e documentar todo o processo.

## 🎯 Objetivos de Aprendizagem
- Aplicar conceitos de **Infraestrutura como Código (IaC)** com CloudFormation;  
- Criar e gerenciar **stacks** na AWS de forma prática;  
- Compreender a estrutura de um **template YAML/JSON** no CloudFormation;  
- Utilizar o **GitHub** como ferramenta de versionamento e documentação técnica.

## ⚙️ Tecnologias Utilizadas
- **AWS CloudFormation**
- **AWS Management Console**
- **Git & GitHub**
- **Markdown (.md)**
- **YAML**

## 🧱 Estrutura do Projeto

```
📁 aws-cloudformation-desafio
│
├── 📄 README.md                  → Documentação detalhada
├── 📁 templates/                 → Templates YAML/JSON criados
│   └── vpc-template.yaml         → Exemplo de Stack VPC
│
├── 📁 images/                    → Prints de tela da AWS e resultados
│   ├── stack-created.png
│   ├── stack-details.png
│   └── cloudformation-dashboard.png
│
└── 📄 .gitignore
```

## 🚀 Etapas Realizadas

### 1. Criação da Stack
No **AWS CloudFormation**, foi criado um **template YAML** básico para provisionar uma **VPC**, **sub-rede** e **security group**.

**Exemplo de template (`vpc-template.yaml`):**
```yaml
AWSTemplateFormatVersion: "2010-09-09"
Description: "Primeira Stack - Exemplo de VPC com Subnet e Security Group"

Resources:
  MyVPC:
    Type: AWS::EC2::VPC
    Properties:
      CidrBlock: 10.0.0.0/16
      EnableDnsSupport: true
      EnableDnsHostnames: true
      Tags:
        - Key: Name
          Value: MinhaPrimeiraVPC

  MySubnet:
    Type: AWS::EC2::Subnet
    Properties:
      VpcId: !Ref MyVPC
      CidrBlock: 10.0.1.0/24
      MapPublicIpOnLaunch: true
      Tags:
        - Key: Name
          Value: MinhaSubnetPublica

  MySecurityGroup:
    Type: AWS::EC2::SecurityGroup
    Properties:
      GroupDescription: "Acesso SSH e HTTP liberado"
      VpcId: !Ref MyVPC
      SecurityGroupIngress:
        - IpProtocol: tcp
          FromPort: 22
          ToPort: 22
          CidrIp: 0.0.0.0/0
        - IpProtocol: tcp
          FromPort: 80
          ToPort: 80
          CidrIp: 0.0.0.0/0
      Tags:
        - Key: Name
          Value: MeuSecurityGroup
```

### 2. Deploy da Stack
A stack foi criada diretamente pelo console da AWS:

1. Acesse o serviço **CloudFormation**.  
2. Clique em **Create Stack > With new resources (standard)**.  
3. Faça upload do arquivo `vpc-template.yaml`.  
4. Clique em **Next** até chegar em **Submit**.  
5. Aguarde o status **CREATE_COMPLETE**.

📸 *Print sugerido:* inclua no repositório uma imagem da sua stack criada (ex: `images/stack-created.png`).

### 3. Verificação dos Recursos
Após a criação, acesse o **EC2 Dashboard** → **VPCs** → **Subnets** → **Security Groups**  
Verifique se os recursos foram provisionados corretamente.

📸 *Print sugerido:* `images/vpc-details.png`

### 4. Documentação e Versionamento
O projeto foi versionado no GitHub, com commits mostrando cada etapa:
```bash
git init
git add .
git commit -m "Primeiro commit - criação do template CloudFormation"
git remote add origin https://github.com/SEU-USUARIO/aws-cloudformation-desafio.git
git push -u origin main
```

## 🧠 Insights Adquiridos
Durante o desenvolvimento, aprendi:
- A importância de **IaC (Infrastructure as Code)** para replicar ambientes rapidamente;
- Como o CloudFormation facilita o **controle de mudanças e auditoria** da infraestrutura;
- A diferença entre **Stack**, **Template** e **Resources** na AWS;
- Como integrar o **GitHub** para documentação e versionamento técnico.

## 🏁 Conclusão
Este desafio proporcionou uma experiência prática com **Infraestrutura como Código**, reforçando o entendimento sobre **automação, boas práticas e versionamento de ambientes AWS**.  
O uso do **GitHub** para documentação técnica foi essencial para consolidar o aprendizado e compartilhar conhecimento.

## 📎 Referências
- [Documentação AWS CloudFormation](https://docs.aws.amazon.com/cloudformation/)
- [Guia de Markdown do GitHub](https://docs.github.com/pt/get-started/writing-on-github)
- [GitHub Quick Start - DIO](https://github.com/digitalinnovationone)
