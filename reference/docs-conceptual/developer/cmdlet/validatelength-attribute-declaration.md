---
title: Объявление атрибута Валидателенгс | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: a25fa2410fcc6803563573596af1bc99052c3ffa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369183"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="79fdf-102">Объявление атрибута ValidateLength</span><span class="sxs-lookup"><span data-stu-id="79fdf-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="79fdf-103">Атрибут Валидателенгс указывает минимальное и максимальное число символов для аргумента параметра командлета.</span><span class="sxs-lookup"><span data-stu-id="79fdf-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="79fdf-104">Этот атрибут также может использоваться функциями Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="79fdf-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="79fdf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="79fdf-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="79fdf-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="79fdf-106">Parameters</span></span>

<span data-ttu-id="79fdf-107">требуется `MinLength` ([System. Int32](/dotnet/api/System.Int32)).</span><span class="sxs-lookup"><span data-stu-id="79fdf-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="79fdf-108">Указывает минимальное допустимое число символов.</span><span class="sxs-lookup"><span data-stu-id="79fdf-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="79fdf-109">требуется `MaxLength` ([System. Int32](/dotnet/api/System.Int32)).</span><span class="sxs-lookup"><span data-stu-id="79fdf-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="79fdf-110">Указывает максимально допустимое число символов.</span><span class="sxs-lookup"><span data-stu-id="79fdf-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="79fdf-111">Замечания</span><span class="sxs-lookup"><span data-stu-id="79fdf-111">Remarks</span></span>

- <span data-ttu-id="79fdf-112">Дополнительные сведения об объявлении этого атрибута см. в разделе [как объявлять правила проверки входных данных](./how-to-validate-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="79fdf-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="79fdf-113">Если этот атрибут не используется, соответствующий аргумент параметра может иметь любую длину.</span><span class="sxs-lookup"><span data-stu-id="79fdf-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="79fdf-114">Среда выполнения Windows PowerShell выдает ошибку при следующих условиях:</span><span class="sxs-lookup"><span data-stu-id="79fdf-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="79fdf-115">Если значение параметра атрибута `MaxLength` меньше значения параметра атрибута `MinLength`.</span><span class="sxs-lookup"><span data-stu-id="79fdf-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="79fdf-116">Если параметру атрибута `MaxLength` присвоено значение 0.</span><span class="sxs-lookup"><span data-stu-id="79fdf-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="79fdf-117">Если аргумент не является строкой.</span><span class="sxs-lookup"><span data-stu-id="79fdf-117">When the argument is not a string.</span></span>

- <span data-ttu-id="79fdf-118">Атрибут Валидателенгс определяется классом [System. Management. Automation. валидателенгсаттрибуте](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .</span><span class="sxs-lookup"><span data-stu-id="79fdf-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="79fdf-119">См. также:</span><span class="sxs-lookup"><span data-stu-id="79fdf-119">See Also</span></span>

[<span data-ttu-id="79fdf-120">System. Management. Automation. Валидателенгсаттрибуте</span><span class="sxs-lookup"><span data-stu-id="79fdf-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="79fdf-121">Запись командлета Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="79fdf-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)