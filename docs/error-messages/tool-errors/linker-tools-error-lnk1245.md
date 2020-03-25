---
title: 連結器工具錯誤 LNK1245
ms.date: 11/04/2016
f1_keywords:
- LNK1245
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
ms.openlocfilehash: 19e3f820b5bd7fdd8eac2f7b5a96fb5923ae0b92
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183796"
---
# <a name="linker-tools-error-lnk1245"></a>連結器工具錯誤 LNK1245

指定了不正確子系統 ' 子系統 ';/SUBSYSTEM 必須是 WINDOWS、WINDOWSCE 或 CONSOLE

[/clr](../../build/reference/clr-common-language-runtime-compilation.md)是用來編譯物件，而下列其中一個條件成立：

- 定義了自訂進入點（[/ENTRY](../../build/reference/entry-entry-point-symbol.md)），因此連結器無法推斷子系統。

- 已將值傳遞給對/clr 物件不正確[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)連結器選項。

在這兩種情況下，解決方法是將有效的值指定給/SUBSYSTEM 連結器選項。
