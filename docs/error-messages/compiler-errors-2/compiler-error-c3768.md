---
title: 編譯器錯誤 C3768 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3768
dev_langs:
- C++
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3634ecf3eb1417095cce144706838113b5ad2a0e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3768"></a>編譯器錯誤 C3768
無法取得純 managed 程式碼中的虛擬 vararg 函式的位址  
  
 **/Clr: pure** Visual Studio 2015 中的編譯器選項已被取代。  
  
 編譯時`/clr:pure`，您無法取得虛擬機器的位址`vararg`函式。  
  
## <a name="example"></a>範例  

 下列範例會產生 C3768:  
  
```  
// C3768.cpp  
// compile with: /clr:pure  
struct A  
{  
   virtual void f(...);  
};  
  
int main()  
{  
   &(A::f);   // C3768  
}  
```