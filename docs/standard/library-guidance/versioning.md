---
title: Bibliotecas de controle de versão e .NET
description: Recomendações de melhores práticas para controle de versão de bibliotecas do .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: f95c8ade1f91af5c13184b839b327c9397c6fe5a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187852"
---
# <a name="versioning"></a><span data-ttu-id="0102d-103">Controle de versão</span><span class="sxs-lookup"><span data-stu-id="0102d-103">Versioning</span></span>

<span data-ttu-id="0102d-104">Uma biblioteca de software raramente está completa na versão 1.0.</span><span class="sxs-lookup"><span data-stu-id="0102d-104">A software library is rarely complete in version 1.0.</span></span> <span data-ttu-id="0102d-105">Boas bibliotecas evoluem com o tempo, adicionando recursos, corrigindo bugs e melhorando o desempenho.</span><span class="sxs-lookup"><span data-stu-id="0102d-105">Good libraries evolve over time, adding features, fixing bugs and improving performance.</span></span> <span data-ttu-id="0102d-106">É importante que você possa liberar novas versões de uma biblioteca do .NET, fornecendo valor adicional a cada versão, sem interromper os usuários existentes.</span><span class="sxs-lookup"><span data-stu-id="0102d-106">It is important that you can release new versions of a .NET library, providing additional value with each version, without breaking existing users.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="0102d-107">Alterações da falha</span><span class="sxs-lookup"><span data-stu-id="0102d-107">Breaking changes</span></span>

<span data-ttu-id="0102d-108">Para obter informações sobre como lidar com alterações da falha entre as versões, veja [Alterações da falha](./breaking-changes.md).</span><span class="sxs-lookup"><span data-stu-id="0102d-108">For information about handling breaking changes between versions, see [Breaking changes](./breaking-changes.md).</span></span>

## <a name="version-numbers"></a><span data-ttu-id="0102d-109">Números de versão</span><span class="sxs-lookup"><span data-stu-id="0102d-109">Version numbers</span></span>

<span data-ttu-id="0102d-110">Uma biblioteca .NET tem várias maneiras de especificar uma versão.</span><span class="sxs-lookup"><span data-stu-id="0102d-110">A .NET library has many ways to specify a version.</span></span> <span data-ttu-id="0102d-111">Essas versões são as mais importantes:</span><span class="sxs-lookup"><span data-stu-id="0102d-111">These versions are the most important:</span></span>

### <a name="nuget-package-version"></a><span data-ttu-id="0102d-112">Versão do pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="0102d-112">NuGet package version</span></span>

<span data-ttu-id="0102d-113">A [Versão do pacote NuGet](/nuget/reference/package-versioning) é exibida em NuGet.org, o gerenciador de pacotes do NuGet do Visual Studio e adicionada ao código-fonte quando o pacote é usado.</span><span class="sxs-lookup"><span data-stu-id="0102d-113">The [NuGet package version](/nuget/reference/package-versioning) is displayed on NuGet.org, the Visual Studio NuGet package manager, and is added to source code when the package is used.</span></span> <span data-ttu-id="0102d-114">A versão do pacote NuGet é o número de versão que os usuários normalmente verão e ao qual eles farão referência ao falarem sobre a versão de uma biblioteca que está sendo usada.</span><span class="sxs-lookup"><span data-stu-id="0102d-114">The NuGet package version is the version number users will commonly see, and they'll refer to it when they talk about the version of a library they're using.</span></span> <span data-ttu-id="0102d-115">A versão do pacote NuGet é usada pelo NuGet e não tem nenhum efeito sobre o comportamento de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0102d-115">The NuGet package version is used by NuGet and has no effect on runtime behavior.</span></span>

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

