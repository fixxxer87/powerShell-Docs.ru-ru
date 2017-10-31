---
ms.date: 2017-06-05
keywords: "powershell,командлет"
title: "Написание и запуск сценариев в интегрированной среде сценариев Windows PowerShell"
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: dd3055df8c84195f0145b1a058f1d17c9c382f33
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Написание и запуск сценариев в интегрированной среде сценариев Windows PowerShell
Эта статья содержит инструкции по созданию, редактированию, выполнению и сохранению сценариев в области сценариев.

## <a name="how-to-create-and-run-scripts"></a>Создание и выполнение сценариев
В области скриптов можно открывать и редактировать файлы Windows PowerShell. Сейчас нас интересуют следующие типы файлов Windows PowerShell: файлы скриптов (PS1), файлы данных скриптов (PSD1) и файлы модулей скриптов (PSM1). Эти типы файлов имеют цветовую подсветку синтаксиса в редакторе области сценариев. Другие стандартные файлы, которые можно открыть в области сценариев, — это файлы конфигурации (PS1XML), XML-файлы и текстовые файлы.

> [!NOTE]
> Политика выполнения Windows PowerShell определяет, можно ли выполнять сценарии, загружать профили Windows PowerShell и файлы конфигурации. Политика выполнения по умолчанию, Restricted, запрещает выполнение сценариев и блокирует загрузку профилей. Чтобы изменить эту политику выполнения и разрешить загрузку и использование профилей, изучите статьи [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) и [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).

### <a name="to-create-a-new-script-file"></a>Создание файла сценария
Нажмите кнопку **Создать** на панели инструментов или откройте меню **Файл** и выберите пункт **Создать**. Созданный файл появится в новой вкладке, расположенной под текущей вкладкой PowerShell. Помните, что вкладки PowerShell отображаются, только если их несколько. По умолчанию создается файл сценария (PS1), но его можно сохранить с новым именем и расширением. На одной вкладке PowerShell может быть создано несколько файлов сценариев.

### <a name="to-open-an-existing-script"></a>Открытие существующего сценария
Нажмите кнопку **Открыть...** на панели инструментов или откройте меню **Файл** и выберите пункт **Открыть**. В диалоговом окне **Открыть** выберите файл, который требуется открыть. Открытый файл появится в новой вкладке.

### <a name="to-close-a-script-tab"></a>Закрытие вкладки сценария
Щелкните вкладку того сценария, который нужно закрыть, а затем выполните одно из следующих действий:

1. щелкните значок **Закрыть** (X) на вкладке сценария;

2. выберите пункт **Закрыть** в меню **Файл**.

Если файл был изменен с момента последнего сохранения, будет предложено сохранить или отменить изменения.

### <a name="to-display-the-file-path"></a>Отображение пути к файлу
На вкладке файла наведите курсор на его имя. Появится подсказка с полным путем к файлу сценария.

### <a name="to-run-a-script"></a>Запуск сценария
Нажмите кнопку **Выполнить сценарий** на панели инструментов или откройте меню **Файл** и выберите пункт **Выполнить**.

### <a name="to-run-a-portion-of-a-script"></a>Выполнение части сценария

1. Выберите часть сценария в области сценариев.

2. Нажмите кнопку **Выполнить выделенный фрагмент** на панели инструментов или откройте меню **Файл** и выберите пункт **Выполнить выделенный фрагмент**.

### <a name="to-stop-a-running-script"></a>Остановка выполняемого сценария
Нажмите кнопку **Остановить операцию** на панели инструментов, нажмите клавиши CTRL+BREAK или выберите пункт **Остановить операцию** в меню **Файл**. Нажатие клавиш **CTRL+C** также сработает, если нет выделенного текста. В противном случае нажатие клавиш **CTRL+C** приведет к копированию выделенного текста.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Написание и редактирование текста в области сценариев
Для редактирования текста в области сценариев выполните описанные ниже действия. Текст можно копировать, вырезать, вставлять, искать и заменять. Также можно отменить и повторить последнее выполненное действие. Для этого используются такие же сочетания клавиш, как и во всех других приложениях Windows.

### <a name="to-enter-text-in-the-script-pane"></a>Ввод текста в области сценариев

1. Установите курсор в область сценариев, щелкнув кнопкой мыши любую ее часть или выбрав пункт **Перейти в область сценариев** в меню **Вид**.

2. Создайте сценарий. Цветовая подсветка синтаксиса и заполнение нажатием клавиши TAB делают эту задачу гораздо проще в интегрированной среде сценариев Windows PowerShell.

