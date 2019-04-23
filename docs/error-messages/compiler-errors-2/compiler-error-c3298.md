---
title: 編譯器錯誤 C3298
ms.date: 11/04/2016
f1_keywords:
- C3298
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
ms.openlocfilehash: fe6913d402c6ce4df3551c159eb56a12590799cb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779124"
---
# <a name="compiler-error-c3298"></a>編譯器錯誤 C3298

'constraint_1': 無法將 'constraint_2' 當做條件約束使用，因為 'constraint_2' 具有 ref 條件約束，而且 'constraint_1' 具有值條件約束

您不能指定條件約束的互斥特性。 例如，泛型類型參數不能同時限制為實值類型和參考類型。

如需詳細資訊，請參閱 <<c0> [ 泛型類型參數的條件約束 (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)。</c0>

## <a name="example"></a>範例

下列範例會產生 C3298。

```
// C3298.cpp
// compile with: /clr /c
generic<class T, class U>
where T : ref class
where U : T, value class   // C3298
public ref struct R {};
```