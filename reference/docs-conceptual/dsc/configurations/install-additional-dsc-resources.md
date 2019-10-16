---
ms.date: 12/12/2018
keywords: dsc,powershell,resource,gallery,setup
title: Установка дополнительных ресурсов DSC
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954491"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="52a9e-103">Установка дополнительных ресурсов DSC</span><span class="sxs-lookup"><span data-stu-id="52a9e-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="52a9e-104">PowerShell включает в себя несколько установочных ресурсов для Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="52a9e-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="52a9e-105">Модуль **PSDesiredStateConfiguration** содержит все OOB ресурсы DSC, доступные в конкретно вашем экземпляре PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52a9e-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="52a9e-106">Это список OOB ресурсов, включенных в PowerShell 4.0, и описание возможностей ресурса.</span><span class="sxs-lookup"><span data-stu-id="52a9e-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="52a9e-107">Этот список неполный, так как количество OOB ресурсов увеличивалось с каждой версией PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52a9e-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="52a9e-108">Ресурс</span><span class="sxs-lookup"><span data-stu-id="52a9e-108">Resource</span></span>  |<span data-ttu-id="52a9e-109">Описание</span><span class="sxs-lookup"><span data-stu-id="52a9e-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="52a9e-110">**File**</span><span class="sxs-lookup"><span data-stu-id="52a9e-110">**File**</span></span>|<span data-ttu-id="52a9e-111">Управляет состоянием файлов и каталогов.</span><span class="sxs-lookup"><span data-stu-id="52a9e-111">Controls the state of files and directories.</span></span> <span data-ttu-id="52a9e-112">Копирует файлы из **Источника** в **Место назначения** и обновляет их при изменении **Источника** путем сравнения дат, контрольных сумм и хэшей.</span><span class="sxs-lookup"><span data-stu-id="52a9e-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="52a9e-113">**Archive**</span><span class="sxs-lookup"><span data-stu-id="52a9e-113">**Archive**</span></span>|<span data-ttu-id="52a9e-114">Распаковывает архивы и указывает местоположение.</span><span class="sxs-lookup"><span data-stu-id="52a9e-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="52a9e-115">Проверяет архивы с указанной **Контрольной суммой**.</span><span class="sxs-lookup"><span data-stu-id="52a9e-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="52a9e-116">**Environment**</span><span class="sxs-lookup"><span data-stu-id="52a9e-116">**Environment**</span></span>|<span data-ttu-id="52a9e-117">Управляет переменными среды.</span><span class="sxs-lookup"><span data-stu-id="52a9e-117">Manages environment variables.</span></span>|
|<span data-ttu-id="52a9e-118">**Группа**</span><span class="sxs-lookup"><span data-stu-id="52a9e-118">**Group**</span></span>|<span data-ttu-id="52a9e-119">Управляет локальными группами и контролирует членство в группах.</span><span class="sxs-lookup"><span data-stu-id="52a9e-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="52a9e-120">**Log**</span><span class="sxs-lookup"><span data-stu-id="52a9e-120">**Log**</span></span>|<span data-ttu-id="52a9e-121">Записывает сообщения в журнал событий `Microsoft-Windows-Desired State Configuration/Analytic`.</span><span class="sxs-lookup"><span data-stu-id="52a9e-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="52a9e-122">**Пакет**</span><span class="sxs-lookup"><span data-stu-id="52a9e-122">**Package**</span></span>|<span data-ttu-id="52a9e-123">Устанавливает или удаляет пакеты, используя **Аргументы**, **LogPath**, **ReturnCode**, другие параметры.</span><span class="sxs-lookup"><span data-stu-id="52a9e-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="52a9e-124">**Registry**</span><span class="sxs-lookup"><span data-stu-id="52a9e-124">**Registry**</span></span>|<span data-ttu-id="52a9e-125">Управляет разделами и значениями реестра.</span><span class="sxs-lookup"><span data-stu-id="52a9e-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="52a9e-126">**Script**</span><span class="sxs-lookup"><span data-stu-id="52a9e-126">**Script**</span></span>|<span data-ttu-id="52a9e-127">Позволяет разрабатывать собственные блоки сценариев [get-test-set](../resources/get-test-set.md).</span><span class="sxs-lookup"><span data-stu-id="52a9e-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="52a9e-128">**Служба**</span><span class="sxs-lookup"><span data-stu-id="52a9e-128">**Service**</span></span>|<span data-ttu-id="52a9e-129">Настраивает службы Windows.</span><span class="sxs-lookup"><span data-stu-id="52a9e-129">Configures Windows services.</span></span>|
|<span data-ttu-id="52a9e-130">**User**</span><span class="sxs-lookup"><span data-stu-id="52a9e-130">**User**</span></span> |<span data-ttu-id="52a9e-131">Управляет локальными пользователями и атрибутами.</span><span class="sxs-lookup"><span data-stu-id="52a9e-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="52a9e-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="52a9e-132">**WindowsFeature**</span></span>|<span data-ttu-id="52a9e-133">Управляет ролями и функциями.</span><span class="sxs-lookup"><span data-stu-id="52a9e-133">Manages roles and features.</span></span>|
|<span data-ttu-id="52a9e-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="52a9e-134">**WindowsProcess**</span></span>|<span data-ttu-id="52a9e-135">Настраивает процессы Windows.</span><span class="sxs-lookup"><span data-stu-id="52a9e-135">Configures Windows processes.</span></span>|

