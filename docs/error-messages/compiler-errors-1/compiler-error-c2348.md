---
title: 編譯器錯誤 C2348
ms.date: 11/04/2016
f1_keywords:
- C2348
helpviewer_keywords:
- C2348
ms.assetid: 4c4d701f-ccf1-46fe-9ddb-3f341684f269
ms.openlocfilehash: a0f74179e187baea80993c5dda3f35f602f876c1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508538"
---
# <a name="compiler-error-c2348"></a>編譯器錯誤 C2348

' type name '：不是 C 樣式的匯總，無法在 embedded IDL 中匯出

若要 **`struct`** 使用 [export](../../windows/attributes/export.md) 屬性將放在 .idl 檔中， **`struct`** 必須只包含資料。

下列範例會產生 C2348：

```cpp
// C2348.cpp
// C2348 error expected
[ module(name="SimpleMidlTest") ];

[export]
struct Point {
   // Delete the following two lines to resolve.
   Point() : m_i(0), m_j(0) {}
   Point(int i, int j) : m_i(i), m_j(j) {}

   int m_i;
   int m_j;
};
```
