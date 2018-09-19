---
title: 編譯器錯誤 C2758 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2758
dev_langs:
- C++
helpviewer_keywords:
- C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ffa6d33dba70a463d789f3b0f016dc1d157eb65
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072923"
---
# <a name="compiler-error-c2758"></a>編譯器錯誤 C2758

'member'：必須初始化參考類型的成員

當建構函式未初始化初始設定式清單中參考類型的成員時，會產生編譯器錯誤 C2758。 編譯器會將成員保持未定義的狀態。 在建構函式的初始化清單中宣告參考成員變數或提供值時，必須初始化。

下列範例會產生 C2758：

```
// C2758.cpp
// Compile by using: cl /W3 /c C2758.cpp
struct A {
   const int i;

   A(int n) { };   // C2758
   // try the following line instead
   // A(int n) : i{n} {};
};
```