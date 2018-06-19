---
title: 編譯器錯誤 C3228 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3228
dev_langs:
- C++
helpviewer_keywords:
- C3228
ms.assetid: 9015adf9-17b0-4312-b4a7-c1f33e4126f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c949aef15e9049f47b68094ae89b297bee1fc700
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248992"
---
# <a name="compiler-error-c3228"></a>編譯器錯誤 C3228
'function': 'param' 的泛型類型引數不可為 'type'，它必須是實值類型或控制代碼類型  
  
 傳遞了不正確的類型作為泛型類型引數。  
  
 下列範例會產生 C3228：  
  
```  
// C3228.cpp  
// compile with: /clr  
class A {};  
  
value class B {};  
  
generic <class T>  
void Test() {}  
  
ref class C {  
public:  
   generic <class T>  
   static void f() {}  
};  
  
int main() {  
   C::f<A>();   // C3228  
   C::f<B>();   // OK  
  
   Test<C>();   // C3228  
   Test<C ^>();   // OK  
}  
```