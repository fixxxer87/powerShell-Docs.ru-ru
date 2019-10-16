---
title: Создание оснастки Windows PowerShell | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: 465ab9e8fa29716ce0f46ad0dcf01d0ddd615bcd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364233"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="3ac5d-102">Написание оснастки Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ac5d-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="3ac5d-103">В этом примере показано, как создать оснастку Windows PowerShell, которая может использоваться для регистрации всех командлетов и поставщиков Windows PowerShell в сборке.</span><span class="sxs-lookup"><span data-stu-id="3ac5d-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="3ac5d-104">При использовании этого типа оснастки не следует выбирать командлеты и поставщики, которые нужно зарегистрировать.</span><span class="sxs-lookup"><span data-stu-id="3ac5d-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="3ac5d-105">Чтобы создать оснастку, которая позволяет выбрать регистрируемые объекты, см. раздел [написание пользовательской оснастки Windows PowerShell](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="3ac5d-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="3ac5d-106">Написание оснастки Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ac5d-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="3ac5d-107">Добавьте атрибут Рунинсталлераттрибуте.</span><span class="sxs-lookup"><span data-stu-id="3ac5d-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="3ac5d-108">Создайте открытый класс, производный от класса [System. Management. Automation. PSSnapin](/dotnet/api/System.Management.Automation.PSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="3ac5d-108">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="3ac5d-109">В этом примере имя класса — «GetProcPSSnapIn01».</span><span class="sxs-lookup"><span data-stu-id="3ac5d-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="3ac5d-110">Добавьте открытое свойство для имени оснастки (обязательно).</span><span class="sxs-lookup"><span data-stu-id="3ac5d-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="3ac5d-111">При именовании оснасток не используйте следующие символы: #.</span><span class="sxs-lookup"><span data-stu-id="3ac5d-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="3ac5d-112">, () {} [] &-/\ $; : "" \< >;?</span><span class="sxs-lookup"><span data-stu-id="3ac5d-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="3ac5d-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="3ac5d-113">@ \` \*</span></span>

    <span data-ttu-id="3ac5d-114">В этом примере имя оснастки — «GetProcPSSnapIn01».</span><span class="sxs-lookup"><span data-stu-id="3ac5d-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="3ac5d-115">Добавьте открытое свойство для поставщика оснастки (обязательно).</span><span class="sxs-lookup"><span data-stu-id="3ac5d-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="3ac5d-116">В этом примере поставщиком является "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="3ac5d-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="3ac5d-117">Добавьте открытое свойство для ресурса поставщика оснастки (необязательно).</span><span class="sxs-lookup"><span data-stu-id="3ac5d-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="3ac5d-118">В этом примере ресурсом поставщика является "GetProcPSSnapIn01, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="3ac5d-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="3ac5d-119">Добавьте открытое свойство для описания оснастки (обязательно).</span><span class="sxs-lookup"><span data-stu-id="3ac5d-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="3ac5d-120">В этом примере описание: «это оснастка Windows PowerShell, которая регистрирует командлет Get-proc».</span><span class="sxs-lookup"><span data-stu-id="3ac5d-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="3ac5d-121">Добавьте открытое свойство для ресурса описания оснастки (необязательно).</span><span class="sxs-lookup"><span data-stu-id="3ac5d-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="3ac5d-122">В этом примере ресурсом поставщика является «GetProcPSSnapIn01, это оснастка Windows PowerShell, которая регистрирует командлет Get-proc».</span><span class="sxs-lookup"><span data-stu-id="3ac5d-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="3ac5d-123">Пример</span><span class="sxs-lookup"><span data-stu-id="3ac5d-123">Example</span></span>

<span data-ttu-id="3ac5d-124">В этом примере показано, как создать оснастку Windows PowerShell, которая может использоваться для регистрации командлета Get-proc в оболочке Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3ac5d-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="3ac5d-125">Имейте в виду, что в этом примере полная сборка будет содержать только класс оснастки GetProcPSSnapIn01 и класс командлета Get-proc.</span><span class="sxs-lookup"><span data-stu-id="3ac5d-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="3ac5d-126">См. также:</span><span class="sxs-lookup"><span data-stu-id="3ac5d-126">See Also</span></span>

[<span data-ttu-id="3ac5d-127">Регистрация командлетов, поставщиков и ведущих приложений</span><span class="sxs-lookup"><span data-stu-id="3ac5d-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="3ac5d-128">Пакет SDK оболочки Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ac5d-128">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)