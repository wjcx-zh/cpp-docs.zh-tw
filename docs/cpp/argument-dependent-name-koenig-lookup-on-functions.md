---
title: 函式上的引數相依名稱 (Koenig) 查閱 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d1977948eae8844b1b8c44310141abaab33b940
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409363"
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>函式上的引數相依名稱 (Koenig) 查閱
編譯器可以使用與引數相關的名稱查閱來尋找不合格的函式呼叫的定義。 與引數相關的名稱查閱也稱為 Koenig 查閱。 函式呼叫中每個引數的類型都是在命名空間、類別、結構、等位或範本階層內定義。 當您指定不合格[後置](../cpp/postfix-expressions.md)函式呼叫，編譯器會搜尋每個引數型別相關聯的階層中的函式定義。  
  
## <a name="example"></a>範例  
 在這個範例中，編譯器會注意到 `f()` 函式接受 `x` 引數。 引數 `x` 的類型是 `A::X`，而該類型是在命名空間 `A` 中定義的。 編譯器會搜尋命名空間 `A` 並尋找 `f()` 函式的定義，且此定義接受類型為 `A::X` 的引數。  
  
```cpp 
// argument_dependent_name_koenig_lookup_on_functions.cpp  
namespace A  
{  
   struct X  
   {  
   };  
   void f(const X&)  
   {  
   }  
}  
int main()  
{  
// The compiler finds A::f() in namespace A, which is where   
// the type of argument x is defined. The type of x is A::X.  
   A::X x;  
   f(x);     
}  
```  