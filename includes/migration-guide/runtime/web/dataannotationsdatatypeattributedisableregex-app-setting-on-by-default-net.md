---
ms.openlocfilehash: 94c582d25ae1cd2249ed2e3774134a86cf77327b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73085533"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>A configuração de aplicativo "dataAnnotations:dataTypeAttribute:disableRegEx" é habilitada por padrão no .NET Framework 4.7.2

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6.1, foi introduzida uma configuração de aplicativo (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) que permite que os usuários desabilitem o uso de expressões regulares em atributos de tipo de dados (como <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> e <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>). Isso ajuda a reduzir vulnerabilidades de segurança, por exemplo, impedindo que um ataque de negação de serviço use expressões regulares específicas.<br/>No .NET Framework 4.6.1, essa configuração de aplicativo para desabilitar o uso de expressões regulares era definida como <code>false</code> por padrão. Começando com o .NET Framework 4.7.2, <code>true</code> este switch de configuração é definido por padrão para reduzir ainda mais a vulnerabilidade segura para aplicativos web que visam o .NET Framework 4.7.2 ou superior.|
|Sugestão|Se observar que as expressões regulares em seu aplicativo Web não funcionam após atualizar para o .NET Framework 4.7.2, você poderá atualizar o valor da <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> configuração <code>false</code> para voltar ao comportamento anterior.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Secundária|
|Versão|4.7.2|
|Type|Runtime|
