---
ms.date: 06/12/2017
keywords: dsc,powershell,конфигурация,установка
title: Обновление узлов на опрашиваемом сервере
ms.openlocfilehash: 516e50b0c39e4747a123307cb3f5e25259ac7ce5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417715"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="0ae0a-103">Обновление узлов на опрашиваемом сервере</span><span class="sxs-lookup"><span data-stu-id="0ae0a-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="0ae0a-104">В следующих разделах предполагается, что вы уже настроили опрашиваемый сервер.</span><span class="sxs-lookup"><span data-stu-id="0ae0a-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="0ae0a-105">Если вы не настроили опрашиваемый сервер, можно воспользоваться следующими руководствами.</span><span class="sxs-lookup"><span data-stu-id="0ae0a-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="0ae0a-106">Настройка опрашиваемого SMB-сервера DSC</span><span class="sxs-lookup"><span data-stu-id="0ae0a-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="0ae0a-107">Настройка опрашиваемого HTTP-сервера DSC</span><span class="sxs-lookup"><span data-stu-id="0ae0a-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="0ae0a-108">Для каждого целевого узла можно настроить скачивание конфигураций, ресурсов и даже отчет о состоянии.</span><span class="sxs-lookup"><span data-stu-id="0ae0a-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="0ae0a-109">В этой статье показано, как передать ресурсы, чтобы они были доступны для загрузки, и настроить клиенты, чтобы ресурсы загружались автоматически.</span><span class="sxs-lookup"><span data-stu-id="0ae0a-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="0ae0a-110">Когда Узел получает назначенную конфигурацию с помощью команды **получить** или **отправить** (v5), он автоматически загружает любые ресурсы, требуемые конфигурацией, из расположения, указанного в LCM.</span><span class="sxs-lookup"><span data-stu-id="0ae0a-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="0ae0a-111">Использование командлета Update-DSCConfiguration</span><span class="sxs-lookup"><span data-stu-id="0ae0a-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="0ae0a-112">Начиная с PowerShell 5.0, командлет [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) принуждает узел обновлять свою конфигурацию с опрашиваемого сервера, настроенного в LCM.</span><span class="sxs-lookup"><span data-stu-id="0ae0a-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="0ae0a-113">Использование Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="0ae0a-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="0ae0a-114">В PowerShell 4.0 вы по прежнему можете вручную заставить клиента — получателя данных обновить свою конфигурацию, используя [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="0ae0a-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="0ae0a-115">В следующем примере создается сеанс CIM с указанными учетными данными, который вызывает соответствующий метод CIM и удаляет сеанс.</span><span class="sxs-lookup"><span data-stu-id="0ae0a-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="0ae0a-116">См. также</span><span class="sxs-lookup"><span data-stu-id="0ae0a-116">See Also</span></span>

[<span data-ttu-id="0ae0a-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="0ae0a-117">PerformRequiredConfigurationChecks</span></span>](/powershell/scripting/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)