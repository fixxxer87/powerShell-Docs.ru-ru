---
ms.date: 09/20/2019
keywords: dsc,powershell,конфигурация,установка
title: Ресурс PackageManagement DSC
ms.openlocfilehash: dfc23bfabbc45041e15c56a29a77c5bdda430a30
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953241"
---
# <a name="dsc-packagemanagement-resource"></a><span data-ttu-id="b9ae5-103">Ресурс PackageManagement DSC</span><span class="sxs-lookup"><span data-stu-id="b9ae5-103">DSC PackageManagement Resource</span></span>

<span data-ttu-id="b9ae5-104">Область применения: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="b9ae5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="b9ae5-105">Ресурс **PackageManagement** в службе настройки требуемого состояния Windows PowerShell (DSC) предоставляет механизм установки пакетов управления пакетами на целевом узле или их удаления.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-105">The **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Package Management packages on a target node.</span></span> <span data-ttu-id="b9ae5-106">Для этого ресурса требуется модуль **PackageManagement**, доступный из [http://PowerShellGallery.com](https://PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="b9ae5-106">This resource requires the **PackageManagement** module, available from [http://PowerShellGallery.com](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9ae5-107">Указанные ниже сведения о свойствах относятся к модулю **PackageManagement** версии 1.1.7.0 и новее.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-107">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9ae5-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b9ae5-108">Syntax</span></span>

```Syntax
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ AdditionalParameters = [HashTable] ]
    [ MaximumVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ ProviderName = [string] ]
    [ RequiredVersion = [string] ]
    [ Source = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="b9ae5-109">Свойства</span><span class="sxs-lookup"><span data-stu-id="b9ae5-109">Properties</span></span>

|<span data-ttu-id="b9ae5-110">Свойство</span><span class="sxs-lookup"><span data-stu-id="b9ae5-110">Property</span></span> |<span data-ttu-id="b9ae5-111">Описание</span><span class="sxs-lookup"><span data-stu-id="b9ae5-111">Description</span></span> |
|---|---|
|<span data-ttu-id="b9ae5-112">Name</span><span class="sxs-lookup"><span data-stu-id="b9ae5-112">Name</span></span> |<span data-ttu-id="b9ae5-113">Указывает имя устанавливаемого или удаляемого пакета.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-113">Specifies the name of the Package to be installed or uninstalled.</span></span> |
|<span data-ttu-id="b9ae5-114">AdditionalParameters</span><span class="sxs-lookup"><span data-stu-id="b9ae5-114">AdditionalParameters</span></span> |<span data-ttu-id="b9ae5-115">Предоставляет определенную хэш-таблицу параметров, которые передаются в аргумент `Get-Package -AdditionalArguments`.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-115">Provider specific hashtable of parameters that would be passed to `Get-Package -AdditionalArguments`.</span></span> <span data-ttu-id="b9ae5-116">Например, для поставщика NuGet можно передать дополнительные параметры, такие как DestinationPath.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-116">For example, for NuGet provider you can pass additional parameters like DestinationPath.</span></span> |
|<span data-ttu-id="b9ae5-117">MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="b9ae5-117">MaximumVersion</span></span> |<span data-ttu-id="b9ae5-118">Указывает максимальную версию пакета, которую требуется найти.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-118">Specifies the maximum allowed version of the package that you want to find.</span></span> <span data-ttu-id="b9ae5-119">Если этот параметр не указан, ресурс находит новейшую версию пакета.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-119">If you do not add this parameter, the resource finds the highest available version of the package.</span></span> |
|<span data-ttu-id="b9ae5-120">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b9ae5-120">MinimumVersion</span></span> |<span data-ttu-id="b9ae5-121">Указывает минимальную версию пакета, которую требуется найти.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-121">Specifies the minimum allowed version of the package that you want to find.</span></span> <span data-ttu-id="b9ae5-122">Если этот параметр не указан, ресурс находит новейшую доступную версию пакета, номер которой не превышает тот, что указан в параметре **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-122">If you do not add this parameter, the resource finds the highest available version of the package that also satisfies any maximum specified version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="b9ae5-123">ProviderName</span><span class="sxs-lookup"><span data-stu-id="b9ae5-123">ProviderName</span></span> |<span data-ttu-id="b9ae5-124">Указывает имя поставщика пакетов, на который распространяется область поиска пакетов.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-124">Specifies a package provider name to which to scope your package search.</span></span> <span data-ttu-id="b9ae5-125">Чтобы получить имена поставщиков пакетов, выполните командлет `Get-PackageProvider`.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-125">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span> |
|<span data-ttu-id="b9ae5-126">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b9ae5-126">RequiredVersion</span></span> |<span data-ttu-id="b9ae5-127">Указывает точную версию пакета, который вы хотите установить.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-127">Specifies the exact version of the package that you want to install.</span></span> <span data-ttu-id="b9ae5-128">Если этот параметр не указан, ресурс DSC устанавливает новейшую версию пакета, номер которой не превышает тот, что указан в параметре **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-128">If you do not specify this parameter, this DSC resource installs the newest available version of the package that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span> |
|<span data-ttu-id="b9ae5-129">Источник</span><span class="sxs-lookup"><span data-stu-id="b9ae5-129">Source</span></span> |<span data-ttu-id="b9ae5-130">Указывает имя источника пакета, в котором его можно найти.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-130">Specifies the name of the package source where the package can be found.</span></span> <span data-ttu-id="b9ae5-131">Это может быть универсальный код ресурса (URI) или источник, зарегистрированный с помощью командлета `Register-PackageSource` или ресурса DSC PackageManagementSource.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-131">This can either be a URI or a source registered with `Register-PackageSource` or PackageManagementSource DSC resource.</span></span> |
|<span data-ttu-id="b9ae5-132">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="b9ae5-132">SourceCredential</span></span> |<span data-ttu-id="b9ae5-133">Указывает учетную запись пользователя с правами для установки пакета для заданного поставщика или источника пакетов.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-133">Specifies a user account that has rights to install a package for a specified package provider or source.</span></span> |

## <a name="additional-parameters"></a><span data-ttu-id="b9ae5-134">Дополнительные параметры</span><span class="sxs-lookup"><span data-stu-id="b9ae5-134">Additional Parameters</span></span>

<span data-ttu-id="b9ae5-135">В следующей таблице перечислены параметры свойства AdditionalParameters.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-135">The following table lists options for the AdditionalParameters property.</span></span>

|<span data-ttu-id="b9ae5-136">Параметр</span><span class="sxs-lookup"><span data-stu-id="b9ae5-136">Parameter</span></span> |<span data-ttu-id="b9ae5-137">Описание</span><span class="sxs-lookup"><span data-stu-id="b9ae5-137">Description</span></span> |
|---|---|
|<span data-ttu-id="b9ae5-138">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="b9ae5-138">DestinationPath</span></span> |<span data-ttu-id="b9ae5-139">Используется поставщиками, такими как встроенный поставщик NuGet.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-139">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="b9ae5-140">Указывает расположение файла, в котором вы хотите установить пакет.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-140">Specifies a file location where you want the package to be installed.</span></span> |
|<span data-ttu-id="b9ae5-141">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="b9ae5-141">InstallationPolicy</span></span> |<span data-ttu-id="b9ae5-142">Используется поставщиками, такими как встроенный поставщик NuGet.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-142">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="b9ae5-143">Определяет, доверяете ли вы источнику пакета.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-143">Determines whether you trust the package's source.</span></span> <span data-ttu-id="b9ae5-144">Одно из двух значений: **Untrusted** или **Trusted**.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-144">One of: **Untrusted** or **Trusted**.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="b9ae5-145">Общие свойства</span><span class="sxs-lookup"><span data-stu-id="b9ae5-145">Common properties</span></span>

|<span data-ttu-id="b9ae5-146">Свойство</span><span class="sxs-lookup"><span data-stu-id="b9ae5-146">Property</span></span> |<span data-ttu-id="b9ae5-147">Описание</span><span class="sxs-lookup"><span data-stu-id="b9ae5-147">Description</span></span> |
|---|---|
|<span data-ttu-id="b9ae5-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b9ae5-148">DependsOn</span></span> |<span data-ttu-id="b9ae5-149">Указывает, что перед настройкой этого ресурса необходимо запустить настройку другого ресурса.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b9ae5-150">Например, если идентификатор первого запускаемого блока сценария для конфигурации ресурса — ResourceName, а его тип — ResourceType, то синтаксис использования этого свойства таков: `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="b9ae5-151">Ensure</span><span class="sxs-lookup"><span data-stu-id="b9ae5-151">Ensure</span></span> |<span data-ttu-id="b9ae5-152">Определяет, следует ли установить или удалить пакет.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-152">Determines whether the package is to be installed or uninstalled.</span></span> <span data-ttu-id="b9ae5-153">Значение по умолчанию — **Present**.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-153">The default value is **Present**.</span></span> |
|<span data-ttu-id="b9ae5-154">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="b9ae5-154">PsDscRunAsCredential</span></span> |<span data-ttu-id="b9ae5-155">Задает учетные данные для выполнения всего ресурса от другого имени.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-155">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="b9ae5-156">В WMF 5.0 было добавлено общее свойство **PsDscRunAsCredential**, разрешающее запуск любого ресурса DSC в контексте других учетных данных.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-156">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="b9ae5-157">Дополнительные сведения см. в разделе [Использование учетных данных с ресурсами DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="b9ae5-157">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="b9ae5-158">Пример</span><span class="sxs-lookup"><span data-stu-id="b9ae5-158">Example</span></span>

<span data-ttu-id="b9ae5-159">В этом примере устанавливается пакет NuGet **JQuery** и модуль PowerShell **GistProvider** с помощью ресурса DSC **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="b9ae5-159">This example installs the **JQuery** NuGet package and **GistProvider** PowerShell module using the **PackageManagement** DSC resource.</span></span> <span data-ttu-id="b9ae5-160">В этом примере сначала обеспечивается доступность нужных источников пакета, а затем определяется ожидаемое состояние пакетов **JQuery** и **GistProvider** (для NuGet и PowerShell).</span><span class="sxs-lookup"><span data-stu-id="b9ae5-160">This example first ensures the required package sources are available then defines the expected state of the **JQuery** and **GistProvider** packages (NuGet and PowerShell, respectively).</span></span>

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```