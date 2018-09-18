---
title: 編譯器錯誤 C2936 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2936
dev_langs:
- C++
helpviewer_keywords:
- C2936
ms.assetid: 5d1ba0fc-0c78-4a37-a83b-1ef8527763be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 839d2f3dd005e4bd8bd697c74e5940a0331c1acc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054242"
---
# <a name="compiler-error-c2936"></a>編譯器錯誤 C2936

'class' : type-class-id 重複定義為全域資料變數

您無法將泛型或範本類別用作為全域資料變數。

此錯誤可能是大括弧不對稱所造成。

下列範例會產生 C2936：

```
// C2936.cpp
// compile with: /c
template<class T> struct TC { };
int TC<int>;   // C2936

// OK
struct TC2 { };
int TC2;
```

使用泛型時，也會發生 C2936：

```
// C2936b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
int GC<int>;   // C2936

// OK
ref struct GC2 {};
int GC2;
```