---
title: 編譯器錯誤 C2577 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2577
dev_langs:
- C++
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5d9a2b09fc9b8b15c4fc21f5eb537f18f5d3b03e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065812"
---
# <a name="compiler-error-c2577"></a>編譯器錯誤 C2577

'member': 解構函式/完成項不能有傳回型別

解構函式或完成項無法傳回值為`void`或任何其他類型。 移除`return`解構函式定義中的陳述式。

## <a name="example"></a>範例

下列範例會產生 C2577。

```
// C2577.cpp
// compile with: /c
class A {
public:
   A() {}
   ~A(){
      return 0;   // C2577
   }
};
```