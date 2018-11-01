---
title: 編譯器警告 (層級 1) C4237
ms.date: 11/04/2016
f1_keywords:
- C4237
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
ms.openlocfilehash: 04fcb99e1dd1e348716e25affb22b54079d53aa9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472679"
---
# <a name="compiler-warning-level-1-c4237"></a>編譯器警告 (層級 1) C4237

'keyword' 關鍵字尚不支援，但保留供日後使用

中的 Visual c + + 編譯器，不會實作 c + + 規格中的關鍵字，但關鍵字不提供為使用者定義的符號。

下列範例會產生 C4237:

```
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```