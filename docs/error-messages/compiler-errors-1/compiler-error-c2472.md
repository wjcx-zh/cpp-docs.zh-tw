---
title: 編譯器錯誤 C2472 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2472
dev_langs:
- C++
helpviewer_keywords:
- C2472
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d89a6d6b10fa76c7fbf1bf11c4ebe2ecff5f98ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2472"></a>編譯器錯誤 C2472
'function' 無法在 Managed 程式碼中產生: 'message'，請以 /clr 編譯以便產生混合影像  
  
 在純粹 Common Language Runtime (CLR) 環境內使用 Managed 程式碼不支援的類型時，會發生這個錯誤。 請使用 **/clr** 進行編譯，來解決這個錯誤。  
  
 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
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
 [/clr (通用語言執行平台編譯)](../../build/reference/clr-common-language-runtime-compilation.md)