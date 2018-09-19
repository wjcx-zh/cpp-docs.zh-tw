---
title: 編譯器錯誤 C2809 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2809
dev_langs:
- C++
helpviewer_keywords:
- C2809
ms.assetid: ce796b8e-1a8c-4074-995d-1ad09afd0e93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6503f395a795056d0952c7a55f2c69300501313e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018863"
---
# <a name="compiler-error-c2809"></a>編譯器錯誤 C2809

'operator operator' 具有沒有型式參數

運算子缺少必要的參數。

下列範例會產生 C2809:

```
// C2809.cpp
// compile with: /c
class A{};
int operator+ ();   // C2809
int operator+ (A);   // OK
```