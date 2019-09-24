---
ms.openlocfilehash: b965c3a975b0f2cadd906799fef1665261d96d6e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182014"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="fb77f-101">EnvelopedCms usa como padrão a criptografia AES-256</span><span class="sxs-lookup"><span data-stu-id="fb77f-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="fb77f-102">O algoritmo de criptografia simétrica padrão usado `EnvelopedCms` pelo foi alterado de TripleDES para AES-256.</span><span class="sxs-lookup"><span data-stu-id="fb77f-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="details"></a><span data-ttu-id="fb77f-103">Detalhes</span><span class="sxs-lookup"><span data-stu-id="fb77f-103">Details</span></span>

<span data-ttu-id="fb77f-104">No .NET Core Preview 7 e em versões anteriores, <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> quando é usado para criptografar dados sem especificar um algoritmo de criptografia simétrica por meio de uma sobrecarga de construtor, os dados foram criptografados com o algoritmo TripleDES/3DES/3DEA/DES3-Ede.</span><span class="sxs-lookup"><span data-stu-id="fb77f-104">In .NET Core Preview 7 and earlier versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data was encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="fb77f-105">A partir do .NET Core 3,0 Preview 8 (por meio da versão 4.6.0 do pacote NuGet [System. Security. Cryptography. Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) ), o algoritmo padrão foi alterado para AES-256 para modernização do algoritmo e para melhorar a segurança das opções padrão.</span><span class="sxs-lookup"><span data-stu-id="fb77f-105">Starting with .NET Core 3.0 Preview 8 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="fb77f-106">Se um certificado de destinatário de mensagem tiver uma chave pública Diffie-Hellman (não-EC), a operação de criptografia poderá <xref:System.Security.Cryptography.CryptographicException> falhar com um devido a limitações na plataforma subjacente.</span><span class="sxs-lookup"><span data-stu-id="fb77f-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="fb77f-107">No código de exemplo a seguir, os dados são criptografados com TripleDES se executados no .NET Core 3,0 Preview 7 ou anterior.</span><span class="sxs-lookup"><span data-stu-id="fb77f-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 3.0 Preview 7 or earlier.</span></span> <span data-ttu-id="fb77f-108">Se estiver executando no .NET Core 3,0 Preview 8 ou posterior, ele será criptografado com AES-256.</span><span class="sxs-lookup"><span data-stu-id="fb77f-108">If running on .NET Core 3.0 Preview 8 or later, it is encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="fb77f-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="fb77f-109">Version introduced</span></span>

<span data-ttu-id="fb77f-110">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="fb77f-110">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fb77f-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="fb77f-111">Recommended action</span></span>

<span data-ttu-id="fb77f-112">Se você for afetado negativamente pela alteração, poderá restaurar a criptografia TripleDES especificando explicitamente o identificador do algoritmo de criptografia em um <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> Construtor que inclua um parâmetro do tipo <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, como:</span><span class="sxs-lookup"><span data-stu-id="fb77f-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="fb77f-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="fb77f-113">Category</span></span>

<span data-ttu-id="fb77f-114">Criptografia</span><span class="sxs-lookup"><span data-stu-id="fb77f-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fb77f-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fb77f-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->