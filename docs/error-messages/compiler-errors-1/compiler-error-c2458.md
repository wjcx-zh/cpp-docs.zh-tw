---
title: 編譯器錯誤 C2458 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2458
dev_langs:
- C++
helpviewer_keywords:
- C2458
ms.assetid: ed21901f-1067-42f5-b275-19b480decf5c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94a95ab1eab00424774d5117e3ae37685a2ac1fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035459"
---
# <a name="compiler-error-c2458"></a>編譯器錯誤 C2458

'identifier': 重複定義內定義

類別、 結構、 等位或列舉型別重新定義它自己宣告中。

下列範例會產生 C2458:

```
// C2458.cpp
class C {
   enum i { C };   // C2458
};
```