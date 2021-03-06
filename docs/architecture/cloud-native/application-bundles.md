---
title: Pacotes de aplicativos nativos de nuvem
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Pacotes de aplicativos nativos de nuvem
ms.date: 06/30/2019
ms.openlocfilehash: 0c67035af08d3c337ff027f3742e1ce8a83f8d0f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183710"
---
# <a name="cloud-native-application-bundles"></a>Pacotes de aplicativos nativos de nuvem

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Uma importante propriedade dos aplicativos nativos de nuvem é que eles aproveitam as propriedades da nuvem para acelerar o desenvolvimento. Isso geralmente significa que um aplicativo completo usa diferentes tipos de tecnologias. Os aplicativos podem ser enviados em contêineres do Docker, alguns serviços podem usar Azure Functions enquanto outras partes podem ser executadas diretamente em máquinas virtuais alocadas em servidores de metal grandes com aceleração de GPU de hardware. Dois aplicativos nativos de nuvem são os mesmos, portanto, é difícil fornecer um único mecanismo para enviá-los.

Os contêineres do Docker podem ser executados em kubernetes usando um gráfico Helm para implantação. O Azure Functions pode ser alocado usando modelos Terraform. Por fim, as máquinas virtuais podem ser alocadas usando Terraform, mas são criadas usando Ansible. Essa é uma bagunça de tecnologias e não há como empacotá-las juntas em um pacote razoável. Até agora.

Os pacotes de aplicativos nativos de nuvem (CNABs) são um esforço conjunto de várias empresas que se envolvem com a Comunidade, como Microsoft, Docker e HashiCorp, para desenvolver uma especificação para empacotar aplicativos distribuídos.

O esforço foi anunciado em dezembro de 2018, portanto, ainda há um pouco de trabalho a ser feito para expor o esforço para a comunidade maior. No entanto, já existe uma [especificação aberta](https://github.com/deislabs/cnab-spec) e uma implementação de referência conhecida como [duffle](https://duffle.sh/). Essa ferramenta, que foi escrita em go, é um esforço conjunto entre o Docker e a Microsoft.

O CNABs pode conter diferentes tipos de tecnologias de instalação. Isso permite que itens como gráficos Helm, modelos de Terraform e guias estratégicos Ansible coexistam no mesmo pacote. Uma vez criados, os pacotes são independentes e portáteis; Eles podem ser instalados de um Pen stick.  Os pacotes são assinados criptograficamente para garantir que eles se originem da parte que afirma.

O núcleo de um CNAB é um arquivo chamado `bundle.json`. Esse arquivo define o conteúdo do pacote, seja Terraform ou imagens ou qualquer outra coisa. A Figura 11-9 define um CNAB que invoca alguns Terraform. Observe, no entanto, que ela realmente define uma imagem de invocação que é usada para invocar o Terraform. Quando empacotado, o arquivo do Docker localizado no diretório *CNAB* é incorporado a uma imagem do Docker, que será incluída no pacote. Ter o Terraform instalado dentro de um contêiner do Docker no grupo significa que os usuários não precisam ter o Terraform instalado em seu computador para executar o agrupamento.

```json
{
    "name": "terraform",
    "version": "0.1.0",
    "schemaVersion": "v1.0.0-WD",
    "parameters": {
        "backend": {
            "type": "boolean",
            "defaultValue": false,
            "destination": {
                "env": "TF_VAR_backend"
            }
        }
    },
    "invocationImages": [
        {
        "imageType": "docker",
        "image": "cnab/terraform:latest"
        }
    ],
    "credentials": {
        "tenant_id": {
            "env": "TF_VAR_tenant_id"
        },
        "client_id": {
            "env": "TF_VAR_client_id"
        },
        "client_secret": {
            "env": "TF_VAR_client_secret"
        },
        "subscription_id": {
            "env": "TF_VAR_subscription_id"
        },
        "ssh_authorized_key": {
            "env": "TF_VAR_ssh_authorized_key"
        }
    },
    "actions": {
        "status": {
            "modifies": true
        }
    }
}
```

**Figura 11-13** -um arquivo Terraform de exemplo

O `bundle.json` também define um conjunto de parâmetros que são passados para o Terraform. A parametrização do pacote permite a instalação em uma variedade de ambientes diferentes.

O formato CNAB também é flexível, permitindo que ele seja usado em qualquer nuvem. Ele pode até ser usado em soluções locais, como [OpenStack](https://www.openstack.org/).

## <a name="devops-decisions"></a>Decisões DevOpss

Há tantas ferramentas incríveis no DevOps de espaço em dia e até mesmo livros e artigos fantásticos sobre como obter sucesso. Um livro favorito para começar a usar o DevOps Journey é [o projeto Phoenix](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), que segue a transformação de uma empresa fictícia da NoOps para a DevOps. Uma coisa é para determinados: A DevOps não é mais uma "boa para ter" ao implantar aplicativos complexos de nuvem nativos. É um requisito e deve ser planejado e reoriginado no início de qualquer projeto.

>[!div class="step-by-step"]
>[Anterior](infrastructure-as-code.md)
