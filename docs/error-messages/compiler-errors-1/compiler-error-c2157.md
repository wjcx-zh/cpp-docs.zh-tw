---
title: 編譯器錯誤 C2157 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2157
dev_langs:
- C++
helpviewer_keywords:
- C2157
ms.assetid: babbca24-16dc-4b69-be14-a675029249c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd17b03cc48555800e3c36cc3f5512506f011372
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072060"
---
# <a name="compiler-error-c2157"></a>編譯器錯誤 C2157

'function': 在 pragma 清單中使用之前必須先宣告

未宣告函式名稱，便在 [alloc_text](../../preprocessor/alloc-text.md) pragma 的函式清單中參考此名稱。

下列範例會產生 C2157：

```
// C2157.cpp
// compile with: /c
#pragma alloc_text( "func", func)   // C2157

// OK
extern "C" void func();
#pragma alloc_text( "func", func)
```