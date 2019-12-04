---
title: 編譯器錯誤 C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: fd6fdecd3a491ce5f068f4d51d413e6767aabe2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758693"
---
# <a name="compiler-error-c2272"></a>編譯器錯誤 C2272

' function '：不允許在靜態成員函式上使用修飾詞

`static` 成員函式是使用記憶體模型規範（例如[const](../../cpp/const-cpp.md)或[volatile](../../cpp/volatile-cpp.md)）進行宣告，而且 `static` 成員函式上不允許這類修飾詞。

下列範例會產生 C2272：

```cpp
// C2272.cpp
// compile with: /c
class CMyClass {
public:
   static void func1() const volatile;   // C2272  func1 is static
   void func2() const volatile;   // OK
};
```
