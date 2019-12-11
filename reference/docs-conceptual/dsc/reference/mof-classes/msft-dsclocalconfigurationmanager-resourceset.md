---
ms.date: 06/12/2017
keywords: dsc,powershell,конфигурация,установка
title: Метод ResourceSet
ms.openlocfilehash: 18364027b249e502e1f0b8802d9f3e031c7b07ce
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954961"
---
# <a name="resourceset-method"></a><span data-ttu-id="c2ee5-103">Метод ResourceSet</span><span class="sxs-lookup"><span data-stu-id="c2ee5-103">ResourceSet method</span></span>

<span data-ttu-id="c2ee5-104">Напрямую вызывает метод **Set** ресурса DSC.</span><span class="sxs-lookup"><span data-stu-id="c2ee5-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="c2ee5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c2ee5-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="c2ee5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c2ee5-106">Parameters</span></span>

<span data-ttu-id="c2ee5-107">*ResourceType* \[in\] Имя вызываемого ресурса.</span><span class="sxs-lookup"><span data-stu-id="c2ee5-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="c2ee5-108">*ModuleName* \[in\] Имя модуля, содержащего вызываемый ресурс.</span><span class="sxs-lookup"><span data-stu-id="c2ee5-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="c2ee5-109">*resourceProperty* \[in\] Указывает имя свойства ресурса и его значение в хэш-таблице как ключ и значение соответственно.</span><span class="sxs-lookup"><span data-stu-id="c2ee5-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="c2ee5-110">Используйте командлет [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) для обнаружения свойств ресурсов и их типов.</span><span class="sxs-lookup"><span data-stu-id="c2ee5-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="c2ee5-111">*RebootRequired* \[out\] В выходных данных это свойство имеет значение **true**, если целевой узел необходимо перезагрузить.</span><span class="sxs-lookup"><span data-stu-id="c2ee5-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="c2ee5-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c2ee5-112">Return value</span></span>

<span data-ttu-id="c2ee5-113">Возвращает нуль в случае успешного выполнения; в противном случае возвращает код ошибки.</span><span class="sxs-lookup"><span data-stu-id="c2ee5-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c2ee5-114">Замечания</span><span class="sxs-lookup"><span data-stu-id="c2ee5-114">Remarks</span></span>

<span data-ttu-id="c2ee5-115">Это статический метод.</span><span class="sxs-lookup"><span data-stu-id="c2ee5-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c2ee5-116">Требования</span><span class="sxs-lookup"><span data-stu-id="c2ee5-116">Requirements</span></span>

<span data-ttu-id="c2ee5-117">**MOF-файл:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c2ee5-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c2ee5-118">**Пространство имен**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c2ee5-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c2ee5-119">См. также:</span><span class="sxs-lookup"><span data-stu-id="c2ee5-119">See also</span></span>

[<span data-ttu-id="c2ee5-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c2ee5-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)