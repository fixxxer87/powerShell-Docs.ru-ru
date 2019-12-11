---
ms.date: 06/12/2017
keywords: dsc,powershell,конфигурация,установка
title: Метод SendMetaConfigurationApply
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954881"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="5d2d1-103">Метод SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="5d2d1-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="5d2d1-104">Задает параметры локального диспетчера конфигураций, которые используются для управления агентом конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d2d1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5d2d1-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="5d2d1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5d2d1-106">Parameters</span></span>

<span data-ttu-id="5d2d1-107">*ConfigurationData* \[in\] Данные среды для конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="5d2d1-108">*force* \[in\] **true** для принудительной остановки конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="5d2d1-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5d2d1-109">Return value</span></span>

<span data-ttu-id="5d2d1-110">Возвращает нуль в случае успешного выполнения; в противном случае возвращает код ошибки.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d2d1-111">Замечания</span><span class="sxs-lookup"><span data-stu-id="5d2d1-111">Remarks</span></span>

<span data-ttu-id="5d2d1-112">Это статический метод.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d2d1-113">Требования</span><span class="sxs-lookup"><span data-stu-id="5d2d1-113">Requirements</span></span>

<span data-ttu-id="5d2d1-114">**MOF-файл:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5d2d1-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5d2d1-115">**Пространство имен**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5d2d1-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5d2d1-116">См. также:</span><span class="sxs-lookup"><span data-stu-id="5d2d1-116">See also</span></span>

[<span data-ttu-id="5d2d1-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5d2d1-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)