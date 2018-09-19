---
title: 編譯器錯誤 C2381 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2381
dev_langs:
- C++
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f09cd8c16eeb5ec797643cb6653d069df41b136
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076940"
---
# <a name="compiler-error-c2381"></a>編譯器錯誤 C2381

'function': 重複定義;__declspec （noreturn） 不同

函式已宣告，並接著定義但所使用的定義[noreturn](../../cpp/noreturn.md) `__declspec`修飾詞。 善用`noreturn`構成函式的重複定義; 的宣告和定義要使用同意`noreturn`。

下列範例會產生 C2381:

```
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```