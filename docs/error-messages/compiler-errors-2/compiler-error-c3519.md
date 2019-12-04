---
title: 編譯器錯誤 C3519
ms.date: 11/04/2016
f1_keywords:
- C3519
helpviewer_keywords:
- C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
ms.openlocfilehash: 7e56ff814b1a2dd6ec3cb41db2cbcc21d7dcf2d9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750165"
---
# <a name="compiler-error-c3519"></a>編譯器錯誤 C3519

' invalid_param '： embedded_idl 屬性的參數無效

參數已傳遞至[#import](../../preprocessor/hash-import-directive-cpp.md)的 `embedded_idl` 屬性，但編譯器無法辨識參數。

`embedded_idl` 所允許的唯一參數是 `emitidl` 和 `no_emitidl`。

下列範例會產生 C3519：

```cpp
// C3519.cpp
// compile with: /LD
[module(name="MyLib2")];
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidcl")
// C3519
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidl")
// OK
```
