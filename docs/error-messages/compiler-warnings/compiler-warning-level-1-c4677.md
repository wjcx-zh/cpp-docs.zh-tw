---
title: 編譯器警告 (層級 1) C4677
ms.date: 11/04/2016
f1_keywords:
- C4677
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
ms.openlocfilehash: 66b8d42b63bcbf328703523c4eeda7a047f4643c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533012"
---
# <a name="compiler-warning-level-1-c4677"></a>編譯器警告 (層級 1) C4677

'function': 非私用成員簽章含有組件私用類型 'private_type'

具有公用組件外部的存取範圍的類型會使用具有外部組件的私用存取的類型。 參考公用組件類型的元件不能使用的型別成員或參考組件私用類型的成員。

## <a name="example"></a>範例

下列範例會產生 C4677。

```
// C4677.cpp
// compile with: /clr /c /W1
delegate void TestDel();
public delegate void TestDel2();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;   // C4677
   static event TestDel2^ MyClass_Event2;   // OK
};
```