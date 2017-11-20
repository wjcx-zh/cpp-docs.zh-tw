---
title: "編譯器警告 （層級 4） C4668 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4668
dev_langs: C++
helpviewer_keywords: C4668
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 059bf2dcb2d854ad05d21a9314d0d6a3f2a7a432
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4668"></a>編譯器警告 (層級 4) C4668
'symbol' 未定義成前置處理器巨集，以 '0' 取代 'directives'  
  
 前置處理器指示詞搭配使用未定義的符號。 符號會評估為 false。 若要定義符號，您可以使用[#define 指示詞](../../preprocessor/hash-define-directive-c-cpp.md)或[/D](../../build/reference/d-preprocessor-definitions.md)編譯器選項。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4668:  
  
```  
// C4668.cpp  
// compile with: /W4  
#include <stdio.h>  
  
#pragma warning (default : 4668)   // turn warning on  
  
int main()   
{  
    #if q   // C4668, q is not defined  
        printf_s("defined");  
    #else  
        printf_s("undefined");  
    #endif  
}  
```