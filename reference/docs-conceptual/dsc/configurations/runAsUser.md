---
ms.date: 06/12/2017
keywords: dsc,powershell,конфигурация,установка
title: Использование учетных данных с ресурсами DSC
ms.openlocfilehash: fea2e3cad8d081c17853e127203f1d40d98c5de2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953981"
---
# <a name="use-credentials-with-dsc-resources"></a>Использование учетных данных с ресурсами DSC

> Область применения: Windows PowerShell 5.0, Windows PowerShell 5.1

Ресурс DSC можно запускать с определенным набором учетных данных. Для этого используется автоматическое свойство **PsDscRunAsCredential** в конфигурации. По умолчанию DSC запускает каждый ресурс в качестве системной учетной записи. Иногда бывает необходим запуск с учетной записью обычного пользователя, например, при установке MSI-пакетов в контексте определенного пользователя, при установке разделов реестра пользователя, доступе к конкретному локальному каталогу пользователя или сетевой папке. Согласно требованиям целевого компьютера нужно обязательно указать **SeInteractiveLogonRight** для любой учетной записи, назначенной свойству **PSDSCRunAsCredential**. Дополнительные сведения см. в статье [Account Rights Constants](/windows/desktop/secauthz/account-rights-constants) (Константы прав учетных записей).

У каждого ресурса есть свойство **PsDscRunAsCredential**, которому можно назначить учетные данные любого пользователя (объект [PSCredential](/dotnet/api/system.management.automation.pscredential)). Учетные данные можно жестко задать в качестве значения свойства конфигурации или установить в качестве значения [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential). В этом случае пользователю будет предложено ввести учетные данные при компиляции конфигурации (дополнительные сведения о компиляции конфигураций см. в разделе [Конфигурации](configurations.md)).

> [!NOTE]
> В PowerShell 5.0 использование свойства **PsDscRunAsCredential** в конфигурациях, вызывающих составные ресурсы, не поддерживалось. В PowerShell 5.1 свойство **PsDscRunAsCredential** поддерживается в конфигурациях, вызывающих составные ресурсы. Свойство **PsDscRunAsCredential** недоступно в PowerShell 4.0.

В следующем примере `Get-Credential` используется для запроса учетных данных пользователя. Ресурс **Registry** используется для изменения раздела реестра, указывающего цвет фона для окна командной строки Windows.

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```

> [!NOTE]
> В этом примере предполагается, что у вас есть действительный сертификат в `C:\publicKeys\targetNode.cer` и что отображаемое значение представляет собой отпечаток этого сертификата. Сведения о шифровании учетных данных в MOF-файлах конфигурации DSC см. в разделе [Защита MOF-файла](../pull-server/secureMOF.md).
