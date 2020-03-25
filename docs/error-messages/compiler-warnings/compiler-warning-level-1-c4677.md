---
title: 編譯器警告 (層級 1) C4677
ms.date: 11/04/2016
f1_keywords:
- C4677
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
ms.openlocfilehash: 5b31fd22c917b2c0f505ca189425f8160f62f748
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175541"
---
# <a name="compiler-warning-level-1-c4677"></a>編譯器警告 (層級 1) C4677

' function '：非私用成員的簽章包含元件私用類型 ' private_type '

在元件外部具有公用存取範圍的類型，會使用在元件外部具有私用存取的類型。 參考公用元件類型的元件將無法使用類型成員或參考元件私用類型的成員。

## <a name="example"></a>範例

下列範例會產生 C4677。

```cpp
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
