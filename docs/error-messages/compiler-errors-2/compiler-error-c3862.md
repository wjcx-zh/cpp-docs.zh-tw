---
title: "編譯器錯誤 C3862 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3862
dev_langs:
- C++
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 63fa12348ee2ab58782fad02719918bfe7929ff8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3862"></a>編譯器錯誤 C3862
'function': 無法編譯 unmanaged 函式以 /clr: pure 或 /clr: safe  
  
 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
 編譯**/clr: pure**或**/clr: safe**會產生 MSIL 僅映像，沒有原生 (unmanaged) 程式碼的映像。  因此，您無法使用`unmanaged`pragma 中的**/clr: pure**或**/clr: safe**編譯。  
  
 如需詳細資訊，請參閱[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)和[managed、 unmanaged](../../preprocessor/managed-unmanaged.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3862:  
  
```  
// C3862.cpp  
// compile with: /clr:pure /c  
#pragma unmanaged  
void f() {}   // C3862  
```