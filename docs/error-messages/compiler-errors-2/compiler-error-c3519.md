---
title: 編譯器錯誤 C3519 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3519
dev_langs:
- C++
helpviewer_keywords:
- C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ac9c1bfe01cee659ae8b637df23a86315b5310f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072780"
---
# <a name="compiler-error-c3519"></a>編譯器錯誤 C3519

'invalid_param': 對 embedded_idl 屬性無效的參數

參數已傳遞給`embedded_idl`的屬性[#import](../../preprocessor/hash-import-directive-cpp.md)，但編譯器無法辨認的參數。

唯一允許的參數`embedded_idl`都`emitidl`和`no_emitidl`。

下列範例會產生 C3519:

```
// C3519.cpp
// compile with: /LD
[module(name="MyLib2")];
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidcl")
// C3519
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidl")
// OK
```