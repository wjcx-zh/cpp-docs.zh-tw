---
title: "編譯器錯誤 C2472 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2472
dev_langs:
- C++
helpviewer_keywords:
- C2472
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 058e05e851aed1a31e8f59edcb75c034e186ddaf
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2472"></a>編譯器錯誤 C2472
'function' 無法在 Managed 程式碼中產生: 'message'，請以 /clr 編譯以便產生混合影像  
  
 在純粹 Common Language Runtime (CLR) 環境內使用 Managed 程式碼不支援的類型時，會發生這個錯誤。 請使用 **/clr** 進行編譯，來解決這個錯誤。  
  
 **/Clr: pure**和**/clr: safe** Visual Studio 2015 中的編譯器選項已被取代。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2472。  
  
```  
// C2472.cpp  
// compile with: /clr:pure  
// C2472 expected  
  
#include <cstdlib>  
  
int main()  
{  
   int * __ptr32 p32;  
   int * __ptr64 p64;  
  
   p32 = (int * __ptr32)malloc(4);  
   p64 = p32;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [/clr （common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)
