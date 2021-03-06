---
title: 'Обновляемая Справка по разработке: пошаговая операция | Документация Майкрософт'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366993"
---
# <a name="updatable-help-authoring-step-by-step"></a>Создание обновляемой справки: пошаговые инструкции

В этом документе перечислены этапы процесса создания обновляемой справки.

## <a name="authoring-updatable-help-step-by-step"></a>Создание обновляемой справки: пошаговое руководство

Обновляемая справка предназначена для конечных пользователей, но она также предоставляет значительные преимущества авторам модулей и средствам записи справки, включая возможность добавления содержимого, исправления ошибок, доставки в нескольких культурах пользовательского интерфейса и реагирования на комментарии и запросы пользователя, долго после модуль отправлен. В этом разделе объясняется, как упаковывать и отправлять файлы справки, чтобы пользователи могли загружать и устанавливать их с помощью командлетов [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) и [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .

В следующих шагах представлен обзор процесса поддержки обновляемой справки.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Шаг 1. Поиск веб-сайта для файлов справки

Первым шагом в создании обновляемой справки является поиск расположения в Интернете для файлов справки вашего модуля. На самом деле можно использовать два разных расположения. Файл справочной информации о модуле (HelpInfo XML) можно разместить в одном расположении в Интернете, а CAB-файлы содержимого справки — в другом расположении в Интернете. Все CAB-файлы содержимого справки для модуля должны находиться в одном расположении. Вы можете поместить CAB-файлы содержимого справки для разных модулей в одном расположении.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Шаг 2. Добавление ключа HelpInfoURI в манифест модуля

Добавьте ключ **HelpInfoURI** в манифест модуля. Значение ключа — это универсальный код ресурса (URI) расположения XML-файла данных HelpInfo для модуля. В целях безопасности адрес должен начинаться с "http" или "HTTPS". URI должен указывать расположение в Интернете, но не должно включать имя XML-файла HelpInfo.

Пример:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Шаг 3. Создание XML-файла HelpInfo

Файл сведений HelpInfo XML содержит универсальный код ресурса (URI) расположения файлов справки в Интернете и номера версий самых новых файлов справки для модуля в каждой поддерживаемой культуре пользовательского интерфейса. Каждый модуль Windows PowerShell имеет один XML-файл HelpInfo. При обновлении файлов справки вы редактируете или заменяете XML-файл HelpInfo; Вы не добавите еще одну. Дополнительные сведения см. [в разделе Создание XML-файла HelpInfo](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>Шаг 4. Подписание файлов справки

Цифровые подписи не требуются, но они являются рекомендациями при совместном использовании файлов.

### <a name="step-5-create-cab-files"></a>Шаг 5. Создание CAB-файлов

Используйте средство, которое создает CAB-файлы (например, MakeCab. exe) для создания. CAB-файл, содержащий файлы справки для модуля. Создайте отдельный CAB-файл для файлов справки в каждой поддерживаемой культуре пользовательского интерфейса. Дополнительные сведения см. [в разделе Подготовка обновляемых CAB-файлов справки](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>Шаг 6. Отправка файлов

Чтобы опубликовать новые или обновленные файлы справки, отправьте CAB-файлы в расположение в Интернете, указанное элементом **хелпконтентури** в файле HelpInfo XML. Затем отправьте XML-файл HelpInfo в расположение в Интернете, указанное значением ключа **HelpInfoUri** в манифесте модуля.
