---
title: 編譯器錯誤 C2479
ms.date: 11/04/2016
f1_keywords:
- C2479
helpviewer_keywords:
- C2479
ms.assetid: c74c7869-e65b-4ca1-b6fa-eb39fed4458a
ms.openlocfilehash: c7bddd21faab8c55f349c6e03fbcd3db42c3fa7d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743558"
---
# <a name="compiler-error-c2479"></a>編譯器錯誤 C2479

' identifier '： ' allocate （） ' 只對靜態範圍的資料項目有效

`__declspec( allocate())` 語法只能用於靜態資料。

下列範例會產生 C2479：

```cpp
// C2479.cpp
// compile with: /c
#pragma section("mycode", read)
static __declspec(allocate("mycode")) void DoNothing() {}   // C2479
__declspec(allocate("mycode"))  int i = 0;   // OK
```
