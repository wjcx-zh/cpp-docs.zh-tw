---
title: 編譯器警告 (層級 1) C4237
ms.date: 11/04/2016
f1_keywords:
- C4237
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
ms.openlocfilehash: 04fcb99e1dd1e348716e25affb22b54079d53aa9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207379"
---
# <a name="compiler-warning-level-1-c4237"></a>編譯器警告 (層級 1) C4237

'keyword' 關鍵字尚不支援，但保留供日後使用

中的關鍵字C++視覺效果中不會實作規格C++編譯器，但關鍵字不提供為使用者定義的符號。

下列範例會產生 C4237:

```
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```