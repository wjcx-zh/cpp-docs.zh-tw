---
title: 編譯器警告 (層級 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: 63a22fed0832677837eb786268fc92946d295b79
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541767"
---
# <a name="compiler-warning-level-4-c4234"></a>編譯器警告 (層級 4) C4234

使用非標準的擴充：保留給未來使用的 ' 關鍵字 ' 關鍵字

編譯器尚未執行您使用的關鍵字。

此警告會自動升級為錯誤。 如果您想要修改此行為，請使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要讓 C4234 成為層級4警告問題，

```cpp
#pragma warning(2:4234)
```

在原始程式碼檔中。