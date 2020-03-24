---
title: 連結器工具錯誤 LNK1158
ms.date: 11/04/2016
f1_keywords:
- LNK1158
helpviewer_keywords:
- LNK1158
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
ms.openlocfilehash: 2602c488db660ce067c672df4a746c388d987120
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184056"
---
# <a name="linker-tools-error-lnk1158"></a>連結器工具錯誤 LNK1158

無法執行 ' filename '

[連結](../../build/reference/linking.md)所呼叫的指定可執行檔不在包含連結的目錄中，也不在 PATH 環境變數中指定的目錄中。

例如，如果您嘗試在具有32位作業系統的電腦上，使用 PGOPTIMIZE 參數來處理[/ltcg](../../build/reference/ltcg-link-time-code-generation.md)連結器選項，就會發生此錯誤。
