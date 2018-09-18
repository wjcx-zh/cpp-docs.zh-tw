---
title: 連結器工具錯誤 LNK1245 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1245
dev_langs:
- C++
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef7bace5cec937399d7a2ed440e21b9b751f4141
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041788"
---
# <a name="linker-tools-error-lnk1245"></a>連結器工具錯誤 LNK1245

無效的子系統 '' 指定子系統;/SUBSYSTEM 必須是 WINDOWS、 WINDOWSCE 或 CONSOLE

[/clr](../../build/reference/clr-common-language-runtime-compilation.md)用來編譯的物件和其中一個下列條件為 true:

- 定義自訂的進入點 ([/ENTRY](../../build/reference/entry-entry-point-symbol.md))，使連結器無法推斷子系統。

- 的值傳遞給[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) /clr 物件無效的連結器選項。

這兩種情況下，解決方式是指定有效的值至 /SUBSYSTEM 連結器選項。