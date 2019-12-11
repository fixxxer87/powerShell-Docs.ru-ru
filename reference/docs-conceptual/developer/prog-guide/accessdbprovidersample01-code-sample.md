---
title: Пример кода AccessDbProviderSample01 | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 22cfbc63bd369ebcb2fd8a0d0e8d1995941bbb0f
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/23/2019
ms.locfileid: "74418002"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="6eab7-102">Пример кода AccessDbProviderSample01</span><span class="sxs-lookup"><span data-stu-id="6eab7-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="6eab7-103">В следующем коде показана реализация поставщика Windows PowerShell, описанного в статье [Создание базового поставщика Windows PowerShell](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="6eab7-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="6eab7-104">Эта реализация предоставляет методы для запуска и остановки поставщика, хотя он не предоставляет средства для доступа к хранилищу данных или для получения или установки данных в хранилище данных, он предоставляет базовые функциональные возможности, необходимые для всех поставщиков.</span><span class="sxs-lookup"><span data-stu-id="6eab7-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="6eab7-105">C# Исходный файл (AccessDBSampleProvider01.cs) для этого поставщика можно скачать с помощью пакета средств разработки программного обеспечения Windows для компонентов среды выполнения Windows Vista и Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="6eab7-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6eab7-106">Инструкции по загрузке см. в статье [Установка Windows PowerShell и Загрузка пакета SDK для Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="6eab7-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="6eab7-107">Скачанные исходные файлы доступны в **\<примеров PowerShell >** Directory.</span><span class="sxs-lookup"><span data-stu-id="6eab7-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="6eab7-108">Дополнительные сведения о других реализациях поставщиков Windows PowerShell см. в разделе [Разработка поставщика Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="6eab7-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="6eab7-109">Пример кода</span><span class="sxs-lookup"><span data-stu-id="6eab7-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="6eab7-110">См. также</span><span class="sxs-lookup"><span data-stu-id="6eab7-110">See Also</span></span>

[<span data-ttu-id="6eab7-111">Руководством программиста Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6eab7-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="6eab7-112">Пакет SDK для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6eab7-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)