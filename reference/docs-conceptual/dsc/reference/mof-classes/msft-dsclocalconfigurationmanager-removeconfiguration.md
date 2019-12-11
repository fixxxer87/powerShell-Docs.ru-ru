---
ms.date: 06/12/2017
keywords: dsc,powershell,конфигурация,установка
title: Метод RemoveConfiguration
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953401"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="b67c7-103">Метод RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="b67c7-103">RemoveConfiguration method</span></span>

<span data-ttu-id="b67c7-104">Удаляет файлы конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b67c7-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="b67c7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b67c7-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="b67c7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b67c7-106">Parameters</span></span>

<span data-ttu-id="b67c7-107">*Stage* \[in\] Указывает, какой документ конфигурации необходимо удалить.</span><span class="sxs-lookup"><span data-stu-id="b67c7-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="b67c7-108">Допустимы следующие значения:</span><span class="sxs-lookup"><span data-stu-id="b67c7-108">The following values are valid:</span></span>

|<span data-ttu-id="b67c7-109">Значение</span><span class="sxs-lookup"><span data-stu-id="b67c7-109">Value</span></span> |<span data-ttu-id="b67c7-110">Описание</span><span class="sxs-lookup"><span data-stu-id="b67c7-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="b67c7-111">**1**</span><span class="sxs-lookup"><span data-stu-id="b67c7-111">**1**</span></span> | <span data-ttu-id="b67c7-112">Документ **текущей** конфигурации (current.mof).</span><span class="sxs-lookup"><span data-stu-id="b67c7-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="b67c7-113">**2**</span><span class="sxs-lookup"><span data-stu-id="b67c7-113">**2**</span></span> | <span data-ttu-id="b67c7-114">Документ **ожидающей** конфигурации (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="b67c7-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="b67c7-115">**4**</span><span class="sxs-lookup"><span data-stu-id="b67c7-115">**4**</span></span> | <span data-ttu-id="b67c7-116">Документ **предыдущей** конфигурации (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="b67c7-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="b67c7-117">*Force* \[in\] **true** для принудительного удаления конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b67c7-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="b67c7-118">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b67c7-118">Return value</span></span>

<span data-ttu-id="b67c7-119">Возвращает нуль в случае успешного выполнения; в противном случае возвращает код ошибки.</span><span class="sxs-lookup"><span data-stu-id="b67c7-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b67c7-120">Замечания</span><span class="sxs-lookup"><span data-stu-id="b67c7-120">Remarks</span></span>

<span data-ttu-id="b67c7-121">Это статический метод.</span><span class="sxs-lookup"><span data-stu-id="b67c7-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b67c7-122">Требования</span><span class="sxs-lookup"><span data-stu-id="b67c7-122">Requirements</span></span>

<span data-ttu-id="b67c7-123">**MOF-файл:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b67c7-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b67c7-124">**Пространство имен**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b67c7-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b67c7-125">См. также:</span><span class="sxs-lookup"><span data-stu-id="b67c7-125">See also</span></span>

[<span data-ttu-id="b67c7-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b67c7-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)