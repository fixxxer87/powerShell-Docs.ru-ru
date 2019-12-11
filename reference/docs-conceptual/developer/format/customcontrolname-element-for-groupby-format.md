---
title: Элемент Кустомконтролнаме для GroupBy (Format) | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368883"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="37c40-102">Элемент CustomControlName для элемента GroupBy (формат)</span><span class="sxs-lookup"><span data-stu-id="37c40-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="37c40-103">Задает имя пользовательского элемента управления, используемого для вывода новой группы.</span><span class="sxs-lookup"><span data-stu-id="37c40-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="37c40-104">Этот элемент используется при определении представления таблицы, списка, расширенного или пользовательского элемента управления.</span><span class="sxs-lookup"><span data-stu-id="37c40-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="37c40-105">Элемент конфигурации (Format) Виевдефинитионс элемент (Format) элемент представления (Format) элемент GroupBy для элемента представления (Format) Кустомконтролнаме в GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="37c40-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="37c40-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="37c40-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="37c40-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="37c40-107">Attributes and Elements</span></span>

<span data-ttu-id="37c40-108">В следующих разделах описываются атрибуты, дочерние элементы и родительские элементы элемента `CustomControlName`.</span><span class="sxs-lookup"><span data-stu-id="37c40-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="37c40-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="37c40-109">Attributes</span></span>

<span data-ttu-id="37c40-110">Нет.</span><span class="sxs-lookup"><span data-stu-id="37c40-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="37c40-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="37c40-111">Child Elements</span></span>

<span data-ttu-id="37c40-112">Нет.</span><span class="sxs-lookup"><span data-stu-id="37c40-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="37c40-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="37c40-113">Parent Elements</span></span>

|<span data-ttu-id="37c40-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="37c40-114">Element</span></span>|<span data-ttu-id="37c40-115">Описание</span><span class="sxs-lookup"><span data-stu-id="37c40-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37c40-116">Элемент GroupBy для представления (формат)</span><span class="sxs-lookup"><span data-stu-id="37c40-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="37c40-117">Определяет, как Windows PowerShell отображает новую группу объектов.</span><span class="sxs-lookup"><span data-stu-id="37c40-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="37c40-118">Текстовое значение</span><span class="sxs-lookup"><span data-stu-id="37c40-118">Text Value</span></span>

<span data-ttu-id="37c40-119">Укажите имя пользовательского элемента управления, используемого для вывода новой группы.</span><span class="sxs-lookup"><span data-stu-id="37c40-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="37c40-120">Замечания</span><span class="sxs-lookup"><span data-stu-id="37c40-120">Remarks</span></span>

<span data-ttu-id="37c40-121">Можно создавать стандартные элементы управления, которые могут использоваться всеми представлениями файла форматирования, а также создавать элементы управления представления, которые могут использоваться в определенном представлении.</span><span class="sxs-lookup"><span data-stu-id="37c40-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="37c40-122">Следующие элементы определяют имена этих настраиваемых элементов управления:</span><span class="sxs-lookup"><span data-stu-id="37c40-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="37c40-123">Элемент Name для элемента управления для элементов управления Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="37c40-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="37c40-124">Элемент Name для элемента управления для элементов управления в представлении (формат)</span><span class="sxs-lookup"><span data-stu-id="37c40-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="37c40-125">См. также:</span><span class="sxs-lookup"><span data-stu-id="37c40-125">See Also</span></span>

[<span data-ttu-id="37c40-126">Элемент GroupBy для представления (формат)</span><span class="sxs-lookup"><span data-stu-id="37c40-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="37c40-127">Элемент Name для элемента управления для элементов управления Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="37c40-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="37c40-128">Элемент Name для элемента управления для элементов управления в представлении (формат)</span><span class="sxs-lookup"><span data-stu-id="37c40-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="37c40-129">Написание файла форматирования PowerShell</span><span class="sxs-lookup"><span data-stu-id="37c40-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)