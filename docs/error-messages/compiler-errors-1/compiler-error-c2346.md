---
title: "編譯器錯誤 C2346 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2346
dev_langs:
- C++
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: bf0133aba65b8477bd949cd90b51edbd407bcda7
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2346"></a>編譯器錯誤 C2346
'function' 無法編譯為原生： 原因  
  
 編譯器無法編譯為 MSIL 函式。  
  
 如需詳細資訊，請參閱[managed、 unmanaged](../../preprocessor/managed-unmanaged.md)和[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  無法編譯為 MSIL 函式中移除的程式碼。  
  
2.  可能不會編譯之模組的**/clr**，或將標記為使用未受管理的 pragma unmanaged 函式。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2346。  
  
```  
// C2346.cpp  
// processor: x86  
// compile with: /clr   
// C2346 expected  
struct S  
{  
   S()  
   {  
      { __asm { nop } }  
   }  
   virtual __clrcall ~S() { }  
};  
  
void main()  
{  
   S s;  
}  
```
