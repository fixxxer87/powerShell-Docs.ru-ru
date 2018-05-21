---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: коллекции,powershell,командлет,psgallery
title: Элементы с совместимыми выпусками PowerShell
ms.openlocfilehash: dd2c67417994e960845f7cef09320a0f688a0212
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="items-with-compatible-powershell-editions"></a><span data-ttu-id="3744a-103">Элементы с совместимыми выпусками PowerShell</span><span class="sxs-lookup"><span data-stu-id="3744a-103">Items with compatible PowerShell Editions</span></span>

<span data-ttu-id="3744a-104">Начиная с версии 5.1 доступны различные выпуски среды PowerShell, что означает различные наборы возможностей и совместимость с разными платформами.</span><span class="sxs-lookup"><span data-stu-id="3744a-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="3744a-105">**Выпуск Desktop Edition:** построен на основе .NET Framework и обеспечивает совместимость со скриптами и модулями, которые предназначены для версий PowerShell, выполняющихся в полноценных выпусках Windows, таких как Server Core и Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="3744a-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="3744a-106">**Выпуск Core Edition:** построен на основе .NET Core и обеспечивает совместимость со скриптами и модулями, которые предназначены для версий PowerShell, выполняющихся в выпусках Windows с ограниченными возможностями, таких как Nano Server и Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="3744a-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a><span data-ttu-id="3744a-107">Коллекция PowerShell извлекает поддерживаемые метаданные PSEditions и позволяет отфильтровывать элементы, совместимые с конкретными выпусками PowerShell</span><span class="sxs-lookup"><span data-stu-id="3744a-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the items compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="3744a-108">Если элемент имеет указанные совместимые версии PSEdition, они будут перечислены в разделе "Выпуски PowerShell" на странице отображения элемента, а также в результатах элементов.</span><span class="sxs-lookup"><span data-stu-id="3744a-108">If an item has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the item display page and also in items results.</span></span>

![Страница отображения элемента с выпусками PSEdition](../../Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="3744a-110">Поиск элементов в коллекции пользовательского интерфейса, работающих в PowerShellCore</span><span class="sxs-lookup"><span data-stu-id="3744a-110">Search for items in the gallery UI which works on PowerShellCore</span></span>

<span data-ttu-id="3744a-111">Для фильтрации элементов в коллекции PowerShell используйте Tags:"PSEdition_Desktop" и Tags:"PSEdition_Core".</span><span class="sxs-lookup"><span data-stu-id="3744a-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the items on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="3744a-112">Для поиска элементов, совместимых с выпуском PowerShell Core, используйте Tags:"PSEdition_Core".</span><span class="sxs-lookup"><span data-stu-id="3744a-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Результаты поиска элементов, совместимых с Core PSEdition](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="3744a-114">Для поиска элементов, совместимых с выпуском PowerShell Desktop, используйте Tags:"PSEdition_Desktop".</span><span class="sxs-lookup"><span data-stu-id="3744a-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Результаты поиска элементов, совместимых с Desktop PSEdition](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a><span data-ttu-id="3744a-116">Дополнительные сведения о разработке и поиске элементов с совместимыми выпусками PowerShell</span><span class="sxs-lookup"><span data-stu-id="3744a-116">More details on authoring and finding the items with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="3744a-117">Модули с PSEdition</span><span class="sxs-lookup"><span data-stu-id="3744a-117">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="3744a-118">Скрипты с PSEdition</span><span class="sxs-lookup"><span data-stu-id="3744a-118">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)