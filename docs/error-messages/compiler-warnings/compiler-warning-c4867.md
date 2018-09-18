---
title: 編譯器警告 C4867 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4867
dev_langs:
- C++
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b444156ae87e43b068521a3ad6687abe71df293f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074314"
---
# <a name="compiler-warning-c4867"></a>編譯器警告 C4867

'function': 函式呼叫遺漏引數清單;使用 'call' 建立成員的指標

成員函式的指標未正確初始化。

針對 Visual c + + 2005年所進行的編譯器一致性工作可能會導致此警告： 增強的指標對成員一致性。  Visual c + + 2005年之前編譯的程式碼現在會產生 C4867。

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