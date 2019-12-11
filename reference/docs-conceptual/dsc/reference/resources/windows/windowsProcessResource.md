---
ms.date: 09/20/2019
keywords: dsc,powershell,конфигурация,установка
title: Ресурс WindowsProcess в DSC
ms.openlocfilehash: e168cdebb04f7ec83b73a537a5f188299f40d8b7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952841"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="41f7b-103">Ресурс WindowsProcess в DSC</span><span class="sxs-lookup"><span data-stu-id="41f7b-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="41f7b-104">Область применения: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="41f7b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="41f7b-105">Ресурс **WindowsProcess** в DSC Windows PowerShell предоставляет механизм настройки процессов на целевом узле.</span><span class="sxs-lookup"><span data-stu-id="41f7b-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="41f7b-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="41f7b-106">Syntax</span></span>

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="41f7b-107">Свойства</span><span class="sxs-lookup"><span data-stu-id="41f7b-107">Properties</span></span>

|<span data-ttu-id="41f7b-108">Свойство</span><span class="sxs-lookup"><span data-stu-id="41f7b-108">Property</span></span> |<span data-ttu-id="41f7b-109">Описание</span><span class="sxs-lookup"><span data-stu-id="41f7b-109">Description</span></span> |
|---|---|
|<span data-ttu-id="41f7b-110">Аргументы</span><span class="sxs-lookup"><span data-stu-id="41f7b-110">Arguments</span></span> |<span data-ttu-id="41f7b-111">Указывает строку аргументов, которая будет передана процессу "как есть".</span><span class="sxs-lookup"><span data-stu-id="41f7b-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="41f7b-112">Если необходимо передать несколько аргументов, поместите их все в эту строку.</span><span class="sxs-lookup"><span data-stu-id="41f7b-112">If you need to pass several arguments, put them all in this string.</span></span> |
|<span data-ttu-id="41f7b-113">путь</span><span class="sxs-lookup"><span data-stu-id="41f7b-113">Path</span></span> |<span data-ttu-id="41f7b-114">Путь к исполняемому файлу процесса.</span><span class="sxs-lookup"><span data-stu-id="41f7b-114">The path to the process executable.</span></span> <span data-ttu-id="41f7b-115">Если это имя исполняемого файла (а не полный путь к нему), ресурс DSC будет искать переменную среды `$env:Path`, чтобы найти исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="41f7b-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment `$env:Path` variable to find the executable file.</span></span> <span data-ttu-id="41f7b-116">Если значение этого свойства — полный путь, ресурс DSC не будет использовать переменную среды `$env:Path` для поиска файла и вызовет ошибку в случае отсутствия пути.</span><span class="sxs-lookup"><span data-stu-id="41f7b-116">If the value of this property is a fully qualified path, DSC will not use the `$env:Path` variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="41f7b-117">Относительные пути не допускаются.</span><span class="sxs-lookup"><span data-stu-id="41f7b-117">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="41f7b-118">Учетные данные</span><span class="sxs-lookup"><span data-stu-id="41f7b-118">Credential</span></span> |<span data-ttu-id="41f7b-119">Указывает учетные данные для запуска процесса.</span><span class="sxs-lookup"><span data-stu-id="41f7b-119">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="41f7b-120">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="41f7b-120">StandardErrorPath</span></span> |<span data-ttu-id="41f7b-121">Указывает путь к каталогу для записи стандартных ошибок.</span><span class="sxs-lookup"><span data-stu-id="41f7b-121">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="41f7b-122">Все существующие файлы в этом каталоге будут перезаписаны.</span><span class="sxs-lookup"><span data-stu-id="41f7b-122">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="41f7b-123">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="41f7b-123">StandardInputPath</span></span> |<span data-ttu-id="41f7b-124">Указывает расположение стандартного ввода.</span><span class="sxs-lookup"><span data-stu-id="41f7b-124">Indicates the standard input location.</span></span> |
|<span data-ttu-id="41f7b-125">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="41f7b-125">StandardOutputPath</span></span> |<span data-ttu-id="41f7b-126">Указывает расположение стандартного вывода.</span><span class="sxs-lookup"><span data-stu-id="41f7b-126">Indicates the location to write the standard output.</span></span> <span data-ttu-id="41f7b-127">Все существующие файлы в этом каталоге будут перезаписаны.</span><span class="sxs-lookup"><span data-stu-id="41f7b-127">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="41f7b-128">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="41f7b-128">WorkingDirectory</span></span> |<span data-ttu-id="41f7b-129">Указывает расположение, которое будет использоваться в качестве текущего рабочего каталога для процесса.</span><span class="sxs-lookup"><span data-stu-id="41f7b-129">Indicates the location that will be used as the current working directory for the process.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="41f7b-130">Общие свойства</span><span class="sxs-lookup"><span data-stu-id="41f7b-130">Common properties</span></span>

|<span data-ttu-id="41f7b-131">Свойство</span><span class="sxs-lookup"><span data-stu-id="41f7b-131">Property</span></span> |<span data-ttu-id="41f7b-132">Описание</span><span class="sxs-lookup"><span data-stu-id="41f7b-132">Description</span></span> |
|---|---|
|<span data-ttu-id="41f7b-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="41f7b-133">DependsOn</span></span> |<span data-ttu-id="41f7b-134">Указывает, что перед настройкой этого ресурса необходимо запустить настройку другого ресурса.</span><span class="sxs-lookup"><span data-stu-id="41f7b-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="41f7b-135">Например, если идентификатор первого запускаемого блока сценария для конфигурации ресурса — ResourceName, а его тип — ResourceType, то синтаксис использования этого свойства таков: `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="41f7b-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="41f7b-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="41f7b-136">Ensure</span></span> |<span data-ttu-id="41f7b-137">Указывает, существует ли процесс.</span><span class="sxs-lookup"><span data-stu-id="41f7b-137">Indicates if the process exists.</span></span> <span data-ttu-id="41f7b-138">Чтобы гарантировать, что процесс существует, укажите для этого свойства значение **Present**.</span><span class="sxs-lookup"><span data-stu-id="41f7b-138">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="41f7b-139">В противном случае укажите значение **Absent**.</span><span class="sxs-lookup"><span data-stu-id="41f7b-139">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="41f7b-140">Значение по умолчанию — **Present**.</span><span class="sxs-lookup"><span data-stu-id="41f7b-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="41f7b-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="41f7b-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="41f7b-142">Задает учетные данные для выполнения всего ресурса от другого имени.</span><span class="sxs-lookup"><span data-stu-id="41f7b-142">Sets the credential for running the entire resource as.</span></span> |