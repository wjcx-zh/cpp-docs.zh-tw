---
title: 編譯器錯誤 C2751 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2751
dev_langs:
- C++
helpviewer_keywords:
- C2751
ms.assetid: 44a3abdf-8a87-4a09-b34b-532c220c310a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97a4021eb4cc5092f4bb9424e141666aea4a00f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021781"
---
# <a name="compiler-error-c2751"></a>編譯器錯誤 C2751

'parameter': 不限定的函式參數名稱

您無法使用限定的名稱做為函式參數。

下列範例會產生 C2751:

```
// C2751.cpp
namespace std {
   template<typename T>
   class list {};
}

#define list std::list
void f(int &list){}   // C2751
```