<span data-ttu-id="52a9e-136">Ресурсы OOB обеспечивают обычным операциям хорошую отправную точку.</span><span class="sxs-lookup"><span data-stu-id="52a9e-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="52a9e-137">Если ресурсы OOB не соответствуют вашим потребностям, вы можете написать свой собственный [Пользовательский ресурс](../resources/authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="52a9e-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="52a9e-138">Прежде чем написать собственный ресурс для решения проблемы, вы должны просмотреть огромное количество уже созданных как Microsoft, так и сообществом PowerShell ресурсов DSC.</span><span class="sxs-lookup"><span data-stu-id="52a9e-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="52a9e-139">Ресурсы DSC можно найти как в [коллекции PowerShell](https://www.powershellgallery.com/), так и на [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="52a9e-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="52a9e-140">Вы также можете установить ресурсы DSC непосредственно из консоли PowerShell, используя [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="52a9e-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="52a9e-141">Установка PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="52a9e-141">Installing PowerShellGet</span></span>

<span data-ttu-id="52a9e-142">Чтобы определить, есть ли у вас **PowerShell**, или получить справку по его установке, см. руководство [Установка PowerShellGet](/powershell/gallery/installing-psget).</span><span class="sxs-lookup"><span data-stu-id="52a9e-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="52a9e-143">Поиск ресурсов DSC с помощью PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="52a9e-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="52a9e-144">После установки **PowerShellGet** на компьютер, вы можете найти и установить ресурсы DSC, размещенные в [коллекции PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="52a9e-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="52a9e-145">Сначала используйте командлет [Find-DSCResource](/powershell/module/powershellget/find-dscresource), чтобы найти ресурсы DSC.</span><span class="sxs-lookup"><span data-stu-id="52a9e-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="52a9e-146">При первом запуске `Find-DSCResource` вы увидите следующую подсказку для установки "поставщика NuGet".</span><span class="sxs-lookup"><span data-stu-id="52a9e-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="52a9e-147">После нажатия "y" (установки поставщика NuGet) вы увидите список ресурсов DSC, которые вы можете установить из коллекции PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52a9e-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="52a9e-148">Список не отображается, поскольку очень велик.</span><span class="sxs-lookup"><span data-stu-id="52a9e-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="52a9e-149">Вы также можете указать параметр `-Name`, используя подстановочные знаки, или параметр `-Filter` без подстановочных знаков, чтобы сузить область поиска.</span><span class="sxs-lookup"><span data-stu-id="52a9e-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="52a9e-150">В этом примере предпринимается попытка найти ресурс DSC TimeZone с использованием подстановочных знаков.</span><span class="sxs-lookup"><span data-stu-id="52a9e-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52a9e-151">В настоящее время в командлете `Find-DSCResource` есть ошибка, которая не позволяет использовать подстановочные знаки в параметрах `-Name` и `-Filter`.</span><span class="sxs-lookup"><span data-stu-id="52a9e-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="52a9e-152">Во втором примере, поданном ниже, показано возможное решение с помощью `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="52a9e-152">The second example below shows a workaround using `Where-Object`.</span></span>

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

<span data-ttu-id="52a9e-153">Вы также можете использовать `Where-Object` для поиска ресурсов DSC с более детальной фильтрацией.</span><span class="sxs-lookup"><span data-stu-id="52a9e-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="52a9e-154">Этот подход будет медленнее, чем использование встроенных параметров фильтрации.</span><span class="sxs-lookup"><span data-stu-id="52a9e-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="52a9e-155">Дополнительные сведения о фильтрации см. в разделе [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="52a9e-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="52a9e-156">Установка ресурсов DSC с помощью PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="52a9e-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="52a9e-157">Чтобы установить ресурс DSC, используйте командлет [Install-Module](/powershell/module/PowershellGet/Install-Module), указав имя модуля, отображаемого в имени **модуля** в результатах поиска.</span><span class="sxs-lookup"><span data-stu-id="52a9e-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="52a9e-158">Ресурс TimeZone существует в модуле ComputerManagementDSC, поэтому в этом примере устанавливается этот модуль.</span><span class="sxs-lookup"><span data-stu-id="52a9e-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="52a9e-159">Если коллекция PowerShell не является надежной, вы увидите предупреждение ниже с запросом подтверждения и указанием, как избежать последующих запросов при установке.</span><span class="sxs-lookup"><span data-stu-id="52a9e-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="52a9e-160">Нажмите "y", чтобы продолжить установку модуля.</span><span class="sxs-lookup"><span data-stu-id="52a9e-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="52a9e-161">После установки вы можете проверить, установлен ли ваш новый ресурс, используя [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="52a9e-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="52a9e-162">Вы также можете просмотреть другие ресурсы в только что установленном модуле, указав параметр `-ModuleName`.</span><span class="sxs-lookup"><span data-stu-id="52a9e-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a><span data-ttu-id="52a9e-163">См. также:</span><span class="sxs-lookup"><span data-stu-id="52a9e-163">See also</span></span>

- [<span data-ttu-id="52a9e-164">Общие сведения о ресурсах</span><span class="sxs-lookup"><span data-stu-id="52a9e-164">What are Resources?</span></span>](../resources/resources.md)