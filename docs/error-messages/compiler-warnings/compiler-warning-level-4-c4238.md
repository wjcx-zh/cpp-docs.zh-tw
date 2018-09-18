---
title: 編譯器警告 （層級 4） C4238 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4238
dev_langs:
- C++
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4d5f358d08f81e6b8097140ad47d54f4b3b3fed
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057024"
---
# <a name="compiler-warning-level-4-c4238"></a>編譯器警告 (層級 4) C4238

使用非標準擴充： 類別右值當做左值

與舊版的 Visual c + + 中，Microsoft 擴充功能的相容性 (**/Ze**) 可讓您使用的類別類型，因為在內容中的右值也會隱含或明確地取得其位址。 在某些情況下，如下列範例中，這很危險。

## <a name="example"></a>範例

```
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

這種用法會導致 ANSI 相容性錯誤 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。