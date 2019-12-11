---
title: Создание справки по командлетам PowerShell | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361073"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="02961-102">Написание справки по командлетам PowerShell</span><span class="sxs-lookup"><span data-stu-id="02961-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="02961-103">Командлеты PowerShell могут быть полезными, но если в разделах справки не ясно объясняется, что делает командлет и как его использовать, командлет может не использовать или, что еще хуже, может привести к невозможности разочарования пользователей.</span><span class="sxs-lookup"><span data-stu-id="02961-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="02961-104">Формат файлов справки по командлетам на основе XML повышает согласованность, но для получения отличной справки требуется гораздо больше.</span><span class="sxs-lookup"><span data-stu-id="02961-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="02961-105">Если вы никогда не написали справку по командлетам, ознакомьтесь со следующими рекомендациями.</span><span class="sxs-lookup"><span data-stu-id="02961-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="02961-106">Схема XML, необходимая для создания раздела справки по командлету, описана в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="02961-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="02961-107">Начните с [создания файла справки по командлету](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="02961-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="02961-108">Этот раздел включает описание XML-узлов верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="02961-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="02961-109">Рекомендации по написанию справки по командлетам</span><span class="sxs-lookup"><span data-stu-id="02961-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="02961-110">Запись хорошо</span><span class="sxs-lookup"><span data-stu-id="02961-110">Write well</span></span>
<span data-ttu-id="02961-111">Ничего не заменяет хорошо написанный раздел.</span><span class="sxs-lookup"><span data-stu-id="02961-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="02961-112">Если вы не являетесь профессиональным средством записи, найдите средство записи или редактор, которые помогут вам.</span><span class="sxs-lookup"><span data-stu-id="02961-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="02961-113">Другой вариант — скопировать текст справки в Microsoft Word и использовать проверки грамматики и орфографии для улучшения работы.</span><span class="sxs-lookup"><span data-stu-id="02961-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="02961-114">Писать просто</span><span class="sxs-lookup"><span data-stu-id="02961-114">Write simply</span></span>
<span data-ttu-id="02961-115">Используйте простые слова и фразы.</span><span class="sxs-lookup"><span data-stu-id="02961-115">Use simple words and phrases.</span></span>
<span data-ttu-id="02961-116">Избегайте жаргоне.</span><span class="sxs-lookup"><span data-stu-id="02961-116">Avoid jargon.</span></span>
<span data-ttu-id="02961-117">Учтите, что многие читатели оснащены только словарем на иностранном языке и вашим разделом справки.</span><span class="sxs-lookup"><span data-stu-id="02961-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="02961-118">Согласованная запись</span><span class="sxs-lookup"><span data-stu-id="02961-118">Write consistently</span></span>
<span data-ttu-id="02961-119">Справка по связанным командлетам должна быть похожей (например, Get-x и Set-x).</span><span class="sxs-lookup"><span data-stu-id="02961-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="02961-120">Используйте стандартные описания для стандартных параметров, таких как **Force** и **InputObject**.</span><span class="sxs-lookup"><span data-stu-id="02961-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="02961-121">(Скопируйте их из справки по основным командлетам.) Используйте стандартные термины.</span><span class="sxs-lookup"><span data-stu-id="02961-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="02961-122">Например, используйте параметр "Parameter", а не "Argument" и используйте "командлет", а не "Command" или "Command-let".</span><span class="sxs-lookup"><span data-stu-id="02961-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="02961-123">Запуск краткого обзорного элемента с помощью команды</span><span class="sxs-lookup"><span data-stu-id="02961-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="02961-124">Поле «краткий обзор» информирует пользователя о том, что делает командлет, а не то, как он работает.</span><span class="sxs-lookup"><span data-stu-id="02961-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="02961-125">Команды создают инструкцию на основе задачи, которая информирует пользователей, если этот командлет соответствует требованиям.</span><span class="sxs-lookup"><span data-stu-id="02961-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="02961-126">Используйте простые команды, такие как «Get», «CREATE» и «Change».</span><span class="sxs-lookup"><span data-stu-id="02961-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="02961-127">Старайтесь избегать «Set», которые могут быть неясными и обсловными словами, например «Modify».</span><span class="sxs-lookup"><span data-stu-id="02961-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="02961-128">Сосредоточиться на объектах</span><span class="sxs-lookup"><span data-stu-id="02961-128">Focus on objects</span></span>
<span data-ttu-id="02961-129">Большинство командлетов Get отображают нечто, но их основная функция заключается в получении объекта.</span><span class="sxs-lookup"><span data-stu-id="02961-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="02961-130">В справке Сосредоточьтесь на объекте, чтобы пользователи понимали, что по умолчанию отображается один из множества и что они могут использовать методы и свойства объекта, полученные для них различными способами.</span><span class="sxs-lookup"><span data-stu-id="02961-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="02961-131">Запись подробного описания</span><span class="sxs-lookup"><span data-stu-id="02961-131">Write detailed descriptions</span></span>
<span data-ttu-id="02961-132">Кратко перечислите все, что может делать командлет в подробном описании.</span><span class="sxs-lookup"><span data-stu-id="02961-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="02961-133">Если функция Main должна изменить одно свойство, но командлет может изменить все свойства, перечислите его в подробном описании.</span><span class="sxs-lookup"><span data-stu-id="02961-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="02961-134">Использовать стандартный синтаксис</span><span class="sxs-lookup"><span data-stu-id="02961-134">Use conventional syntax</span></span>
<span data-ttu-id="02961-135">Используйте стандартный формат Backus-Наура, который часто используется для справки командной строки Windows и UNIX.</span><span class="sxs-lookup"><span data-stu-id="02961-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="02961-136">Использование Microsoft .NET типов платформы для значений параметров</span><span class="sxs-lookup"><span data-stu-id="02961-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="02961-137">Заполнители для значений параметров (в описании синтаксиса и параметров) показывают типы .NET Framework объектов, которые будет принимать параметр.</span><span class="sxs-lookup"><span data-stu-id="02961-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="02961-138">Группа разработчиков PowerShell разработала это соглашение, помогающее научить пользователей о .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="02961-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="02961-139">Описание параметров записи завершено</span><span class="sxs-lookup"><span data-stu-id="02961-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="02961-140">Описания параметров должны информировать пользователей о двух вещах: о том, что делает параметр (его результат) и о том, что они должны вводить для значений параметров.</span><span class="sxs-lookup"><span data-stu-id="02961-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="02961-141">Напишите практические примеры</span><span class="sxs-lookup"><span data-stu-id="02961-141">Write practical examples</span></span>
<span data-ttu-id="02961-142">В примерах должно быть показано, как использовать все параметры, но самое важное — продемонстрировать, как использовать командлет в реальных задачах.</span><span class="sxs-lookup"><span data-stu-id="02961-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="02961-143">Начните с простого примера и напишите все сложные примеры.</span><span class="sxs-lookup"><span data-stu-id="02961-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="02961-144">В последнем примере показано, как использовать командлет в конвейере.</span><span class="sxs-lookup"><span data-stu-id="02961-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="02961-145">Использование поля "Примечания"</span><span class="sxs-lookup"><span data-stu-id="02961-145">Use the Notes field</span></span>
<span data-ttu-id="02961-146">Используйте поле Примечания для объяснения концепций, необходимых пользователям для понимания командлета.</span><span class="sxs-lookup"><span data-stu-id="02961-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="02961-147">Также можно использовать заметки, чтобы помочь пользователям избежать распространенных ошибок.</span><span class="sxs-lookup"><span data-stu-id="02961-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="02961-148">Избегайте URL-адресов при их изменении.</span><span class="sxs-lookup"><span data-stu-id="02961-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="02961-149">Вместо этого предоставьте пользователям условия поиска.</span><span class="sxs-lookup"><span data-stu-id="02961-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="02961-150">Тестирование справки</span><span class="sxs-lookup"><span data-stu-id="02961-150">Test your Help</span></span>
<span data-ttu-id="02961-151">Протестируйте справку так же, как при тестировании кода.</span><span class="sxs-lookup"><span data-stu-id="02961-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="02961-152">Ваши друзья и коллеги читают содержимое справки и предоставляют отзывы.</span><span class="sxs-lookup"><span data-stu-id="02961-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="02961-153">Вы также можете запросить отзывы из групп новостей.</span><span class="sxs-lookup"><span data-stu-id="02961-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="02961-154">См. также:</span><span class="sxs-lookup"><span data-stu-id="02961-154">See Also</span></span>

 [<span data-ttu-id="02961-155">Создание файла справки по командлетам</span><span class="sxs-lookup"><span data-stu-id="02961-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="02961-156">Добавление имени командлета и кратких сведений в раздел справки по командлетам</span><span class="sxs-lookup"><span data-stu-id="02961-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="02961-157">Добавление подробного описания в раздел справки по командлету</span><span class="sxs-lookup"><span data-stu-id="02961-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="02961-158">Добавление синтаксиса в раздел справки по командлету</span><span class="sxs-lookup"><span data-stu-id="02961-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="02961-159">Добавление параметров в раздел справки по командлету</span><span class="sxs-lookup"><span data-stu-id="02961-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="02961-160">Добавление типов входных данных в раздел справки по командлетам</span><span class="sxs-lookup"><span data-stu-id="02961-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="02961-161">Добавление возвращаемых значений в раздел справки по командлетам</span><span class="sxs-lookup"><span data-stu-id="02961-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="02961-162">Добавление заметок в раздел справки по командлетам</span><span class="sxs-lookup"><span data-stu-id="02961-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="02961-163">Добавление примеров в раздел справки по командлетам</span><span class="sxs-lookup"><span data-stu-id="02961-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="02961-164">Добавление связанных ссылок в раздел справки по командлетам</span><span class="sxs-lookup"><span data-stu-id="02961-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="02961-165">Пакет SDK для Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="02961-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)