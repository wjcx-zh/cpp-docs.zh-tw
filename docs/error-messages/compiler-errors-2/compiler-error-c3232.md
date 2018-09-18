---
title: 編譯器錯誤 C3232 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3232
dev_langs:
- C++
helpviewer_keywords:
- C3232
ms.assetid: 3119b3a9-0eff-4a3f-b805-e4d160af9e39
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e7b3e8c306b8e883fd3edb0b2781b297842bb0a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018362"
---
# <a name="compiler-error-c3232"></a>編譯器錯誤 C3232

'param': 泛型類型參數不可使用在限定名稱中

泛型類型參數的使用方式錯誤。

下列範例會產生 C3232：

```
// C3232.cpp
// compile with: /clr
generic <class T>
ref class C {
   typename T::TYPE t;   // C3232
};
```