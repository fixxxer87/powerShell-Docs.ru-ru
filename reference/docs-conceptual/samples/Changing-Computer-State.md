---
ms.date: 06/05/2017
keywords: powershell,командлет
title: Изменение состояния компьютера
ms.openlocfilehash: de3e31e358548943a015b7bba275c4461202b20f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2019
ms.locfileid: "70386286"
---
# <a name="changing-computer-state"></a>Изменение состояния компьютера

Чтобы вернуть компьютер в исходное состояние в Windows PowerShell, используйте стандартную программу командной строки, инструментарий WMI или класс CIM. Хотя Windows PowerShell используется только для запуска программы, сведения об изменении состояния электропитания для компьютера в Windows PowerShell иллюстрируют некоторые важные особенности работы с внешними средствами в Windows PowerShell.

## <a name="locking-a-computer"></a>Блокировка компьютера

Единственным способом непосредственной блокировки компьютера с помощью стандартных средств является вызов функции **LockWorkstation()** в **user32.dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Эта команда немедленно блокирует рабочую станцию. Она использует *rundll32.exe*, который запускает библиотеки DLL Windows (и сохраняет их библиотеки для многократного использования), чтобы запустить user32.dll — библиотеку функций управления Windows.

Если рабочая станция блокируется при включенном быстром переключении пользователей, например, в Windows XP, на компьютере отображается экран входа в систему, а не заставка текущего пользователя.

Чтобы завершить работу конкретных сеансов на сервере терминалов, используйте программу командной строки **tsshutdn.exe**.

## <a name="logging-off-the-current-session"></a>Выход из текущего сеанса

Выйти из сеанса в локальной системе можно несколькими способами. Самый простой заключается в использовании программы командной строки удаленного рабочего стола или служб терминалов — **logoff.exe** (для получения дополнительных сведений введите **logoff /?** в командной строке Windows PowerShell). Чтобы выйти из текущего активного сеанса, введите **logoff** без аргументов.

Можно также использовать средство **shutdown.exe** с параметром выхода:

```
shutdown.exe -l
```

Еще один вариант — использование инструментария WMI. Класс Win32_OperatingSystem имеет метод Win32Shutdown. Вызов метода с флагом 0 инициирует выход из системы:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Дополнительные сведения и другие возможности метода Win32Shutdown см. в статье Win32Shutdown Method of the Win32_OperatingSystem Class (Метод Win32Shutdown класса Win32_OperatingSystem) на сайте MSDN.

Наконец, можно использовать CIM с тем же классом Win32_OperatingSystem, как описано выше в методе WMI.

```powershell
Get-CIMInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a>Завершение работы или перезапуск компьютера

Завершение работы и перезапуск компьютеров обычно относятся к схожим типам задач. Средства, завершающие работу компьютера, обычно также перезапускают его и наоборот. Существует два варианта непосредственной перезагрузки компьютера из Windows PowerShell. Используйте Tsshutdn.exe или Shutdown.exe с соответствующими аргументами. Подробные сведения об использовании можно получить, запустив **tsshutdn.exe /?** или **shutdown.exe /?** .

Операции завершения работы и перезапуска можно также выполнять непосредственно из Windows PowerShell.

Чтобы завершить работу компьютера, используйте команду Stop-Computer.

```powershell
Stop-Computer
```

Чтобы перезапустить операционную систему, используйте команду Restart-Computer.

```powershell
Restart-Computer
```

Чтобы выполнить немедленную перезагрузку компьютера, используйте параметр -Force.

```powershell
Restart-Computer -Force
```
