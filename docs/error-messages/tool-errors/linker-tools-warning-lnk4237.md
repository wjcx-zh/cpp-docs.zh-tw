---
title: 連結器工具警告 LNK4237 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4237
dev_langs:
- C++
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 479bd4ff8a4f48da679c9e17ec100668de84d089
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113704"
---
# <a name="linker-tools-warning-lnk4237"></a>連結器工具警告 LNK4237

指定時從 'dll'; 匯入了請使用 /subsystem: console 或 /subsystem: windows。

[了](../../build/reference/subsystem-specify-subsystem.md)時建置的 windows (Win32) 應用程式直接使用一或多個項目指定：

- kernel32.dll

- gdi32.dll

- user32.dll

- 其中一個 msvcrt\* dll。

解決這個警告不指定**了**。