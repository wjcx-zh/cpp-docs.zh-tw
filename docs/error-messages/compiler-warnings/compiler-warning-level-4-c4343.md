---
title: 編譯器警告 (層級 4) C4343
ms.date: 11/04/2016
f1_keywords:
- C4343
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
ms.openlocfilehash: c8f0bb514a3da932500f986e50a20af0947827c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403983"
---
# <a name="compiler-warning-level-4-c4343"></a>編譯器警告 (層級 4) C4343

\#pragma optimize 覆寫了 /Og 選項

這個警告 (僅適用於 Itanium 處理器系列 (IPF) 編譯器) 報告 pragma [optimize](../../preprocessor/optimize.md) 已覆寫 [/Og](../../build/reference/og-global-optimizations.md) 編譯器選項。

下列範例會產生 C4343：

```
// C4343.cpp
// compile with: /Og /W4 /LD
// processor: IPF
#pragma optimize ("g", off)   // C4343
```