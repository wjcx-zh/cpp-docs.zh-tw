---
title: "編譯器警告 C4867 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
translationtype: Machine Translation
ms.sourcegitcommit: 84964b0a49b236bae056125de8155b18880eb378
ms.openlocfilehash: 86437fca7bfeef662bef9fe8311fb746a661264d
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-c4867"></a>編譯器警告 C4867
'function': 函式呼叫遺漏引數清單。使用 '呼叫' 建立成員的指標  
  
 成員函式的指標未正確初始化。  
  
 Visual c + + 2005 所完成之編譯器一致性處理，可以產生這個警告︰ 增強的成員指標一致性。  編譯 Visual c + + 2005年之前的程式碼現在會產生 C4867。  
  
 為錯誤一律發出這個警告。 使用[警告](../../preprocessor/warning.md)pragma 來停用這個警告。 如需 C4867 和 MFC/ATL 的詳細資訊，請參閱[_ATL_ENABLE_PTM_WARNING](http://msdn.microsoft.com/Library/00b9ff5c-9834-4c40-911e-ee88d512c4af)。  
  
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
