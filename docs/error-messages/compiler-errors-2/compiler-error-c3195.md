---
title: 編譯器錯誤 C3195
ms.date: 11/04/2016
f1_keywords:
- C3195
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
ms.openlocfilehash: c8274e121e953c3e51a0f2ff8c68c315759ce3e1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760422"
---
# <a name="compiler-error-c3195"></a>編譯器錯誤 C3195

'operator': 已被保留，不能做為 ref 類別或實值型別的成員。 必須使用 'operator' 關鍵字定義 CLR 或 WinRT 運算子

編譯器偵測到使用 Managed Extensions for C++ 語法的運算子定義。 您必須使用運算子C++的語法。

下列範例會產生 C3195，並示範如何修正此問題：

```cpp
// C3195.cpp
// compile with: /clr /LD
#using <mscorlib.dll>
value struct V {
   static V op_Addition(V v, int i);   // C3195
   static V operator +(V v, char c);   // OK for new C++ syntax
};
```
