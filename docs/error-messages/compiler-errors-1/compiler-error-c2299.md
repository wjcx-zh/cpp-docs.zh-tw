---
title: 編譯器錯誤 C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: 4776ddede31dbcebe56a5919fd111f4df7248215
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182687"
---
# <a name="compiler-error-c2299"></a>編譯器錯誤 C2299

'function': 行為變更： 明確特製化不能複製建構函式或複製指派運算子

這項錯誤也可能導致針對視覺效果所進行的編譯器一致性工作C++2005年： 視覺效果的舊版C++允許的複製建構函式或複製指派運算子的明確特製化。

若要解決 C2299，請勿複製建構函式或指派運算子的樣板函式，但非樣板函式接受類別型別。 藉由明確指定樣板引數呼叫的複製建構函式或指派運算子的任何程式碼，就必須移除樣板引數。

下列範例會產生 C2299:

```
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```