---
title: Пример GetProcessSample04 | Документация Майкрософт
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365713"
---
# <a name="getprocesssample04-sample"></a><span data-ttu-id="da334-102">Пример командлета GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="da334-102">GetProcessSample04 Sample</span></span>

<span data-ttu-id="da334-103">В этом примере показано, как реализовать командлет, который получает процессы на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="da334-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="da334-104">Она создает неустранимую ошибку в случае возникновения ошибки при получении процесса.</span><span class="sxs-lookup"><span data-stu-id="da334-104">It generates a nonterminating error if an error occurs while retrieving a process.</span></span> <span data-ttu-id="da334-105">Этот командлет является упрощенной версией командлета `Get-Process`, предоставляемого Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="da334-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="da334-106">Как создать пример с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da334-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="da334-107">С установленным пакетом SDK для Windows PowerShell 2,0 перейдите в папку GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="da334-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample04 folder.</span></span> <span data-ttu-id="da334-108">Расположение по умолчанию — C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="da334-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span></span>

2. <span data-ttu-id="da334-109">Дважды щелкните значок файла решения (SLN).</span><span class="sxs-lookup"><span data-stu-id="da334-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="da334-110">Откроется пример проекта в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da334-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="da334-111">В меню **Сборка** выберите пункт **построить решение**.</span><span class="sxs-lookup"><span data-stu-id="da334-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="da334-112">Библиотека для образца будет построена в папках \bin или \bin\Debug по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="da334-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="da334-113">Запуск примера</span><span class="sxs-lookup"><span data-stu-id="da334-113">How to run the sample</span></span>

1. <span data-ttu-id="da334-114">Создайте следующую папку модуля:</span><span class="sxs-lookup"><span data-stu-id="da334-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. <span data-ttu-id="da334-115">Скопируйте пример сборки в папку Module.</span><span class="sxs-lookup"><span data-stu-id="da334-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="da334-116">Запустите Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da334-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="da334-117">Выполните следующую команду, чтобы загрузить сборку в Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="da334-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample04`

5. <span data-ttu-id="da334-118">Выполните следующую команду, чтобы запустить командлет:</span><span class="sxs-lookup"><span data-stu-id="da334-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="da334-119">Требования</span><span class="sxs-lookup"><span data-stu-id="da334-119">Requirements</span></span>

<span data-ttu-id="da334-120">Для работы с этим образцом требуется Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="da334-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="da334-121">Демонстрирующее</span><span class="sxs-lookup"><span data-stu-id="da334-121">Demonstrates</span></span>

<span data-ttu-id="da334-122">В этом образце демонстрируется следующее.</span><span class="sxs-lookup"><span data-stu-id="da334-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="da334-123">Объявление класса командлета с помощью атрибута командлета.</span><span class="sxs-lookup"><span data-stu-id="da334-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="da334-124">Объявление параметра командлета с помощью атрибута Parameter.</span><span class="sxs-lookup"><span data-stu-id="da334-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="da334-125">Указание расположения параметра.</span><span class="sxs-lookup"><span data-stu-id="da334-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="da334-126">Указание того, что параметр принимает входные данные из конвейера.</span><span class="sxs-lookup"><span data-stu-id="da334-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="da334-127">Входные данные могут быть взяты из объекта или значения из свойства объекта, имя свойства которого совпадает с именем параметра.</span><span class="sxs-lookup"><span data-stu-id="da334-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="da334-128">Объявление атрибута проверки для входных параметров.</span><span class="sxs-lookup"><span data-stu-id="da334-128">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="da334-129">Перехват незавершающей ошибки и запись сообщения об ошибке в поток ошибок.</span><span class="sxs-lookup"><span data-stu-id="da334-129">Trapping a nonterminating error and writing an error message to the error stream.</span></span>

## <a name="example"></a><span data-ttu-id="da334-130">Пример</span><span class="sxs-lookup"><span data-stu-id="da334-130">Example</span></span>

<span data-ttu-id="da334-131">В этом примере показано, как создать командлет, который обрабатывает неустранимые ошибки и записывает сообщения об ошибках в поток ошибок.</span><span class="sxs-lookup"><span data-stu-id="da334-131">This sample shows how to create a cmdlet that handles nonterminating errors and writes error messages to the error stream.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes specified by the Name
      /// parameter. Then, the WriteObject method writes the
      /// associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
              {
                  Process[] processes;

                  try
                  {
                      processes = Process.GetProcessesByName(name);
                  }
                  catch (InvalidOperationException ex)
                  {
                      WriteError(new ErrorRecord(
                         ex,
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="da334-132">См. также:</span><span class="sxs-lookup"><span data-stu-id="da334-132">See Also</span></span>

[<span data-ttu-id="da334-133">Запись командлета Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="da334-133">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)