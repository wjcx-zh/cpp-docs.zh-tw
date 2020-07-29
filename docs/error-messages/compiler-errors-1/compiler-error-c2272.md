---
title: 編譯器錯誤 C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: e4163d68e0fbfea062279ba91e2c902855245e4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220388"
---
# <a name="compiler-error-c2272"></a>編譯器錯誤 C2272

' function '：不允許在靜態成員函式上使用修飾詞

**`static`** 成員函式是使用記憶體模型規範（如[const](../../cpp/const-cpp.md)或[volatile](../../cpp/volatile-cpp.md)）來宣告，且成員函式不允許這類修飾詞 **`static`** 。

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
