---
title: 編譯器錯誤 C2879
ms.date: 11/04/2016
f1_keywords:
- C2879
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
ms.openlocfilehash: 9ac8f5e5edb1a6ed7314c5b5d125fcc9bfbe67de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378894"
---
# <a name="compiler-error-c2879"></a>編譯器錯誤 C2879

'symbol': 只有現有的命名空間可以由命名空間別名定義授的替代名稱

您無法建立[命名空間別名](../../cpp/namespaces-cpp.md#namespace_aliases)以外的命名空間的符號。

下列範例會產生 C2879:

```
// C2879.cpp
int main() {
   int i;
   namespace A = i;   // C2879 i is not a namespace
}
```