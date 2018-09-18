---
title: 編譯器錯誤 C2793 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2793
dev_langs:
- C++
helpviewer_keywords:
- C2793
ms.assetid: ce35f4e8-c357-40ca-95c4-15ff001ad69d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d5b9f350a3d3845649c9423a412ed5286cb13723
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026201"
---
# <a name="compiler-error-c2793"></a>編譯器錯誤 C2793

'token': 非預期的語彙基元下列 ':: '，識別項或關鍵字 'operator' 必須是

唯一的權杖，可以遵循`__super::`是識別項或關鍵字`operator`。

下列範例會產生 C2793

```
// C2793.cpp
struct B {
   void mf();
};

struct D : B {
   void mf() {
      __super::(); // C2793
   }
};
```