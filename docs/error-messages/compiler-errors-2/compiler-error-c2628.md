---
title: 編譯器錯誤 C2628 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2628
dev_langs:
- C++
helpviewer_keywords:
- C2628
ms.assetid: 19a25e77-d5be-4107-88d5-0745b6281f98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43a7d0515013158932f627b883ab36a2793ab5bd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051343"
---
# <a name="compiler-error-c2628"></a>編譯器錯誤 C2628

'type1' 後面接著 'type2' 是不合法 (是否忘記 ';'？)

分號可能會遺失。

下列範例會產生 C2628:

```
// C2628.cpp
class CMyClass {}
int main(){}   // C2628 error
```

可能的解決方式：

```
// C2628b.cpp
class CMyClass {};
int main(){}
```