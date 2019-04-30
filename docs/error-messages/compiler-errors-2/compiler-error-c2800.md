---
title: 編譯器錯誤 C2800
ms.date: 11/04/2016
f1_keywords:
- C2800
helpviewer_keywords:
- C2800
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
ms.openlocfilehash: e893866a28c124e9e6cbc9663a488f89ac2d291b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408546"
---
# <a name="compiler-error-c2800"></a>編譯器錯誤 C2800

無法多載 'operator operator'

下列運算子無法多載： 類別成員存取 (`.`)，成員的指標 (`.*`)，範圍解析 (`::`)，條件運算式 (`? :`)，和`sizeof`。

下列範例會產生 C2800:

```
// C2800.cpp
// compile with: /c
class C {
   operator:: ();   // C2800
};
```