---
title: "編譯器警告 （層級 1） C4461 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4461
dev_langs: C++
helpviewer_keywords: C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cc417e7044eb3eac12365676c6c1be9abeddfed0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4461"></a>編譯器警告 (層級 1) C4461
'type': 此類別具有完成項 'finalizer'，但沒有解構函式 'dtor'  
  
 出現型別中的完成項的暗示若要刪除的資源。 除非從類型的解構函式明確地呼叫完成項，common language runtime 會決定何時執行完成項之後您物件超出範圍。  
  
 如果您在類型中定義的解構函式，並明確呼叫解構函式的完成項，您可以確定的方式執行完成項。  
  
 如需詳細資訊，請參閱[解構函式與完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4461。  
  
```  
// C4461.cpp  
// compile with: /W1 /clr /c  
ref class A {  
protected:  
   !A() {}   // C4461  
};  
  
// OK  
ref struct B {  
   ~B() {  
      B::!B();  
   }  
  
   !B() {}  
};  
```