---
title: "編譯器警告 C4972 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4972
dev_langs:
- C++
helpviewer_keywords:
- C4972
ms.assetid: d18e8e65-b2ef-4d75-a207-fbd0c17c9060
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: a0ac41ed06c30600c4189dbcca3af4da3dfa595f
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-warning-c4972"></a>編譯器警告 C4972
直接修改或將 Unbox 作業的結果視為左值，將無法驗證  
  
 對實值類型的控制代碼取值 (也稱為 Unboxing)，然後指派給它，這個作業無法驗證。  
  
 如需詳細資訊，請參閱[Boxing](../../windows/boxing-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4972。  
  
```  
// C4972.cpp  
// compile with: /clr:safe  
using namespace System;  
ref struct R {  
   int ^ p;   // a value type  
};  
  
int main() {  
   R ^ r = gcnew R;  
   *(r->p) = 10;   // C4972  
  
   // OK  
   r->p = 10;  
   Console::WriteLine( r->p );  
   Console::WriteLine( *(r->p) );  
}  
```
