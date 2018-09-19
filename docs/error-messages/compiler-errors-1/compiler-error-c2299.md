---
title: 編譯器錯誤 C2299 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2299
dev_langs:
- C++
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4977f4a5ac81cf4c04d3b143f6f7e670a9d9279
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049614"
---
# <a name="compiler-error-c2299"></a>編譯器錯誤 C2299

'function': 行為變更： 明確特製化不能複製建構函式或複製指派運算子

這項錯誤也可能因為針對 Visual c + + 2005年所進行的編譯器一致性處理而產生： 舊版 Visual c + + 允許的複製建構函式或複製指派運算子的明確特製化。

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