---
title: 編譯器錯誤 C2807
ms.date: 11/04/2016
f1_keywords:
- C2807
helpviewer_keywords:
- C2807
ms.assetid: bd7a207a-f379-4de6-8ee8-c7cab78b3480
ms.openlocfilehash: 5e3fd05b1c2473efbc1cd102056c73b2f221981d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62281909"
---
# <a name="compiler-error-c2807"></a>編譯器錯誤 C2807

第二個型式參數，並後置 'operator operator' 必須是 'int'

後置運算子的第二個參數具有錯誤的類型。

下列範例會產生 C2807:

```
// C2807.cpp
// compile with: /c
class X {
public:
   X operator++ ( X );   // C2807 nonvoid parameter
   X operator++ ( int );   // OK, int parameter
};
```