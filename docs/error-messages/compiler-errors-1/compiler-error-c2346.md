---
title: 編譯器錯誤 C2346 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2346
dev_langs:
- C++
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9459d7330738180e92776e93fcba9a07bfd39640
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222289"
---
# <a name="compiler-error-c2346"></a>編譯器錯誤 C2346
'function' 無法編譯為原生： 原因  
  
 編譯器無法編譯為 MSIL 函式。  
  
 如需詳細資訊，請參閱[managed、 unmanaged](../../preprocessor/managed-unmanaged.md)和[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  無法編譯為 MSIL 函式中移除的程式碼。  
  
2.  可能不會編譯之模組的 **/clr**，或將標記為使用未受管理的 pragma unmanaged 函式。  
  
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