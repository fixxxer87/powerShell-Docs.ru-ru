---
ms.date: 06/12/2017
contributor: JKeithB
keywords: коллекции,powershell,командлет,psgallery
title: Приступая к работе с коллекцией PowerShell
ms.openlocfilehash: ee3fe7d9c65ad1a8f9ffd2ddec0f4ce6659bc3d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328465"
---
# <a name="getting-started-with-the-powershell-gallery"></a>Начало работы с коллекцией PowerShell

PowerShell Gallery — это репозиторий пакета, который содержит скрипты, модули и ресурсы DSC, которые вы можете загрузить и использовать. Командлеты из модуля [PowerShellGet](/powershell/module/powershellget) используются для установки пакетов из коллекции PowerShell. Входить в систему для скачивания элементов из коллекции PowerShell необязательно.

> [!NOTE]
> Можно скачать пакет непосредственно из коллекции PowerShell, но делать это не рекомендуется. Дополнительные сведения см. в статье [Скачивание пакета вручную](how-to/working-with-packages/manual-download.md).

## <a name="discovering-packages-from-the-powershell-gallery"></a>Обнаружение пакетов в коллекции PowerShell

Найти пакеты в коллекции PowerShell можно при помощи элемента управления **Поиск** на [домашней странице](https://www.powershellgallery.com) коллекции PowerShell или просмотрев страницы "Модули" и "Скрипты" на странице [пакетов](https://www.powershellgallery.com/packages). Найти пакеты в коллекции PowerShell можно также при помощи командлетов [Find-Module][], [Find-DscResource] и [Find-Script][] (в зависимости от типа пакета) с параметром `-Repository PSGallery`.

Вы можете отфильтровать результаты в коллекции используя следующие параметры:

- Name
- AllVersions
- MinimumVersion
- RequiredVersion
- Tag
- Includes
- DscResource
- RoleCapability
- Команда
- Фильтр

Если вас интересуют только определенные ресурсы DSC в коллекции, выполните командлет [Find-DscResource][]. Командлет Find-DscResource возвращает сведения о ресурсах DSC, содержащихся в коллекции. Поскольку ресурсы DSC всегда являются частью модуля, вам по-прежнему потребуется выполнить командлет [Install-Module][], чтобы установить их.

## <a name="learning-about-packages-in-the-powershell-gallery"></a>Изучение пакетов в коллекции PowerShell

Когда вы нашли пакет, который вас интересует, о нем можно узнать больше. Для этого можно изучить страницу конкретного пакета в коллекции. На ней представлены все метаданные, переданные вместе с пакетом. Эти метаданные предоставляются автором пакета и не проверяются корпорацией Майкрософт. Владелец пакета привязан к учетной записи в коллекции, используемой для публикации пакета, поэтому надежнее ориентироваться на нее, а не на информацию в поле "Автор".

Если вы нашли пакет, который, по вашему мнению, опубликован с нарушениями, щелкните **Сообщить о нарушении** на странице этого пакета.

При использовании командлетов [Find-Module][] или [Find-Script][] эти данные можно доступны в возвращенном объекте PSGetModuleInfo. Например, при выполнении `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` возвращаются сведения о модуле PSReadLine, содержащемся в коллекции.

## <a name="downloading-packages-from-the-powershell-gallery"></a>Скачивание пакетов из коллекции PowerShell

При скачивании пакетов из коллекции PowerShell рекомендуется сделать следующее:

### <a name="inspect"></a>Изучение

Чтобы скачать пакет из коллекции для изучения, выполните командлет [Save-Module][] или [Save-Script][] (в зависимости от типа пакета). Так вы сможете сохранить пакет локально без установки и проверить его содержимое. Не забудьте удалить пакет, сохраненный вручную.

Некоторые из этих пакетов созданы корпорацией Майкрософт, а другие — сообществом PowerShell. Корпорация Майкрософт рекомендует ознакомиться с содержимым и кодом пакетов в этой коллекции перед их установкой.

Если вы нашли пакет, который, по вашему мнению, опубликован с нарушениями, щелкните **Сообщить о нарушении** на странице этого пакета.

### <a name="install"></a>Установка

Чтобы установить пакет из коллекции для использования, выполните командлет [Install-Module][] или [Install-Script][] (в зависимости от типа пакета).

Командлет [Install-Module][] устанавливает модуль в `$env:ProgramFiles\WindowsPowerShell\Modules` по умолчанию.
Для выполнения этой операции необходима учетная запись администратора. При добавлении параметра `-Scope CurrentUser` модуль будет установлен в каталог `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.

Командлет [Install-Script][] по умолчанию устанавливает скрипт в каталог `$env:ProgramFiles\WindowsPowerShell\Scripts`.
Для выполнения этой операции необходима учетная запись администратора. При добавлении параметра `-Scope CurrentUser` скрипт будет установлен в каталог `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.

По умолчанию командлеты [Install-Module][] и [Install-Script][] устанавливают последнюю версию пакета. Чтобы установить более раннюю версию пакета, добавьте параметр `-RequiredVersion`.

### <a name="deploy"></a>Развертывание

Чтобы развернуть пакет из коллекции PowerShell в службе автоматизации Azure, щелкните **Служба автоматизации Azure**, а затем **Deploy to Azure Automation** (Развернуть в службе автоматизации Azure) на странице сведений о пакете. После этого вы будете перенаправлены на портал управления Azure, на который нужно войти с использованием учетных данных учетной записи Azure. Обратите внимание, что развертывание пакетов с зависимостями приводит к развертыванию всех зависимостей в службе автоматизации Azure. Кнопку "Развернуть в службе автоматизации Azure" можно отключить, добавив тег **AzureAutomationNotSupported** в метаданные пакета.

Дополнительные сведения о службе автоматизации Azure см. в [соответствующей](/azure/automation) документации.

## <a name="updating-packages-from-the-powershell-gallery"></a>Обновление пакетов из коллекции PowerShell

Чтобы обновить пакеты, установленные из коллекции PowerShell, выполните командлет [Update-Module][] или [Update-Script][]. При запуске без дополнительных параметров [Update-Module][] пытается обновить все модули, установленные командлетом [Install-Module][]. Чтобы выборочно обновить модули, добавьте параметр `-Name`.

Аналогично при запуске без дополнительных параметров [Update-Script][] пытается обновить все сценарии, установленные командлетом [Install-Script][]. Чтобы выборочно обновить скрипты, добавьте параметр `-Name`.

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>Перечисление пакетов, установленных из коллекции PowerShell

Чтобы узнать, какие модули вы установили из коллекции PowerShell, выполните командлет [Get-InstalledModule][]. Эта команда перечисляет все модули в системе, установленные непосредственно из коллекции PowerShell.

Аналогично, чтобы узнать, какие скрипты были установлены из коллекции PowerShell, выполните командлет [Get-InstalledScript][]. Эта команда перечисляет все скрипты в системе, установленные непосредственно из коллекции PowerShell.

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
