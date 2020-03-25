---
title: 連結器工具警告 LNK4237
ms.date: 11/04/2016
f1_keywords:
- LNK4237
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
ms.openlocfilehash: aaa26393f1ce76d3e1bc40e5ba4978d1bcdb4fc9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193754"
---
# <a name="linker-tools-warning-lnk4237"></a>連結器工具警告 LNK4237

/SUBSYSTEM：從 ' dll ' 匯入時所指定的原生;使用/SUBSYSTEM： CONSOLE 或/SUBSYSTEM： WINDOWS。

[/SUBSYSTEM： NATIVE](../../build/reference/subsystem-specify-subsystem.md)是在建立直接使用下列一或多項的 Windows （Win32）應用程式時所指定：

- kernel32.dll

- gdi32 .dll

- user32.dll

- 其中一個 msvcrt.lib\* dll。

請不要指定 **/SUBSYSTEM： NATIVE**來解決這個警告。
