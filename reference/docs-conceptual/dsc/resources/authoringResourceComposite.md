---
ms.date: 06/12/2017
keywords: dsc,powershell,конфигурация,установка
title: Составные ресурсы — использование конфигурации DSC как ресурса
ms.openlocfilehash: 7fa6ee56d4706b96fb47123c7aa00c4df6256492
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2019
ms.locfileid: "73933826"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="7d5e6-103">Составные ресурсы: использование конфигурации DSC как ресурса</span><span class="sxs-lookup"><span data-stu-id="7d5e6-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="7d5e6-104">Область применения: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7d5e6-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7d5e6-105">На практике конфигурации часто становятся длинными и сложными — вызывают множество разных ресурсов и задают большое количество свойств.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="7d5e6-106">Для решения этой проблемы можно использовать настройку требуемого состояния (DSC) Windows PowerShell как ресурс для других конфигураций.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="7d5e6-107">Мы называем это составным ресурсом.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-107">We call this a composite resource.</span></span> <span data-ttu-id="7d5e6-108">Составной ресурс — это конфигурация DSC с возможностью настройки параметров.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="7d5e6-109">Параметры конфигурации выступают как свойства ресурса.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="7d5e6-110">Конфигурация сохраняется как файл с расширением **.schema.psm1** и применяется вместо MOF-схемы и ресурса сценария в типовом ресурсе DSC (дополнительные сведения о ресурсах DSC см. в статье [Ресурсы настройки требуемого состояния Windows PowerShell](resources.md).</span><span class="sxs-lookup"><span data-stu-id="7d5e6-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="7d5e6-111">Создание составного ресурса</span><span class="sxs-lookup"><span data-stu-id="7d5e6-111">Creating the composite resource</span></span>

<span data-ttu-id="7d5e6-112">В нашем примере создается конфигурация, которая вызывает ряд существующих ресурсов для настройки виртуальных машин.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="7d5e6-113">Вместо указания значений для настройки в блоках конфигурации она принимает ряд параметров, которые будут использоваться в блоках конфигурации.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Create VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="7d5e6-114">Сохранение конфигурации как составного ресурса</span><span class="sxs-lookup"><span data-stu-id="7d5e6-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="7d5e6-115">Чтобы использовать параметризованную конфигурацию как ресурс DSC, сохраните ее в структуре папок, как и любой другой ресурс на базе MOF, и присвойте имя с расширением **. schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="7d5e6-116">В этом примере мы назовем файл **xVirtualMachine.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-116">For this example, we'll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="7d5e6-117">Кроме того, необходимо создать манифест с именем **xVirtualMachine.psd1**, содержащий указанную ниже строку.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="7d5e6-118">Он дополняет **MyDscResources.psd1** — манифест модуля для всех ресурсов в папке **MyDscResources**.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="7d5e6-119">После выполнения этих действия структура папок должна выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="7d5e6-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="7d5e6-120">Теперь ресурс можно обнаружить с помощью командлета Get-DscResource, а его свойство — с помощью того же командлета или комбинации клавиш **Ctrl + Space**, активирующей автозаполнение в интегрированной среде сценариев Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="7d5e6-121">Применение составного ресурса</span><span class="sxs-lookup"><span data-stu-id="7d5e6-121">Using the composite resource</span></span>

<span data-ttu-id="7d5e6-122">Теперь создадим конфигурацию, которая вызывает составной ресурс.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="7d5e6-123">Эта конфигурация вызывает составной ресурс xVirtualMachine для создания виртуальной машины, а затем ресурс **xComputer**, чтобы ее переименовать.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

```powershell
configuration RenameVM
{
    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

<span data-ttu-id="7d5e6-124">С помощью этого ресурса также можно создать несколько виртуальных машин путем передачи массива имен виртуальных машин в ресурс xVirtualMachine.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-124">You can also use this resource to create multiple VMs by passing in an array of VM names to the xVirtualMachine resource.</span></span>

```PowerShell
Configuration MultipleVms
{
    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VMs
        {
            VMName = "IIS01", "SQL01", "SQL02"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="7d5e6-125">Поддержка PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7d5e6-125">Supporting PsDscRunAsCredential</span></span>

> [!NOTE]
> <span data-ttu-id="7d5e6-126">**PsDscRunAsCredential** поддерживается в PowerShell 5.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-126">**PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="7d5e6-127">Свойство **PsDscRunAsCredential** может использоваться в блоке ресурса [конфигураций DSC](../configurations/configurations.md), чтобы указать, что ресурс должен выполняться с указанным набором учетных данных.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-127">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="7d5e6-128">Дополнительные сведения см. в разделе [Запуск DSC с учетными данными пользователя](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="7d5e6-128">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="7d5e6-129">Чтобы получить доступ к пользовательскому контексту из настраиваемого ресурса, можно использовать автоматическую переменную `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="7d5e6-129">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="7d5e6-130">Например, следующий код пропишет пользовательский контекст, по которому выполняется ресурс, в подробный выходной поток:</span><span class="sxs-lookup"><span data-stu-id="7d5e6-130">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="7d5e6-131">См. также</span><span class="sxs-lookup"><span data-stu-id="7d5e6-131">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="7d5e6-132">Концепции</span><span class="sxs-lookup"><span data-stu-id="7d5e6-132">Concepts</span></span>
* [<span data-ttu-id="7d5e6-133">Написание пользовательских ресурсов DSC с использованием MOF</span><span class="sxs-lookup"><span data-stu-id="7d5e6-133">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="7d5e6-134">Начало работы с настройкой требуемого состояния Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7d5e6-134">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)