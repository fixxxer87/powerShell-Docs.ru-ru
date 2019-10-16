---
title: Синтаксис справки на основе комментариев | Документация Майкрософт
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367763"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="0ef9b-102">Синтаксис справки на основе комментариев</span><span class="sxs-lookup"><span data-stu-id="0ef9b-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="0ef9b-103">В этом разделе описывается синтаксис справки на основе комментариев.</span><span class="sxs-lookup"><span data-stu-id="0ef9b-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="0ef9b-104">Схема синтаксиса</span><span class="sxs-lookup"><span data-stu-id="0ef9b-104">Syntax Diagram</span></span>

 <span data-ttu-id="0ef9b-105">Синтаксис для справки на основе комментариев выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0ef9b-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="0ef9b-106">Описание синтаксиса</span><span class="sxs-lookup"><span data-stu-id="0ef9b-106">Syntax Description</span></span>

 <span data-ttu-id="0ef9b-107">Справка на основе комментариев записывается в виде набора комментариев.</span><span class="sxs-lookup"><span data-stu-id="0ef9b-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="0ef9b-108">Можно ввести символ комментария (#) перед каждой строкой комментариев или использовать символы "\< #" и "# >" для создания блока комментариев.</span><span class="sxs-lookup"><span data-stu-id="0ef9b-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="0ef9b-109">Все строки внутри блока комментариев обрабатываются как комментарии.</span><span class="sxs-lookup"><span data-stu-id="0ef9b-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="0ef9b-110">Каждый раздел справки на основе комментариев определяется по ключевому слову, и каждому ключевому слову предшествует точка (.).</span><span class="sxs-lookup"><span data-stu-id="0ef9b-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="0ef9b-111">Ключевые слова могут отображаться в любом порядке.</span><span class="sxs-lookup"><span data-stu-id="0ef9b-111">The keywords can appear in any order.</span></span> <span data-ttu-id="0ef9b-112">Имена ключевых слов не учитывают регистр.</span><span class="sxs-lookup"><span data-stu-id="0ef9b-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="0ef9b-113">Блок комментариев должен содержать по крайней мере одно ключевое слово справки.</span><span class="sxs-lookup"><span data-stu-id="0ef9b-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="0ef9b-114">Некоторые ключевые слова, такие как EXAMPLE, могут встречаться много раз в одном блоке комментариев.</span><span class="sxs-lookup"><span data-stu-id="0ef9b-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="0ef9b-115">Содержимое справки для каждого ключевого слова начинается в строке после ключевого слова и может охватывать несколько строк.</span><span class="sxs-lookup"><span data-stu-id="0ef9b-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="0ef9b-116">Все строки в разделе справки на основе комментариев должны быть непрерывными.</span><span class="sxs-lookup"><span data-stu-id="0ef9b-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="0ef9b-117">Если раздел справки на основе комментариев следует за комментарием, который не является частью раздела справки, должна существовать хотя бы одна пустая строка между последней строкой комментария, отличной от справки, и началом справки на основе комментариев.</span><span class="sxs-lookup"><span data-stu-id="0ef9b-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="0ef9b-118">Например, следующий раздел справки на основе комментариев содержит. Ключевое слово Description и его значение, которое является описанием функции или скрипта.</span><span class="sxs-lookup"><span data-stu-id="0ef9b-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```