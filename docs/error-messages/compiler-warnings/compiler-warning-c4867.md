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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a412080d05e570711fcc65926459f9d2fcc45ed3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4867"></a>編譯器警告 C4867
'function': 函式呼叫遺漏引數清單。使用 '呼叫' 建立成員的指標  
  
 成員函式的指標未正確初始化。  
  
 針對 Visual c + + 2005年所進行的編譯器一致性工作可能會產生這個警告： 增強的指標對成員一致性。  Visual c + + 2005年之前編譯的程式碼現在會產生 C4867。  
  
 為錯誤，永遠會發出這個警告。 請使用 [warning](../../preprocessor/warning.md) pragma 來停用這個警告。 如需 C4867 和 MFC/ATL 的詳細資訊，請參閱[_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning)。  
  
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