3. Подробную информацию о заполнении нажатием клавиши TAB, помогающем при вводе кода, см. в статье [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) (Использование заполнения нажатием клавиши TAB в областях сценариев и консоли).

### <a name="to-find-text-in-the-script-pane"></a>Поиск текста в области сценариев

1. Чтобы найти текст в любой части сценария, нажмите клавиши **CTRL+F** или выберите **Найти в сценарии** в меню **Правка**.

2. Чтобы найти текст после курсора, нажмите клавишу **F3** или выберите **Найти следующее в сценарии** в меню **Правка**.

3. Чтобы найти текст до курсора, нажмите клавиши **SHIFT+F3** или выберите **Find Previous in Script** (Найти предыдущее в сценарии) в меню **Правка**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Поиск и замена текста в области сценариев
Нажмите клавиши **CRTL+H** или выберите **Replace in Script** (Заменить в сценарии) в меню **Правка**. Введите искомый текст и текст, которым его нужно заменить, а затем нажмите клавишу **ВВОД**.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Переход к определенной строке текста в области сценариев

1. В области сценариев нажмите клавиши **CTRL+G** или выберите **Перейти к строке** в меню **Правка**.

2. Введите номер строки.

### <a name="to-copy-text-in-the-script-pane"></a>Копирование текста в области сценариев

1. В области сценариев выделите текст, который требуется скопировать.

2. Нажмите клавиши **CTRL+C**, щелкните значок **Копировать** на панели инструментов или выберите **Копировать** в меню **Правка**.

### <a name="to-cut-text-in-the-script-pane"></a>Вырезание текста в области сценариев

1. В области сценариев выделите текст, который требуется вырезать.

2. Нажмите клавиши **CTRL+X**, щелкните значок **Вырезать** на панели инструментов или выберите **Вырезать** в меню **Правка**.

### <a name="to-paste-text-into-the-script-pane"></a>Вставка текста в области сценариев
Нажмите клавиши **CTRL+V**, щелкните значок **Вставить** на панели инструментов или выберите **Вставить** в меню **Правка**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Отмена действия в области сценариев
Нажмите клавиши **CTRL+Z**, щелкните значок **Отменить** на панели инструментов или выберите **Отменить** в меню **Правка**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Повторное выполнение действия в области сценариев
Нажмите клавиши **CTRL+Y**, щелкните значок **Повторить** на панели инструментов или выберите **Повторить** в меню **Правка**.

## <a name="how-to-save-a-script"></a>Сохранение сценария
Используйте следующую процедуру, чтобы сохранить и назвать сценарий. Звездочка рядом с именем сценария обозначает, что файл не был сохранен после изменения. После сохранения звездочка исчезает.

### <a name="to-save-a-script"></a>Сохранение сценария
Нажмите клавиши **CTRL+S**, щелкните значок **Сохранить** на панели инструментов или выберите **Сохранить** в меню **Файл**.

### <a name="to-save-and-name-a-script"></a>Сохранение сценария с определенным именем

1. В меню **Файл** выберите команду **Сохранить как**. Появится диалоговое окно **Сохранить как**.

2. В поле **Имя файла** введите имя файла.

3. В поле **Тип файла** выберите тип файла. Например, в поле **Тип файла** выберите "Сценарии PowerShell (\* .ps1)".

4. Нажмите кнопку **Сохранить**.

### <a name="to-save-a-script-in-ascii-encoding"></a>Сохранение сценария в кодировке ASCII
По умолчанию интегрированная среда сценариев Windows PowerShell сохраняет новые файлы сценариев (PS1), файлы данных сценариев (PSD1) и файлы модулей сценариев (PSM1) в кодировке Юникод (BigEndianUnicode). Чтобы сохранить сценарий в другой кодировке, например ASCII (ANSI), используйте методы **Сохранить** или **Сохранить как** объекта [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile).

Следующая команда сохраняет новый сценарий в кодировке ASCII и с именем MyScript.ps1:

```
$psise.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

Следующая команда заменяет текущий файл сценария на файл с таким же именем, но в кодировке ASCII:

```
$psise.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

Следующая команда возвращает кодировку текущего файла:

```
$psise.CurrentFile.encoding
```

Интегрированная среда сценариев Windows PowerShell поддерживает следующие параметры кодировки: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 и Default. Значение параметра Default зависит от системы.

Интегрированная среда сценариев Windows PowerShell не изменяет кодировку сценариев, созданных в других редакторах, даже при использовании команд "Сохранить" или "Сохранить как" в интегрированной среде сценариев Windows PowerShell.

## <a name="see-also"></a>См. также
- [Использование интегрированной среды сценариев Windows PowerShell](Using-the-Windows-PowerShell-ISE.md)