<span data-ttu-id="0102d-116">O identificador de pacote do NuGet combinado com a versão do pacote NuGet é usado para identificar um pacote no NuGet.</span><span class="sxs-lookup"><span data-stu-id="0102d-116">The NuGet package identifier combined with the NuGet package version is used to identify a package in NuGet.</span></span> <span data-ttu-id="0102d-117">Por exemplo, `Newtonsoft.Json` + `11.0.2`.</span><span class="sxs-lookup"><span data-stu-id="0102d-117">For example, `Newtonsoft.Json` + `11.0.2`.</span></span> <span data-ttu-id="0102d-118">Um pacote com um sufixo é um pacote de pré-lançamento e tem um comportamento especial que o torna ideal para teste.</span><span class="sxs-lookup"><span data-stu-id="0102d-118">A package with a suffix is a pre-release package and has special behavior that makes it ideal for testing.</span></span> <span data-ttu-id="0102d-119">Para obter mais informações, veja [Pacotes pré-lançamento](./nuget.md#pre-release-packages).</span><span class="sxs-lookup"><span data-stu-id="0102d-119">For more information, see [Pre-release packages](./nuget.md#pre-release-packages).</span></span>

<span data-ttu-id="0102d-120">Como a versão do pacote NuGet é a versão mais visível para os desenvolvedores, é uma boa ideia atualizá-la usando [SemVer (Controle de Versão de Semântica)](https://semver.org/).</span><span class="sxs-lookup"><span data-stu-id="0102d-120">Because the NuGet package version is the most visible version to developers, it's a good idea to update it using [Semantic Versioning (SemVer)](https://semver.org/).</span></span> <span data-ttu-id="0102d-121">SemVer indica a importância das alterações entre as versões e ajuda os desenvolvedores a tomarem uma decisão bem informada ao escolherem qual versão usar.</span><span class="sxs-lookup"><span data-stu-id="0102d-121">SemVer indicates the significance of changes between release and helps developers make an informed decision when choosing what version to use.</span></span> <span data-ttu-id="0102d-122">Por exemplo, ir de `1.0` para `2.0` indica que potencialmente há alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="0102d-122">For example, going from `1.0` to `2.0` indicates that there are potentially breaking changes.</span></span>

<span data-ttu-id="0102d-123">**✔️ CONSIDERAR** o uso do [SemVer 2.0.0](https://semver.org/) para criar a versão do seu pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="0102d-123">**✔️ CONSIDER** using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="0102d-124">**✔️ FAÇA** uso da versão do pacote NuGet na documentação pública, uma vez que é o número de versão que os usuários verão normalmente.</span><span class="sxs-lookup"><span data-stu-id="0102d-124">**✔️ DO** use the NuGet package version in public documentation as it's the version number that users will commonly see.</span></span>

<span data-ttu-id="0102d-125">**✔️ FAÇA** a inclusão de um sufixo de pré-lançamento ao liberar um pacote não estável.</span><span class="sxs-lookup"><span data-stu-id="0102d-125">**✔️ DO** include a pre-release suffix when releasing a non-stable package.</span></span>

> <span data-ttu-id="0102d-126">Os usuários devem aceitar receberem pacotes de pré-lançamento, assim, eles entenderão que o pacote não está concluído.</span><span class="sxs-lookup"><span data-stu-id="0102d-126">Users must opt in to getting pre-release packages, so they will understand that the package is not complete.</span></span>

### <a name="assembly-version"></a><span data-ttu-id="0102d-127">Versão do assembly</span><span class="sxs-lookup"><span data-stu-id="0102d-127">Assembly version</span></span>

<span data-ttu-id="0102d-128">A versão do assembly é o que o CLR usa no tempo de execução para selecionar qual versão de um assembly carregar.</span><span class="sxs-lookup"><span data-stu-id="0102d-128">The assembly version is what the CLR uses at runtime to select which version of an assembly to load.</span></span> <span data-ttu-id="0102d-129">Selecionar um assembly usando o controle de versão só se aplica aos assemblies com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="0102d-129">Selecting an assembly using versioning only applies to assemblies with a strong name.</span></span>

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

<span data-ttu-id="0102d-130">O Windows .NET Framework CLR exige uma correspondência exata para carregar um assembly de nome forte.</span><span class="sxs-lookup"><span data-stu-id="0102d-130">The Windows .NET Framework CLR demands an exact match to load a strong named assembly.</span></span> <span data-ttu-id="0102d-131">Por exemplo, `Libary1, Version=1.0.0.0` foi compilado com uma referência ao `Newtonsoft.Json, Version=11.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="0102d-131">For example, `Libary1, Version=1.0.0.0` was compiled with a reference to `Newtonsoft.Json, Version=11.0.0.0`.</span></span> <span data-ttu-id="0102d-132">O .NET Framework só carregará a versão exata `11.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="0102d-132">The .NET Framework will only load that exact version `11.0.0.0`.</span></span> <span data-ttu-id="0102d-133">Para carregar uma versão diferente no tempo de execução, um redirecionamento de associação deve ser adicionado ao arquivo de configuração do aplicativo .NET.</span><span class="sxs-lookup"><span data-stu-id="0102d-133">To load a different version at runtime, a binding redirect must be added to the .NET application's config file.</span></span>

<span data-ttu-id="0102d-134">Nomenclatura forte combinada com a versão do assembly habilita [carregamento de versão do assembly estrita](../../framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="0102d-134">Strong naming combined with assembly version enables [strict assembly version loading](../../framework/app-domains/assembly-versioning.md).</span></span> <span data-ttu-id="0102d-135">Embora dar um nome forte a uma biblioteca tenha uma série de benefícios, isso tenderá a resultar em exceções de tempo de execução de que um assembly não pode ser encontrado e [exigirá que redirecionamentos de associação](../../framework/configure-apps/redirect-assembly-versions.md) em `app.config`/`web.config` sejam corrigidos.</span><span class="sxs-lookup"><span data-stu-id="0102d-135">While strong naming a library has a number of benefits, it often results in runtime exceptions that an assembly can't be found and [requires binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) in `app.config`/`web.config` to be fixed.</span></span> <span data-ttu-id="0102d-136">O carregamento do assembly do .NET Core foi relaxado e o .NET Core CLR carregará automaticamente os assemblies no tempo de execução com uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="0102d-136">.NET Core assembly loading has been relaxed, and the .NET Core CLR will automatically load assemblies at runtime with a higher version.</span></span>

<span data-ttu-id="0102d-137">**✔️ CONSIDERE** incluir apenas uma versão principal em AssemblyVersion.</span><span class="sxs-lookup"><span data-stu-id="0102d-137">**✔️ CONSIDER** only including a major version in the AssemblyVersion.</span></span>

> <span data-ttu-id="0102d-138">Por exemplo, Biblioteca 1.0 e Biblioteca 1.0.1 têm ambas uma AssemblyVersion de `1.0.0.0`, enquanto a Biblioteca 2.0 tem uma AssemblyVersion de `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="0102d-138">e.g. Library 1.0 and Library 1.0.1 both have an AssemblyVersion of `1.0.0.0`, while Library 2.0 has AssemblyVersion of `2.0.0.0`.</span></span> <span data-ttu-id="0102d-139">Quando a versão do assembly é alterada com menos frequência, ela reduz os redirecionamentos de associação.</span><span class="sxs-lookup"><span data-stu-id="0102d-139">When the assembly version changes less often, it reduces binding redirects.</span></span>

<span data-ttu-id="0102d-140">**✔️ CONSIDERE** manter o número de versão principal do AssemblyVersion e a versão do pacote NuGet em sincronia.</span><span class="sxs-lookup"><span data-stu-id="0102d-140">**✔️ CONSIDER** keeping the major version number of the AssemblyVersion and the NuGet package version in sync.</span></span>

> <span data-ttu-id="0102d-141">A versão do AssemblyVersion é incluída em algumas mensagens informativas exibidas ao usuário, por exemplo, o nome do assembly e os nomes de tipo qualificados do assembly em mensagens de exceção.</span><span class="sxs-lookup"><span data-stu-id="0102d-141">The AssemblyVersion is included in some informational messages displayed to the user, e.g. the assembly name and assembly qualified type names in exception messages.</span></span> <span data-ttu-id="0102d-142">Manter uma relação entre as versões fornece mais informações para desenvolvedores sobre qual versão eles estão usando.</span><span class="sxs-lookup"><span data-stu-id="0102d-142">Maintaining a relationship between the versions provides more information to developers about which version they are using.</span></span>

<span data-ttu-id="0102d-143">**❌ NÃO** tenha uma AssemblyVersion fixa.</span><span class="sxs-lookup"><span data-stu-id="0102d-143">**❌ DO NOT** have a fixed AssemblyVersion.</span></span>

> <span data-ttu-id="0102d-144">Embora um AssemblyVersion inalterável evite a necessidade de redirecionamentos de associação, isso significa que apenas uma única versão do assembly pode ser instalada no GAC (Cache de Assembly Global).</span><span class="sxs-lookup"><span data-stu-id="0102d-144">While an unchanging AssemblyVersion avoids the need for binding redirects, it means that only a single version of the assembly can be installed in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="0102d-145">Além disso, os aplicativos que fazem referência ao assembly no GAC serão interrompidos se outro aplicativo atualizar o assembly do GAC com alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="0102d-145">Also, the applications that reference the assembly in the GAC will break if another application updates the GAC assembly with breaking changes.</span></span>

### <a name="assembly-file-version"></a><span data-ttu-id="0102d-146">Versão do arquivo do assembly</span><span class="sxs-lookup"><span data-stu-id="0102d-146">Assembly file version</span></span>

<span data-ttu-id="0102d-147">A versão de arquivo do assembly é usada para exibir uma versão de arquivo no Windows e não tem nenhum efeito sobre o comportamento de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0102d-147">The assembly file version is used to display a file version in Windows and has no effect on runtime behavior.</span></span> <span data-ttu-id="0102d-148">Configurar esta versão é opcional.</span><span class="sxs-lookup"><span data-stu-id="0102d-148">Setting this version is optional.</span></span> <span data-ttu-id="0102d-149">Ele ficará visível na caixa de diálogo Propriedades do Arquivo no Windows Explorer:</span><span class="sxs-lookup"><span data-stu-id="0102d-149">It's visible in the File Properties dialog in Windows Explorer:</span></span>

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

<span data-ttu-id="0102d-150">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span><span class="sxs-lookup"><span data-stu-id="0102d-150">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span></span>

> [!NOTE]
> <span data-ttu-id="0102d-151">Um aviso de compilação inócuo será gerado se essa versão não seguir o formato `Major.Minor.Build.Revision`.</span><span class="sxs-lookup"><span data-stu-id="0102d-151">An innocuous build warning is raised if this version does not follow the format `Major.Minor.Build.Revision`.</span></span> <span data-ttu-id="0102d-152">O aviso pode ser ignorado com segurança.</span><span class="sxs-lookup"><span data-stu-id="0102d-152">The warning can be safely ignored.</span></span>

<span data-ttu-id="0102d-153">**✔️ CONSIDERE** incluir um número de build de integração contínua como a revisão AssemblyFileVersion.</span><span class="sxs-lookup"><span data-stu-id="0102d-153">**✔️ CONSIDER** including a continuous integration build number as the AssemblyFileVersion revision.</span></span>

> <span data-ttu-id="0102d-154">Por exemplo, você está criando a versão 1.0.0 do seu projeto e o número de build de integração contínua é 99, portanto, sua AssemblyFileVersion é 1.0.0.99.</span><span class="sxs-lookup"><span data-stu-id="0102d-154">For example, you are building version 1.0.0 of your project, and the continuous integration build number is 99 so your AssemblyFileVersion is 1.0.0.99.</span></span>

### <a name="assembly-informational-version"></a><span data-ttu-id="0102d-155">Versão informativa do assembly</span><span class="sxs-lookup"><span data-stu-id="0102d-155">Assembly informational version</span></span>

<span data-ttu-id="0102d-156">A versão informativa do assembly é usada para registrar informações adicionais de versão e não tem nenhum efeito sobre o comportamento de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0102d-156">The assembly informational version is used to record additional version information and has no effect on runtime behavior.</span></span> <span data-ttu-id="0102d-157">Configurar esta versão é opcional.</span><span class="sxs-lookup"><span data-stu-id="0102d-157">Setting this version is optional.</span></span> <span data-ttu-id="0102d-158">Se você estiver usando SourceLink, essa versão será definida na compilação com a versão do pacote NuGet além de uma versão de controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="0102d-158">If you're using SourceLink, this version will be set on build with the NuGet package version plus a source control version.</span></span> <span data-ttu-id="0102d-159">Por exemplo, `1.0.0-beta1+204ff0a` inclui o hash de confirmação do código-fonte do qual o assembly foi criado.</span><span class="sxs-lookup"><span data-stu-id="0102d-159">For example, `1.0.0-beta1+204ff0a` includes the commit hash of the source code the assembly was built from.</span></span> <span data-ttu-id="0102d-160">Para obter mais informações, veja [SourceLink](./sourcelink.md).</span><span class="sxs-lookup"><span data-stu-id="0102d-160">For more information, see [SourceLink](./sourcelink.md).</span></span>

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

<span data-ttu-id="0102d-161">**❌ EVITE** definir a versão informativa do assembly você mesmo.</span><span class="sxs-lookup"><span data-stu-id="0102d-161">**❌ AVOID** setting the assembly informational version yourself.</span></span>

> <span data-ttu-id="0102d-162">Permita a SourceLink gerar automaticamente a versão que contém metadados de controle do código-fonte e NuGet.</span><span class="sxs-lookup"><span data-stu-id="0102d-162">Allow SourceLink to automatically generate the version containing NuGet and source control metadata.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="0102d-163">[Anterior](./publish-nuget-package.md)
[Próximo](./breaking-changes.md)</span><span class="sxs-lookup"><span data-stu-id="0102d-163">[Previous](./publish-nuget-package.md)
[Next](./breaking-changes.md)</span></span>