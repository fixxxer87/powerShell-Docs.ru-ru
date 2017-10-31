---
ms.date: 2017-06-05
keywords: "powershell,командлет"
title: "Справка по командной строке PowerShell.exe"
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c2583dac14f32db414f0a4377b1694ab7fa7523b
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2017
---
# <a name="powershellexe-command-line-help"></a>Справка по командной строке PowerShell.exe
Запускает сеанс Windows PowerShell. Можно использовать PowerShell.exe для запуска сеанса Windows PowerShell из командной строки другого средства, такого как Cmd.exe, или использовать его в командной строке Windows PowerShell для запуска нового сеанса. Используйте указанные параметры для настройки сеанса.

## <a name="syntax"></a>Синтаксис

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}] 
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive] 
       [-NoProfile] 
       [-OutputFormat {Text | XML}] 
       [-PSConsoleFile <FilePath> | -Version <Windows PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]
        

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a>Параметры

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>
Принимает строковую версию команды в кодировке Base 64. Используйте этот параметр для отправки в Windows PowerShell команд, требующих сложных кавычек или фигурных скобок.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>
Задает политику выполнения по умолчанию для текущего сеанса и сохраняет ее в переменной среды $env:PSExecutionPolicyPreference. Этот параметр не изменяет политику выполнения Windows PowerShell, заданную в реестре. Дополнительные сведения о политиках выполнения Windows PowerShell, включая список допустимых значений, см. в статье about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).

### <a name="-file-filepath-parameters"></a>-File <FilePath> \[<Parameters>]
Запускает указанный сценарий в локальной области ("с точкой"), чтобы создаваемые сценарием функции и переменные были доступны в текущем сеансе. Введите путь к файлу сценария и любые параметры. Параметр **File** должен быть последним в команде, поскольку все символы, введенные после параметра **File**, интерпретируются как путь к файлу сценария и следующие за ним параметры сценария.

Параметры сценария и их значения можно включить в значение параметра **File**. Пример: `-File .\Get-Script.ps1 -Domain Central`. Обратите внимание, что передаваемые в сценарий параметры имеют вид строк литералов (после интерпретации текущей оболочкой).
Например, если вы находитесь в cmd.exe и хотите передать значение переменной среды, используйте синтаксис cmd.exe: `powershell -File .\test.ps1 -Sample %windir%`. Если вы используете синтаксис PowerShell, в этом примере сценарий получит литерал "$env:windir", а не значение этой переменной среды: `powershell -File .\test.ps1 -Sample $env:windir`

Обычно параметры-переключатели сценария включаются или опускаются. Например, приведенная ниже команда использует параметр **All** файла сценария Get-Script.ps1: `-File .\Get-Script.ps1 -All`

### <a name="-inputformat-text--xml"></a>\-InputFormat {Text | XML}
Описывает формат данных, отправляемых в Windows PowerShell. Допустимые значения: "Text" (текстовые строки) или "XML" (сериализованный формат CLIXML).

### <a name="-mta"></a>-Mta
Запускает оболочку с использованием многопотокового подразделения. Этот параметр впервые появился в Windows PowerShell 3.0. В Windows PowerShell 3.0 по умолчанию используется однопотоковое подразделение (STA). В Windows PowerShell 2.0 по умолчанию используется многопотоковое подразделение (MTA).

### <a name="-noexit"></a>-NoExit
Не завершает работу после выполнения команд запуска.

### <a name="-nologo"></a>-NoLogo
Скрывает баннер авторских прав при запуске программы.

### <a name="-noninteractive"></a>-NonInteractive
Не предоставляет пользователю интерактивную командную строку.

### <a name="-noprofile"></a>-NoProfile
Не загружает профиль Windows PowerShell.

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}
Определяет формат выходных данных Windows PowerShell. Допустимые значения: "Text" (текстовые строки) или "XML" (сериализованный формат CLIXML).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>
Загружает указанный файл консоли Windows PowerShell. Введите путь и имя файла консоли. Для создания файла консоли используйте командлет [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) в Windows PowerShell.

### <a name="-sta"></a>-Sta
Запускает Windows PowerShell с использованием многопотокового подразделения. В Windows PowerShell 3.0 по умолчанию используется однопотоковое подразделение (STA). В Windows PowerShell 2.0 по умолчанию используется многопотоковое подразделение (MTA).

### <a name="-version-windows-powershell-version"></a>-Version <Windows PowerShell Version>
Запускает заданную версию Windows PowerShell. Указанная версия должна быть установлена в системе. Если на компьютере установлен Windows PowerShell 3.0, допустимыми значениями являются "3.0" и "2.0". По умолчанию используется значение "3.0".

Если Windows PowerShell 3.0 не установлен, допустимо только значение "2.0". Другие значения игнорируются.

Дополнительные сведения см. в разделе "Установка Windows PowerShell" статьи [Начало работы с Windows PowerShell [СТАРЫЙ MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>
Задает стиль окна для сеанса. Допустимые значения: Normal, Minimized, Maximized и Hidden.

### <a name="-command"></a>-Command
Выполняет указанные команды (вместе с параметрами) как введенные в командной строке Windows PowerShell и завершает работу, если не указан параметр NoExit.
В сущности, любой текст после `-Command` отправляется в PowerShell в виде одной командной строки (это поведение отличается от того, как отправляемые в сценарий параметры обрабатываются `-File`).

Значением Command может быть строка "-". или блок сценария. Если для Command задано значение "-", текст команды считывается из стандартного ввода.

Блоки сценариев должны быть заключены в фигурные скобки ({}). Указать блок сценария можно только при использовании PowerShell.exe в Windows PowerShell. Результаты сценария возвращаются родительской оболочке как десериализованные объекты XML, а не как активные объекты.

Если значением Command является строка, параметр **Command** должен быть последним в команде, так как любой знак, введенный после команды, интерпретируется как ее аргумент.

При написании строки команды Windows PowerShell используйте следующий формат:

```
"& {<command>}"
```

где кавычки отделяют строку, а оператор вызова (&) запускает выполнение команды.

### <a name="-help---"></a>-Help, -?, /?
Показывает это сообщение. При вводе команды PowerShell.exe в Windows PowerShell добавляйте в начало параметров команды дефис (-), а не косую черту (/). В Cmd.exe можно использовать как дефис, так и косую черту.

> [!NOTE]
> Замечание по устранению неполадок. Обратите внимание, что в Windows PowerShell 2.0 запуск некоторых программ в Windows PowerShell завершается ошибкой с кодом LastExitCode 0xc0000142.

## <a name="examples"></a>ПРИМЕРЫ

```
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a Powerhell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate wayh to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```
