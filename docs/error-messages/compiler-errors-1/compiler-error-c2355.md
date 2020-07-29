---
title: 編譯器錯誤 C2355
ms.date: 11/04/2016
f1_keywords:
- C2355
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
ms.openlocfilehash: 4e78d20fb59beead08aaddcf85138f845cfc0390
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212757"
---
# <a name="compiler-error-c2355"></a>編譯器錯誤 C2355

'this'：只能在非靜態成員函式或非靜態資料成員初始設定式內部參考

**`this`** 指標只在非靜態成員函式或非靜態資料成員初始化運算式中有效。 在類別宣告之外的成員函式定義的類別範圍不正確地限定時，就會產生這個錯誤。 當 **`this`** 指標用於未在類別中宣告的函式時，也可能會發生此錯誤。

若要修正此問題，請確定成員函式定義符合類別中的成員函式宣告，而且未宣告為靜態。 關於資料成員初始設定式，請確定資料成員未宣告為靜態。

下列範例會產生 C2355，並示範如何修正此問題：

```cpp
// C2355.cpp
// compile with: /c
class MyClass {};
MyClass *p = this;   // C2355

// OK
class MyClass2 {
public:
   void Test() {
      MyClass2 *p = this;
   }
};
```
