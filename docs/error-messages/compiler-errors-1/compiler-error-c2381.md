---
title: 編譯器錯誤 C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: a36655b0b3a28536538998656d7ce354c409d07c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225523"
---
# <a name="compiler-error-c2381"></a>編譯器錯誤 C2381

' function '：重複定義;__declspec （noreturn）不同

已宣告函式，然後定義，但定義使用[noreturn](../../cpp/noreturn.md) **`__declspec`** 修飾詞。 使用會 `noreturn` 構成函數的重新定義; 宣告和定義必須同意使用 `noreturn` 。

下列範例會產生 C2381：

```cpp
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```
