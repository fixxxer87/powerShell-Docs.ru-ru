---
ms.date: 06/12/2017
keywords: dsc,powershell,конфигурация,установка
title: Метод PerformRequiredConfigurationChecks
ms.openlocfilehash: 909e3a48d08e0220ab0efc6a03bea7ead5d9843e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2019
ms.locfileid: "71955011"
---
# <a name="performrequiredconfigurationchecks-method"></a><span data-ttu-id="95645-103">Метод PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="95645-103">PerformRequiredConfigurationChecks method</span></span>

<span data-ttu-id="95645-104">Запускает проверку согласованности с помощью планировщика заданий.</span><span class="sxs-lookup"><span data-stu-id="95645-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="95645-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="95645-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="95645-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="95645-106">Parameters</span></span>

<span data-ttu-id="95645-107">*Flags* \[in\] Битовая маска, определяющая тип выполняемой проверки согласованности.</span><span class="sxs-lookup"><span data-stu-id="95645-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="95645-108">Допустимы следующие значения, которые можно объединить с помощью битовой операции **OR**:</span><span class="sxs-lookup"><span data-stu-id="95645-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="95645-109">Значение</span><span class="sxs-lookup"><span data-stu-id="95645-109">Value</span></span> |<span data-ttu-id="95645-110">Описание</span><span class="sxs-lookup"><span data-stu-id="95645-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="95645-111">**1**</span><span class="sxs-lookup"><span data-stu-id="95645-111">**1**</span></span> | <span data-ttu-id="95645-112">Обычная проверка согласованности.</span><span class="sxs-lookup"><span data-stu-id="95645-112">A normal consistency check.</span></span> |
|<span data-ttu-id="95645-113">**2**</span><span class="sxs-lookup"><span data-stu-id="95645-113">**2**</span></span> | <span data-ttu-id="95645-114">Продолжение проверки согласованности после перезагрузки.</span><span class="sxs-lookup"><span data-stu-id="95645-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="95645-115">Это значение не следует использовать в сочетании с другими значениями.</span><span class="sxs-lookup"><span data-stu-id="95645-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="95645-116">**4**</span><span class="sxs-lookup"><span data-stu-id="95645-116">**4**</span></span> | <span data-ttu-id="95645-117">Конфигурация должна извлекаться с запрашивающего сервера, указанного в метаконфигурации для узла.</span><span class="sxs-lookup"><span data-stu-id="95645-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="95645-118">Это значение следует всегда использовать в сочетании с **1**, если указано значение **5**.</span><span class="sxs-lookup"><span data-stu-id="95645-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="95645-119">**8**</span><span class="sxs-lookup"><span data-stu-id="95645-119">**8**</span></span> | <span data-ttu-id="95645-120">Состояние отправки на сервер отчетов.</span><span class="sxs-lookup"><span data-stu-id="95645-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="95645-121">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="95645-121">Return value</span></span>

<span data-ttu-id="95645-122">Возвращает нуль в случае успешного выполнения; в противном случае возвращает код ошибки.</span><span class="sxs-lookup"><span data-stu-id="95645-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="95645-123">Замечания</span><span class="sxs-lookup"><span data-stu-id="95645-123">Remarks</span></span>

<span data-ttu-id="95645-124">Это статический метод.</span><span class="sxs-lookup"><span data-stu-id="95645-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="95645-125">Требования</span><span class="sxs-lookup"><span data-stu-id="95645-125">Requirements</span></span>

<span data-ttu-id="95645-126">**MOF-файл:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="95645-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="95645-127">**Пространство имен**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="95645-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="95645-128">См. также:</span><span class="sxs-lookup"><span data-stu-id="95645-128">See also</span></span>

[<span data-ttu-id="95645-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="95645-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)