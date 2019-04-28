---
title: 編譯器錯誤 C3195
ms.date: 11/04/2016
f1_keywords:
- C3195
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
ms.openlocfilehash: 4a54a9c629a1abaa4f1c5d15d06448e82cf25561
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329097"
---
# <a name="compiler-error-c3195"></a>編譯器錯誤 C3195

'operator': 已被保留，不能做為 ref 類別或實值型別的成員。 必須使用 'operator' 關鍵字定義 CLR 或 WinRT 運算子

編譯器偵測到使用 Managed Extensions for C++ 語法的運算子定義。 您必須使用C++運算子的語法。

下列範例會產生 C3195，並示範如何修正此問題：

```
// C3195.cpp
// compile with: /clr /LD
#using <mscorlib.dll>
value struct V {
   static V op_Addition(V v, int i);   // C3195
   static V operator +(V v, char c);   // OK for new C++ syntax
};
```