---
title: 編譯器警告 (層級 1) C4237
ms.date: 11/04/2016
f1_keywords:
- C4237
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
ms.openlocfilehash: c68e84daa2ca1aa023123203bb851e92758f9e40
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447688"
---
# <a name="compiler-warning-level-1-c4237"></a>編譯器警告 (層級 1) C4237

'keyword' 關鍵字尚不支援，但保留供日後使用

中的關鍵字C++中 Microsoft 不會實作規格C++編譯器，但關鍵字不提供為使用者定義的符號。

下列範例會產生 C4237:

```
// C4237.cpp
// compile with: /W1 /c
int export;   // C4237
```