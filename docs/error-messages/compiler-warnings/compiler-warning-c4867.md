---
title: 編譯器警告 C4867
ms.date: 11/04/2016
f1_keywords:
- C4867
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
ms.openlocfilehash: 0fd5de46f713aed08508f8755c9e54c3ff46366b
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447200"
---
# <a name="compiler-warning-c4867"></a>編譯器警告 C4867

'function': 函式呼叫遺漏引數清單;使用 'call' 建立成員的指標

成員函式的指標未正確初始化。

針對 Visual Studio 2005 所進行的編譯器一致性工作可能會導致此警告： 增強的指標對成員一致性。  Visual Studio 2005 之前編譯的程式碼現在會產生 C4867。

為錯誤，永遠會發出這個警告。 請使用 [warning](../../preprocessor/warning.md) pragma 來停用這個警告。 如需 C4867 和 MFC/ATL 的詳細資訊，請參閱 < [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning)。

## <a name="example"></a>範例

下列範例會產生 C4867。

```
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