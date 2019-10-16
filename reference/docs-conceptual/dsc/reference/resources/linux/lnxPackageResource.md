---
ms.date: 09/20/2019
keywords: dsc,powershell,конфигурация,установка
title: Ресурс nxPackage в DSC для Linux
ms.openlocfilehash: 4091cbbd5e34a84b9011870da4bda93281378347
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954821"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="a308a-103">Ресурс nxPackage в DSC для Linux</span><span class="sxs-lookup"><span data-stu-id="a308a-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="a308a-104">Ресурс **nxPackage** в настройке требуемого состояния PowerShell предоставляет механизм управления пакетами на узле Linux.</span><span class="sxs-lookup"><span data-stu-id="a308a-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="a308a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a308a-105">Syntax</span></span>

```Syntax
nxPackage <string> #ResourceName
{
    Name = <string>
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ FilePath = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="a308a-106">Свойства</span><span class="sxs-lookup"><span data-stu-id="a308a-106">Properties</span></span>

|<span data-ttu-id="a308a-107">Свойство</span><span class="sxs-lookup"><span data-stu-id="a308a-107">Property</span></span> |<span data-ttu-id="a308a-108">Описание</span><span class="sxs-lookup"><span data-stu-id="a308a-108">Description</span></span> |
|---|---|
|<span data-ttu-id="a308a-109">Name</span><span class="sxs-lookup"><span data-stu-id="a308a-109">Name</span></span> |<span data-ttu-id="a308a-110">Указывает имя пакета, для которого требуется обеспечить определенное состояние.</span><span class="sxs-lookup"><span data-stu-id="a308a-110">The name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="a308a-111">PackageManager</span><span class="sxs-lookup"><span data-stu-id="a308a-111">PackageManager</span></span> |<span data-ttu-id="a308a-112">Поддерживаются значения **yum**, **apt** и **zypper**.</span><span class="sxs-lookup"><span data-stu-id="a308a-112">Supported values are **yum**, **apt**, and **zypper**.</span></span> <span data-ttu-id="a308a-113">Указывает, какой диспетчер пакетов нужно использовать при установке пакетов.</span><span class="sxs-lookup"><span data-stu-id="a308a-113">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="a308a-114">Если свойство **FilePath** указано, пакет будет установлен по указанному пути.</span><span class="sxs-lookup"><span data-stu-id="a308a-114">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="a308a-115">В противном случае для установки пакета будет использоваться диспетчер пакетов из предварительно настроенного репозитория.</span><span class="sxs-lookup"><span data-stu-id="a308a-115">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="a308a-116">Если ни одно из свойств **PackageManager** и **FilePath** не указано, будет использоваться диспетчер пакетов, предусмотренный для системы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a308a-116">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span> |
|<span data-ttu-id="a308a-117">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="a308a-117">PackageGroup</span></span> |<span data-ttu-id="a308a-118">Если свойство имеет значение `$true`, в качестве параметра **Name** должно быть задано имя группы пакетов для использования с **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="a308a-118">If `$true`, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="a308a-119">**PackageGroup** не используется, если задано свойство **FilePath**.</span><span class="sxs-lookup"><span data-stu-id="a308a-119">**PackageGroup** is not valid when providing a **FilePath**.</span></span> |
|<span data-ttu-id="a308a-120">Аргументы</span><span class="sxs-lookup"><span data-stu-id="a308a-120">Arguments</span></span> |<span data-ttu-id="a308a-121">Строка аргументов, которая будет передана в пакет в указанном виде.</span><span class="sxs-lookup"><span data-stu-id="a308a-121">A string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="a308a-122">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="a308a-122">ReturnCode</span></span> |<span data-ttu-id="a308a-123">Ожидаемый код возврата.</span><span class="sxs-lookup"><span data-stu-id="a308a-123">The expected return code.</span></span> <span data-ttu-id="a308a-124">Если фактический код возврата не соответствует указанному здесь значению, настройка вернет ошибку.</span><span class="sxs-lookup"><span data-stu-id="a308a-124">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |
|<span data-ttu-id="a308a-125">FilePath</span><span class="sxs-lookup"><span data-stu-id="a308a-125">FilePath</span></span> |<span data-ttu-id="a308a-126">Путь к файлу пакета.</span><span class="sxs-lookup"><span data-stu-id="a308a-126">The file path where the package resides.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="a308a-127">Общие свойства</span><span class="sxs-lookup"><span data-stu-id="a308a-127">Common properties</span></span>

|<span data-ttu-id="a308a-128">Свойство</span><span class="sxs-lookup"><span data-stu-id="a308a-128">Property</span></span> |<span data-ttu-id="a308a-129">Описание</span><span class="sxs-lookup"><span data-stu-id="a308a-129">Description</span></span> |
|---|---|
|<span data-ttu-id="a308a-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a308a-130">DependsOn</span></span> |<span data-ttu-id="a308a-131">Указывает, что перед настройкой этого ресурса необходимо запустить настройку другого ресурса.</span><span class="sxs-lookup"><span data-stu-id="a308a-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a308a-132">Например, если идентификатор первого запускаемого блока сценария для конфигурации ресурса — ResourceName, а его тип — ResourceType, то синтаксис использования этого свойства таков: `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a308a-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="a308a-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="a308a-133">Ensure</span></span> |<span data-ttu-id="a308a-134">Определяет, нужно ли проверять существование пакета.</span><span class="sxs-lookup"><span data-stu-id="a308a-134">Determines whether to check if the package exists.</span></span> <span data-ttu-id="a308a-135">Чтобы гарантировать, что пакет существует, укажите для этого свойства значение **Present**.</span><span class="sxs-lookup"><span data-stu-id="a308a-135">Set this property to **Present** to ensure the package exists.</span></span> <span data-ttu-id="a308a-136">Чтобы гарантировать, что пакет не существует, укажите для этого свойства значение **Absent**.</span><span class="sxs-lookup"><span data-stu-id="a308a-136">Set it to **Absent** to ensure the package does not exist.</span></span> <span data-ttu-id="a308a-137">Значение по умолчанию — **Present**.</span><span class="sxs-lookup"><span data-stu-id="a308a-137">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="a308a-138">Пример</span><span class="sxs-lookup"><span data-stu-id="a308a-138">Example</span></span>

<span data-ttu-id="a308a-139">В следующем примере с помощью диспетчера пакетов Yum проверяется, установлен ли пакет с именем httpd на компьютере Linux.</span><span class="sxs-lookup"><span data-stu-id="a308a-139">The following example ensures that the package named "httpd" is installed on a Linux computer, using the "Yum" package manager.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxPackage httpd
    {
        Name = "httpd"
        Ensure = "Present"
        PackageManager = "Yum"
    }
}
```