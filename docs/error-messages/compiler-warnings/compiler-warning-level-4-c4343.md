---
title: 編譯器警告 (層級 4) C4343
ms.date: 11/04/2016
f1_keywords:
- C4343
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
ms.openlocfilehash: 59803440966b8396ba231dc5a7265620c37f9cc1
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991192"
---
# <a name="compiler-warning-level-4-c4343"></a>編譯器警告 (層級 4) C4343

\#pragma optimize （"g"，off）覆寫/Og 選項

這個警告 (僅適用於 Itanium 處理器系列 (IPF) 編譯器) 報告 pragma [optimize](../../preprocessor/optimize.md) 已覆寫 [/Og](../../build/reference/og-global-optimizations.md) 編譯器選項。

下列範例會產生 C4343：

```cpp
// C4343.cpp
// compile with: /Og /W4 /LD
// processor: IPF
#pragma optimize ("g", off)   // C4343
```
