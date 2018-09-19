---
title: 編譯器錯誤 C2733 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2733
dev_langs:
- C++
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 42749c26f4a8a474f3dac076b80a1bfe71e89d58
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110441"
---
# <a name="compiler-error-c2733"></a>編譯器錯誤 C2733

第二個 C 連結的多載函式 'function' 不允許

使用 C 連結宣告多個多載函式。 使用 C 連結時，只有一種指定的函式可以是外部。 多載函式具有相同的未裝飾的名稱，因為它們無法搭配 C 程式。

下列範例會產生 C2733:

```
// C2733.cpp
extern "C" {
   void F1(int);
}

extern "C" {
   void F1();   // C2733
   // try the following line instead
   // void F2();
}
```