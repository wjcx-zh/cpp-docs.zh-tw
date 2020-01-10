---
title: 編譯器錯誤 C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: 834b9939a99c694c702bb268b928575b4beb8856
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745391"
---
# <a name="compiler-error-c2381"></a>編譯器錯誤 C2381

' function '：重複定義;__declspec （noreturn）不同

已宣告函式並加以定義，但是定義使用[noreturn](../../cpp/noreturn.md) `__declspec` 修飾詞。 使用 `noreturn` 構成函數的重新定義;宣告和定義必須同意使用 `noreturn`。

下列範例會產生 C2381：

```cpp
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```
