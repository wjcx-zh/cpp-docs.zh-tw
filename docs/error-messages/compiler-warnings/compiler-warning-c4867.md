---
title: "編譯器警告 C4867 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4867
dev_langs:
- C++
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: bb94e24657d16b2a3eda3a770c2b6ae734c6006f
ms.openlocfilehash: a052194893db90177b88eea8f80435777ae37773
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-c4867"></a>編譯器警告 C4867
'function': 函式呼叫遺漏引數清單。使用 '呼叫' 建立成員的指標  
  
 成員函式的指標未正確初始化。  
  
 針對 Visual c + + 2005年所進行的編譯器一致性工作可能會產生這個警告︰ 增強的指標對成員一致性。  Visual c + + 2005年之前編譯的程式碼現在會產生 C4867。  
  
 為錯誤，永遠會發出這個警告。 使用[警告](../../preprocessor/warning.md)pragma 來停用這個警告。 如需 C4867 和 MFC/ATL 的詳細資訊，請參閱[_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning)。  
  
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
