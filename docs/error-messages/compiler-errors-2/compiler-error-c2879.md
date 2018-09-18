---
title: 編譯器錯誤 C2879 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2879
dev_langs:
- C++
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 632142ea0efd8a9d009f18b898213cfa92514b16
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042472"
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