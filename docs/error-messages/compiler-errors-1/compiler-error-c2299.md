---
title: 編譯器錯誤 C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: 009a441ec610053176e79126d9f2663f29b26bc6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759044"
---
# <a name="compiler-error-c2299"></a>編譯器錯誤 C2299

' function '：行為變更：明確特製化不可以是複製的建立程式或複製指派運算子

這項錯誤也會因為針對 Visual Studio 2005 而進行的編譯器一致性工作而產生：舊版的視覺效果C++允許複製程式化或複製指派運算子的明確特製化。

若要解決 C2299，請勿將複製的「分析程式」或「指派運算子」設為範本函式，而不是採用類別類型的非樣板函數。 藉由明確指定樣板引數來呼叫複製器或指派運算子的任何程式碼，都必須移除樣板引數。

下列範例會產生 C2299：

```cpp
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```
