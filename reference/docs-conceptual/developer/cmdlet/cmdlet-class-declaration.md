---
title: Объявление класса командлета | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 979025ad5c34ab73dcc23d0e38ffb9acc431f15a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363523"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="aab3b-102">Объявление класса командлета</span><span class="sxs-lookup"><span data-stu-id="aab3b-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="aab3b-103">Класс Microsoft .NET Framework объявляется как командлет, указывая атрибут **командлета** в качестве метаданных для класса.</span><span class="sxs-lookup"><span data-stu-id="aab3b-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="aab3b-104">(Атрибут **командлета** является единственным обязательным атрибутом для всех командлетов).</span><span class="sxs-lookup"><span data-stu-id="aab3b-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="aab3b-105">При указании атрибута **командлета** необходимо указать пару глагол-существительное, которая идентифицирует командлет для пользователя.</span><span class="sxs-lookup"><span data-stu-id="aab3b-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="aab3b-106">И необходимо описать функциональные возможности Windows PowerShell, поддерживаемые командлетом.</span><span class="sxs-lookup"><span data-stu-id="aab3b-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="aab3b-107">Дополнительные сведения о синтаксисе объявления, который используется для указания атрибута **командлета** , см. в разделе [объявление атрибута командлета](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="aab3b-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="aab3b-108">Атрибут **командлета** определяется классом [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .</span><span class="sxs-lookup"><span data-stu-id="aab3b-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="aab3b-109">Свойства этого класса соответствуют параметрам объявления, которые используются при объявлении атрибута.</span><span class="sxs-lookup"><span data-stu-id="aab3b-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="aab3b-110">Существительные</span><span class="sxs-lookup"><span data-stu-id="aab3b-110">Nouns</span></span>

<span data-ttu-id="aab3b-111">Существительное командлет задает ресурсы, с которыми работает командлет.</span><span class="sxs-lookup"><span data-stu-id="aab3b-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="aab3b-112">Существительное отличает командлеты от других командлетов.</span><span class="sxs-lookup"><span data-stu-id="aab3b-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="aab3b-113">Существительные в именах командлетов должны быть специфичными, а в случае универсальных существительных, таких как *Server*, лучше добавить короткий префикс, который отличает ресурс от других аналогичных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="aab3b-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="aab3b-114">Например, имя командлета, включающее существительное с префиксом, — `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="aab3b-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="aab3b-115">Сочетание определенного существительного с более общей командой позволяет пользователю быстро найти командлет по его действию, а затем указать командлет по его ресурсу, избегая дублирования имени командлета.</span><span class="sxs-lookup"><span data-stu-id="aab3b-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="aab3b-116">Список специальных символов, которые нельзя использовать в именах командлетов, см. в разделе [необходимые рекомендации по разработке](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="aab3b-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="aab3b-117">Команды</span><span class="sxs-lookup"><span data-stu-id="aab3b-117">Verbs</span></span>

<span data-ttu-id="aab3b-118">При указании глагола руководство по разработке требует использования одной из предопределенных команд, предоставляемых Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aab3b-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="aab3b-119">Используя одну из этих предопределенных команд, вы обеспечите согласованность между написанными командлетами и командлетами, написанными корпорацией Майкрософт и другими пользователями.</span><span class="sxs-lookup"><span data-stu-id="aab3b-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="aab3b-120">Например, команда Get используется для командлетов, извлекающих данные.</span><span class="sxs-lookup"><span data-stu-id="aab3b-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="aab3b-121">Дополнительные сведения о рекомендациях для глаголов см. в разделе [имена глаголов командлетов](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="aab3b-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="aab3b-122">Список специальных символов, которые нельзя использовать в именах командлетов, см. в разделе [необходимые рекомендации по разработке](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="aab3b-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="aab3b-123">Поддержка функций Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="aab3b-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="aab3b-124">Атрибут **командлета** также позволяет указать, что командлет поддерживает некоторые общие функциональные возможности, предоставляемые Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aab3b-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="aab3b-125">Сюда входит поддержка общих функциональных возможностей, таких как подтверждение отзывов пользователей (Эта функция называется поддержкой функции ShouldProcess) и поддержка транзакций.</span><span class="sxs-lookup"><span data-stu-id="aab3b-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="aab3b-126">(Поддержка транзакций была представлена в Windows PowerShell 2,0).</span><span class="sxs-lookup"><span data-stu-id="aab3b-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="aab3b-127">Дополнительные сведения о синтаксисе объявления, который используется для указания атрибута **командлета** , см. в разделе [объявление атрибута командлета](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="aab3b-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="aab3b-128">Определение класса командлета</span><span class="sxs-lookup"><span data-stu-id="aab3b-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="aab3b-129">Следующий код является определением для класса командлета proc.</span><span class="sxs-lookup"><span data-stu-id="aab3b-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="aab3b-130">Обратите внимание, что используется регистр Pascal, а имя класса включает глагол и существительное командлета.</span><span class="sxs-lookup"><span data-stu-id="aab3b-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="aab3b-131">Регистр символов в стиле Pascal</span><span class="sxs-lookup"><span data-stu-id="aab3b-131">Pascal Casing</span></span>

<span data-ttu-id="aab3b-132">При именовании командлетов используйте регистр символов в стиле Pascal.</span><span class="sxs-lookup"><span data-stu-id="aab3b-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="aab3b-133">Например, командлеты `Get-Item` и `Get-ItemProperty` показывают правильный способ использования прописных букв при именовании командлетов.</span><span class="sxs-lookup"><span data-stu-id="aab3b-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="aab3b-134">См. также:</span><span class="sxs-lookup"><span data-stu-id="aab3b-134">See Also</span></span>

[<span data-ttu-id="aab3b-135">System. Management. Automation. CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="aab3b-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="aab3b-136">Объявление CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="aab3b-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="aab3b-137">Имена команд командлета</span><span class="sxs-lookup"><span data-stu-id="aab3b-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="aab3b-138">Запись командлета Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="aab3b-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="aab3b-139">Пакет SDK для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="aab3b-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)