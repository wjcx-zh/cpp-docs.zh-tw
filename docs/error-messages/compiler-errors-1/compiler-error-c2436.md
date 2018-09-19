---
title: 編譯器錯誤 C2436 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2436
dev_langs:
- C++
helpviewer_keywords:
- C2436
ms.assetid: ca4cc813-bc1d-4c0a-9a2c-3a5fe673d084
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f32b94f0e68de893897a5bdf48977a47417e6729
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032987"
---
# <a name="compiler-error-c2436"></a>編譯器錯誤 C2436

'identifier': 成員函式或建構函式初始設定式清單中的巢狀的類別

無法初始化成員函式或建構函式初始設定式清單中的本機類別。

下列範例會產生 C2436:

```
// C2436.cpp
struct S{
   int f();
   struct Inner{
      int i;
   };
   S():f(10), Inner(0){}   // C2436
};
```