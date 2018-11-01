---
title: 連結器工具錯誤 LNK1245
ms.date: 11/04/2016
f1_keywords:
- LNK1245
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
ms.openlocfilehash: 4cf9a6c4356872b727a10a360396e51e38928b29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505478"
---
# <a name="linker-tools-error-lnk1245"></a>連結器工具錯誤 LNK1245

無效的子系統 '' 指定子系統;/SUBSYSTEM 必須是 WINDOWS、 WINDOWSCE 或 CONSOLE

[/clr](../../build/reference/clr-common-language-runtime-compilation.md)用來編譯的物件和其中一個下列條件為 true:

- 定義自訂的進入點 ([/ENTRY](../../build/reference/entry-entry-point-symbol.md))，使連結器無法推斷子系統。

- 的值傳遞給[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) /clr 物件無效的連結器選項。

這兩種情況下，解決方式是指定有效的值至 /SUBSYSTEM 連結器選項。