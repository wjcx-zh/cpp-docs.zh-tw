---
title: 編譯器錯誤 C3297
ms.date: 11/04/2016
f1_keywords:
- C3297
helpviewer_keywords:
- C3297
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
ms.openlocfilehash: e4661119680dff34dfaa43fb9ce71bf97150a8bd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777675"
---
# <a name="compiler-error-c3297"></a>編譯器錯誤 C3297

'constraint_2': 因為 'constraint_1' 有值條件約束，所以 'constraint_1' 不能用做條件約束

值類別已密封。 如果條件約束是值類別，它絕對不會衍生其他的條件約束。

如需詳細資訊，請參閱 <<c0> [ 泛型類型參數的條件約束 (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)。</c0>

## <a name="example"></a>範例

下列範例會產生 C3297。

```
// C3297.cpp
// compile with: /clr /c
generic<class T, class U>
where T : value class
where U : T   // C3297
public ref struct R {};
```