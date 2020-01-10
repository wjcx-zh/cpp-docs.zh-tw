---
title: 編譯器警告 C4867
ms.date: 11/04/2016
f1_keywords:
- C4867
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
ms.openlocfilehash: e093d262bc26cf0acfbb181d621fffc1aa391ee9
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626595"
---
# <a name="compiler-warning-c4867"></a>編譯器警告 C4867

' function '：函式呼叫遺漏引數清單;使用「呼叫」來建立成員的指標

成員函式的指標初始化不正確。

這項警告可能會因為針對 Visual Studio 2005 而進行的編譯器一致性工作所產生：增強的成員一致性。  在 Visual Studio 2005 之前編譯的程式碼現在會產生 C4867。

此警告一律會發出為錯誤。 請使用 [warning](../../preprocessor/warning.md) pragma 來停用這個警告。 如需 C4867 和 MFC/ATL 的詳細資訊，請參閱[_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning)。

## <a name="example"></a>範例

下列範例會產生 C4867。

```cpp
// C4867.cpp
// compile with: /c
class A {
public:
   void f(int) {}

   typedef void (A::*TAmtd)(int);

   struct B {
      TAmtd p;
   };

   void g() {
      B b = {f};   // C4867
      B b2 = {&A::f};   // OK
   }
};
```