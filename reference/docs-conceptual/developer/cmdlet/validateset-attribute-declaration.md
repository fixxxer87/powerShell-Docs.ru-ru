---
title: Объявление атрибута "Validate" | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364283"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="ff8da-102">Объявление атрибута ValidateSet</span><span class="sxs-lookup"><span data-stu-id="ff8da-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="ff8da-103">Атрибут Валидатесетаттрибуте задает набор возможных значений для аргумента параметра командлета.</span><span class="sxs-lookup"><span data-stu-id="ff8da-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="ff8da-104">Этот атрибут также может использоваться функциями Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ff8da-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="ff8da-105">Если этот атрибут указан, среда выполнения Windows PowerShell определяет, соответствует ли переданный аргумент параметру командлета элементу в указанном наборе элементов.</span><span class="sxs-lookup"><span data-stu-id="ff8da-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="ff8da-106">Командлет выполняется, только если аргумент параметра соответствует элементу в наборе.</span><span class="sxs-lookup"><span data-stu-id="ff8da-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="ff8da-107">Если совпадений не найдено, среда выполнения Windows PowerShell выдает ошибку.</span><span class="sxs-lookup"><span data-stu-id="ff8da-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="ff8da-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ff8da-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="ff8da-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="ff8da-109">Parameters</span></span>

<span data-ttu-id="ff8da-110">требуется `ValidValues` ([System. String](/dotnet/api/System.String)).</span><span class="sxs-lookup"><span data-stu-id="ff8da-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="ff8da-111">Указывает допустимые значения элементов параметров.</span><span class="sxs-lookup"><span data-stu-id="ff8da-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="ff8da-112">В следующем примере показано, как указать один элемент или несколько элементов.</span><span class="sxs-lookup"><span data-stu-id="ff8da-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="ff8da-113">`IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)) необязательный именованный параметр.</span><span class="sxs-lookup"><span data-stu-id="ff8da-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="ff8da-114">Значение по умолчанию `true` указывает, что регистр игнорируется.</span><span class="sxs-lookup"><span data-stu-id="ff8da-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="ff8da-115">Значение `false` делает командлет с учетом регистра.</span><span class="sxs-lookup"><span data-stu-id="ff8da-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff8da-116">Замечания</span><span class="sxs-lookup"><span data-stu-id="ff8da-116">Remarks</span></span>

- <span data-ttu-id="ff8da-117">Этот атрибут можно использовать только один раз для каждого параметра.</span><span class="sxs-lookup"><span data-stu-id="ff8da-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="ff8da-118">Если значение параметра является массивом, каждый элемент массива должен соответствовать элементу набора атрибутов.</span><span class="sxs-lookup"><span data-stu-id="ff8da-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="ff8da-119">Атрибут Валидатесетаттрибуте определяется классом [System. Management. Automation. валидатесетаттрибуте](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .</span><span class="sxs-lookup"><span data-stu-id="ff8da-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff8da-120">См. также:</span><span class="sxs-lookup"><span data-stu-id="ff8da-120">See Also</span></span>

[<span data-ttu-id="ff8da-121">System. Management. Automation. Валидатесетаттрибуте</span><span class="sxs-lookup"><span data-stu-id="ff8da-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="ff8da-122">Запись командлета Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff8da-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)